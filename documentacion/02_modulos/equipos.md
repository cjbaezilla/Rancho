# Módulo de Gestión de Equipos

## Descripción General

El Módulo de Gestión de Equipos constituye el núcleo central del sistema "Rancho", permitiendo el seguimiento integral de las máquinas agrícolas a lo largo de todo su ciclo de vida. Este módulo abarca desde el registro inicial del equipo en la etapa de fabricación, su proceso de importación, armado, entrega al cliente, y finalmente el seguimiento de su operación a través del tiempo, incluyendo el control de hectáreas trabajadas, mantenciones realizadas e historial de fallas.

La gestión eficiente de equipos agrícolas de alta tecnología requiere un control minucioso debido a varios factores: su alto valor económico, la complejidad técnica, los requerimientos de mantenimiento específicos, y la necesidad de maximizar su disponibilidad durante los períodos críticos de operación agrícola.

## Objetivos del Módulo

- Proporcionar trazabilidad completa de cada equipo desde su fabricación hasta su operación
- Controlar el proceso de recepción, armado y entrega de equipos nuevos
- Registrar y monitorear el uso de los equipos mediante el control de hectáreas trabajadas
- Facilitar la programación y seguimiento de mantenciones preventivas
- Mantener un historial detallado de fallas y reparaciones
- Gestionar la información de garantía de cada equipo

## Estructura de Datos

El módulo se estructura principalmente en las siguientes tablas de la base de datos:

### 1. Tabla `tipo_equipos`

Define las categorías o modelos de equipos disponibles:

| Campo | Descripción |
|-------|-------------|
| id_tipo_equipo | Identificador único del tipo de equipo |
| nombre | Nombre del tipo/modelo de equipo |
| descripcion | Descripción detallada |
| fabricante | Fabricante del equipo |
| pais_origen | País de origen (por defecto 'Suecia') |
| tiempo_garantia_anios | Duración de la garantía en años |
| hectareas_garantia | Hectáreas cubiertas por garantía |
| tiempo_armado_estimado | Tiempo estimado de armado en días |

### 2. Tabla `equipos`

Almacena la información de cada equipo individual:

| Campo | Descripción |
|-------|-------------|
| id_equipo | Identificador único del equipo |
| id_tipo_equipo | Tipo de equipo relacionado |
| numero_serie | Número de serie único del equipo |
| fecha_fabricacion | Fecha de fabricación |
| fecha_salida_origen | Fecha de salida desde origen |
| fecha_llegada_taller | Fecha de llegada al taller |
| fecha_armado_completo | Fecha de finalización del armado |
| fecha_entrega_programada | Fecha programada para entrega |
| fecha_entrega_real | Fecha real de entrega al cliente |
| id_cliente | Cliente propietario (nulo si no está vendido) |
| estado_actual | Estado actual del equipo |
| hectareas_trabajadas | Total de hectáreas trabajadas |
| ultima_actualizacion_hectareas | Fecha de última actualización |
| notas | Observaciones adicionales |

### 3. Tabla `historial_hectareas`

Registra el historial de hectáreas trabajadas:

| Campo | Descripción |
|-------|-------------|
| id_historial | Identificador único del registro |
| id_equipo | Equipo relacionado |
| fecha_registro | Fecha del registro |
| hectareas_anteriores | Hectáreas acumuladas previas |
| hectareas_actuales | Hectáreas acumuladas actuales |
| hectareas_incremento | Hectáreas incrementadas (calculado) |
| notas | Observaciones adicionales |

### 4. Tabla `historial_estados_equipo`

Mantiene un registro de los cambios de estado:

| Campo | Descripción |
|-------|-------------|
| id_historial_estado | Identificador único del registro |
| id_equipo | Equipo relacionado |
| estado_anterior | Estado previo |
| estado_nuevo | Nuevo estado |
| fecha_cambio | Fecha y hora del cambio |
| usuario_cambio | Usuario que realizó el cambio |
| comentario | Observaciones adicionales |

### 5. Tabla `embarques` y `detalle_embarques`

Gestionan la información de embarques desde origen:

**Tabla `embarques`**
| Campo | Descripción |
|-------|-------------|
| id_embarque | Identificador único del embarque |
| codigo_embarque | Código único del embarque |
| fecha_salida_origen | Fecha de salida desde origen |
| fecha_estimada_llegada | Fecha estimada de llegada |
| fecha_llegada_real | Fecha real de llegada |
| estado | Estado del embarque |
| notas | Observaciones adicionales |

**Tabla `detalle_embarques`**
| Campo | Descripción |
|-------|-------------|
| id_detalle_embarque | Identificador único del detalle |
| id_embarque | Embarque relacionado |
| id_equipo | Equipo incluido en el embarque |
| estado_recepcion | Estado de recepción del equipo |
| notas_recepcion | Observaciones de recepción |

### 6. Tabla `registros_fallas`

Documenta las fallas presentadas por los equipos:

| Campo | Descripción |
|-------|-------------|
| id_falla | Identificador único de la falla |
| id_equipo | Equipo relacionado |
| id_orden | Orden de trabajo asociada |
| fecha_deteccion | Fecha y hora de detección |
| descripcion_falla | Descripción detallada del problema |
| componente_afectado | Componente específico con falla |
| causa_probable | Causa probable identificada |
| solucion_aplicada | Solución implementada |
| tiempo_reparacion | Tiempo de reparación en horas |
| dentro_garantia | Indica si aplica garantía |
| es_reincidente | Indica si es falla reincidente |
| id_falla_previa | Referencia a falla previa si es reincidente |

### 7. Tabla `historico_fallas_equipo`

Consolida estadísticas de fallas por equipo:

| Campo | Descripción |
|-------|-------------|
| id_historico | Identificador único |
| id_equipo | Equipo relacionado |
| total_fallas | Cantidad total de fallas |
| total_fallas_garantia | Fallas cubiertas por garantía |
| fecha_ultima_falla | Fecha de última falla |
| fecha_actualizacion | Fecha de actualización |
| porcentaje_fallas_garantia | Porcentaje en garantía (calculado) |
| es_equipo_problematico | Indicador de equipo problemático (calculado) |

## Funcionalidades Principales

### 1. Gestión del Ciclo de Vida del Equipo

- **Registro Inicial**: Crear ficha del equipo con datos de fabricación y especificaciones.
- **Seguimiento de Importación**: Registrar embarque, fechas y estado del proceso de importación.
- **Control de Armado**: Gestionar el proceso de armado con seguimiento de avance y tiempos.
- **Entrega al Cliente**: Programar y registrar entrega, con documentación asociada.
- **Seguimiento Operativo**: Actualizar estado, ubicación y condiciones del equipo.

### 2. Control de Hectáreas Trabajadas

- **Registro Periódico**: Actualizar hectáreas trabajadas con cada mantención o contacto.
- **Historial Detallado**: Mantener registro histórico de incrementos de hectáreas.
- **Análisis de Rendimiento**: Evaluar rendimiento según hectáreas vs. tiempo.
- **Alertas de Mantención**: Generar alertas basadas en umbrales de hectáreas.
- **Reportes de Uso**: Crear informes de utilización por equipo, cliente o región.

### 3. Gestión de Estados y Ubicación

- **Cambios de Estado**: Registrar transiciones entre diferentes estados del equipo.
- **Ubicación Actual**: Controlar si el equipo está en taller, en campo, en tránsito, etc.
- **Historial de Movimientos**: Mantener registro cronológico de cambios de estado y ubicación.
- **Disponibilidad**: Conocer equipos disponibles para mantención o demostración.
- **Reportes de Estado**: Generar informes de distribución de equipos por estado.

### 4. Control de Embarques y Recepción

- **Gestión de Embarques**: Registrar embarques desde origen con detalle de equipos.
- **Seguimiento en Tránsito**: Controlar estado y ubicación durante transporte.
- **Recepción e Inspección**: Documentar estado de llegada e inspección inicial.
- **Novedades y Reclamos**: Registrar novedades para gestión con fabricante o aseguradora.
- **Estadísticas de Embarques**: Analizar tiempos promedio y eficiencia logística.

### 5. Análisis de Fallas y Confiabilidad

- **Registro Detallado de Fallas**: Documentar cada falla con causas y soluciones.
- **Patrones de Fallas**: Identificar componentes con mayor incidencia de fallas.
- **Reincidencias**: Controlar fallas repetitivas en un mismo equipo.
- **Aplicación de Garantías**: Gestionar reclamos de garantía al fabricante.
- **Indicadores de Confiabilidad**: Calcular MTBF (tiempo medio entre fallas) y métricas similares.

## Integraciones con Otros Módulos

El módulo de Equipos se integra estrechamente con:

- **Módulo de Clientes**: Para asociar equipos a sus propietarios y gestionar la relación.
- **Módulo de Mantenciones**: Para programar y ejecutar mantenciones preventivas y correctivas.
- **Módulo de Repuestos**: Para gestionar compatibilidad y uso de repuestos por equipo.
- **Módulo de Logística**: Para controlar embarques, recepción y despacho.
- **Módulo de KPIs**: Para generar métricas e indicadores relacionados con los equipos.

## Reportes Principales

### 1. Ficha Técnica del Equipo
Presenta información completa del equipo, incluyendo especificaciones, historial de mantenciones, fallas y actualizaciones de hectáreas.

### 2. Estado de Flota
Visión general de todos los equipos según su estado actual, con filtros por cliente, tipo y región.

### 3. Historial de Uso
Evolución detallada de hectáreas trabajadas, con gráficos de tendencia y proyecciones.

### 4. Análisis de Fallas
Estadísticas de fallas por tipo de equipo, componente y condiciones de operación.

### 5. Programación de Mantenciones
Calendario de mantenciones próximas basado en hectáreas y/o tiempo.

## Indicadores Clave (KPIs)

- **Tiempo Medio Entre Fallas (MTBF)**: Promedio de tiempo/hectáreas entre fallas por tipo de equipo.
- **Tiempo Medio de Reparación (MTTR)**: Promedio de tiempo necesario para reparar fallas.
- **Tasa de Fallas en Garantía**: Porcentaje de fallas cubiertas por garantía.
- **Tiempo Promedio de Armado**: Días promedio desde llegada hasta completar armado.
- **Hectáreas Promedio Anuales**: Promedio de hectáreas trabajadas por año y tipo de equipo.

## Beneficios para el Negocio

La implementación efectiva de este módulo permite:

1. **Control Total del Ciclo de Vida**: Visibilidad completa desde fabricación hasta operación.
2. **Optimización de Procesos**: Mejora en tiempos de armado, entrega y mantención.
3. **Reducción de Tiempos Muertos**: Minimización de inactividad por fallas imprevistas.
4. **Planificación Eficiente**: Anticipación a necesidades de mantención y repuestos.
5. **Gestión Proactiva de Garantías**: Maximización del beneficio de garantías del fabricante.
6. **Información para Innovación**: Identificación de oportunidades de mejora en equipos y procesos.

## Ejemplos de Uso

### Ejemplo 1: Recepción y Armado de Equipo Nuevo

Un coordinador de taller recibe un nuevo tractor y realiza el siguiente proceso en el sistema:

1. Verifica el embarque en sistema, confirmando llegada del equipo TR-130-23002
2. Registra la inspección de recepción, documentando estado general y posibles novedades
3. Crea el plan de armado, asignando técnicos y estimando fecha de finalización
4. Actualiza el avance diario del proceso de armado
5. Al finalizar, registra la fecha de armado completo y cambia estado a "listo_despacho"
6. Programa fecha de entrega al cliente y genera documentación necesaria

### Ejemplo 2: Seguimiento de Uso y Mantención Preventiva

Un técnico de campo visita a un cliente y realiza:

1. Accede a la ficha del equipo CS-250-23001 desde su dispositivo móvil
2. Registra la actualización de hectáreas trabajadas (de 180.75 a 230.50)
3. El sistema detecta automáticamente que se alcanzó el umbral para mantención de 250 horas
4. Genera una alerta y sugiere programar la mantención preventiva
5. El técnico acuerda fecha con el cliente y registra la programación en el sistema
6. El módulo de mantenciones recibe la información y genera la orden de trabajo

## Consideraciones y Mejores Prácticas

1. **Datos Completos**: Mantener información actualizada de cada equipo es fundamental.
2. **Actualización Periódica**: Establecer protocolos para actualización regular de hectáreas.
3. **Documentación Visual**: Incluir fotografías en inspecciones y cambios de estado.
4. **Categorización de Fallas**: Utilizar categorías estandarizadas para facilitar análisis.
5. **Validación de Datos**: Implementar controles para evitar errores en registro de lecturas.
6. **Seguridad de Acceso**: Definir permisos específicos para modificación de información crítica.

El Módulo de Gestión de Equipos proporciona la columna vertebral del sistema "Rancho", permitiendo un control integral de los activos más valiosos del negocio: las máquinas agrícolas y su operación efectiva. 