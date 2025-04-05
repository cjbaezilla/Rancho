# KPIs de Mantenciones

## Descripción General

Los Indicadores Clave de Desempeño (KPIs) del área de Mantenciones están diseñados para medir la eficiencia, efectividad y calidad de todos los procesos relacionados con el mantenimiento preventivo y correctivo de los equipos agrícolas. Estos indicadores son fundamentales para optimizar la disponibilidad de la maquinaria, reducir costos operativos y garantizar la satisfacción del cliente.

## Indicadores Principales

### 1. Tiempo Medio Entre Fallas (MTBF)

**Definición:** Mide el tiempo promedio operativo entre fallas de un equipo, indicando su confiabilidad.

**Fórmula:** 
```sql
MTBF = SUM(Tiempo total operativo) / Número de fallas
```

**Unidad:** Horas o días

**Fuentes de datos:** 
- Tabla `historico_fallas_equipo`
- Tabla `equipos` (campo `hectareas_trabajadas`)

**Meta objetivo:** Incremento anual del 15%

**Visualización recomendada:** Gráfico de tendencia por modelo de equipo y por cliente

### 2. Tiempo Medio de Reparación (MTTR)

**Definición:** Mide el tiempo promedio requerido para completar una reparación desde el momento del reporte.

**Fórmula:** 
```sql
MTTR = SUM(tiempo_finalizacion - tiempo_inicio) / COUNT(id_solicitud)
```

**Unidad:** Horas

**Fuentes de datos:** 
- Tabla `solicitudes_mantencion`
- Tabla `ordenes_trabajo`

**Meta objetivo:** Reducción trimestral del 5%

**Visualización recomendada:** Gráfico comparativo por tipo de falla y técnico asignado

### 3. Tasa de Cumplimiento de Mantenciones Preventivas

**Definición:** Porcentaje de mantenciones preventivas completadas según lo programado.

**Fórmula:** 
```sql
Tasa = (Mantenciones preventivas realizadas a tiempo / Mantenciones preventivas programadas) * 100
```

**Unidad:** Porcentaje

**Fuentes de datos:** 
- Tabla `mantenciones_programadas`
- Tabla `programacion_mantencion`

**Meta objetivo:** >95%

**Visualización recomendada:** Gráfico de barras mensual con línea de meta

### 4. Efectividad de Mantención Preventiva

**Definición:** Mide la capacidad de las mantenciones preventivas para evitar fallas.

**Fórmula:** 
```sql
Efectividad = (1 - (Número de fallas entre mantenciones / Total de equipos mantenidos)) * 100
```

**Unidad:** Porcentaje

**Fuentes de datos:** 
- Tabla `registros_fallas`
- Tabla `mantenciones_programadas`

**Meta objetivo:** >90%

**Visualización recomendada:** Gráfico de tendencia por tipo de mantención

### 5. Tasa de Reincidencia de Fallas

**Definición:** Porcentaje de equipos que presentan la misma falla dentro de los 30 días posteriores a una reparación.

**Fórmula:** 
```sql
Tasa = (Número de reincidencias / Total de reparaciones) * 100
```

**Unidad:** Porcentaje

**Fuentes de datos:** 
- Tabla `registros_fallas`
- Tabla `ordenes_trabajo`

**Meta objetivo:** <5%

**Visualización recomendada:** Gráfico de Pareto por tipo de falla

### 6. Precisión de Estimación de Tiempo

**Definición:** Mide la precisión de las estimaciones de tiempo para completar mantenciones.

**Fórmula:** 
```sql
Precisión = (1 - ABS(Horas reales - Horas estimadas) / Horas estimadas) * 100
```

**Unidad:** Porcentaje

**Fuentes de datos:** 
- Tabla `mantenciones_programadas` (campos `horas_estimadas` y `horas_reales`)
- Tabla `ordenes_trabajo`

**Meta objetivo:** >85%

**Visualización recomendada:** Gráfico de dispersión (estimado vs. real)

### 7. Costo por Hectárea de Mantención

**Definición:** Costo promedio de mantención por hectárea trabajada por los equipos.

**Fórmula:** 
```sql
Costo/Hectárea = SUM(Costo total mantenciones) / SUM(Hectáreas trabajadas)
```

**Unidad:** Pesos/Hectárea

**Fuentes de datos:** 
- Tabla `mantenciones_programadas` (campo `costo_real`)
- Tabla `ordenes_trabajo`
- Tabla `historial_hectareas`

**Meta objetivo:** Reducción anual del 5-10%

**Visualización recomendada:** Gráfico de tendencia por modelo de equipo

### 8. Índice de Disponibilidad de Equipos

**Definición:** Porcentaje del tiempo total en que los equipos están disponibles para operación.

**Fórmula:** 
```sql
Disponibilidad = ((Tiempo total - Tiempo en mantención) / Tiempo total) * 100
```

**Unidad:** Porcentaje

**Fuentes de datos:** 
- Tabla `historial_estados_equipo`
- Tabla `ordenes_trabajo`

**Meta objetivo:** >98%

**Visualización recomendada:** Mapa de calor por equipo y mes

## Métricas de Proceso

### 1. Tiempo de Respuesta a Solicitudes

**Definición:** Tiempo promedio entre la recepción de una solicitud y el inicio de la atención.

**Fórmula:** 
```sql
Tiempo = AVG(fecha_asignacion - fecha_solicitud)
```

**Unidad:** Horas

**Fuentes de datos:** 
- Tabla `solicitudes_mantencion`

**Meta objetivo:** <4 horas para prioridad alta, <24 horas para prioridad media

**Visualización recomendada:** Gráfico de barras por nivel de prioridad

### 2. Eficiencia en Uso de Repuestos

**Definición:** Relación entre el costo de repuestos y el costo total de la mantención.

**Fórmula:** 
```sql
Eficiencia = (Costo de repuestos / Costo total de mantención) * 100
```

**Unidad:** Porcentaje

**Fuentes de datos:** 
- Tabla `detalle_repuestos_orden`
- Tabla `ordenes_trabajo`

**Meta objetivo:** <50%

**Visualización recomendada:** Gráfico circular por tipo de mantención

### 3. Productividad Técnica

**Definición:** Número de órdenes de trabajo completadas por técnico por período.

**Fórmula:** 
```sql
Productividad = COUNT(id_orden) / COUNT(DISTINCT id_tecnico)
```

**Unidad:** Órdenes/técnico/período

**Fuentes de datos:** 
- Tabla `ordenes_trabajo`
- Tabla `tecnicos`

**Meta objetivo:** >4 órdenes/día para mantenciones estándar

**Visualización recomendada:** Ranking de técnicos por productividad

## Implementación en la Base de Datos

El sistema "Rancho" cuenta con la tabla `metricas_kpi_mantencion` para almacenar y procesar estos indicadores, con la siguiente estructura:

```sql
CREATE TABLE IF NOT EXISTS `metricas_kpi_mantencion` (
  `id_metrica` INT UNSIGNED NOT NULL AUTO_INCREMENT,
  `fecha_calculo` DATE NOT NULL,
  `periodo_inicio` DATE NOT NULL,
  `periodo_fin` DATE NOT NULL,
  `id_tipo_mantencion` INT UNSIGNED NULL,
  `id_equipo` INT UNSIGNED NULL,
  `id_cliente` INT UNSIGNED NULL,
  `mtbf_valor` DECIMAL(10,2) NULL,
  `mttr_valor` DECIMAL(10,2) NULL,
  `tasa_cumplimiento` DECIMAL(5,2) NULL,
  `efectividad_preventiva` DECIMAL(5,2) NULL,
  `tasa_reincidencia` DECIMAL(5,2) NULL,
  `precision_estimacion` DECIMAL(5,2) NULL,
  `costo_por_hectarea` DECIMAL(10,2) NULL,
  `disponibilidad` DECIMAL(5,2) NULL,
  `tiempo_respuesta` DECIMAL(10,2) NULL,
  `eficiencia_repuestos` DECIMAL(5,2) NULL,
  `productividad_tecnica` DECIMAL(5,2) NULL,
  PRIMARY KEY (`id_metrica`)
)
```

## Proceso de Actualización

Los KPIs de mantenciones se actualizan mediante un procedimiento almacenado programado para ejecutarse diariamente, calculando los valores para diferentes períodos:

1. Último día
2. Última semana
3. Último mes
4. Último trimestre
5. Último año

## Integración con Otros KPIs

Los KPIs de mantenciones se relacionan directamente con:

1. **KPIs de Logística**: Para medir el impacto de los tiempos de entrega de repuestos en la duración de mantenciones
2. **KPIs de Postventa**: Para correlacionar la efectividad de las mantenciones con la satisfacción del cliente
3. **KPIs de Trazabilidad**: Para evaluar la calidad del registro de información durante las mantenciones
4. **KPIs de Cliente y Negocio**: Para analizar el impacto financiero de las estrategias de mantención

## Análisis y Mejora Continua

El sistema proporciona herramientas para:

1. Identificar equipos con rendimiento por debajo del esperado
2. Detectar patrones de fallas recurrentes
3. Evaluar la eficiencia comparativa de diferentes técnicos
4. Optimizar la programación de mantenciones preventivas
5. Mejorar la precisión de estimaciones de tiempo y costo

Estas métricas son revisadas semanalmente por el equipo de gestión técnica, y mensualmente en reuniones de mejora continua con representantes de todas las áreas. 