# Módulo de Gestión de Mantenciones

## Descripción General

El Módulo de Gestión de Mantenciones es un componente esencial del sistema "Rancho", diseñado para administrar de manera eficiente y efectiva todas las actividades relacionadas con el mantenimiento preventivo y correctivo de los equipos agrícolas. Este módulo permite planificar, programar, ejecutar y dar seguimiento a las mantenciones, optimizando los recursos del taller y maximizando la disponibilidad operativa de la maquinaria de los clientes.

En el contexto de equipos agrícolas de alta tecnología, donde el costo de inactividad durante temporadas críticas puede ser extremadamente alto, contar con un sistema robusto de gestión de mantenciones resulta fundamental para garantizar la confiabilidad y prolongar la vida útil de los equipos.

## Objetivos del Módulo

- Facilitar la planificación y programación de mantenciones preventivas basadas en hectáreas trabajadas o intervalos de tiempo
- Permitir a los clientes agendar directamente sus mantenciones a través del sistema
- Gestionar eficientemente las solicitudes de mantención correctiva
- Optimizar la asignación de técnicos y recursos para cada mantención
- Mantener un registro detallado de todas las intervenciones realizadas a cada equipo
- Generar información valiosa para análisis de confiabilidad y mejora continua

## Estructura de Datos

El módulo se basa principalmente en las siguientes tablas de la base de datos:

### 1. Tabla `tipo_mantencion`

Define los diferentes tipos de mantenciones disponibles:

| Campo | Descripción |
|-------|-------------|
| id_tipo_mantencion | Identificador único del tipo de mantención |
| nombre | Nombre del tipo de mantención |
| descripcion | Descripción detallada |
| es_preventiva | Indica si es mantenimiento preventivo o correctivo |

### 2. Tabla `programacion_mantencion`

Establece la programación de mantenciones preventivas por equipo:

| Campo | Descripción |
|-------|-------------|
| id_programacion | Identificador único |
| id_equipo | Equipo relacionado |
| id_tipo_mantencion | Tipo de mantención relacionado |
| intervalo_hectareas | Intervalo de hectáreas para mantención preventiva |
| intervalo_dias | Intervalo de días para mantención preventiva |
| hectareas_proxima_mantencion | Hectáreas a las que corresponde la próxima mantención |
| fecha_proxima_mantencion | Fecha estimada para la próxima mantención |
| activo | Indica si la programación está activa |

### 3. Tabla `mantenciones_programadas`

Registra las mantenciones preventivas programadas:

| Campo | Descripción |
|-------|-------------|
| id_mantencion_programada | Identificador único |
| id_equipo | Equipo relacionado |
| id_tipo_mantencion | Tipo de mantención |
| fecha_programada | Fecha programada para la mantención |
| fecha_realizada | Fecha en que se realizó efectivamente |
| estado | Estado actual (pendiente, en_proceso, completada, cancelada) |
| notas | Observaciones adicionales |
| costo_estimado | Costo estimado de la mantención |
| costo_real | Costo real una vez realizada |
| horas_estimadas | Tiempo estimado de trabajo |
| horas_reales | Tiempo real empleado |

### 4. Tabla `solicitudes_mantencion`

Gestiona las solicitudes de mantención correctiva:

| Campo | Descripción |
|-------|-------------|
| id_solicitud | Identificador único |
| id_cliente | Cliente que solicita la mantención |
| id_equipo | Equipo que requiere mantención |
| fecha_solicitud | Fecha y hora de la solicitud |
| descripcion_problema | Descripción detallada del problema |
| prioridad | Nivel de prioridad (baja, media, alta, urgente) |
| estado | Estado actual de la solicitud |
| fecha_asignacion | Fecha de asignación a técnico |
| fecha_inicio | Fecha de inicio de los trabajos |
| fecha_finalizacion | Fecha de finalización |
| dentro_garantia | Indica si está cubierta por garantía |
| notas | Observaciones adicionales |

### 5. Tabla `agendamientos_cliente`

Permite a los clientes agendar mantenciones directamente:

| Campo | Descripción |
|-------|-------------|
| id_agendamiento | Identificador único |
| id_cliente | Cliente que agenda la mantención |
| id_equipo | Equipo para mantención |
| id_tipo_mantencion | Tipo de mantención solicitada |
| fecha_solicitud | Fecha en que se realizó el agendamiento |
| fecha_preferida | Fecha preferida por el cliente |
| horario_preferido | Preferencia de horario (mañana, tarde) |
| lugar | Lugar donde se realizará (taller, campo) |
| direccion_campo | Dirección en caso de mantención en campo |
| estado | Estado del agendamiento |
| fecha_confirmada | Fecha confirmada por el taller |
| hora_confirmada | Hora confirmada por el taller |
| id_mantencion_programada | Mantención programada generada |
| notas_cliente | Observaciones del cliente |
| notas_internas | Notas internas del taller |

### 6. Tabla `ordenes_trabajo`

Gestiona las órdenes de trabajo generadas para cada mantención:

| Campo | Descripción |
|-------|-------------|
| id_orden | Identificador único |
| id_solicitud | Solicitud relacionada (si es correctiva) |
| id_mantencion_programada | Mantención programada relacionada (si es preventiva) |
| id_tecnico | Técnico asignado |
| fecha_creacion | Fecha de creación de la orden |
| fecha_inicio | Fecha de inicio de los trabajos |
| fecha_finalizacion | Fecha de finalización |
| estado | Estado actual |
| diagnostico | Diagnóstico realizado |
| solucion | Solución aplicada |
| horas_trabajo | Horas dedicadas |
| costo_mano_obra | Costo de la mano de obra |
| costo_repuestos | Costo de los repuestos utilizados |
| costo_total | Costo total calculado |
| precio_cliente | Precio cobrado al cliente |
| margen | Margen de ganancia calculado |
| porcentaje_margen | Porcentaje de margen calculado |

### 7. Tabla `detalle_repuestos_orden`

Detalla los repuestos utilizados en cada orden:

| Campo | Descripción |
|-------|-------------|
| id_detalle | Identificador único |
| id_orden | Orden relacionada |
| id_repuesto | Repuesto utilizado |
| cantidad | Cantidad utilizada |
| precio_unitario | Precio unitario cobrado |
| costo_unitario | Costo unitario para el taller |
| subtotal | Subtotal calculado (precio x cantidad) |
| subtotal_costo | Subtotal de costo calculado |

## Funcionalidades Principales

### 1. Programación de Mantenciones Preventivas

- **Configuración de Intervalos**: Definir intervalos de mantención por hectáreas o tiempo.
- **Cálculo Automático**: Determinar próximas fechas o umbrales de hectáreas para mantención.
- **Generación de Mantenciones**: Crear automáticamente mantenciones programadas al alcanzar umbrales.
- **Secuenciación de Actividades**: Definir rutinas estándar para cada tipo de mantención.
- **Notificaciones Anticipadas**: Alertar sobre mantenciones próximas a vencer.

### 2. Agendamiento de Mantenciones por Cliente

- **Solicitud de Horarios**: Permitir a los clientes proponer fechas/horarios preferidos.
- **Selección de Tipo de Mantención**: Elegir entre las mantenciones disponibles para su equipo.
- **Elección de Ubicación**: Optar por mantención en taller o en campo.
- **Confirmación de Agendamiento**: Recibir confirmación o propuesta alternativa del taller.
- **Seguimiento de Estado**: Consultar estado actual del agendamiento.
- **Reprogramación**: Solicitar cambios en fechas ya programadas.

### 3. Gestión de Mantenciones Correctivas

- **Recepción de Solicitudes**: Registrar problemas reportados por clientes.
- **Evaluación y Priorización**: Clasificar según urgencia y criticidad.
- **Asignación de Recursos**: Designar técnicos y definir plazos de atención.
- **Validación de Garantía**: Verificar cobertura de garantía aplicable.
- **Seguimiento de Resolución**: Controlar avance hasta la solución del problema.
- **Comunicación con Cliente**: Mantener informado al cliente del estado.

### 4. Ejecución y Control de Trabajos

- **Generación de Órdenes**: Crear órdenes de trabajo detalladas.
- **Asignación de Técnicos**: Distribuir cargas de trabajo según especialidad.
- **Registro de Actividades**: Documentar trabajos realizados, tiempos y observaciones.
- **Consumo de Repuestos**: Controlar repuestos utilizados en cada mantención.
- **Seguimiento en Tiempo Real**: Actualizar avance de cada orden en ejecución.
- **Control de Calidad**: Verificar cumplimiento de estándares de servicio.

### 5. Análisis de Desempeño y Métricas

- **Cumplimiento de Programación**: Evaluar ejecución de mantenciones preventivas vs. programadas.
- **Tiempos de Respuesta**: Medir tiempos desde solicitud hasta resolución.
- **Efectividad de Mantenciones**: Analizar reincidencia de fallas post-mantención.
- **Rentabilidad por Servicio**: Calcular márgenes por tipo de mantención.
- **Productividad de Técnicos**: Evaluar rendimiento individual y por equipo.
- **Tendencias de Fallas**: Identificar componentes con mayor frecuencia de fallas.

## Integraciones con Otros Módulos

El módulo de Mantenciones se integra estrechamente con:

- **Módulo de Equipos**: Para obtener información del equipo, historial y hectáreas.
- **Módulo de Clientes**: Para gestionar la relación con el propietario del equipo.
- **Módulo de Repuestos**: Para verificar disponibilidad y consumir inventario.
- **Módulo de KPIs**: Para alimentar indicadores de mantenimiento y confiabilidad.
- **Módulo de Postventa**: Para evaluar satisfacción después de cada servicio.

## Reportes Principales

### 1. Plan de Mantenciones
Calendario que muestra todas las mantenciones programadas en un período, con filtros por técnico, cliente y tipo.

### 2. Historial de Mantenciones por Equipo
Registro completo de todas las intervenciones realizadas a un equipo específico, con detalle de trabajos y repuestos.

### 3. Panel de Control de Mantenciones Pendientes
Vista consolidada de mantenciones preventivas por vencer y correctivas sin resolver, con alertas por prioridad.

### 4. Análisis de Confiabilidad
Evaluación de tiempos entre fallas y efectividad de mantenciones preventivas por tipo de equipo.

### 5. Rendimiento de Técnicos
Productividad, calidad y eficiencia de cada técnico en la ejecución de mantenciones.

## Indicadores Clave (KPIs)

- **Porcentaje de Cumplimiento Preventivo**: Mantenciones preventivas realizadas vs. programadas.
- **Tiempo Medio Entre Fallas (MTBF)**: Promedio de tiempo/hectáreas operativas entre fallas.
- **Tiempo Medio de Reparación (MTTR)**: Promedio de tiempo para resolver fallas.
- **Tasa de Reincidencia**: Porcentaje de fallas que se repiten en un período corto post-mantención.
- **Disponibilidad Técnica**: Porcentaje de tiempo que los equipos están operativos.
- **Porcentaje de Ordenes Realizadas a Tiempo**: Cumplimiento de plazos comprometidos.

## Beneficios para el Negocio

La implementación efectiva de este módulo permite:

1. **Reducción de Fallas Imprevistas**: Minimizar paradas no programadas mediante mantención preventiva efectiva.
2. **Optimización de Recursos Técnicos**: Mejorar planificación y asignación de personal y equipamiento.
3. **Incremento de Disponibilidad**: Maximizar tiempo operativo de equipos, especialmente en períodos críticos.
4. **Mejora en Satisfacción**: Ofrecer respuesta oportuna y efectiva a necesidades del cliente.
5. **Control de Costos**: Optimizar uso de repuestos y mano de obra en cada intervención.
6. **Generación de Ingresos Recurrentes**: Establecer programas de mantención como fuente estable de ingresos.
7. **Fidelización de Clientes**: Fortalecer relación mediante servicio técnico de excelencia.

## Ejemplos de Uso

### Ejemplo 1: Mantención Preventiva Programada

Un tractor TR-130-23001 alcanza 450 hectáreas trabajadas. El sistema:

1. Detecta proximidad al umbral de 500 hectáreas para mantención preventiva
2. Genera alerta para coordinador de mantenciones
3. El coordinador contacta al cliente para proponer fechas
4. Se programa la mantención para la semana siguiente
5. Se genera orden de trabajo y se asigna técnico especializado
6. Se preparan repuestos necesarios según la rutina estándar
7. Se ejecuta la mantención en la fecha acordada
8. Se registran trabajos realizados y próximo umbral de mantención

### Ejemplo 2: Agendamiento Realizado por Cliente

Un cliente ingresa al sistema y realiza el siguiente proceso:

1. Selecciona su equipo CS-250-23001
2. Elige tipo de mantención "Pre-Temporada"
3. Propone fecha 15/07/2023 en horario de mañana
4. Indica que prefiere la mantención en sus instalaciones
5. Agrega notas sobre preparación para cosecha
6. El sistema registra la solicitud con estado "solicitado"
7. El coordinador de mantenciones recibe notificación
8. Verifica disponibilidad de técnicos y repuestos
9. Confirma la fecha solicitada y asigna hora específica
10. El sistema genera una mantención programada vinculada al agendamiento
11. El cliente recibe confirmación y puede seguir el estado

### Ejemplo 3: Respuesta a Falla Reportada

Un cliente reporta pérdida de potencia en su tractor:

1. Se registra solicitud de mantención correctiva con prioridad alta
2. Se asigna a técnico especialista en motores
3. El técnico realiza diagnóstico inicial vía telefónica
4. Se programa visita técnica para el día siguiente
5. Se crea orden de trabajo con estimación inicial
6. Durante la visita, se diagnostica filtro de combustible obstruido
7. Se reemplaza el filtro y se realiza limpieza del sistema
8. Se registran trabajos realizados, repuestos utilizados y tiempo empleado
9. Se genera informe para el cliente con recomendaciones
10. Se envía encuesta de satisfacción posterior al servicio

## Consideraciones y Mejores Prácticas

1. **Priorización Adecuada**: Establecer criterios claros para priorizar solicitudes en temporadas de alta demanda.
2. **Rutinas Estandarizadas**: Definir detalladamente los procedimientos para cada tipo de mantención.
3. **Capacidad de Taller**: Considerar capacidad instalada al programar mantenciones para evitar sobrecargas.
4. **Coordinación de Recursos**: Asegurar disponibilidad de repuestos antes de confirmar fechas de mantención.
5. **Flexibilidad en Campo**: Adaptar protocolos para mantenciones realizadas en instalaciones del cliente.
6. **Documentación Completa**: Mantener registro detallado de cada intervención para análisis posterior.
7. **Comunicación Proactiva**: Informar oportunamente al cliente sobre cualquier cambio en la programación.

El Módulo de Gestión de Mantenciones constituye un pilar fundamental del sistema "Rancho", proporcionando las herramientas necesarias para garantizar la confiabilidad y disponibilidad de los equipos agrícolas, maximizando así la productividad y satisfacción de los clientes. 