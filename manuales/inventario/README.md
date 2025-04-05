# Manual de Usuario: Encargado de Inventario

## Introducción

Bienvenido al manual del Encargado de Inventario del Sistema de Gestión "Rancho". Como encargado de inventario, usted es responsable de gestionar el stock de repuestos, realizar pedidos a proveedores, controlar las existencias, y asegurar que el taller cuente con los insumos necesarios para realizar las mantenciones y reparaciones de manera oportuna.

## Índice de Contenidos

1. [Acceso al Sistema](#acceso-al-sistema)
2. [Panel de Control de Inventario](#panel-de-control-de-inventario)
3. [Gestión de Catálogo](#gestión-de-catálogo)
4. [Control de Stock](#control-de-stock)
5. [Pedidos a Proveedores](#pedidos-a-proveedores)
6. [Recepción de Mercadería](#recepción-de-mercadería)
7. [Análisis e Informes](#análisis-e-informes)
8. [Preguntas Frecuentes](#preguntas-frecuentes)

## Acceso al Sistema

### Inicio de Sesión

1. Acceda a la URL del sistema: `https://rancho.sistema.com`
2. Ingrese sus credenciales:
   - Usuario: Su correo electrónico corporativo
   - Contraseña: Su contraseña personal
3. Haga clic en "Iniciar Sesión"

![Ejemplo de pantalla de inicio de sesión](../img/inventario_login.png)

### Recuperación de Contraseña

Si olvidó su contraseña:
1. Haga clic en "¿Olvidó su contraseña?"
2. Ingrese su correo electrónico registrado
3. Siga las instrucciones enviadas a su correo para restablecer su contraseña

## Panel de Control de Inventario

El panel de control es su centro de operaciones diarias, diseñado para facilitar la gestión de inventario.

### Componentes Principales

- **Alertas de Stock**: Muestra repuestos bajo el nivel mínimo
- **Pedidos Pendientes**: Órdenes realizadas a proveedores en proceso
- **Recepciones Programadas**: Entregas de proveedores para hoy/esta semana
- **Solicitudes Internas**: Peticiones de repuestos del área de taller
- **KPIs de Inventario**: Indicadores clave de gestión de inventario

### Personalización del Panel

Puede personalizar su panel según sus preferencias:
1. Haga clic en "Configurar Panel"
2. Arrastre y suelte los widgets que desea visualizar
3. Configure el rango de tiempo para los datos mostrados
4. Guarde los cambios

## Gestión de Catálogo

En esta sección se administra toda la información relacionada con los repuestos disponibles.

### Búsqueda de Repuestos

Para encontrar repuestos en el catálogo:
1. Utilice la barra de búsqueda principal
2. Puede buscar por:
   - Código
   - Nombre
   - Descripción
   - Categoría
   - Equipos compatibles
3. Utilice los filtros avanzados para refinar los resultados

### Creación de Nuevos Repuestos

Para agregar un nuevo repuesto al catálogo:
1. Vaya a "Catálogo" > "Nuevo Repuesto"
2. Complete la información requerida:
   - Código único
   - Nombre
   - Descripción detallada
   - Categoría
   - Fabricante
   - Información de costos y precios
   - Stock mínimo recomendado
   - Ubicación en bodega
3. En la sección "Compatibilidad", seleccione los equipos con los que es compatible
4. Adjunte imágenes o documentación técnica si está disponible
5. Haga clic en "Guardar Repuesto"

### Actualización de Información

Para mantener actualizada la información:
1. Busque el repuesto que desea modificar
2. Haga clic en "Editar"
3. Actualice los campos necesarios
4. Haga clic en "Guardar Cambios"

### Ejemplo: Registro de un Nuevo Repuesto

**Caso de uso**: Ha llegado un nuevo modelo de filtro hidráulico que debe agregarse al catálogo.

1. Vaya a "Catálogo" > "Nuevo Repuesto"
2. Complete la información:
   - Código: RP-H-010
   - Nombre: Filtro hidráulico de alta presión
   - Descripción: "Filtro para sistema hidráulico de alta presión, con capacidad de filtrado de 10 micrones y resistente a presiones de hasta 350 bar"
   - Categoría: Hidráulica
   - Fabricante: HydroPure
   - Costo: $45.000
   - Precio de venta: $75.000
   - Stock mínimo: 5 unidades
   - Ubicación: Estante H-3, Posición 4
3. En "Compatibilidad", seleccione:
   - Tractor Agrícola 130HP
   - Tractor Agrícola 150HP
   - Cosechadora 250HP
4. Adjunte la imagen del producto y la ficha técnica del fabricante
5. Haga clic en "Guardar Repuesto"

## Control de Stock

Esta sección le permite gestionar las existencias de repuestos en el inventario.

### Visualización de Inventario

Para revisar el estado actual del inventario:
1. Vaya a "Inventario" > "Estado Actual"
2. Puede filtrar por:
   - Categoría
   - Ubicación
   - Nivel de stock (bajo mínimo, óptimo, exceso)
   - Rotación (alta, media, baja)
3. Para cada repuesto podrá ver:
   - Stock actual
   - Stock mínimo
   - Stock óptimo
   - Últimos movimientos
   - Pedidos en curso

### Ajustes de Inventario

Para corregir discrepancias:
1. Vaya a "Inventario" > "Ajustes"
2. Haga clic en "Nuevo Ajuste"
3. Busque el repuesto a ajustar
4. Ingrese la cantidad actual correcta
5. Seleccione el motivo del ajuste:
   - Inventario físico
   - Mermas
   - Devolución
   - Corrección administrativa
6. Agregue observaciones detallando la razón
7. Haga clic en "Registrar Ajuste"

### Inventario Físico

Para realizar un conteo físico:
1. Vaya a "Inventario" > "Inventario Físico" > "Nuevo Conteo"
2. Seleccione el alcance:
   - Completo
   - Por categoría
   - Por ubicación
3. Genere la planilla de conteo
4. Realice el conteo físico usando la planilla o dispositivo móvil
5. Ingrese las cantidades contadas
6. El sistema identificará las diferencias
7. Revise las discrepancias y realice un segundo conteo si es necesario
8. Apruebe el ajuste final

### Ejemplo: Realización de Ajuste por Merma

**Caso de uso**: Durante el despacho de un pedido, detecta que dos unidades de aceite hidráulico están dañadas.

1. Vaya a "Inventario" > "Ajustes"
2. Haga clic en "Nuevo Ajuste"
3. Busque "Aceite hidráulico 20L" (RP-L-001)
4. Información actual:
   - Stock según sistema: 25 unidades
   - Stock real: 23 unidades (descontando las dañadas)
5. Ingrese 23 como cantidad correcta
6. Motivo: "Merma"
7. Observaciones: "Se detectaron 2 envases con sellos rotos y evidencia de filtración. Se han separado para disposición adecuada."
8. Haga clic en "Registrar Ajuste"
9. El sistema actualizará el inventario y registrará la merma en los informes correspondientes

## Pedidos a Proveedores

Esta sección maneja todo el proceso de solicitud de repuestos a proveedores.

### Creación de Pedidos

Para generar un nuevo pedido:
1. Vaya a "Proveedores" > "Nuevo Pedido"
2. Seleccione el proveedor
3. Añada los repuestos requeridos:
   - Manualmente seleccionándolos del catálogo
   - Automáticamente basado en niveles de stock (haga clic en "Sugerir Pedido")
   - Desde solicitudes pendientes del taller
4. Para cada repuesto, especifique:
   - Cantidad
   - Precio acordado
   - Fecha de entrega requerida
5. Agregue condiciones de pago y entrega
6. Haga clic en "Generar Pedido"

### Seguimiento de Pedidos

Para monitorear los pedidos realizados:
1. Vaya a "Proveedores" > "Pedidos Pendientes"
2. Verá todos los pedidos organizados por:
   - Fecha estimada de entrega
   - Proveedor
   - Prioridad
3. Para cada pedido puede:
   - Ver detalles completos
   - Actualizar estado
   - Registrar comunicaciones con el proveedor
   - Modificar fechas o cantidades (si el proveedor lo permite)

### Evaluación de Proveedores

Para gestionar la relación con proveedores:
1. Vaya a "Proveedores" > "Evaluación"
2. Seleccione el proveedor a evaluar
3. Revise métricas como:
   - Tiempo promedio de entrega
   - Cumplimiento de plazos
   - Calidad de productos
   - Precios competitivos
   - Respuesta a urgencias
4. Registre incidencias o reconocimientos

### Ejemplo: Generación de Pedido Urgente

**Caso de uso**: Varios repuestos están bajo el stock mínimo y se requieren con urgencia.

1. Vaya a "Proveedores" > "Nuevo Pedido"
2. Seleccione "HydroRepuestos" como proveedor
3. Haga clic en "Sugerir Pedido" > "Bajo Mínimo"
4. El sistema muestra los repuestos críticos:
   - 5 unidades de "Filtro de aceite motor" (RP-M-001) - Stock actual: 2, Mínimo: 5
   - 3 unidades de "Kit de empaques motor" (RP-M-002) - Stock actual: 0, Mínimo: 2
   - 2 unidades de "Bomba hidráulica" (RP-H-001) - Stock actual: 0, Mínimo: 1
5. Marque todos como "Urgente"
6. Especifique "Entrega Prioritaria" en las condiciones
7. Haga clic en "Generar Pedido"
8. Llame al proveedor para confirmar disponibilidad y tiempos
9. Registre la comunicación en "Seguimiento de Pedido"

## Recepción de Mercadería

Esta sección gestiona el proceso de recepción de productos de los proveedores.

### Registro de Recepciones

Cuando llega un pedido:
1. Vaya a "Proveedores" > "Recepción de Mercadería"
2. Seleccione el pedido correspondiente
3. Haga clic en "Iniciar Recepción"
4. Para cada ítem, verifique:
   - Cantidad recibida vs. solicitada
   - Estado del producto
   - Concordancia con especificaciones
5. Marque cada ítem como:
   - Recibido completo
   - Recibido parcial (indique cantidad)
   - Con observaciones (describa el problema)
   - No recibido
6. Adjunte la documentación del proveedor (guía, factura)
7. Haga clic en "Completar Recepción"

### Control de Calidad

Para verificar la calidad de los productos recibidos:
1. Durante la recepción, marque los ítems que requieren inspección
2. Vaya a "Calidad" > "Inspecciones Pendientes"
3. Seleccione el ítem a inspeccionar
4. Registre los resultados de las pruebas realizadas
5. Determine si el producto:
   - Es aceptado y pasa a inventario
   - Requiere acondicionamiento antes de incorporarse
   - Debe ser devuelto al proveedor

### Devoluciones a Proveedores

Si necesita devolver productos:
1. Vaya a "Proveedores" > "Devoluciones"
2. Haga clic en "Nueva Devolución"
3. Seleccione el pedido original
4. Marque los ítems a devolver
5. Registre para cada uno:
   - Cantidad a devolver
   - Motivo (defectuoso, incorrecto, dañado en transporte, etc.)
   - Evidencia fotográfica
6. Seleccione la acción requerida:
   - Reemplazo
   - Nota de crédito
   - Reembolso
7. Genere la documentación de devolución

### Ejemplo: Recepción Parcial con Incidencias

**Caso de uso**: Llega un pedido incompleto y con algunos productos dañados.

1. Vaya a "Proveedores" > "Recepción de Mercadería"
2. Seleccione el pedido #PO-2023-045 de HydroRepuestos
3. Inicie la recepción
4. Registre:
   - "Filtro de aceite motor" (RP-M-001): 5/5 recibidos, estado correcto
   - "Kit de empaques motor" (RP-M-002): 2/3 recibidos, estado correcto
   - "Bomba hidráulica" (RP-H-001): 2/2 recibidos, uno con "carcasa exterior golpeada"
5. Para la bomba dañada:
   - Marque como "Con observaciones"
   - Tome fotografías del daño
   - Describa: "Carcasa exterior presenta abolladura en la zona de acople. Requiere verificación de funcionamiento."
6. Adjunte la guía de despacho #54321
7. Complete la recepción
8. El sistema:
   - Actualizará el inventario con los ítems correctos
   - Generará una solicitud de inspección para la bomba dañada
   - Mantendrá pendiente 1 unidad del kit de empaques

## Análisis e Informes

Esta sección proporciona herramientas para analizar la gestión de inventario.

### KPIs de Inventario

Para monitorear el rendimiento:
1. Vaya a "Análisis" > "KPIs Inventario"
2. Visualice métricas como:
   - Rotación de inventario
   - Valor total del inventario
   - Índice de cobertura
   - Exactitud del inventario
   - Ítems críticos (alto valor + bajo stock)
3. Configure alertas para desviaciones importantes

### Análisis de Consumo

Para entender patrones de uso:
1. Vaya a "Análisis" > "Consumo"
2. Seleccione el período a analizar
3. Visualice:
   - Repuestos más utilizados
   - Tendencias temporales
   - Consumo por categoría
   - Consumo por tipo de equipo
   - Estacionalidad

### Proyecciones y Planificación

Para anticipar necesidades futuras:
1. Vaya a "Análisis" > "Proyecciones"
2. Configure los parámetros:
   - Período a proyectar
   - Equipos base para la proyección
   - Factores estacionales
3. El sistema generará:
   - Proyección de demanda
   - Sugerencia de compras
   - Calendario de pedidos
   - Impacto financiero

### Ejemplo: Análisis de Rotación de Inventario

**Caso de uso**: El gerente solicita un análisis de rotación para optimizar el capital invertido.

1. Vaya a "Análisis" > "Rotación de Inventario"
2. Configure:
   - Período: Último trimestre
   - Agrupación: Por categoría
   - Visualización: Gráfico y tabla
3. El sistema muestra:
   - Categoría "Consumibles": Rotación 8.5 (excelente)
   - Categoría "Motor": Rotación 4.2 (buena)
   - Categoría "Cosechadora": Rotación 1.3 (baja)
4. Para la categoría "Cosechadora":
   - Haga clic en "Ver Detalle"
   - Identifique repuestos de baja rotación y alto valor
   - Genere un plan de acción:
     * Reducir stock de ítems específicos
     * Crear promociones para impulsar ventas
     * Revisar política de stock mínimo

## Gestión de Ubicaciones

Esta sección permite administrar la organización física del almacén.

### Mapa de Bodega

Para visualizar la organización:
1. Vaya a "Bodega" > "Mapa"
2. Navegue por la representación visual del almacén
3. Vea la ocupación por zonas
4. Identifique ubicaciones disponibles

### Asignación de Ubicaciones

Para gestionar donde se almacena cada repuesto:
1. Vaya a "Bodega" > "Asignación"
2. Puede:
   - Asignar ubicación a un nuevo repuesto
   - Modificar ubicación existente
   - Optimizar ubicaciones según rotación
3. El sistema puede sugerir la mejor ubicación basado en:
   - Frecuencia de uso
   - Tamaño y peso
   - Categoría
   - Relación con otros repuestos

### Ejemplo: Reorganización de Ubicaciones

**Caso de uso**: Necesita optimizar las ubicaciones de los filtros para facilitar el picking.

1. Vaya a "Bodega" > "Optimización"
2. Seleccione "Categoría: Filtros"
3. Solicite "Análisis de ubicación óptima"
4. El sistema sugiere:
   - Mover todos los filtros al Estante F, cercano a la zona de despacho
   - Organizar por subcategoría y tamaño
   - Colocar los de mayor rotación a altura media (ergonomía)
5. Revise y apruebe el plan
6. Genere etiquetas para las nuevas ubicaciones
7. Ejecute la reorganización y actualice el sistema

## Preguntas Frecuentes

### ¿Cómo gestiono repuestos de temporada?
Utilice la función "Gestión Estacional" en "Inventario" > "Planificación" para establecer niveles de stock variables según la temporada agrícola. Configure alertas anticipadas para abastecerse antes de los picos de demanda.

### ¿Qué hago si un repuesto no está catalogado?
Vaya a "Catálogo" > "Nuevo Repuesto" y cree una entrada temporal con la información disponible. Marque la casilla "Requiere validación técnica" para que el departamento técnico complete la información faltante. Mientras tanto, puede gestionarlo en inventario.

### ¿Cómo manejo los repuestos obsoletos?
Utilice "Inventario" > "Gestión de Obsolescencia" para identificar repuestos sin movimiento por más de 12 meses. El sistema sugerirá acciones como: descuentos especiales, transferencia a otras sucursales, devolución al fabricante o baja con descuento fiscal.

### ¿Puedo reservar repuestos para órdenes de trabajo programadas?
Sí, cuando reciba una solicitud de taller para una mantención futura, use "Inventario" > "Reservas" para apartar los repuestos necesarios. Estos seguirán visibles en inventario pero con la etiqueta "Reservado" y la fecha de la reserva.

### ¿Cómo manejo productos que requieren condiciones especiales de almacenamiento?
Para repuestos con requerimientos específicos (temperatura, humedad, etc.), utilice "Catálogo" > "Editar" y en la sección "Almacenamiento" marque las condiciones necesarias. El sistema le alertará sobre estas consideraciones al asignar ubicación y durante el inventario físico. 