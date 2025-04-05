# Caso de Uso: Recepción y Armado de Equipo Nuevo

## Descripción General

Este caso de uso describe el proceso completo de recepción, armado y preparación para entrega de un equipo agrícola nuevo importado. El flujo abarca desde la notificación de embarque desde origen (generalmente Suecia), pasando por la recepción física en el taller, el proceso detallado de armado, hasta la preparación final para entrega al cliente, incluyendo las pruebas y configuraciones necesarias.

La recepción y armado de equipos nuevos constituye uno de los procesos más importantes del taller, ya que sienta las bases para el correcto funcionamiento del equipo durante toda su vida útil. Un armado correcto y meticuloso garantiza un mejor desempeño, reduce la probabilidad de fallas y mejora la satisfacción inicial del cliente.

## Actores Involucrados

- **Coordinador de Logística**: Responsable de seguimiento de embarques y coordinación de recepción.
- **Jefe de Taller**: Encargado de programar y supervisar el proceso de armado.
- **Técnicos Especializados**: Ejecutan las tareas específicas de armado y configuración.
- **Administrador del Sistema**: Configura parámetros y mantiene actualizada la información técnica.
- **Vendedor**: Coordina con el cliente la entrega y proporciona información de avance.
- **Cliente**: Destinatario final del equipo, puede participar en la recepción o pruebas finales.

## Precondiciones

1. El equipo debe estar registrado en el sistema con su información básica.
2. El embarque que contiene el equipo debe estar creado y en estado "en_transito".
3. Debe existir una programación preliminar de armado con recursos asignados.
4. El taller debe contar con capacidad y personal técnico disponible para el armado.
5. Se debe haber definido si el equipo está pre-vendido o será para stock.

## Flujo Principal

### 1. Preparación para Recepción

1.1. **Notificación de Próxima Llegada**
   - El sistema genera una alerta a Logística sobre la llegada inminente basada en la fecha estimada.
   - El Coordinador de Logística prepara el espacio en taller y recursos necesarios.
   - Se actualiza la programación preliminar de armado para asegurar disponibilidad de técnicos.

1.2. **Confirmación de Llegada**
   - El proveedor logístico notifica la fecha y hora exacta de llegada.
   - Logística confirma recursos para descarga y actualiza agenda de recepción.
   - Se notifica a los técnicos involucrados sobre la fecha de inicio del armado.

### 2. Recepción Física

2.1. **Recepción del Embarque**
   - Se recibe físicamente el embarque en el taller.
   - El Coordinador de Logística registra la llegada en el sistema:
     ```sql
     UPDATE embarques 
     SET fecha_llegada_real = CURRENT_DATE(), estado = 'recibido' 
     WHERE id_embarque = [ID_EMBARQUE];
     ```
   - El sistema actualiza automáticamente los equipos asociados al embarque:
     ```sql
     UPDATE equipos 
     SET fecha_llegada_taller = CURRENT_DATE(), estado_actual = 'en_taller' 
     WHERE id_equipo IN (SELECT id_equipo FROM detalle_embarques WHERE id_embarque = [ID_EMBARQUE]);
     ```

2.2. **Inspección Inicial**
   - Se realiza una inspección visual del embalaje para detectar daños evidentes.
   - Se documenta con fotografías el estado de recepción.
   - Se registra el estado de recepción en el sistema:
     ```sql
     UPDATE detalle_embarques 
     SET estado_recepcion = '[ESTADO]', notas_recepcion = '[NOTAS]' 
     WHERE id_embarque = [ID_EMBARQUE] AND id_equipo = [ID_EQUIPO];
     ```

2.3. **Desembalaje e Inventario**
   - Se procede al desembalaje cuidadoso del equipo.
   - Se verifica el inventario de componentes contra la lista de empaque.
   - Se registran discrepancias o faltantes para gestión con proveedor.
   - Se actualiza el historial de estados del equipo:
     ```sql
     INSERT INTO historial_estados_equipo 
     (id_equipo, estado_anterior, estado_nuevo, fecha_cambio, usuario_cambio, comentario)
     VALUES ([ID_EQUIPO], 'en_taller', 'en_armado', CURRENT_TIMESTAMP, '[USUARIO]', 'Inicio de proceso de armado');
     ```

### 3. Planificación Detallada de Armado

3.1. **Creación del Plan de Armado**
   - El Jefe de Taller crea un plan detallado de armado basado en el tipo de equipo:
     - Secuencia de actividades
     - Técnicos asignados a cada etapa
     - Tiempos estimados por actividad
     - Puntos de control y verificación

3.2. **Asignación de Recursos**
   - Se asignan los técnicos específicos a cada etapa del armado.
   - Se reservan herramientas especiales y áreas de trabajo.
   - Se planifican pruebas intermedias y finales.

### 4. Proceso de Armado

4.1. **Ensamblaje Mecánico**
   - Se realiza el armado de componentes mecánicos principales según manual del fabricante.
   - Se registra avance y observaciones por etapa.
   - Se efectúan verificaciones intermedias de ajustes y alineaciones.

4.2. **Instalación de Sistemas Hidráulicos**
   - Se ensamblan componentes hidráulicos y se realizan conexiones.
   - Se purgan sistemas y se comprueban presiones según especificaciones.
   - Se verifican posibles fugas o anomalías.

4.3. **Instalación Eléctrica y Electrónica**
   - Se instalan componentes eléctricos y electrónicos.
   - Se realizan conexiones y se verifica cableado.
   - Se prueban sistemas electrónicos básicos.

4.4. **Montaje de Implementos y Accesorios**
   - Se instalan implementos específicos según configuración del equipo.
   - Se ajustan y calibran accesorios.
   - Se verifica compatibilidad y funcionamiento.

4.5. **Registro de Avance**
   - Cada técnico registra el avance de sus actividades asignadas.
   - Se documentan con fotografías las etapas críticas.
   - Se actualizan estimaciones de tiempo restante según avance real.

### 5. Configuración y Pruebas

5.1. **Configuración de Software y Sistemas**
   - Se instala y configura el software operativo del equipo.
   - Se establecen parámetros iniciales según tipo de operación.
   - Se realizan actualizaciones de firmware si es necesario.

5.2. **Calibración de Sistemas**
   - Se calibran sensores y sistemas de control.
   - Se ajustan parámetros operativos según especificaciones.
   - Se documentan valores de calibración inicial.

5.3. **Pruebas Operativas**
   - Se realizan pruebas operativas de todos los sistemas:
     - Funcionamiento de motor y transmisión
     - Sistemas hidráulicos bajo carga
     - Sistemas electrónicos y de control
     - Implementos y accesorios
   - Se documentan resultados y parámetros de operación.

5.4. **Corrección de Anomalías**
   - Se corrigen anomalías detectadas durante las pruebas.
   - Se realizan ajustes finales según resultados.
   - Se documenta cualquier situación especial para seguimiento futuro.

### 6. Finalización y Preparación para Entrega

6.1. **Inspección Final**
   - El Jefe de Taller realiza una inspección completa del equipo armado.
   - Se verifica cumplimiento de todos los estándares del fabricante.
   - Se aprueba el resultado final o se solicitan correcciones adicionales.

6.2. **Registro de Finalización**
   - Se registra la finalización del armado en el sistema:
     ```sql
     UPDATE equipos 
     SET fecha_armado_completo = CURRENT_DATE(), estado_actual = 'listo_despacho' 
     WHERE id_equipo = [ID_EQUIPO];
     ```
   - Se actualiza el historial de estados:
     ```sql
     INSERT INTO historial_estados_equipo 
     (id_equipo, estado_anterior, estado_nuevo, fecha_cambio, usuario_cambio, comentario)
     VALUES ([ID_EQUIPO], 'en_armado', 'listo_despacho', CURRENT_TIMESTAMP, '[USUARIO]', 'Armado completo, listo para entrega');
     ```

6.3. **Preparación Estética**
   - Se realiza limpieza detallada del equipo.
   - Se aplican acabados finales y protectores.
   - Se instalan elementos de identificación y seguridad.

6.4. **Actualización de Métricas**
   - El sistema registra métricas de KPI relacionadas con el proceso:
     ```sql
     INSERT INTO metricas_kpi_logistica 
     (id_equipo, tiempo_embarque_dias, tiempo_armado_dias, fecha_registro)
     VALUES ([ID_EQUIPO], 
             DATEDIFF(fecha_llegada_taller, fecha_salida_origen), 
             DATEDIFF(fecha_armado_completo, fecha_llegada_taller), 
             CURRENT_DATE());
     ```

### 7. Coordinación de Entrega

7.1. **Notificación de Disponibilidad**
   - Se notifica al área comercial que el equipo está listo para entrega.
   - Si el equipo está pre-vendido, se contacta al cliente para coordinar entrega.
   - Si es para stock, se registra disponibilidad para demostración o venta.

7.2. **Programación de Entrega**
   - Se acuerda fecha de entrega con el cliente (si aplica).
   - Se registra la fecha programada:
     ```sql
     UPDATE equipos 
     SET fecha_entrega_programada = '[FECHA]' 
     WHERE id_equipo = [ID_EQUIPO];
     ```
   - Se asignan recursos para la entrega y capacitación inicial.

7.3. **Preparación de Documentación**
   - Se preparan manuales, garantías y documentación técnica.
   - Se genera protocolo de entrega para capacitación al cliente.
   - Se completa documentación legal y administrativa.

## Flujos Alternativos

### A. Detección de Daños en Recepción

A.1. Si se detectan daños en la inspección inicial:
   - Se documenta detalladamente con fotografías los daños detectados.
   - Se notifica inmediatamente al proveedor y aseguradora.
   - Se evalúa el impacto en el proceso de armado y tiempos estimados.
   - Se decide si proceder con el armado o esperar resolución de reclamo.
   - Se registra la novedad en el sistema:
     ```sql
     UPDATE detalle_embarques 
     SET estado_recepcion = 'recibido_con_novedad', 
         notas_recepcion = 'Daños detectados en: [DESCRIPCIÓN]' 
     WHERE id_embarque = [ID_EMBARQUE] AND id_equipo = [ID_EQUIPO];
     ```

### B. Faltantes de Componentes

B.1. Si se detectan faltantes en el inventario inicial:
   - Se documenta detalladamente los componentes faltantes.
   - Se inicia gestión inmediata con proveedor para envío de faltantes.
   - Se evalúa impacto en cronograma y posibilidades de armado parcial.
   - Se actualiza la planificación según resolución.
   - Se registra la situación en el sistema:
     ```sql
     INSERT INTO notificaciones 
     (tipo, id_referencia, descripcion, fecha_creacion, fecha_vencimiento, estado, prioridad)
     VALUES ('seguimiento_proveedor', [ID_EQUIPO], 'Faltantes en embarque: [DETALLE]', 
             CURRENT_TIMESTAMP, DATE_ADD(CURRENT_DATE(), INTERVAL 7 DAY), 'pendiente', 'alta');
     ```

### C. Problemas Durante el Armado

C.1. Si se detectan problemas técnicos durante el armado:
   - El técnico documenta el problema específico.
   - Se evalúa si puede resolverse localmente o requiere soporte del fabricante.
   - Se estima el impacto en tiempo y recursos.
   - Se ajusta la planificación según sea necesario.
   - Se registra el incidente para seguimiento:
     ```sql
     INSERT INTO notificaciones 
     (tipo, id_referencia, descripcion, fecha_creacion, estado, prioridad)
     VALUES ('seguimiento_tecnico', [ID_EQUIPO], 'Problema técnico: [DESCRIPCIÓN]', 
             CURRENT_TIMESTAMP, 'pendiente', 'alta');
     ```

### D. Cambios en Configuración Solicitados por Cliente

D.1. Si el cliente solicita cambios en la configuración durante el proceso:
   - Se evalúa viabilidad técnica del cambio solicitado.
   - Se estima impacto en tiempo y costos.
   - Se obtiene aprobación formal del cliente para cambios y costos adicionales.
   - Se actualiza la planificación de armado.
   - Se documenta el cambio en el sistema:
     ```sql
     UPDATE equipos 
     SET notas = CONCAT(IFNULL(notas, ''), '\nCambio solicitado por cliente: [DESCRIPCIÓN]') 
     WHERE id_equipo = [ID_EQUIPO];
     ```

## Postcondiciones

1. El equipo queda completamente armado y probado según especificaciones del fabricante.
2. Toda la documentación técnica y legal está completa y lista para entrega.
3. El equipo está registrado en sistema como "listo_despacho" con fecha de armado completo.
4. Las métricas de KPI de logística y armado están actualizadas.
5. Se ha notificado la disponibilidad del equipo para entrega o venta.
6. Existe un registro detallado de todo el proceso de armado y pruebas realizadas.

## Requisitos Especiales

1. **Trazabilidad**: Todo el proceso debe ser completamente trazable, con registro de responsables y fechas para cada actividad.
2. **Calidad**: Deben cumplirse todos los estándares y especificaciones del fabricante, documentando cualquier desviación.
3. **Seguridad**: El proceso debe realizarse siguiendo todos los protocolos de seguridad industrial.
4. **Eficiencia**: El tiempo total de armado debe ajustarse a lo esperado según el tipo de equipo.
5. **Documentación**: Cada etapa debe estar debidamente documentada, incluyendo registro fotográfico de puntos críticos.

## Frecuencia

La frecuencia de este caso de uso depende del volumen de importaciones del taller, pero típicamente ocurre:
- Entre 5-10 veces al mes en temporada alta
- Entre 2-5 veces al mes en temporada baja
- Con picos estacionales según el ciclo agrícola regional

## Reglas de Negocio Relacionadas

1. Todo equipo debe pasar por pruebas completas antes de ser marcado como listo para entrega.
2. Cualquier desviación mayor a 2 días en el tiempo estimado de armado debe ser justificada y documentada.
3. Los equipos se procesan generalmente en orden de llegada, salvo priorización explícita por gerencia.
4. Los cambios solicitados por cliente durante el armado deben ser formalmente aprobados y pueden generar costos adicionales.
5. La asignación de técnicos debe respetar las certificaciones requeridas por tipo de equipo.

## Puntos de Extensión

Este caso de uso puede extenderse mediante:

1. **Integración con Capacitación**: Añadir módulo de capacitación a operadores durante proceso de entrega.
2. **Personalización Avanzada**: Proceso de configuración especializada según tipo de operación del cliente.
3. **Control de Calidad Extendido**: Inspecciones adicionales por terceros o representantes del fabricante.
4. **Demostración en Campo**: Pruebas operativas en condiciones reales antes de entrega final.

## Consideraciones de Implementación

1. **Integración Móvil**: Los técnicos deben poder registrar avances desde dispositivos móviles en el taller.
2. **Gestión Documental**: El sistema debe facilitar la anexión de fotografías y documentos técnicos.
3. **Notificaciones**: Implementar alertas automáticas para coordinadores y técnicos sobre cambios o problemas.
4. **Tablero Visual**: Proporcionar visualización tipo Kanban del estado de cada equipo en proceso de armado.
5. **Checklist Dinámicos**: Adaptar las listas de verificación según el tipo específico de equipo.

## Ejemplo Práctico

### Escenario: Recepción y Armado de Tractor TR-130-23002

**Día 1: Recepción**  
El coordinador logístico Juan Pérez recibe notificación de llegada del embarque EMB-2023-006 que incluye el tractor TR-130-23002 pre-vendido al cliente "Agrícola El Triunfo". Juan actualiza el sistema registrando la llegada y coordina el espacio en taller. Al desembalar, se realiza inspección inicial documentando con fotografías todas las partes. Se detecta un pequeño golpe en el guardabarros delantero, que se documenta pero no afecta el proceso de armado.

**Días 2-3: Armado Mecánico**  
El técnico Pedro Soto inicia el armado mecánico, ensamblando el tren de rodaje, alineando ejes y montando el motor según especificaciones. Registra avance al final de cada jornada, documentando con fotografías las etapas críticas.

**Días 4-5: Sistemas Hidráulicos y Eléctricos**  
La técnica María González realiza la instalación y conexión de sistemas hidráulicos, mientras Carlos Fuentes trabaja en los sistemas eléctricos y electrónicos. Se realiza una prueba preliminar de sistemas básicos al finalizar el día 5.

**Día 6: Montaje de Implementos y Ajustes**  
El equipo completa el montaje de implementos específicos solicitados por el cliente (arado reversible). Se realizan ajustes y calibraciones iniciales. Se detecta un problema de comunicación con el controlador electrónico, que requiere actualización de firmware.

**Día 7: Pruebas y Resolución de Problemas**  
Se resuelve el problema del controlador con actualización proporcionada por el fabricante. Se realizan pruebas completas de todos los sistemas bajo supervisión del Jefe de Taller. Se documentan parámetros de operación y se realizan ajustes finales.

**Día 8: Finalización**  
Se completa inspección final con aprobación del Jefe de Taller. Se realiza limpieza detallada, aplicación de protectores y verificación final de documentación. Se registra la finalización del armado y se notifica al área comercial. Se coordina entrega para el día 10 con el cliente.

**Día 10: Entrega**  
Se realiza entrega formal al cliente con capacitación inicial sobre operación y mantenimiento. Se completa documentación de entrega y se registra satisfacción inicial del cliente.

## Diagramas

### Diagrama de Flujo de Proceso
[Diagrama de Flujo de Recepción y Armado](../recursos/diagrama_flujo_recepcion.png)

### Diagrama de Estados del Equipo
[Diagrama de Estados de Equipo](../recursos/diagrama_estados_equipo.png)

## Referencias a Documentación Relacionada

- [Guía de Usuario: Perfil Logística](../04_guias_usuario/perfil_logistica.md)
- [Guía de Usuario: Perfil Técnico](../04_guias_usuario/perfil_tecnico.md)
- [KPIs de Logística](../03_kpis/kpi_logistica.md)
- [Módulo de Gestión de Equipos](../02_modulos/equipos.md)
- [Manuales Técnicos de Armado](https://www.fabricante.com/manuales) (Enlace externo a documentación del fabricante) 