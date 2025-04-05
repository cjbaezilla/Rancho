# Consultas Útiles

Esta sección proporciona consultas SQL listas para usar en el sistema "Rancho", organizadas por categoría y caso de uso.

## Estructura de Consultas

Las consultas están organizadas en las siguientes categorías:

- [Consultas Operativas](./consultas_operativas.md): Consultas para operaciones diarias del taller
- [Consultas para Reportes](./consultas_reportes.md): Consultas para generación de informes periódicos
- [Consultas para Alertas](./consultas_alertas.md): Consultas para detectar situaciones que requieren atención

Cada consulta incluye:
- Título descriptivo
- Objetivo de la consulta
- Código SQL completo
- Descripción de los parámetros (si aplica)
- Ejemplo de resultados esperados

## Consultas Generales Multifuncionales

A continuación se presentan algunas consultas generales que pueden ser útiles en diversos contextos:

### Búsqueda de Equipos por Cliente

```sql
SELECT e.id_equipo, e.numero_serie, te.nombre AS tipo_equipo, 
       e.hectareas_trabajadas, e.estado_actual, e.ultima_actualizacion_hectareas
FROM equipos e
JOIN tipo_equipos te ON e.id_tipo_equipo = te.id_tipo_equipo
WHERE e.id_cliente = ? -- Reemplazar con ID del cliente
ORDER BY e.fecha_entrega_real DESC;
```

### Estado de Mantenciones Programadas

```sql
SELECT mp.id_mantencion_programada, e.numero_serie, te.nombre AS tipo_equipo,
       tm.nombre AS tipo_mantencion, mp.fecha_programada, mp.estado,
       c.nombre AS cliente
FROM mantenciones_programadas mp
JOIN equipos e ON mp.id_equipo = e.id_equipo
JOIN tipo_equipos te ON e.id_tipo_equipo = te.id_tipo_equipo
JOIN tipo_mantencion tm ON mp.id_tipo_mantencion = tm.id_tipo_mantencion
JOIN clientes c ON e.id_cliente = c.id_cliente
WHERE mp.estado = 'pendiente' -- Filtrar por pendientes o modificar según necesidad
ORDER BY mp.fecha_programada ASC;
```

### Historial de Fallas por Equipo

```sql
SELECT rf.id_falla, rf.fecha_deteccion, rf.descripcion_falla, 
       rf.componente_afectado, rf.causa_probable, rf.solucion_aplicada,
       rf.tiempo_reparacion, rf.dentro_garantia, t.nombre AS tecnico,
       rf.es_reincidente
FROM registros_fallas rf
JOIN ordenes_trabajo ot ON rf.id_orden = ot.id_orden
JOIN tecnicos t ON ot.id_tecnico = t.id_tecnico
WHERE rf.id_equipo = ? -- Reemplazar con ID del equipo
ORDER BY rf.fecha_deteccion DESC;
```

### Inventario de Repuestos Críticos

```sql
SELECT r.id_repuesto, r.codigo, r.nombre, r.stock_actual, r.stock_minimo,
       r.precio_venta, cr.nombre AS categoria,
       COUNT(DISTINCT comp.id_tipo_equipo) AS compatible_con_tipos
FROM repuestos r
JOIN categorias_repuestos cr ON r.id_categoria = cr.id_categoria
LEFT JOIN compatibilidad_repuestos comp ON r.id_repuesto = comp.id_repuesto
WHERE r.stock_actual <= r.stock_minimo
GROUP BY r.id_repuesto
ORDER BY (r.stock_minimo - r.stock_actual) DESC, r.nombre;
```

### Indicadores de Satisfacción de Cliente

```sql
SELECT c.id_cliente, c.nombre, 
       AVG(es.puntuacion_general) AS satisfaccion_promedio,
       COUNT(es.id_encuesta) AS total_encuestas,
       SUM(CASE WHEN es.nps = 1 THEN 1 ELSE 0 END) AS promotores,
       SUM(CASE WHEN es.nps = 0 THEN 1 ELSE 0 END) AS pasivos,
       SUM(CASE WHEN es.nps = -1 THEN 1 ELSE 0 END) AS detractores,
       ROUND(((SUM(CASE WHEN es.nps = 1 THEN 1 ELSE 0 END) - 
               SUM(CASE WHEN es.nps = -1 THEN 1 ELSE 0 END)) / 
              COUNT(es.id_encuesta)) * 100, 2) AS indice_nps
FROM clientes c
LEFT JOIN encuestas_satisfaccion es ON c.id_cliente = es.id_cliente
WHERE es.fecha BETWEEN ? AND ? -- Reemplazar con rango de fechas
GROUP BY c.id_cliente
HAVING COUNT(es.id_encuesta) > 0
ORDER BY indice_nps DESC;
```

## Consideraciones de Rendimiento

- Las consultas incluidas están optimizadas para rendimiento, pero pueden requerir ajustes según el volumen de datos.
- Para grandes conjuntos de datos, considere agregar límites (LIMIT) o filtrar por fechas recientes.
- Utilice índices adicionales si observa consultas lentas en tablas específicas.

## Ejemplos de Parámetros

Cuando vea un signo de interrogación (?) en una consulta, reemplácelo con el valor correspondiente:

```sql
-- Ejemplo: Buscar equipos del cliente con ID 3
SELECT e.id_equipo, e.numero_serie, te.nombre AS tipo_equipo 
FROM equipos e
JOIN tipo_equipos te ON e.id_tipo_equipo = te.id_tipo_equipo
WHERE e.id_cliente = 3
ORDER BY e.fecha_entrega_real DESC;
``` 