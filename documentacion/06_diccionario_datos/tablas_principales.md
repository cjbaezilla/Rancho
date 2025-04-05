# Tablas Principales

Esta sección documenta las tablas principales del sistema "Rancho", que representan las entidades fundamentales del negocio.

## Tabla: `clientes`

Almacena la información de los clientes del taller de maquinaria agrícola.

| Campo | Tipo | Descripción | Restricciones |
|-------|------|-------------|---------------|
| `id_cliente` | INT UNSIGNED | Identificador único del cliente | PK, AUTO_INCREMENT |
| `nombre` | VARCHAR(100) | Nombre o razón social del cliente | NOT NULL |
| `rut` | VARCHAR(12) | RUT o identificación tributaria | UNIQUE |
| `direccion` | VARCHAR(200) | Dirección física del cliente | |
| `comuna` | VARCHAR(50) | Comuna del cliente | |
| `region` | VARCHAR(50) | Región del cliente | |
| `telefono` | VARCHAR(20) | Número de contacto | |
| `email` | VARCHAR(100) | Correo electrónico | |
| `fecha_registro` | DATE | Fecha de ingreso al sistema | NOT NULL |
| `ultimo_contacto` | DATETIME | Fecha y hora de última interacción | |
| `activo` | BOOLEAN | Indica si ha tenido actividad en últimos 12 meses | DEFAULT TRUE |

## Tabla: `tipo_equipos`

Catálogo de los tipos de equipos/máquinas disponibles para venta y mantención.

| Campo | Tipo | Descripción | Restricciones |
|-------|------|-------------|---------------|
| `id_tipo_equipo` | INT UNSIGNED | Identificador único del tipo de equipo | PK, AUTO_INCREMENT |
| `nombre` | VARCHAR(100) | Nombre del tipo de equipo | NOT NULL |
| `descripcion` | TEXT | Descripción detallada | |
| `fabricante` | VARCHAR(100) | Fabricante del equipo | |
| `pais_origen` | VARCHAR(50) | País de origen | DEFAULT 'Suecia' |
| `tiempo_garantia_anios` | INT | Tiempo de garantía en años | NOT NULL, DEFAULT 2 |
| `hectareas_garantia` | INT | Hectáreas cubiertas por garantía | NOT NULL, DEFAULT 1000 |
| `tiempo_armado_estimado` | INT | Tiempo estimado de armado en días | |

## Tabla: `equipos`

Registro individual de equipos/máquinas específicos.

| Campo | Tipo | Descripción | Restricciones |
|-------|------|-------------|---------------|
| `id_equipo` | INT UNSIGNED | Identificador único del equipo | PK, AUTO_INCREMENT |
| `id_tipo_equipo` | INT UNSIGNED | Tipo de equipo al que pertenece | FK -> tipo_equipos |
| `numero_serie` | VARCHAR(50) | Número de serie único | UNIQUE, NOT NULL |
| `fecha_fabricacion` | DATE | Fecha de fabricación | |
| `fecha_salida_origen` | DATE | Fecha de salida desde origen | |
| `fecha_llegada_taller` | DATE | Fecha de recepción en taller | |
| `fecha_armado_completo` | DATE | Fecha de finalización de armado | |
| `fecha_entrega_programada` | DATE | Fecha planificada de entrega | |
| `fecha_entrega_real` | DATE | Fecha efectiva de entrega | |
| `id_cliente` | INT UNSIGNED | Cliente propietario | FK -> clientes, NULL si no vendido |
| `estado_actual` | ENUM | Estado actual del equipo | NOT NULL, DEFAULT 'en_transito' |
| `hectareas_trabajadas` | DECIMAL(10,2) | Total de hectáreas trabajadas | NOT NULL, DEFAULT 0 |
| `ultima_actualizacion_hectareas` | DATE | Fecha última actualización hectáreas | |
| `notas` | TEXT | Observaciones adicionales | |

## Tabla: `categorias_repuestos`

Categorías para clasificar los repuestos según su tipo.

| Campo | Tipo | Descripción | Restricciones |
|-------|------|-------------|---------------|
| `id_categoria` | INT UNSIGNED | Identificador único de categoría | PK, AUTO_INCREMENT |
| `nombre` | VARCHAR(100) | Nombre de la categoría | NOT NULL |
| `descripcion` | TEXT | Descripción de la categoría | |

## Tabla: `repuestos`

Catálogo de repuestos disponibles para los equipos.

| Campo | Tipo | Descripción | Restricciones |
|-------|------|-------------|---------------|
| `id_repuesto` | INT UNSIGNED | Identificador único del repuesto | PK, AUTO_INCREMENT |
| `codigo` | VARCHAR(50) | Código único del repuesto | UNIQUE, NOT NULL |
| `nombre` | VARCHAR(100) | Nombre del repuesto | NOT NULL |
| `descripcion` | TEXT | Descripción detallada | |
| `id_categoria` | INT UNSIGNED | Categoría del repuesto | FK -> categorias_repuestos |
| `precio_venta` | DECIMAL(10,2) | Precio de venta al cliente | NOT NULL |
| `costo` | DECIMAL(10,2) | Costo de adquisición | NOT NULL |
| `stock_actual` | INT | Cantidad disponible en inventario | NOT NULL, DEFAULT 0 |
| `stock_minimo` | INT | Nivel mínimo para alerta | NOT NULL, DEFAULT 5 |
| `tiempo_entrega_promedio` | INT | Tiempo promedio de entrega en días | |
| `compatible_con` | TEXT | Descripción de compatibilidad | |

## Tabla: `tecnicos`

Registro de técnicos que realizan mantenciones y reparaciones.

| Campo | Tipo | Descripción | Restricciones |
|-------|------|-------------|---------------|
| `id_tecnico` | INT UNSIGNED | Identificador único del técnico | PK, AUTO_INCREMENT |
| `nombre` | VARCHAR(100) | Nombre completo | NOT NULL |
| `rut` | VARCHAR(12) | RUT o identificación | UNIQUE |
| `especialidad` | VARCHAR(100) | Área de especialización | |
| `telefono` | VARCHAR(20) | Número de contacto | |
| `email` | VARCHAR(100) | Correo electrónico | |
| `activo` | BOOLEAN | Estado laboral actual | DEFAULT TRUE |

## Tabla: `tipo_mantencion`

Tipos de mantenciones disponibles para los equipos.

| Campo | Tipo | Descripción | Restricciones |
|-------|------|-------------|---------------|
| `id_tipo_mantencion` | INT UNSIGNED | Identificador único | PK, AUTO_INCREMENT |
| `nombre` | VARCHAR(100) | Nombre del tipo de mantención | NOT NULL |
| `descripcion` | TEXT | Descripción detallada | |
| `es_preventiva` | BOOLEAN | Indica si es preventiva o correctiva | DEFAULT TRUE |

## Tabla: `embarques`

Registro de embarques de equipos desde el origen.

| Campo | Tipo | Descripción | Restricciones |
|-------|------|-------------|---------------|
| `id_embarque` | INT UNSIGNED | Identificador único | PK, AUTO_INCREMENT |
| `codigo_embarque` | VARCHAR(50) | Código de seguimiento | UNIQUE, NOT NULL |
| `fecha_salida_origen` | DATE | Fecha de salida desde origen | NOT NULL |
| `fecha_estimada_llegada` | DATE | Fecha estimada de llegada | NOT NULL |
| `fecha_llegada_real` | DATE | Fecha efectiva de llegada | |
| `estado` | ENUM | Estado del embarque | DEFAULT 'en_transito' |
| `notas` | TEXT | Observaciones adicionales | | 