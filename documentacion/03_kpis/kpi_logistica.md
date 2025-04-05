# KPIs de Logística y Embarque

## Descripción General

Los Indicadores Clave de Desempeño (KPIs) de Logística y Embarque son métricas diseñadas para evaluar y optimizar todos los procesos relacionados con el movimiento físico de los equipos agrícolas, desde su fabricación en origen (principalmente Suecia) hasta su entrega final al cliente. Estos indicadores permiten monitorear la eficiencia del proceso logístico, identificar cuellos de botella, reducir tiempos de tránsito y mejorar la precisión en la planificación de entregas.

En un negocio especializado en maquinaria agrícola importada, la logística representa un componente crítico debido a los altos costos involucrados, los extensos tiempos de tránsito internacional y la necesidad de cumplir con compromisos de entrega a clientes, especialmente considerando la estacionalidad de las actividades agrícolas.

## Objetivos de Medición

Los KPIs de Logística y Embarque están diseñados para:

- Controlar los tiempos de tránsito desde fabricación hasta entrega
- Evaluar la eficiencia del proceso de armado en taller
- Medir el cumplimiento de fechas programadas de entrega
- Identificar ineficiencias o cuellos de botella en la cadena logística
- Proporcionar información para mejorar la planificación y establecimiento de expectativas con clientes
- Reducir costos logísticos y de inmovilización de equipos

## Estructura de Datos

Estos KPIs se basan principalmente en la siguiente tabla específica para métricas:

### Tabla `metricas_kpi_logistica`

| Campo | Descripción |
|-------|-------------|
| id_metrica | Identificador único de la métrica |
| id_equipo | Equipo relacionado |
| tiempo_embarque_dias | Días desde salida de origen hasta llegada al taller |
| tiempo_armado_dias | Días desde llegada al taller hasta armado completo |
| tiempo_entrega_dias | Días desde llegada al taller hasta entrega al cliente |
| entrega_a_tiempo | Indica si la entrega se realizó en la fecha programada |
| fecha_registro | Fecha de registro de la métrica |

Adicionalmente, los KPIs se nutren de información proveniente de otras tablas del sistema:

- `equipos`: Proporciona fechas clave del ciclo de vida del equipo
- `embarques` y `detalle_embarques`: Información de embarques y su contenido
- `historial_estados_equipo`: Cambios de estado durante el proceso logístico

## Indicadores Principales

### 1. Tiempo Total de Tránsito Internacional

**Descripción**: Mide el tiempo promedio que transcurre desde que el equipo sale del fabricante hasta que llega al taller.

**Fórmula**: Promedio de `tiempo_embarque_dias` para un período determinado.

**Objetivo**: Reducir progresivamente este tiempo a través de mejoras en la cadena logística.

**Visualización**: 
- Gráfico de tendencia mensual/trimestral
- Comparación por fabricante/origen
- Distribución por tipo de equipo

**Valores de Referencia**:
- Excelente: < 40 días
- Aceptable: 40-50 días
- Requiere atención: > 50 días

### 2. Eficiencia de Armado

**Descripción**: Evalúa la eficiencia del proceso de armado en taller, comparando el tiempo real con el estimado según tipo de equipo.

**Fórmula**: 
```
(Tiempo real de armado / Tiempo estimado de armado) * 100
```

**Objetivo**: Mantener un ratio cercano o inferior al 100%, indicando cumplimiento o mejora sobre tiempos estimados.

**Visualización**:
- Gráfico de barras por tipo de equipo
- Tendencia temporal (mejora continua)
- Distribución de desviaciones

**Valores de Referencia**:
- Excelente: < 90%
- Aceptable: 90-110%
- Requiere atención: > 110%

### 3. Tiempo Total de Procesamiento

**Descripción**: Mide el tiempo total desde la llegada del equipo al taller hasta su entrega al cliente.

**Fórmula**: Promedio de `tiempo_entrega_dias` para un período determinado.

**Objetivo**: Minimizar este tiempo para reducir costos de inmovilización y mejorar satisfacción del cliente.

**Visualización**:
- Gráfico de tendencia temporal
- Comparativo por tipo de equipo
- Análisis de componentes (tiempo armado vs. tiempo espera)

**Valores de Referencia**:
- Excelente: < 15 días
- Aceptable: 15-25 días
- Requiere atención: > 25 días

### 4. Cumplimiento de Fechas de Entrega

**Descripción**: Porcentaje de equipos entregados en la fecha comprometida con el cliente.

**Fórmula**: 
```
(Número de equipos con entrega_a_tiempo = TRUE / Total de equipos entregados) * 100
```

**Objetivo**: Maximizar este porcentaje para mejorar confiabilidad y satisfacción del cliente.

**Visualización**:
- Porcentaje global con tendencia temporal
- Análisis por tipo de equipo o región
- Causas de incumplimiento

**Valores de Referencia**:
- Excelente: > 95%
- Aceptable: 85-95%
- Requiere atención: < 85%

### 5. Ratio de Daños en Tránsito

**Descripción**: Porcentaje de equipos que llegan con algún tipo de daño o novedad desde origen.

**Fórmula**: 
```
(Número de equipos con estado_recepcion = 'recibido_con_novedad' / Total de equipos recibidos) * 100
```

**Objetivo**: Minimizar este porcentaje a través de mejoras en embalaje y manipulación.

**Visualización**:
- Tendencia temporal
- Comparativo por proveedor logístico
- Clasificación por tipo de daño

**Valores de Referencia**:
- Excelente: < 2%
- Aceptable: 2-5%
- Requiere atención: > 5%

### 6. Precisión de Estimación de Llegada

**Descripción**: Evalúa la precisión en la estimación de fechas de llegada para planificación.

**Fórmula**: 
```
|Fecha real de llegada - Fecha estimada de llegada| (en días)
```

**Objetivo**: Minimizar esta desviación para mejorar la planificación de recursos.

**Visualización**:
- Distribución de desviaciones
- Tendencia temporal
- Análisis por ruta o temporada

**Valores de Referencia**:
- Excelente: < 3 días
- Aceptable: 3-7 días
- Requiere atención: > 7 días

### 7. Tiempo de Inmovilización

**Descripción**: Mide el tiempo que un equipo permanece inmovilizado en taller sin actividad productiva.

**Fórmula**: Suma de períodos donde el equipo está en estado "en_taller" o "listo_despacho" sin avance en su procesamiento.

**Objetivo**: Minimizar este tiempo para reducir costos financieros y mejorar rotación.

**Visualización**:
- Promedio por tipo de equipo
- Análisis de causas de inmovilización
- Tendencia temporal

**Valores de Referencia**:
- Excelente: < 2 días
- Aceptable: 2-5 días
- Requiere atención: > 5 días

## Análisis Cruzado e Integraciones

Los KPIs de Logística y Embarque cobran mayor valor cuando se analizan en conjunto con otras métricas del sistema:

### Relación con KPIs Financieros
- Costo logístico por equipo
- Impacto del tiempo de tránsito en el capital inmovilizado
- Rentabilidad afectada por costos logísticos

### Relación con KPIs de Satisfacción
- Correlación entre cumplimiento de fechas y satisfacción del cliente
- Impacto de retrasos en puntuaciones NPS

### Relación con KPIs Operativos
- Eficiencia del taller relacionada con precisión de llegadas
- Utilización de recursos técnicos en función de la planificación logística

## Informes y Visualizaciones Recomendadas

### 1. Dashboard de Logística
Panel visual que integra los principales KPIs logísticos con actualización periódica.

### 2. Informe de Rendimiento de Embarques
Análisis detallado de cada embarque con métricas comparativas y tendencias.

### 3. Análisis de Tendencias Logísticas
Estudio de la evolución temporal de los principales indicadores, identificando patrones estacionales o de mejora.

### 4. Reporte de Excepciones
Detalle de casos que se desvían significativamente de los valores objetivo, con análisis de causas.

### 5. Proyección de Entregas
Estimación de fechas futuras basada en el análisis histórico de métricas logísticas.

## Alertas y Acciones Recomendadas

### Alertas Automáticas
- Desviación significativa en tiempo de tránsito estimado
- Acumulación de equipos en estado "listo_despacho"
- Deterioro sostenido en KPIs de cumplimiento

### Acciones Correctivas Potenciales
- Revisión de proveedores logísticos con desempeño deficiente
- Optimización del proceso de armado para tipos de equipos con baja eficiencia
- Implementación de buffer de tiempo en planificación para rutas problemáticas
- Mejora en procesos de comunicación con cliente para gestión de expectativas

## Ejemplos de Uso

### Ejemplo 1: Mejora en Tiempos de Tránsito

El análisis de tendencias mostró un incremento constante en los tiempos de tránsito durante tres trimestres consecutivos (de 45 a 52 días en promedio). Al investigar las causas, se identificó un cambio en la ruta marítima utilizada por el proveedor logístico. Se negoció un nuevo acuerdo con un proveedor alternativo, logrando reducir el tiempo promedio a 42 días en el siguiente trimestre, con un impacto positivo directo en la satisfacción del cliente y reducción de costos financieros por inmovilización.

### Ejemplo 2: Optimización del Proceso de Armado

El KPI de eficiencia de armado mostraba que para las cosechadoras modelo CS-250, el tiempo real superaba consistentemente en 30% al tiempo estimado. Un análisis detallado del proceso reveló un cuello de botella en la calibración de sistemas electrónicos. Se implementó un protocolo de pre-calibración en paralelo con otras actividades de armado, reduciendo el tiempo total y llevando el indicador de eficiencia al 105%, muy cercano al objetivo.

## Consideraciones para Implementación

1. **Calidad de Datos**: Asegurar el registro preciso y oportuno de todas las fechas clave en el proceso logístico.

2. **Contextualización**: Considerar factores externos (estacionalidad, eventos globales, restricciones aduaneras) al interpretar las métricas.

3. **Granularidad Adecuada**: Analizar los KPIs a nivel global, pero también segmentados por tipo de equipo, origen y destino.

4. **Revisión Periódica de Objetivos**: Ajustar valores de referencia conforme se logran mejoras sostenidas.

5. **Integración con Planificación**: Utilizar los insights obtenidos para refinar la planificación futura.

La implementación efectiva de estos KPIs proporciona una visión clara del desempeño logístico, permitiendo optimizar procesos, reducir costos y mejorar la experiencia del cliente a través de entregas más predecibles y oportunas. 