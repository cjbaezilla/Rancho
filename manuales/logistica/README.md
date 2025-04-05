# Manual de Usuario: Encargado de Logística

## Introducción

Bienvenido al manual del Encargado de Logística del Sistema de Gestión "Rancho". Como encargado de logística, usted es responsable de gestionar todos los aspectos relacionados con el movimiento de equipos y repuestos, incluyendo la recepción de embarques desde el fabricante, el seguimiento de equipos en tránsito, la coordinación de entregas a clientes y el despacho de repuestos.

## Índice de Contenidos

1. [Acceso al Sistema](#acceso-al-sistema)
2. [Panel de Control de Logística](#panel-de-control-de-logística)
3. [Gestión de Embarques](#gestión-de-embarques)
4. [Recepción de Equipos](#recepción-de-equipos)
5. [Armado y Preparación](#armado-y-preparación)
6. [Entregas a Clientes](#entregas-a-clientes)
7. [Despacho de Repuestos](#despacho-de-repuestos)
8. [Preguntas Frecuentes](#preguntas-frecuentes)

## Acceso al Sistema

### Inicio de Sesión

1. Acceda a la URL del sistema: `https://rancho.sistema.com`
2. Ingrese sus credenciales:
   - Usuario: Su correo electrónico corporativo
   - Contraseña: Su contraseña personal
3. Haga clic en "Iniciar Sesión"

![Ejemplo de pantalla de inicio de sesión](../img/logistica_login.png)

### Recuperación de Contraseña

Si olvidó su contraseña:
1. Haga clic en "¿Olvidó su contraseña?"
2. Ingrese su correo electrónico registrado
3. Siga las instrucciones enviadas a su correo para restablecer su contraseña

## Panel de Control de Logística

El panel de control es su centro de operaciones diarias, diseñado para facilitar la gestión logística.

### Componentes Principales

- **Embarques en Tránsito**: Muestra los embarques en camino con fechas estimadas de llegada
- **Recepciones Pendientes**: Equipos por recibir en los próximos días
- **Entregas Programadas**: Calendario de entregas a clientes
- **Despachos Pendientes**: Órdenes de repuestos pendientes de despacho
- **KPIs de Logística**: Indicadores clave de rendimiento logístico

### Personalización del Panel

Puede personalizar su panel según sus preferencias:
1. Haga clic en "Configurar Panel"
2. Arrastre y suelte los widgets que desea visualizar
3. Configure el rango de tiempo para los datos mostrados
4. Guarde los cambios

## Gestión de Embarques

En esta sección se administran todos los embarques de equipos desde la fábrica hasta el taller.

### Registro de Nuevos Embarques

Cuando se le notifica un nuevo embarque desde fábrica:
1. Vaya a "Embarques" > "Nuevo Embarque"
2. Complete la información requerida:
   - Código de embarque (proporcionado por fábrica)
   - Fecha de salida desde origen
   - Fecha estimada de llegada
   - Transportista
   - Detalles de la carga (cantidad y tipos de equipos)
3. Haga clic en "Registrar Embarque"

### Seguimiento de Embarques

Para dar seguimiento a los embarques en tránsito:
1. Vaya a "Embarques" > "En Tránsito"
2. Verá la lista de todos los embarques en camino
3. Para cada embarque puede:
   - Ver su ubicación actual (si el transportista proporciona seguimiento)
   - Actualizar la fecha estimada de llegada
   - Registrar incidencias durante el transporte
   - Generar alertas si hay retrasos significativos

### Ejemplo: Registro de un Nuevo Embarque

**Caso de uso**: Ha recibido notificación de un nuevo embarque desde Suecia.

1. Vaya a "Embarques" > "Nuevo Embarque"
2. Complete la información:
   - Código de embarque: EMB-2023-006
   - Fecha de salida: 10/07/2023
   - Fecha estimada de llegada: 01/09/2023
   - Transportista: Global Shipping
   - Contenido:
     * 2 Tractores Agrícolas 130HP
     * 1 Cosechadora 250HP
     * 3 Sembradoras Neumáticas
   - Documentos: Adjunte los documentos de embarque recibidos
3. Haga clic en "Registrar Embarque"
4. El sistema creará automáticamente registros preliminares de los equipos en estado "en_transito"

## Recepción de Equipos

Esta sección se encarga de la recepción y verificación de los equipos cuando llegan al taller.

### Proceso de Recepción

Cuando llega un embarque:
1. Vaya a "Embarques" > "Recepciones Pendientes"
2. Seleccione el embarque que ha llegado
3. Haga clic en "Iniciar Recepción"
4. Para cada equipo en el embarque:
   - Verifique el número de serie
   - Registre el estado del embalaje
   - Documente cualquier daño visible
   - Tome fotografías si es necesario
   - Confirme la recepción o registre novedades
5. Una vez verificados todos los equipos, haga clic en "Completar Recepción"
6. El sistema actualizará automáticamente el estado de los equipos a "en_taller"

### Registro de Incidencias

Si detecta problemas durante la recepción:
1. En la pantalla de recepción, seleccione el equipo afectado
2. Haga clic en "Registrar Novedad"
3. Seleccione el tipo de problema:
   - Daño en transporte
   - Faltante de componentes
   - Error en documentación
4. Describa detalladamente el problema
5. Adjunte fotografías como evidencia
6. Indique si el problema afecta al proceso de armado
7. El sistema notificará automáticamente a los responsables

### Ejemplo: Recepción con Novedades

**Caso de uso**: Ha llegado el embarque EMB-2023-003 y uno de los equipos presenta daños.

1. Vaya a "Embarques" > "Recepciones Pendientes"
2. Seleccione el embarque EMB-2023-003
3. Haga clic en "Iniciar Recepción"
4. Para la Sembradora Neumática (SM-NEU-23001):
   - Estado del embalaje: "Dañado"
   - Haga clic en "Registrar Novedad"
   - Tipo: "Daño en transporte"
   - Descripción: "El embalaje presenta un golpe significativo en el lateral derecho. Al abrir, se observa que dos discos sembradores están deformados."
   - Adjunte fotos del daño
   - Impacto: "Requiere reemplazo de piezas antes del armado"
5. Complete la recepción del resto de los equipos normalmente
6. Haga clic en "Completar Recepción"
7. El sistema generará automáticamente una solicitud al área de repuestos para las piezas necesarias

## Armado y Preparación

Una vez recibidos, los equipos deben ser armados y preparados para entrega.

### Programación de Armado

Para coordinar el proceso de armado:
1. Vaya a "Equipos" > "Pendientes de Armado"
2. Priorice los equipos según:
   - Fecha de llegada
   - Fecha compromiso de entrega (si ya está vendido)
   - Complejidad del armado
3. Para programar el armado:
   - Seleccione el equipo
   - Haga clic en "Programar Armado"
   - Asigne fechas de inicio y fin estimadas
   - Asigne al equipo de técnicos responsables
   - Registre cualquier requerimiento especial

### Seguimiento del Proceso

Para monitorear el avance del armado:
1. Vaya a "Equipos" > "En Proceso de Armado"
2. Verá el estado actual de cada equipo
3. Puede filtrar por:
   - Técnico asignado
   - Días en proceso
   - Porcentaje de avance
4. Para actualizar el estado:
   - Seleccione el equipo
   - Haga clic en "Actualizar Estado"
   - Registre el porcentaje de avance actual
   - Añada observaciones relevantes

### Control de Calidad Pre-entrega

Antes de que un equipo esté listo para entrega:
1. Vaya a "Equipos" > "Control de Calidad"
2. Seleccione el equipo que ha completado el armado
3. Haga clic en "Iniciar Control de Calidad"
4. Complete la lista de verificación pre-entrega:
   - Funcionamiento de todos los sistemas
   - Niveles de fluidos
   - Ajustes y calibraciones
   - Cosmética y presentación
5. Si todo está correcto, marque como "Aprobado" y el sistema actualizará el estado a "listo_despacho"
6. Si detecta problemas, regístrelos y asigne para corrección

### Ejemplo: Programación de Armado de un Equipo Prioritario

**Caso de uso**: Debe programar el armado de una cosechadora que ya está vendida y tiene fecha de entrega comprometida.

1. Vaya a "Equipos" > "Pendientes de Armado"
2. Identifique la Cosechadora 250HP (CS-250-23002) con estado "Prioridad: Alta"
3. Haga clic en "Programar Armado"
4. Complete la programación:
   - Fecha inicio: 05/06/2023
   - Fecha fin estimada: 15/06/2023
   - Equipo asignado: Carlos Fuentes (especialista en cosechadoras) y Pedro Soto
   - Notas: "Equipo vendido a Cooperativa Valle Central. Fecha compromiso de entrega: 20/06/2023. Cliente solicita instalación de monitor de rendimiento adicional."
5. Haga clic en "Guardar Programación"
6. Coordine con el área de repuestos la disponibilidad del monitor adicional

## Entregas a Clientes

Esta sección gestiona todo el proceso de entrega de equipos a los clientes.

### Programación de Entregas

Cuando un equipo está listo para entrega:
1. Vaya a "Equipos" > "Listos para Entrega"
2. Seleccione el equipo a entregar
3. Haga clic en "Programar Entrega"
4. Complete la información:
   - Fecha y hora de entrega
   - Lugar (taller o campo del cliente)
   - Persona que recibirá el equipo
   - Transportista (si aplica)
   - Documentos requeridos
5. Haga clic en "Confirmar Programación"
6. El sistema enviará notificaciones automáticas al cliente y al equipo de ventas

### Preparación de Documentación

Para cada entrega debe preparar:
1. Vaya a "Documentación" > "Generar Documentos de Entrega"
2. Seleccione el equipo
3. El sistema le permitirá generar:
   - Acta de entrega
   - Certificado de garantía
   - Manual de usuario
   - Programa de mantenciones recomendadas
   - Guía de despacho (si corresponde)
4. Revise y finalice cada documento
5. Imprima el set completo para la entrega

### Proceso de Entrega

El día de la entrega:
1. Vaya a "Equipos" > "Entregas del Día"
2. Seleccione el equipo a entregar
3. Haga clic en "Iniciar Proceso de Entrega"
4. Complete la lista de verificación final
5. Registre los datos de quien recibe:
   - Nombre completo
   - Cargo o relación con el cliente
   - Documento de identidad
   - Firma digital o escaneada
6. Tome fotografías del equipo al momento de la entrega
7. Marque como "Entregado" cuando se complete el proceso
8. El sistema actualizará automáticamente el estado del equipo a "entregado"

### Ejemplo: Entrega de un Tractor en Campo

**Caso de uso**: Debe coordinar la entrega de un tractor directamente en el campo del cliente.

1. Vaya a "Equipos" > "Listos para Entrega"
2. Seleccione el Tractor Agrícola 130HP (TR-130-23002)
3. Haga clic en "Programar Entrega"
4. Complete:
   - Fecha: 18/06/2023
   - Hora: 10:00 AM
   - Lugar: Campo cliente - Fundo El Triunfo, Km 5 camino a San Carlos
   - Contacto: Juan Pérez (Administrador)
   - Transporte: Camión plataforma propio
   - Observaciones: "Cliente solicita capacitación básica para operador durante la entrega. Llevar manual en papel."
5. Coordine con el técnico Carlos Fuentes para que acompañe la entrega y realice la capacitación
6. Prepare toda la documentación y confirme la logística del transporte
7. El día de la entrega, complete el proceso según lo establecido y registre la conformidad del cliente

## Despacho de Repuestos

Esta sección se encarga de la preparación y despacho de pedidos de repuestos.

### Gestión de Pedidos Pendientes

Para atender los pedidos de repuestos:
1. Vaya a "Repuestos" > "Pedidos Pendientes"
2. Verá la lista de todos los pedidos organizados por:
   - Fecha del pedido
   - Prioridad
   - Cliente
3. Seleccione un pedido para ver los detalles
4. Haga clic en "Preparar Pedido"

### Preparación de Pedidos

Durante la preparación:
1. El sistema le mostrará la ubicación en bodega de cada repuesto
2. Marque cada ítem a medida que lo recolecta
3. Si detecta faltantes:
   - Haga clic en "Registrar Faltante"
   - Indique si hay alternativas disponibles
   - El sistema notificará al encargado de inventario
4. Una vez recolectados todos los ítems, haga clic en "Completar Preparación"

### Emisión de Documentos

Para preparar la documentación:
1. Vaya a "Repuestos" > "Documentos de Despacho"
2. Seleccione el pedido preparado
3. Genere los documentos necesarios:
   - Guía de despacho
   - Factura (si aplica)
   - Lista de empaque
   - Instrucciones de instalación (si corresponde)
4. Imprima los documentos requeridos

### Coordinación de Entregas

Para coordinar la entrega o despacho:
1. Vaya a "Repuestos" > "Coordinar Entregas"
2. Seleccione los pedidos listos para despacho
3. Asigne el método de entrega:
   - Retiro en taller
   - Despacho a domicilio
   - Entrega por técnico en terreno
4. Para despachos, asigne:
   - Empresa transportista
   - Fecha estimada de entrega
   - Número de seguimiento (si aplica)
5. Haga clic en "Confirmar Despacho"
6. El sistema actualizará el estado del pedido y enviará notificación al cliente

### Ejemplo: Despacho Urgente de Repuestos

**Caso de uso**: Debe procesar un pedido urgente de repuestos para un cliente en plena temporada de cosecha.

1. Vaya a "Repuestos" > "Pedidos Pendientes"
2. Identifique el pedido de Cooperativa Valle Central marcado como "Urgente"
3. Vea el detalle:
   - 1 Bomba hidráulica (RP-H-001)
   - 2 Kits de empaques (RP-M-002)
4. Haga clic en "Preparar Pedido"
5. Recolecte los repuestos de sus ubicaciones en bodega
6. Complete la preparación
7. Genere los documentos de despacho
8. En "Coordinar Entregas", seleccione:
   - Método: "Despacho prioritario"
   - Transportista: "Envíos Express"
   - Tipo de servicio: "Mismo día"
   - Dirección: "Fundo El Milagro, Km 10 camino a Talca"
   - Contacto: "Luis González, +56987654321"
9. Haga clic en "Confirmar Despacho"
10. Registre el número de seguimiento cuando esté disponible

## Métricas e Informes

### KPIs de Logística

Para monitorear el rendimiento logístico:
1. Vaya a "Logística" > "KPIs"
2. Podrá visualizar métricas como:
   - Tiempo promedio de tránsito de embarques
   - Tiempo promedio de armado por tipo de equipo
   - Porcentaje de entregas a tiempo
   - Tiempo medio de despacho de repuestos
   - Incidencias en transporte

### Generación de Informes

Para crear informes personalizados:
1. Vaya a "Informes" > "Logística"
2. Seleccione el tipo de informe:
   - Embarques y recepciones
   - Productividad de armado
   - Cumplimiento de entregas
   - Despachos de repuestos
3. Configure los filtros y parámetros
4. Seleccione el formato de salida (PDF, Excel, etc.)
5. Haga clic en "Generar Informe"

### Ejemplo: Análisis de Tiempos de Armado

**Caso de uso**: El gerente solicita un informe sobre los tiempos de armado del último trimestre.

1. Vaya a "Informes" > "Logística" > "Productividad de Armado"
2. Configure los filtros:
   - Período: Último trimestre
   - Agrupación: Por tipo de equipo
   - Métricas: Tiempo promedio, tiempo mínimo, tiempo máximo, variación
3. Seleccione "Incluir gráfica comparativa"
4. Formato: PDF
5. Haga clic en "Generar Informe"
6. El sistema procesará los datos y generará un informe detallado que puede ser descargado o compartido

## Preguntas Frecuentes

### ¿Cómo actualizo la fecha estimada de llegada de un embarque?
Vaya a "Embarques" > "En Tránsito", seleccione el embarque que desea modificar, haga clic en "Actualizar Información" y cambie la fecha estimada. El sistema recalculará automáticamente las fechas de los procesos subsecuentes.

### ¿Qué hago si hay un faltante de piezas durante el armado?
El técnico registrará el faltante en el sistema. Usted recibirá una notificación. Vaya a "Equipos" > "Gestión de Faltantes" para validar el requerimiento y coordinar con el área de repuestos la obtención de las piezas necesarias.

### ¿Cómo priorizo los despachos cuando hay múltiples pedidos urgentes?
Utilice los criterios: 1) Equipos en temporada crítica, 2) Distancia al cliente, 3) Disponibilidad de transporte, 4) Hora de solicitud. El sistema también ofrece una sugerencia de priorización basada en estos factores.

### ¿Puedo modificar una entrega ya programada?
Sí, vaya a "Equipos" > "Entregas Programadas", seleccione la entrega, haga clic en "Modificar Programación" y realice los cambios necesarios. El sistema notificará automáticamente a todas las partes involucradas.

### ¿Cómo registro un retraso en la entrega de un pedido por parte del transportista?
Vaya a "Repuestos" > "Seguimiento de Despachos", seleccione el pedido afectado, haga clic en "Registrar Incidencia" y documente el retraso. El sistema actualizará la fecha estimada y notificará al cliente. 