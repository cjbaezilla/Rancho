# Preguntas Frecuentes

Esta sección recopila las preguntas más frecuentes sobre el sistema "Rancho" para la gestión de talleres mecánicos especializados en maquinaria agrícola.

## Preguntas Generales del Sistema

### ¿Cuál es el propósito principal del sistema "Rancho"?
El sistema "Rancho" está diseñado para gestionar todas las operaciones de un taller mecánico especializado en maquinaria agrícola, desde la recepción y armado de equipos nuevos hasta el mantenimiento continuo, reparaciones y servicio postventa.

### ¿Qué información necesito para comenzar a usar el sistema?
Para iniciar con el sistema, se requiere registrar la información básica de su taller, incluyendo:
- Datos de clientes
- Catálogo de equipos y tipos de equipos
- Inventario de repuestos
- Personal técnico
- Tipos de mantenciones que ofrece

### ¿Cómo se garantiza la seguridad de los datos?
El sistema implementa múltiples capas de seguridad:
- Autenticación de usuarios con contraseñas cifradas
- Roles de acceso diferenciados
- Auditoría de cambios en tablas principales
- Copias de seguridad automáticas
- Cifrado de conexiones al servidor

## Gestión de Clientes y Equipos

### ¿Cómo registro un equipo nuevo que llega al taller?
1. Acceda al módulo "Gestión de Equipos"
2. Seleccione "Registrar Nuevo Equipo"
3. Complete la información del embarque y recepción
4. Seleccione el tipo de equipo correspondiente
5. Ingrese el número de serie y demás datos técnicos
6. Si ya está vendido, asocie el cliente; de lo contrario, déjelo sin asociar

### ¿Cómo transfiero un equipo de un cliente a otro?
1. Acceda al módulo "Gestión de Equipos"
2. Busque y seleccione el equipo a transferir
3. Utilice la opción "Cambiar Propietario"
4. Seleccione el nuevo cliente
5. Complete la información de la transferencia
6. El historial del equipo se mantendrá, pero se asociará al nuevo cliente

### ¿Es posible registrar múltiples equipos para un mismo cliente?
Sí, un cliente puede tener asociados múltiples equipos. El sistema permite visualizar todos los equipos de un cliente desde su ficha y generar reportes consolidados de mantenciones, garantías y hectáreas trabajadas.

## Mantenciones y Reparaciones

### ¿Cómo se programa una mantención preventiva?
1. Puede programarse automáticamente por hectáreas o tiempo
2. Manualmente desde el módulo "Gestión de Mantenciones"
3. A solicitud del cliente desde "Agendamientos"

El sistema alertará cuando un equipo esté próximo a requerir mantención según los parámetros configurados.

### ¿Cómo gestiono las garantías de los equipos?
El sistema:
- Registra automáticamente el período de garantía según tipo de equipo
- Calcula las hectáreas trabajadas vs. límite de garantía
- Al crear órdenes de trabajo, indica si está en garantía
- Genera reportes de servicios realizados dentro y fuera de garantía

### ¿Puedo realizar mantenciones en terreno?
Sí, el sistema permite registrar mantenciones en taller y en terreno:
1. En el agendamiento, seleccione la opción "en campo"
2. Complete la dirección donde se realizará
3. El técnico podrá registrar la orden de trabajo desde la aplicación móvil

## Repuestos e Inventario

### ¿Cómo identifico qué repuestos son compatibles con un equipo?
El sistema ofrece varias formas:
- Desde la ficha del equipo puede ver repuestos compatibles
- Al crear una orden, muestra automáticamente repuestos compatibles
- La tabla de compatibilidad permite buscar por tipo de equipo o repuesto

### ¿Cómo se controla el stock mínimo de repuestos?
1. Cada repuesto tiene configurado un stock mínimo
2. El sistema genera alertas cuando se alcanza o se está por alcanzar
3. Se incluyen en los reportes diarios de logística
4. Las alertas aparecen en el dashboard de administración

### ¿Se puede registrar un pedido de repuestos para un cliente?
Sí, el sistema permite:
- Crear pedidos de repuestos independientes de mantenciones
- Asociar pedidos a equipos específicos
- Seguir el estado desde solicitud hasta entrega
- Registrar precios y márgenes específicos por pedido

## Reportes y Métricas

### ¿Qué indicadores de desempeño (KPIs) ofrece el sistema?
El sistema incluye 5 categorías de KPIs:
1. **Logística y Embarque**: tiempos de llegada, armado y entrega
2. **Mantenciones**: cumplimiento, tiempos entre fallas, tiempos de reparación
3. **Postventa y Repuestos**: satisfacción, disponibilidad, tiempos de entrega
4. **Trazabilidad y Registro**: histórico de equipos, fallas comunes
5. **Cliente y Negocio**: rentabilidad, recurrencia, valor cliente

### ¿Puedo personalizar los reportes?
El sistema ofrece:
- Reportes predefinidos para cada área
- Filtros configurables por fechas, clientes, tipos de equipo, etc.
- Exportación a Excel, PDF y otros formatos
- API para integración con sistemas de Business Intelligence

### ¿Cómo se calcula el índice NPS de satisfacción?
El NPS (Net Promoter Score) se calcula automáticamente:
1. Las encuestas clasifican respuestas en: Promotores (9-10), Pasivos (7-8), Detractores (0-6)
2. Se calcula: % Promotores - % Detractores
3. El resultado genera un valor entre -100 y +100
4. El sistema ofrece reportes históricos y por segmentos

## Problemas Comunes

### El sistema muestra alerta de "Stock crítico" pero tengo suficientes repuestos
Verifique la configuración de stock mínimo para ese repuesto:
1. Acceda a "Gestión de Repuestos"
2. Busque el repuesto específico
3. Edite el valor de "Stock Mínimo"
4. Guarde los cambios

### No puedo finalizar una orden de trabajo
Las causas comunes son:
- Faltan campos obligatorios (solución aplicada, horas de trabajo)
- No se han registrado repuestos utilizados
- La fecha de finalización es anterior a la fecha de inicio
- No tiene permisos suficientes (solo técnicos y administradores pueden finalizar)

### No aparecen todos los equipos en el reporte de mantenciones
Verifique:
- Los filtros aplicados al reporte
- El estado de los equipos (debe incluir equipos entregados)
- La fecha de filtro (debe cubrir las fechas de las mantenciones)
- Si los equipos tienen programación de mantenciones asociada 