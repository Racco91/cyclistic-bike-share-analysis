# 🚲 Cyclistic Bike-Share Analysis

Análisis de **6.032.469 viajes** de bicicletas compartidas de Chicago para identificar diferencias de comportamiento entre **miembros anuales (Member)** y **usuarios ocasionales (Casual)**.

**Python · Pandas · Tableau**

📊 **Dashboard interactivo:** [Ver Cyclistic Bike-Share Analysis en Tableau Public](https://public.tableau.com/app/profile/ram.n.rovira/viz/CyclisticBike-ShareAnalysisMembervsCasualRiderBehavior/CyclisticOverview)

> Cyclistic es una empresa ficticia utilizada en el caso práctico del Certificado Profesional de Google Data Analytics. Los datos provienen del sistema público Divvy Bike-Share de Chicago.

---

## 📌 Descripción del proyecto

El objetivo del proyecto es comprender **cómo utilizan el servicio de forma diferente los miembros anuales y los usuarios ocasionales**, y transformar esos hallazgos en recomendaciones de negocio orientadas a la conversión de usuarios Casual hacia membresías anuales.

El análisis cubre el período comprendido entre **agosto de 2025 y julio de 2026**.

---

## 🎯 Pregunta de negocio

> **¿De qué manera los miembros anuales y los ciclistas ocasionales utilizan las bicicletas Cyclistic de forma diferente?**

A partir de esta pregunta se analizaron cinco dimensiones principales:

- Volumen y estacionalidad de los viajes.
- Patrones por día de la semana.
- Patrones por hora del día.
- Duración de los viajes.
- Preferencia de bicicleta y distribución geográfica por estaciones.

---

## 🛠️ Herramientas utilizadas

- **Python**
- **Pandas**
- **NumPy**
- **Google Colab**
- **Tableau Public**
- **Git / GitHub**

---

## 📂 Fuente de los datos

Los datos utilizados corresponden a viajes públicos de **Divvy Bike-Share (Chicago)**.

- Período analizado: **2025-08-01 a 2026-07-31**
- Registros finales analizados: **6.032.469 viajes**
- Fuente oficial: [Divvy Trip Data](https://divvy-tripdata.s3.amazonaws.com/index.html)

Los archivos originales y el dataset limpio completo no se incluyen en este repositorio debido a su tamaño. Los datasets agregados utilizados para Tableau se incorporarán en `data/processed/`.

Más detalles en [data/README.md](data/README.md).

---

## 🔄 Proceso de análisis

El proyecto sigue las seis etapas del caso práctico de Google Data Analytics.

### 1. Preguntar

Se definió la pregunta principal de negocio y el objetivo de comparar el comportamiento entre usuarios `member` y `casual`.

### 2. Preparar

Se seleccionaron **12 meses consecutivos de datos**, desde agosto de 2025 hasta julio de 2026.

Durante la revisión inicial se detectaron problemas que podían afectar el análisis:

- inclusión accidental de más de 12 meses;
- meses con el mismo nombre pero distinto año;
- registros duplicados entre archivos mensuales.

### 3. Procesar

La limpieza se realizó con Python y Pandas.

Entre los principales pasos:

- conversión y validación de fechas;
- filtro explícito del período de 12 meses;
- eliminación de duplicados por `ride_id`;
- cálculo de duración de viaje;
- eliminación de duraciones inválidas;
- exclusión de estaciones de prueba/mantenimiento;
- creación de variables temporales como mes, día de la semana, hora y fin de semana;
- validaciones finales de calidad.

### 4. Analizar

Se realizó un análisis exploratorio orientado a identificar diferencias entre ambos segmentos.

#### Participación de viajes

- **Member:** 3.885.831 viajes (**64,42 %**)
- **Casual:** 2.146.638 viajes (**35,58 %**)

#### Estacionalidad

Los usuarios Casual presentan una variación estacional más fuerte. Su participación mensual descendió hasta **17,92 % en enero de 2026** y superó el **40 %** durante meses de mayor demanda.

#### Día de la semana

Los miembros concentran una mayor proporción de actividad de lunes a viernes, mientras que los viajes Casual alcanzan su máximo el **sábado**.

#### Hora del día

Los miembros muestran un pico matutino más marcado. Entre las 06:00 y las 09:00 se concentra el **20,36 %** de sus viajes, frente al **10,80 %** entre usuarios Casual.

#### Duración

- Mediana Member: **8,57 min**
- Mediana Casual: **11,03 min**

La mediana de los viajes Casual es aproximadamente **28,7 % mayor**.

#### Tipo de bicicleta

Ambos segmentos prefieren bicicletas eléctricas:

- Casual: **71,68 %**
- Member: **67,11 %**

Por lo tanto, el tipo de bicicleta no aparece como uno de los principales diferenciadores de comportamiento.

#### Estaciones

El análisis geográfico cubre los viajes con estación de inicio identificada. Se aplicó un umbral mínimo de **5.000 viajes por estación** para evitar interpretar como relevantes ubicaciones con muy poco volumen.

Entre los puntos destacados:

- **Shedd Aquarium:** 81,82 % Casual
- **Field Museum:** 81,06 % Casual
- **Navy Pier:** 76,94 % Casual y 71.171 viajes totales

### 5. Compartir

Se desarrollaron tres dashboards finales en Tableau:

1. **Cyclistic Overview** — resumen ejecutivo.
2. **Rider Behavior** — diferencias por día, hora y tipo de bicicleta.
3. **Geographic Opportunities** — concentración geográfica y estaciones con alta participación Casual.

📊 [Abrir dashboards interactivos en Tableau Public](https://public.tableau.com/app/profile/ram.n.rovira/viz/CyclisticBike-ShareAnalysisMembervsCasualRiderBehavior/CyclisticOverview)

### 6. Actuar

A partir de los patrones observados se proponen tres líneas de acción:

1. **Priorizar estaciones de alto volumen y alta participación Casual**, especialmente ubicaciones como Navy Pier y Shedd Aquarium.
2. **Concentrar campañas de conversión en meses de mayor demanda y fines de semana**, cuando aumenta la participación de viajes Casual.
3. **Probar mensajes e incentivos orientados a membresías** en esas ubicaciones y medir su respuesta antes de escalar la estrategia.

Estas recomendaciones se presentan como hipótesis de negocio a validar, ya que el dataset no contiene información sobre el motivo del viaje ni sobre la respuesta de los usuarios a campañas de marketing.

---

## ⚠️ Limitaciones

- El dataset no incluye el motivo declarado de cada viaje.
- No contiene identificadores que permitan contar usuarios únicos.
- La presencia de patrones temporales compatibles con desplazamientos rutinarios o recreativos **no demuestra causalidad**.
- El análisis geográfico utiliza únicamente viajes con estación de inicio identificada.
- Las recomendaciones de marketing requieren pruebas posteriores para validar su efectividad.

---

## 📁 Estructura del repositorio

```text
cyclistic-bike-share-analysis/
│
├── README.md
├── notebooks/
│   └── cyclistic_analysis.ipynb
├── data/
│   ├── README.md
│   └── processed/
│       ├── cyclistic_tableau_time.csv
│       ├── cyclistic_tableau_duration.csv
│       ├── cyclistic_tableau_bikes.csv
│       └── cyclistic_tableau_stations.csv
├── images/
│   ├── cyclistic_overview.png
│   ├── rider_behavior.png
│   └── geographic_opportunities.png
└── requirements.txt
```

---

## 🔗 Enlaces

- [Tableau Public — Cyclistic Bike-Share Analysis](https://public.tableau.com/app/profile/ram.n.rovira/viz/CyclisticBike-ShareAnalysisMembervsCasualRiderBehavior/CyclisticOverview)
- [Divvy Trip Data — fuente oficial](https://divvy-tripdata.s3.amazonaws.com/index.html)

---

## 👤 Autor

Proyecto desarrollado como parte de un portfolio de análisis de datos.
