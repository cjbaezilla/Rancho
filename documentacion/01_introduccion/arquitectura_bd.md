# Arquitectura de la Base de Datos

## Visión General de la Base de Datos

La base de datos "Rancho" ha sido diseñada siguiendo un modelo relacional que permite gestionar de manera eficiente y coherente toda la información relacionada con un taller mecánico especializado en maquinaria agrícola. Su estructura está orientada a mantener la integridad de los datos, facilitar consultas complejas y permitir un escalamiento futuro conforme crezcan las necesidades del negocio.

## Características Principales

- **Sistema Gestor**: MySQL/MariaDB
- **Conjunto de Caracteres**: utf8mb4 (soporte completo para caracteres especiales y emojis)
- **Colación**: utf8mb4_spanish_ci (ordenamiento específico para idioma español)
- **Modelo**: Relacional normalizado
- **Esquema**: Rancho

## Categorías de Tablas

La base de datos está organizada en varias categorías de tablas, cada una con un propósito específico dentro del sistema:

### 1. Tablas Maestras (Entidades Principales)
Almacenan información fundamental sobre las entidades primarias del negocio.
- `clientes`
- `equipos`
- `tipo_equipos`
- `tecnicos`
- `repuestos`
- `categorias_repuestos`

### 2. Tablas de Transacciones
Registran las operaciones diarias del taller.
- `ordenes_trabajo`
- `solicitudes_mantencion`
- `mantenciones_programadas`
- `pedidos_repuestos`
- `embarques`

### 3. Tablas de Detalle
Contienen información detallada asociada a las transacciones principales.
- `detalle_repuestos_orden`
- `detalle_pedidos_repuestos`
- `detalle_embarques`

### 4. Tablas de Relaciones
Establecen relaciones muchos a muchos entre entidades.
- `compatibilidad_repuestos`

### 5. Tablas de Historial y Registro
Mantienen un registro histórico de cambios y eventos.
- `historial_hectareas`
- `historial_estados_equipo`
- `registros_fallas`
- `interacciones_cliente`
- `auditoria_cambios`

### 6. Tablas de Métricas y KPIs
Almacenan indicadores de desempeño calculados para análisis.
- `metricas_kpi_logistica`
- `metricas_kpi_mantencion`
- `historico_fallas_equipo`
- `tiempos_entrega_repuestos`
- `ranking_repuestos_demandados`
- `metricas_clientes`
- `kpi_margenes`
- `satisfaccion_postventa`

### 7. Tablas de Configuración y Apoyo
Contienen información de configuración y soporte.
- `tipo_mantencion`
- `programacion_mantencion`
- `notificaciones`

## Relaciones Clave

La estructura relacional del esquema se basa en varias relaciones fundamentales:

1. **Cliente-Equipo**: Un cliente puede tener múltiples equipos, pero cada equipo pertenece a un único cliente (cuando está vendido).

2. **Equipo-TipoEquipo**: Cada equipo pertenece a un tipo específico que determina sus características, garantía y programación de mantenciones.

3. **Equipo-Mantenciones**: Un equipo tiene múltiples mantenciones programadas y solicitudes de mantención a lo largo de su vida útil.

4. **Orden-Técnico**: Cada orden de trabajo es asignada a un técnico específico responsable de su ejecución.

5. **Repuesto-Equipos**: Los repuestos tienen relaciones de compatibilidad con diferentes tipos de equipos.

6. **Registro de Hectáreas**: Los equipos tienen un seguimiento de las hectáreas trabajadas a través del tiempo.

## Integridad Referencial

La base de datos implementa restricciones de integridad referencial mediante claves foráneas (FOREIGN KEY) que garantizan la coherencia de los datos. Algunas políticas importantes incluyen:

- **ON DELETE RESTRICT**: Para relaciones críticas donde no debe permitirse la eliminación de registros padre si existen hijos dependientes.
- **ON DELETE CASCADE**: Para relaciones donde la eliminación del registro padre debe provocar la eliminación automática de los registros hijos.
- **ON UPDATE CASCADE**: Para asegurar que las actualizaciones de claves primarias se propaguen a todas las referencias.

## Campos Calculados

El esquema utiliza columnas generadas (GENERATED ALWAYS AS) para calcular automáticamente valores derivados, reduciendo la necesidad de cálculos en la aplicación y asegurando la consistencia. Ejemplos incluyen:

- Cálculo de subtotales en órdenes y pedidos
- Cálculo de márgenes y porcentajes
- Determinación de valores NPS en encuestas de satisfacción
- Hectáreas incrementadas en cada actualización

## Tipos de Datos

La selección de tipos de datos ha sido optimizada para cada columna:

- **INT UNSIGNED**: Para identificadores y contadores
- **DECIMAL(10,2)**: Para valores monetarios y medidas precisas
- **VARCHAR**: Para textos de longitud variable con límite conocido
- **TEXT**: Para contenido extenso sin límite predefinido
- **DATE/DATETIME**: Para registro preciso de fechas y horas
- **ENUM**: Para campos con valores predefinidos y limitados
- **BOOLEAN**: Para indicadores de tipo sí/no

## Índices y Optimización

Se han definido índices estratégicos para optimizar las consultas más frecuentes:

- **Índices Primarios**: En todas las tablas (PRIMARY KEY)
- **Índices Únicos**: Para campos que requieren unicidad (UNIQUE INDEX)
- **Índices de Búsqueda**: Para campos frecuentemente utilizados en filtros y búsquedas

## Diagrama Entidad-Relación

Para una visualización completa de las relaciones entre tablas, consulte el diagrama entidad-relación en el siguiente enlace:
[Diagrama ER de Rancho](../recursos/diagrama_er.png)

## Consideraciones de Escalabilidad

El diseño de la base de datos contempla el crecimiento futuro mediante:

- Separación clara de conceptos en tablas específicas
- Uso de identificadores numéricos autoincremenetales (AUTO_INCREMENT)
- Normalización adecuada para minimizar redundancia
- Campos para auditoría y seguimiento temporal

Esta arquitectura proporciona una base sólida para el sistema de gestión, permitiendo almacenar y recuperar eficientemente toda la información necesaria para la operación del taller y la toma de decisiones estratégicas. 