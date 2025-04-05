# Gestión de Repuestos

## Descripción General

El módulo de Gestión de Repuestos es responsable de administrar todo el ciclo de vida de los repuestos necesarios para el mantenimiento y reparación de los equipos agrícolas. Este módulo permite controlar el inventario, gestionar pedidos, analizar demanda y garantizar la disponibilidad oportuna de componentes críticos para mantener la operatividad de la maquinaria.

## Estructura de Datos

El módulo se basa en las siguientes tablas principales de la base de datos:

### 1. Categorías de Repuestos (`categorias_repuestos`)
- Clasificación organizada de los diferentes tipos de repuestos
- Facilita la búsqueda y organización del inventario
- Permite análisis segmentados por tipo de componente

### 2. Repuestos (`repuestos`)
- Catálogo maestro de todos los repuestos disponibles
- Incluye información detallada como códigos, precios, cantidades y tiempos de entrega
- Gestiona niveles de stock y puntos de reorden

### 3. Compatibilidad de Repuestos (`compatibilidad_repuestos`)
- Establece relaciones entre repuestos y tipos de equipos
- Garantiza que se utilicen los componentes adecuados en cada máquina
- Facilita recomendaciones automáticas de repuestos según el equipo

### 4. Detalle de Repuestos en Órdenes (`detalle_repuestos_orden`)
- Registra los repuestos utilizados en cada orden de trabajo
- Controla cantidades, precios y descuentos aplicados
- Permite análisis de uso de repuestos por tipo de mantención

### 5. Pedidos de Repuestos (`pedidos_repuestos`)
- Gestiona solicitudes de compra de nuevos repuestos
- Controla todo el ciclo desde la solicitud hasta la recepción
- Permite seguimiento de tiempos y cumplimiento de proveedores

### 6. Detalle de Pedidos (`detalle_pedidos_repuestos`)
- Especifica los ítems individuales en cada pedido
- Registra cantidades, precios y estados por ítem
- Facilita la recepción parcial de pedidos

### 7. Tiempos de Entrega de Repuestos (`tiempos_entrega_repuestos`)
- Monitorea y analiza los tiempos reales de entrega
- Compara con tiempos prometidos para evaluar proveedores
- Permite ajustar tiempos estimados para futuros pedidos

### 8. Ranking de Repuestos Demandados (`ranking_repuestos_demandados`)
- Analiza patrones de consumo de repuestos
- Identifica componentes críticos y de alta rotación
- Apoya decisiones de inventario y negociaciones con proveedores

## Funcionalidades Principales

### Gestión de Inventario
- Control preciso de existencias en tiempo real
- Alertas automáticas para niveles de stock bajo
- Planificación de reposición basada en historial y proyecciones

### Pedidos y Aprovisionamiento
- Creación y seguimiento de órdenes de compra
- Gestión de relaciones con proveedores
- Evaluación de tiempos de entrega y cumplimiento

### Compatibilidad y Recomendaciones
- Verificación automática de compatibilidad con equipos
- Sugerencias de repuestos alternativos cuando no hay disponibilidad
- Paquetes predefinidos para mantenimientos programados

### Análisis y Reportes
- Consumo histórico por tipo de repuesto, equipo y cliente
- Proyección de demanda futura para planificación
- Análisis de costos y márgenes en venta de repuestos

### Integración con Mantenciones
- Reserva anticipada de repuestos para mantenciones programadas
- Verificación automática de disponibilidad al agendar servicios
- Actualización de inventario en tiempo real al utilizar repuestos

## Indicadores Clave (KPIs)

1. **Disponibilidad de Repuestos**
   - Porcentaje de solicitudes satisfechas inmediatamente
   - Tiempo promedio para obtener repuestos no disponibles
   - Nivel de servicio por categoría de criticidad

2. **Eficiencia de Inventario**
   - Rotación de inventario por categoría
   - Valor del inventario inmovilizado
   - Precisión del inventario físico vs. sistema

3. **Desempeño de Proveedores**
   - Cumplimiento de tiempos de entrega prometidos
   - Calidad de los repuestos recibidos
   - Competitividad de precios

4. **Impacto en Servicio**
   - Mantenciones retrasadas por falta de repuestos
   - Tiempo adicional de equipo detenido por espera de repuestos
   - Satisfacción del cliente en relación a disponibilidad de componentes

## Procesos Principales

### Proceso de Gestión de Inventario
1. Registro inicial de repuestos en el sistema
2. Actualización automática de stock al recibir o utilizar repuestos
3. Verificación periódica (inventario físico)
4. Análisis y ajuste de niveles óptimos de inventario

### Proceso de Pedido de Repuestos
1. Identificación de necesidad (manual o automática)
2. Generación de orden de compra
3. Seguimiento del estado del pedido
4. Recepción y verificación
5. Actualización de inventario

### Proceso de Asignación a Mantenciones
1. Verificación de disponibilidad para mantenciones programadas
2. Reserva anticipada de componentes
3. Preparación de kits de mantenimiento
4. Registro de consumo real
5. Devolución de excedentes al inventario

## Integración con Otros Módulos

### Con Gestión de Equipos
- Verificación de compatibilidad de repuestos con equipos específicos
- Historial de repuestos utilizados por equipo
- Análisis de fallas recurrentes y consumo de componentes

### Con Gestión de Mantenciones
- Planificación anticipada de necesidades de repuestos
- Disponibilidad inmediata para mantenciones correctivas
- Actualización automática de costos de mantención

### Con Logística y Embarques
- Coordinación de despachos de repuestos a campo
- Optimización de rutas de distribución
- Seguimiento de tiempos de entrega

### Con Servicio Post-venta
- Atención inmediata de solicitudes urgentes de clientes
- Información precisa sobre disponibilidad y tiempos de entrega
- Histórico de consumo por cliente para personalizar servicio 