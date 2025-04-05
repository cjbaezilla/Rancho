# Diccionario de Datos

Este diccionario proporciona información detallada sobre la estructura de la base de datos del sistema "Rancho" para la gestión de talleres mecánicos especializados en maquinaria agrícola.

## Estructura de la Base de Datos

La base de datos "rancho" está diseñada siguiendo el modelo relacional y organizada en torno a las siguientes áreas funcionales:

1. **Gestión de Clientes y Equipos**: Registro de clientes y sus equipos agrícolas
2. **Gestión de Mantenciones**: Programación y seguimiento de mantenciones preventivas y correctivas
3. **Gestión de Repuestos**: Inventario, compatibilidad y uso de repuestos
4. **Logística y Embarques**: Seguimiento de equipos desde origen hasta entrega
5. **Servicio Postventa**: Interacciones con clientes y satisfacción
6. **Métricas e Indicadores**: Tablas para cálculo y almacenamiento de KPIs

## Categorías de Tablas

Para facilitar la comprensión, las tablas se han clasificado en:

- [Tablas Principales](./tablas_principales.md): Entidades fundamentales del sistema
- [Tablas de Relaciones](./tablas_relaciones.md): Relaciones muchos a muchos entre entidades
- [Tablas de Históricos](./tablas_historicos.md): Registros históricos y trazabilidad
- [Tablas de Métricas](./tablas_metricas.md): Almacenamiento de métricas calculadas

## Convenciones de Nombrado

- **Nombres de tablas**: En plural y minúsculas (ej. `clientes`, `equipos`)
- **Claves primarias**: Prefijo `id_` seguido del nombre de la entidad en singular (ej. `id_cliente`)
- **Claves foráneas**: Mismo nombre que la clave primaria a la que hacen referencia
- **Campos booleanos**: Nombres que indican estado o condición (ej. `activo`, `es_reincidente`)
- **Campos de fecha/tiempo**: Prefijo `fecha_` para fechas específicas (ej. `fecha_creacion`)
- **Campos calculados**: Se generan automáticamente y se almacenan (ej. `subtotal`, `porcentaje_margen`)

## Tipos de Datos Comunes

- **INT UNSIGNED**: Para identificadores y contadores
- **VARCHAR**: Para texto de longitud variable (nombres, códigos, etc.)
- **TEXT**: Para descripciones y notas extensas
- **DECIMAL(10,2)**: Para valores monetarios y métricas con dos decimales
- **DATE/DATETIME**: Para fechas y momentos específicos
- **ENUM**: Para valores predefinidos (estados, tipos, etc.)
- **BOOLEAN**: Para valores verdadero/falso

## Cardinalidad y Relaciones

Las relaciones entre tablas siguen estos patrones:

- **Uno a Muchos (1:N)**: La mayoría de las relaciones (ej. un cliente puede tener muchos equipos)
- **Muchos a Muchos (N:M)**: Implementadas mediante tablas intermedias (ej. compatibilidad de repuestos)
- **Uno a Uno (1:1)**: Para extensiones de entidades (ej. métricas específicas por entidad)

## Índices y Optimización

La base de datos utiliza índices para optimizar consultas frecuentes:

- **Índices primarios**: En todas las claves primarias
- **Índices únicos**: Para campos que requieren unicidad (ej. RUT, número de serie)
- **Índices de búsqueda**: En claves foráneas y campos frecuentemente consultados

## Actualizaciones y Crecimiento

Este diccionario se actualizará cuando se realicen cambios en la estructura de la base de datos. Las versiones anteriores se archivarán para referencia histórica. 