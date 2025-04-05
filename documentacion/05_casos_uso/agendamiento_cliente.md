# Caso de Uso: Agendamiento de Mantenciones por Cliente

## Descripción General

Este caso de uso describe el proceso mediante el cual un cliente puede agendar directamente una mantención para su equipo agrícola a través del sistema "Rancho". Esta funcionalidad permite a los clientes solicitar mantenciones preventivas o servicios técnicos programados en fechas convenientes para su operación, eligiendo entre realizar el servicio en el taller o solicitar atención en sus propias instalaciones.

El agendamiento de mantenciones por parte del cliente representa una mejora significativa en la experiencia del usuario, otorgándole mayor autonomía y flexibilidad para programar los servicios necesarios para sus equipos, al tiempo que optimiza la planificación del taller y fortalece la relación de servicio.

## Actores Involucrados

- **Cliente**: Usuario que solicita y agenda la mantención para su equipo.
- **Coordinador de Mantenciones**: Responsable de revisar, confirmar o reasignar los agendamientos.
- **Técnico**: Personal que ejecutará la mantención programada.
- **Sistema**: Plataforma "Rancho" que gestiona el proceso de agendamiento.

## Precondiciones

1. El cliente debe estar registrado en el sistema y tener acceso al módulo de agendamiento.
2. El equipo para el cual se solicita la mantención debe estar registrado y asociado al cliente.
3. El sistema debe tener configurados los tipos de mantenciones disponibles.
4. El cliente debe conocer el estado actual de su equipo (hectáreas trabajadas o tiempo de uso).

## Flujo Principal

### 1. Ingreso al Sistema y Selección de Equipo

1. El cliente ingresa al sistema "Rancho" con sus credenciales.
2. Navega a la sección "Mis Equipos" o "Agendar Mantención".
3. Visualiza el listado de sus equipos registrados con información básica (modelo, número de serie, hectáreas acumuladas, última mantención).
4. Selecciona el equipo para el cual desea programar una mantención.

### 2. Selección de Tipo de Mantención

1. El sistema muestra los tipos de mantenciones disponibles para el equipo seleccionado, incluyendo:
   - Mantenciones programadas próximas a vencer según hectáreas o calendario
   - Opciones de mantenciones preventivas regulares
   - Revisiones pre-temporada o post-temporada
2. El cliente selecciona el tipo de mantención deseado.
3. El sistema muestra una descripción de la mantención seleccionada, incluyendo trabajos a realizar, duración estimada y costo aproximado.

### 3. Selección de Fecha y Ubicación

1. El cliente accede a un calendario que muestra:
   - Días disponibles (en verde)
   - Días con alta ocupación (en amarillo)
   - Días sin disponibilidad (en rojo)
2. Selecciona la fecha preferida para realizar la mantención.
3. Elige preferencia de horario (mañana o tarde).
4. Selecciona la ubicación donde desea recibir el servicio:
   - Taller: El cliente llevará el equipo a las instalaciones del taller
   - Campo: El servicio técnico se desplazará a la ubicación del cliente
5. Si selecciona "Campo", ingresa la dirección específica donde se encuentra el equipo.

### 4. Confirmación de Solicitud

1. El sistema muestra un resumen de la solicitud con todos los detalles:
   - Equipo seleccionado
   - Tipo de mantención
   - Fecha y preferencia horaria
   - Ubicación del servicio
   - Costo estimado
2. El cliente puede agregar notas adicionales o requerimientos especiales.
3. Confirma la solicitud de agendamiento.
4. El sistema registra la solicitud con estado "solicitado" y genera un número de agendamiento.
5. Se muestra una confirmación al cliente con el número de agendamiento y los próximos pasos.

### 5. Procesamiento Interno

1. El coordinador de mantenciones recibe una notificación de nuevo agendamiento.
2. Revisa los detalles y verifica:
   - Disponibilidad de técnicos para la fecha solicitada
   - Disponibilidad de repuestos necesarios
   - Factibilidad técnica y logística
3. Toma una decisión:
   - Confirma el agendamiento en la fecha y hora solicitadas
   - Propone una fecha/hora alternativa si no es posible la solicitada
4. Asigna preliminarmente el técnico que realizará el servicio.
5. Actualiza el estado del agendamiento a "confirmado" o "reprogramado".

### 6. Notificación al Cliente

1. El cliente recibe una notificación (email, SMS o en plataforma) sobre el estado de su agendamiento.
2. La notificación incluye:
   - Confirmación o propuesta alternativa
   - Fecha y hora específica asignada
   - Nombre del técnico asignado (si corresponde)
   - Instrucciones adicionales según el tipo de mantención
3. El cliente puede ver el detalle completo en el sistema.

### 7. Generación de Mantención Programada

1. Una vez confirmado el agendamiento, el sistema genera automáticamente un registro en la tabla de mantenciones programadas.
2. Se vincula el agendamiento con la mantención programada.
3. Se actualiza el calendario de mantenciones del taller.
4. Se reservan los repuestos necesarios para la fecha programada.

### 8. Seguimiento del Agendamiento

1. El cliente puede consultar el estado de su agendamiento en cualquier momento.
2. Recibe recordatorios automáticos conforme se acerca la fecha (una semana antes, un día antes).
3. Puede solicitar modificaciones o cancelación hasta 48 horas antes de la fecha programada.

## Flujos Alternativos

### A. No Hay Disponibilidad en la Fecha Solicitada

1. Si no hay disponibilidad en la fecha seleccionada por el cliente, el coordinador propone fechas alternativas.
2. El cliente recibe una notificación con las alternativas disponibles.
3. El cliente puede aceptar una de las alternativas o proponer otra fecha.
4. El proceso continúa hasta llegar a un acuerdo sobre la fecha.

### B. Cancelación o Reprogramación por el Cliente

1. El cliente solicita cancelar o reprogramar una mantención ya confirmada.
2. Si la solicitud se realiza con más de 48 horas de anticipación:
   - Se cancela sin penalización o se reprograma según disponibilidad
3. Si la solicitud se realiza con menos de 48 horas:
   - Se aplica política de cancelación tardía (posible cargo mínimo)
   - Se intenta reprogramar sujeto a disponibilidad

### C. Cancelación o Reprogramación por el Taller

1. Por causas de fuerza mayor, el taller necesita reprogramar una mantención confirmada.
2. El coordinador contacta al cliente y explica la situación.
3. Se ofrecen alternativas de fecha con prioridad en la agenda.
4. Se registra el cambio y se actualiza el estado del agendamiento.
5. Se puede ofrecer algún beneficio compensatorio por la inconveniencia.

### D. Servicio en Campo No Factible

1. Si durante la revisión, el coordinador determina que el servicio no puede realizarse en campo:
   - Se contacta al cliente para explicar las razones técnicas
   - Se ofrece modificar la ubicación a "taller"
   - Se coordina traslado o se reprograma según la decisión del cliente

## Postcondiciones

1. El sistema contiene un registro de agendamiento con estado actualizado.
2. Se ha generado una mantención programada vinculada al agendamiento.
3. El cliente ha recibido confirmación y detalles de la mantención agendada.
4. Los recursos necesarios (técnicos y repuestos) han sido reservados para la fecha programada.
5. El calendario del taller ha sido actualizado con la nueva mantención.

## Requisitos Especiales

1. **Interfaz Intuitiva**: La interfaz de agendamiento debe ser clara y fácil de usar para clientes sin conocimientos técnicos avanzados.
2. **Disponibilidad**: El sistema de agendamiento debe estar disponible 24/7 para que los clientes puedan programar en cualquier momento.
3. **Sincronización**: Debe existir sincronización en tiempo real entre agendamientos y disponibilidad para evitar conflictos.
4. **Notificaciones**: El sistema debe enviar notificaciones oportunas en cada etapa del proceso.
5. **Capacidad Móvil**: La funcionalidad debe estar optimizada para uso en dispositivos móviles.

## Frecuencia

- Se estima que esta funcionalidad será utilizada aproximadamente 15-20 veces por semana, con mayor concentración en períodos pre-temporada agrícola.
- La frecuencia aumentará significativamente a medida que crezca la base de clientes y se familiaricen con la herramienta.

## Reglas de Negocio Relacionadas

1. Los clientes solo pueden agendar mantenciones para equipos registrados a su nombre.
2. Las mantenciones en campo tendrán un costo adicional por desplazamiento según distancia.
3. La cancelación con menos de 48 horas puede generar un cargo mínimo por reserva de recursos.
4. Las mantenciones por garantía tienen prioridad en la asignación de fechas.
5. Los horarios disponibles para agendamiento son de lunes a viernes, 8:00 - 17:00 hrs.
6. El taller puede rechazar un agendamiento en campo si las condiciones no son adecuadas para el servicio.

## Puntos de Extensión

- **Integración con GPS**: Futura funcionalidad para localizar automáticamente la ubicación del equipo.
- **Videollamada de Diagnóstico**: Opción para realizar una evaluación preliminar mediante videollamada.
- **Pago en Línea**: Posibilidad de pagar anticipadamente el servicio a través de la plataforma.
- **Calificación de Servicio**: Evaluación post-servicio directamente vinculada al agendamiento.
- **Historial de Servicios**: Visualización del historial completo de mantenciones por equipo.

## Diagramas

### Diagrama de Flujo
Ver el diagrama de flujo completo del proceso de agendamiento en [diagrama_flujo_agendamiento.png](../recursos/diagrama_flujo_agendamiento.png)

### Diagrama de Estados
Ver el diagrama de estados del agendamiento en [diagrama_estados_agendamiento.png](../recursos/diagrama_estados_agendamiento.png)

## Interfaces de Usuario

### Interfaz Principal de Agendamiento
Consultar el mockup de la interfaz de usuario en [mockup_agendamiento.png](../recursos/mockup_agendamiento.png)

### Interfaz de Confirmación
Consultar el mockup de la interfaz de confirmación en [mockup_confirmacion_agendamiento.png](../recursos/mockup_confirmacion_agendamiento.png)

## Ejemplo Práctico

### Agendamiento de Mantención Pre-Temporada

**Cliente**: Agrícola El Triunfo  
**Equipo**: Tractor TR-130-23001 con 450 hectáreas trabajadas  
**Escenario**: Preparación para temporada de siembra

1. **Día 1 - Agendamiento**:
   - El cliente ingresa al sistema el 10 de junio de 2023.
   - Selecciona su tractor TR-130-23001.
   - Elige la mantención "Pre-Temporada".
   - Solicita fecha para el 20 de junio en horario de mañana.
   - Selecciona servicio en taller.
   - Agrega nota: "Necesito que revisen especialmente el sistema hidráulico, notamos una pequeña pérdida de presión".
   - Confirma la solicitud y recibe número de agendamiento #A2023-056.

2. **Día 1 - Procesamiento interno**:
   - El coordinador recibe la notificación.
   - Verifica disponibilidad y confirma la fecha solicitada.
   - Asigna hora específica: 9:30 AM.
   - Asigna al técnico Juan Martínez.
   - Actualiza estado a "confirmado".
   - El sistema genera la mantención programada #MP2023-089.

3. **Día 1 - Notificación**:
   - El cliente recibe confirmación por email y en plataforma.
   - Incluye detalles: fecha, hora, técnico asignado.
   - Instrucciones: "Por favor, llegue 15 minutos antes para el proceso de recepción".

4. **Día 19 - Recordatorio**:
   - El cliente recibe recordatorio automático.
   - Confirma asistencia a través de la plataforma.

5. **Día 20 - Ejecución**:
   - Cliente lleva el tractor al taller.
   - Se realiza la mantención programada.
   - El técnico registra trabajos, repuestos utilizados y actualiza hectáreas.
   - Estado del agendamiento actualizado a "completado".
   - Se vincula con la orden de trabajo generada.

6. **Día 21 - Seguimiento**:
   - Cliente recibe encuesta de satisfacción.
   - Sistema registra fecha de próxima mantención recomendada.

## Consideraciones y Recomendaciones

1. **Optimización de Tiempos**: Sugerir al cliente ventanas horarias menos congestionadas puede mejorar la eficiencia.
2. **Comunicación Clara**: Asegurar que el cliente comprenda exactamente qué incluye cada tipo de mantención.
3. **Flexibilidad Controlada**: Permitir cierta flexibilidad en reprogramaciones sin afectar la eficiencia operativa.
4. **Recordatorios Efectivos**: Implementar un sistema escalonado de recordatorios para reducir inasistencias.
5. **Recopilación de Información**: Aprovechar el proceso de agendamiento para recopilar información valiosa sobre el estado del equipo.

Este caso de uso representa una importante mejora en la experiencia del cliente, permitiéndole mayor control sobre el mantenimiento de sus equipos, al tiempo que optimiza la operación del taller a través de una mejor planificación y preparación para cada servicio. 