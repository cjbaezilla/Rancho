# Manual de Usuario: Administrador del Sistema

## Introducción

Bienvenido al manual del Administrador del Sistema de Gestión "Rancho". Como administrador, usted tiene acceso completo a todas las funcionalidades del sistema y es responsable de la configuración general, gestión de usuarios, y supervisión de todos los procesos.

## Índice de Contenidos

1. [Acceso al Sistema](#acceso-al-sistema)
2. [Panel de Control del Administrador](#panel-de-control-del-administrador)
3. [Gestión de Usuarios](#gestión-de-usuarios)
4. [Configuración General](#configuración-general)
5. [Administración de Catálogos](#administración-de-catálogos)
6. [Informes y Métricas](#informes-y-métricas)
7. [Auditoría y Seguridad](#auditoría-y-seguridad)
8. [Respaldo y Mantenimiento](#respaldo-y-mantenimiento)

## Acceso al Sistema

### Inicio de Sesión

1. Acceda a la URL del sistema: `https://rancho.sistema.com`
2. Ingrese sus credenciales de administrador:
   - Usuario: Su nombre de usuario (generalmente su correo electrónico)
   - Contraseña: Su contraseña personal
3. Haga clic en "Iniciar Sesión"

![Ejemplo de pantalla de inicio de sesión](../img/admin_login.png)

### Recuperación de Contraseña

Si olvidó su contraseña:
1. Haga clic en "¿Olvidó su contraseña?"
2. Ingrese su correo electrónico registrado
3. Siga las instrucciones enviadas a su correo para restablecer su contraseña

## Panel de Control del Administrador

El panel de control es su centro de operaciones, desde donde puede acceder a todas las funcionalidades administrativas.

### Componentes Principales

- **Resumen de Actividad**: Visualiza las operaciones recientes en el sistema
- **KPIs Principales**: Muestra indicadores clave de rendimiento
- **Alertas del Sistema**: Notificaciones sobre eventos importantes
- **Accesos Rápidos**: Enlaces a las funciones más utilizadas

### Personalización del Panel

Puede personalizar su panel de control según sus preferencias:
1. Haga clic en "Configurar Panel"
2. Arrastre y suelte los widgets que desea visualizar
3. Configure el rango de tiempo para los datos mostrados
4. Guarde los cambios

## Gestión de Usuarios

Como administrador, es responsable de gestionar todos los usuarios del sistema, incluyendo técnicos, representantes de atención al cliente, y otros administradores.

### Creación de Nuevos Usuarios

1. Vaya a "Administración" > "Usuarios" > "Nuevo Usuario"
2. Complete la información requerida:
   - Nombre completo
   - Correo electrónico (será el nombre de usuario)
   - Perfil de usuario (Administrador, Técnico, Atención al Cliente, etc.)
   - Permisos específicos
3. Haga clic en "Crear Usuario"
4. El sistema enviará automáticamente un correo al nuevo usuario con instrucciones para establecer su contraseña

### Edición de Usuarios Existentes

1. Vaya a "Administración" > "Usuarios"
2. Busque el usuario que desea modificar utilizando los filtros disponibles
3. Haga clic en el ícono de edición
4. Actualice la información necesaria
5. Guarde los cambios

### Gestión de Permisos

Los permisos determinan qué acciones puede realizar cada usuario en el sistema.

1. Vaya a "Administración" > "Perfiles y Permisos"
2. Seleccione el perfil que desea configurar
3. Marque o desmarque los permisos específicos
4. También puede crear perfiles personalizados haciendo clic en "Nuevo Perfil"

### Ejemplo: Creación de un Técnico Especializado

**Caso de uso**: Necesita crear un usuario para un nuevo técnico especializado en sistemas hidráulicos.

1. Vaya a "Administración" > "Usuarios" > "Nuevo Usuario"
2. Complete la información:
   - Nombre: Juan Martínez Silva
   - Correo: jmartinez@tallermaquinaria.cl
   - Perfil: Técnico
   - Especialidad: Sistemas hidráulicos
   - Departamentos: Mantención
3. En la sección de permisos, asegúrese de que tenga acceso a:
   - Módulo de Órdenes de Trabajo (lectura/escritura)
   - Módulo de Equipos (lectura)
   - Módulo de Repuestos (lectura)
4. Haga clic en "Crear Usuario"

## Configuración General

### Parámetros del Sistema

Aquí puede configurar los parámetros generales que afectan al funcionamiento del sistema:

1. Vaya a "Administración" > "Configuración General"
2. Configure los siguientes aspectos:
   - **Información de la Empresa**: Nombre, dirección, teléfono, logotipo
   - **Configuración Regional**: Formato de fecha, moneda, idioma
   - **Parámetros de Notificaciones**: Correos automáticos, recordatorios
   - **Parámetros de Mantenciones**: Intervalos predeterminados, tolerancias

### Configuración de Correo Electrónico

Configure el sistema para enviar notificaciones por correo:

1. Vaya a "Administración" > "Configuración de Correo"
2. Configure el servidor SMTP:
   - Servidor: (ej. smtp.empresa.com)
   - Puerto: (ej. 587)
   - Autenticación: Usuario y contraseña
   - Correo remitente: (ej. notificaciones@tallermaquinaria.cl)
3. Guarde los cambios

### Personalización de Plantillas

Personalice las plantillas de correos y documentos generados por el sistema:

1. Vaya a "Administración" > "Plantillas"
2. Seleccione la plantilla que desea modificar (ej. "Notificación de Mantención Programada")
3. Utilice el editor para modificar el contenido
4. Puede utilizar variables del sistema entre llaves (ej. {NOMBRE_CLIENTE})
5. Guarde los cambios

## Administración de Catálogos

El sistema utiliza diversos catálogos que deben ser administrados:

### Tipos de Equipos

1. Vaya a "Administración" > "Catálogos" > "Tipos de Equipos"
2. Puede agregar, editar o desactivar tipos de equipos
3. Para cada tipo, debe especificar:
   - Nombre
   - Descripción
   - Fabricante
   - País de origen
   - Tiempo de garantía
   - Hectáreas de garantía
   - Tiempo estimado de armado

### Ejemplo: Agregar un Nuevo Tipo de Equipo

**Caso de uso**: La empresa ha comenzado a distribuir un nuevo modelo de tractor.

1. Vaya a "Administración" > "Catálogos" > "Tipos de Equipos" > "Nuevo"
2. Complete la información:
   - Nombre: Tractor Agrícola 150HP
   - Descripción: Tractor de alta potencia con cabina climatizada
   - Fabricante: Valtra
   - País de origen: Suecia
   - Tiempo de garantía: 2 años
   - Hectáreas de garantía: 1200
   - Tiempo estimado de armado: 6 días
3. Haga clic en "Guardar"

### Categorías de Repuestos

1. Vaya a "Administración" > "Catálogos" > "Categorías de Repuestos"
2. Administre las categorías existentes o cree nuevas

### Tipos de Mantención

1. Vaya a "Administración" > "Catálogos" > "Tipos de Mantención"
2. Gestione los diferentes tipos de mantenciones que ofrece el taller

## Informes y Métricas

Como administrador, tiene acceso a todos los informes y métricas del sistema.

### Informes Disponibles

- **Rendimiento del Taller**: Órdenes completadas, tiempo promedio, etc.
- **Análisis de Clientes**: Satisfacción, frecuencia de servicios, etc.
- **KPIs por Categoría**: Logística, Mantenciones, Postventa, etc.
- **Informes Financieros**: Ingresos, costos, márgenes, etc.

### Generación de Informes Personalizados

1. Vaya a "Informes" > "Personalizado"
2. Seleccione las métricas que desea incluir
3. Configure filtros (rango de fechas, clientes específicos, etc.)
4. Seleccione el formato de salida (PDF, Excel, etc.)
5. Haga clic en "Generar Informe"

### Configuración de Informes Programados

Configure informes que se generen automáticamente:

1. Vaya a "Informes" > "Programar Informe"
2. Seleccione el tipo de informe
3. Configure la frecuencia (diaria, semanal, mensual)
4. Especifique los destinatarios
5. Haga clic en "Guardar Programación"

## Auditoría y Seguridad

### Registro de Auditoría

El sistema mantiene un registro de todas las acciones realizadas:

1. Vaya a "Administración" > "Auditoría"
2. Utilice los filtros para buscar acciones específicas:
   - Por usuario
   - Por fecha
   - Por tipo de acción
   - Por tabla afectada
3. Revise los detalles de cada acción (datos anteriores y nuevos)

### Políticas de Seguridad

Configure las políticas de seguridad del sistema:

1. Vaya a "Administración" > "Seguridad"
2. Configure:
   - Complejidad de contraseñas
   - Frecuencia de cambio de contraseñas
   - Intentos fallidos permitidos
   - Tiempo de inactividad para cierre de sesión
3. Guarde los cambios

## Respaldo y Mantenimiento

### Respaldo de Datos

Configure y gestione los respaldos del sistema:

1. Vaya a "Administración" > "Respaldo"
2. Configure la frecuencia de respaldos automáticos
3. Especifique la ubicación de almacenamiento
4. También puede iniciar un respaldo manual haciendo clic en "Iniciar Respaldo"

### Mantenimiento del Sistema

Realice tareas de mantenimiento:

1. Vaya a "Administración" > "Mantenimiento"
2. Puede realizar:
   - Optimización de la base de datos
   - Limpieza de archivos temporales
   - Verificación de integridad de datos

### Actualizaciones del Sistema

Gestione las actualizaciones del software:

1. Vaya a "Administración" > "Actualizaciones"
2. Revise si hay actualizaciones disponibles
3. Lea las notas de la versión
4. Inicie la actualización (se recomienda hacer un respaldo previo)

## Preguntas Frecuentes

### ¿Cómo puedo cambiar el logotipo de la empresa en los informes?
Vaya a "Administración" > "Configuración General" > "Información de la Empresa" y cargue el nuevo logotipo.

### ¿Cómo elimino un usuario que ya no trabaja en la empresa?
En lugar de eliminar usuarios, se recomienda desactivarlos. Vaya a "Administración" > "Usuarios", busque el usuario y cambie su estado a "Inactivo".

### ¿Puedo personalizar los correos electrónicos que envía el sistema?
Sí, vaya a "Administración" > "Plantillas" y edite las plantillas de correo según sus necesidades.

### ¿Cómo configuro nuevos tipos de mantención?
Vaya a "Administración" > "Catálogos" > "Tipos de Mantención" > "Nuevo" y complete la información requerida. 