# Manual de Usuario: Representante de Atención al Cliente

## Introducción

Bienvenido al manual del Representante de Atención al Cliente del Sistema de Gestión "Rancho". Como representante, usted es el puente entre los clientes y el taller, responsable de gestionar la comunicación, registrar solicitudes, coordinar agendamientos y asegurar la satisfacción de los clientes.

## Índice de Contenidos

1. [Acceso al Sistema](#acceso-al-sistema)
2. [Panel de Control de Atención al Cliente](#panel-de-control-de-atención-al-cliente)
3. [Gestión de Clientes](#gestión-de-clientes)
4. [Solicitudes de Mantención](#solicitudes-de-mantención)
5. [Agendamiento de Servicios](#agendamiento-de-servicios)
6. [Pedidos de Repuestos](#pedidos-de-repuestos)
7. [Seguimiento de Satisfacción](#seguimiento-de-satisfacción)
8. [Preguntas Frecuentes](#preguntas-frecuentes)

## Acceso al Sistema

### Inicio de Sesión

1. Acceda a la URL del sistema: `https://rancho.sistema.com`
2. Ingrese sus credenciales:
   - Usuario: Su correo electrónico corporativo
   - Contraseña: Su contraseña personal
3. Haga clic en "Iniciar Sesión"

![Ejemplo de pantalla de inicio de sesión](../img/atencion_login.png)

### Recuperación de Contraseña

Si olvidó su contraseña:
1. Haga clic en "¿Olvidó su contraseña?"
2. Ingrese su correo electrónico registrado
3. Siga las instrucciones enviadas a su correo para restablecer su contraseña

## Panel de Control de Atención al Cliente

El panel de control es su centro de operaciones diarias, diseñado para facilitar la gestión de clientes.

### Componentes Principales

- **Solicitudes Pendientes**: Lista de solicitudes que requieren atención
- **Agendamientos del Día**: Mantenciones programadas para hoy
- **Alertas de Seguimiento**: Recordatorios de seguimiento a clientes
- **Satisfacción de Clientes**: Indicadores de satisfacción recientes
- **Búsqueda Rápida**: Acceso rápido a la información de clientes

### Personalización del Panel

Puede personalizar su panel según sus preferencias:
1. Haga clic en "Configurar Panel"
2. Arrastre y suelte los widgets que desea visualizar
3. Configure el rango de tiempo para los datos mostrados
4. Guarde los cambios

## Gestión de Clientes

### Búsqueda de Clientes

Para encontrar la información de un cliente:
1. Utilice la barra de búsqueda en la parte superior
2. Puede buscar por nombre, RUT, o correo electrónico
3. También puede acceder desde "Clientes" > "Buscar Cliente"

### Registro de Nuevos Clientes

Para registrar un nuevo cliente:
1. Vaya a "Clientes" > "Nuevo Cliente"
2. Complete la información requerida:
   - Nombre/Razón social
   - RUT
   - Dirección
   - Comuna y región
   - Teléfono y correo electrónico
3. Haga clic en "Guardar Cliente"

### Actualización de Información

Para mantener actualizada la base de datos:
1. Busque el cliente que desea modificar
2. Haga clic en "Editar"
3. Actualice la información necesaria
4. Guarde los cambios

### Ejemplo: Registro de un Nuevo Cliente

**Caso de uso**: Un agricultor llega al taller por primera vez solicitando información sobre servicios.

1. Vaya a "Clientes" > "Nuevo Cliente"
2. Complete la información:
   - Nombre: Agrícola Santa Rosa
   - RUT: 76.123.456-7
   - Dirección: Camino Los Nogales Km 5
   - Comuna: San Carlos
   - Región: Ñuble
   - Teléfono: +56912345678
   - Email: contacto@santarosa.cl
3. En "Información Adicional", registre:
   - Tipo de cliente: Empresa agrícola
   - Cultivos principales: Trigo, maíz
   - Extensión aproximada: 200 hectáreas
4. Haga clic en "Guardar Cliente"

## Solicitudes de Mantención

### Registro de Solicitudes

Cuando un cliente solicita una mantención:
1. Vaya a "Mantenciones" > "Nueva Solicitud"
2. Seleccione el cliente (o regístrelo si es nuevo)
3. Seleccione el equipo asociado
4. Registre la descripción del problema reportado
5. Establezca la prioridad según la urgencia
6. Indique si está dentro de garantía
7. Haga clic en "Registrar Solicitud"

### Seguimiento de Solicitudes

Para dar seguimiento a las solicitudes registradas:
1. Vaya a "Mantenciones" > "Solicitudes Pendientes"
2. Puede filtrar por estado, cliente, fecha, etc.
3. Haga clic en una solicitud para ver los detalles
4. Desde allí puede:
   - Actualizar su estado
   - Añadir notas
   - Ver el historial de cambios

### Ejemplo: Registro de una Solicitud Urgente

**Caso de uso**: Un cliente llama reportando que su tractor no enciende en plena temporada de siembra.

1. Vaya a "Mantenciones" > "Nueva Solicitud"
2. Seleccione el cliente: Agrícola El Triunfo
3. Seleccione el equipo: Tractor Agrícola 130HP (TR-130-23001)
4. En "Descripción del Problema" escriba: "Cliente reporta que el tractor no enciende. Intentó arrancar varias veces sin éxito. No hay ruidos anormales ni luces en el panel."
5. Establezca la prioridad como "Urgente"
6. Verifique si está en garantía (según fecha de entrega y hectáreas)
7. En "Notas Adicionales" escriba: "Cliente está en plena temporada de siembra. Solicita atención inmediata, preferiblemente en campo."
8. Haga clic en "Registrar Solicitud"
9. El sistema notificará automáticamente a los técnicos disponibles

## Agendamiento de Servicios

### Programación de Mantenciones

Para agendar mantenciones preventivas:
1. Vaya a "Mantenciones" > "Programar Mantención"
2. Seleccione el cliente y el equipo
3. Seleccione el tipo de mantención
4. Proponga fechas disponibles según el calendario del taller
5. Registre la preferencia del cliente (fecha y horario)
6. Indique si la mantención será en taller o en campo
7. Haga clic en "Confirmar Agendamiento"

### Reprogramación

Si es necesario cambiar una fecha programada:
1. Busque el agendamiento en "Mantenciones" > "Agendamientos"
2. Haga clic en "Reprogramar"
3. Seleccione la nueva fecha y hora
4. Registre el motivo del cambio
5. El sistema enviará una notificación al cliente

### Gestión del Calendario

Para visualizar y gestionar todos los agendamientos:
1. Vaya a "Mantenciones" > "Calendario"
2. Puede ver la programación diaria, semanal o mensual
3. Identifique rápidamente los horarios disponibles
4. Evite sobreprogramación de técnicos o recursos

### Ejemplo: Programación de una Mantención Preventiva

**Caso de uso**: Un cliente solicita programar la mantención de 1000 horas para su cosechadora.

1. Vaya a "Mantenciones" > "Programar Mantención"
2. Seleccione el cliente: Sociedad Agrícola Hermanos Pérez
3. Seleccione el equipo: Cosechadora 250HP (CS-250-23001)
4. Seleccione el tipo: "Mantención 1000 Horas"
5. Revise el calendario y proponga: 15/06/2023 (mañana) o 17/06/2023 (tarde)
6. El cliente prefiere el 17/06/2023 en la tarde
7. Lugar: Taller
8. En "Notas" registre: "Cliente traerá el equipo el día anterior. Solicita revisión adicional del sistema de corte."
9. Haga clic en "Confirmar Agendamiento"
10. Envíe la confirmación por correo al cliente usando "Enviar Confirmación"

## Pedidos de Repuestos

### Registro de Pedidos

Para gestionar pedidos de repuestos:
1. Vaya a "Repuestos" > "Nuevo Pedido"
2. Seleccione el cliente
3. Busque y añada los repuestos solicitados
4. Verifique disponibilidad en tiempo real
5. Calcule el costo total
6. Establezca forma de pago y entrega
7. Haga clic en "Registrar Pedido"

### Seguimiento de Pedidos

Para dar seguimiento a los pedidos:
1. Vaya a "Repuestos" > "Pedidos Pendientes"
2. Filtre por cliente, estado, fecha, etc.
3. Para cada pedido puede:
   - Actualizar su estado
   - Registrar notas
   - Coordinar la entrega
   - Generar documentos (factura, guía de despacho)

### Ejemplo: Gestión de un Pedido Urgente

**Caso de uso**: Un cliente necesita urgentemente repuestos para reparar su equipo durante cosecha.

1. Vaya a "Repuestos" > "Nuevo Pedido"
2. Seleccione el cliente: Cooperativa Valle Central
3. Añada los repuestos:
   - 1 unidad de "Bomba hidráulica" (RP-H-001)
   - 2 unidades de "Kit de empaques" (RP-M-002)
4. Verifique la disponibilidad (el sistema muestra 2 bombas y 3 kits en stock)
5. Marque como "Urgente - Temporada Crítica"
6. En entrega seleccione "Despacho a domicilio"
7. Dirección: Fundo El Milagro, Km 10 camino a Talca
8. Forma de pago: Crédito (cliente con cuenta corriente)
9. Haga clic en "Registrar Pedido"
10. Coordine con logística utilizando "Solicitar Despacho Prioritario"

## Seguimiento de Satisfacción

### Encuestas de Satisfacción

Después de cada servicio o venta:
1. Vaya a "Clientes" > "Encuestas" > "Nueva Encuesta"
2. Seleccione el cliente y el servicio relacionado
3. Elija el tipo de encuesta (post-mantención, post-venta, etc.)
4. Envíe la encuesta por correo o realícela por teléfono
5. Registre las respuestas en el sistema

### Análisis de Resultados

Para analizar la satisfacción de los clientes:
1. Vaya a "Clientes" > "Satisfacción"
2. Visualice gráficos y tendencias
3. Identifique áreas de mejora
4. Vea el detalle de comentarios recibidos

### Gestión de Quejas y Reclamos

Si un cliente presenta una queja:
1. Vaya a "Clientes" > "Gestión de Quejas" > "Nuevo Caso"
2. Registre detalladamente la queja
3. Clasifique según el tipo (calidad, tiempo, atención, etc.)
4. Asigne un responsable para la solución
5. Establezca plazos de resolución
6. Dé seguimiento hasta el cierre

### Ejemplo: Gestión de un Reclamo

**Caso de uso**: Un cliente reclama porque la mantención programada no se realizó en la fecha acordada.

1. Vaya a "Clientes" > "Gestión de Quejas" > "Nuevo Caso"
2. Seleccione el cliente: Inversiones Agromaster Ltda.
3. Tipo de queja: "Incumplimiento de fecha programada"
4. Describa: "Cliente tenía agendada mantención de su pulverizador para el 25/05/2023 a las 10:00, pero el técnico no asistió. Cliente esperó todo el día sin recibir notificación."
5. Prioridad: Alta
6. Asigne al Jefe de Taller como responsable
7. Plazo de resolución: 24 horas
8. Acción inmediata: Llamar al cliente para disculparse y reprogramar con prioridad
9. Haga clic en "Registrar Queja"
10. Documente todas las acciones tomadas en la sección "Seguimiento"

## Registro de Interacciones

### Registro de Comunicaciones

Para mantener un historial completo:
1. Vaya a "Clientes" > "Interacciones" > "Nueva Interacción"
2. Seleccione el cliente
3. Registre:
   - Tipo de contacto (llamada, email, visita, etc.)
   - Fecha y hora
   - Asunto y descripción
   - Resultado o acuerdos
   - Si requiere seguimiento posterior
4. Guarde la interacción

### Seguimiento Proactivo

Para realizar seguimiento programado:
1. Vaya a "Clientes" > "Seguimiento Pendiente"
2. Verá las interacciones marcadas para seguimiento
3. Realice el contacto correspondiente
4. Registre el resultado
5. Si es necesario, programe un nuevo seguimiento

### Ejemplo: Registro de una Llamada de Cliente

**Caso de uso**: Un cliente llama consultando sobre la disponibilidad de un repuesto específico.

1. Vaya a "Clientes" > "Interacciones" > "Nueva Interacción"
2. Seleccione el cliente: Agrícola Los Olivos
3. Tipo: Llamada telefónica
4. Fecha y hora: [fecha actual]
5. Motivo: "Consulta de disponibilidad de repuesto"
6. Descripción: "Cliente consulta si tenemos disponible el disco sembrador RP-S-001 para su sembradora. Necesita 5 unidades."
7. Resultado: "Se verificó inventario, tenemos 20 unidades disponibles. Se informó precio y se ofreció incluir envío sin costo."
8. Seguimiento: Sí
9. Fecha seguimiento: [3 días después]
10. Haga clic en "Guardar Interacción"

## Preguntas Frecuentes

### ¿Cómo puedo saber si un equipo está en garantía?
En la ficha del equipo, la sección "Garantía" muestra si está vigente, hasta qué fecha o hectáreas aplica, y qué cubre específicamente.

### Un cliente no recuerda el modelo exacto de su equipo, ¿cómo lo identifico?
Puede buscarlo por número de serie o, si no lo tiene, utilice la función "Búsqueda de Equipos por Cliente" que muestra todos los equipos asociados al cliente.

### ¿Cómo gestiono un cliente insatisfecho?
Escuche atentamente, registre su queja en "Gestión de Quejas", asigne un responsable con prioridad alta, y mantenga al cliente informado sobre las acciones tomadas. Ofrezca una solución concreta y verifique posteriormente su satisfacción.

### ¿Puedo ver el historial completo de un cliente?
Sí, en la ficha del cliente existe una sección "Historial" que muestra todas las interacciones, mantenciones, compras y encuestas relacionadas con ese cliente.

### ¿Cómo priorizo las solicitudes cuando hay muchas pendientes?
Utilice estos criterios: 1) Equipos en temporada crítica, 2) Clientes con contrato de servicio premium, 3) Reparaciones vs. mantenciones preventivas, 4) Orden de llegada. El sistema ayuda coloreando según prioridad. 