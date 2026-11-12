# Sigma-Telecom-Churn-Prediction

## Descripción del proyecto

La fuga de clientes (Customer Churn) representa uno de los principales desafíos para las empresas de telecomunicaciones, ya que afecta directamente los ingresos, la estabilidad de la cartera de clientes y los costos asociados a la adquisición de nuevos usuarios.

En este proyecto se desarrolló un sistema de aprendizaje automático capaz de predecir qué clientes presentan mayor probabilidad de abandonar la compañía utilizando información contractual, demográfica, de servicios contratados y de facturación. A lo largo del análisis se construyó un pipeline completo de Ciencia de Datos que incluyó integración de datos, limpieza, análisis exploratorio, tratamiento del desbalance de clases, transformación de variables y evaluación comparativa de múltiples algoritmos de clasificación.

---

## Objetivo

Desarrollar un modelo de Machine Learning capaz de identificar clientes con riesgo de fuga para apoyar la toma de decisiones orientadas a la retención y fidelización de usuarios.

---

## Conjunto de datos

El proyecto integra información proveniente de diversas fuentes relacionadas con:

- Información contractual.
- Servicios telefónicos.
- Servicios de internet.
- Información demográfica.
- Facturación mensual.
- Facturación acumulada.
- Estado de permanencia o cancelación del servicio.

Tras la integración mediante la variable `customerID`, se obtuvo un conjunto consolidado compuesto por **7.043 clientes**.

---

## Metodología

### 1. Preparación de datos

- Integración de múltiples tablas mediante `customerID`.
- Conversión de tipos de datos.
- Tratamiento de valores faltantes.
- Creación de la variable objetivo `Fuga`.
- Eliminación de variables con potencial riesgo de fuga de información.
- Codificación de variables categóricas mediante One-Hot Encoding.
- División de los datos en conjuntos de entrenamiento, validación y prueba.
- Aplicación de sobremuestreo (Oversampling) sobre el conjunto de entrenamiento para reducir el impacto del desbalance de clases.

### 2. Análisis Exploratorio de Datos (EDA)

Se analizaron variables categóricas y numéricas para identificar patrones asociados a la fuga de clientes.

Las variables con mayor asociación observada fueron:

- `PaymentMethod`
- `Type`
- `InternetService`
- `OnlineSecurity`
- `TechSupport`

También se analizaron variables económicas relevantes como:

- `MonthlyCharges`
- `TotalCharges`

Los resultados sugieren que las características relacionadas con condiciones contractuales, servicios contratados y facturación contienen una proporción importante de la información necesaria para explicar el comportamiento de abandono.

---

## Métricas de evaluación

Para comparar los diferentes modelos se utilizaron:

### ROC-AUC

Mide la capacidad del modelo para distinguir entre clientes que presentan fuga y clientes que permanecen en la compañía.

### Recall (Sensibilidad)

Mide la proporción de clientes con fuga que fueron identificados correctamente por el modelo.

Dado el contexto de negocio, el Recall resulta especialmente relevante, ya que permite reducir la cantidad de clientes con riesgo de abandono que no son detectados por el sistema.

---

## Modelos evaluados

Se implementaron y compararon los siguientes algoritmos:

- DummyClassifier (Baseline)
- Decision Tree Classifier
- Logistic Regression
- Random Forest Classifier
- LightGBM
- XGBoost

---

## Resultados

| Modelo | ROC-AUC | Recall |
|----------|----------:|----------:|
| DummyClassifier | 0.5000 | 0.0000 |
| Regresión Logística | **0.8349** | 0.7754 |
| Bosque Aleatorio | 0.8283 | 0.8316 |
| LightGBM | 0.8450 | 0.7433 |
| Árbol de Decisión | 0.7890 | **0.8797** |
| XGBoost | 0.7210 | 0.6043 |

---

## Evaluación final del modelo seleccionado

Después de comparar los distintos algoritmos sobre el conjunto de validación, se seleccionó **LightGBM** para realizar la evaluación final sobre el conjunto de prueba.

### Resultados en prueba

- **ROC-AUC:** 0.8492
- **Recall:** 0.7781

La evaluación final confirmó que el modelo mantiene una capacidad adecuada de generalización sobre datos no observados previamente, logrando diferenciar correctamente entre clientes con alta y baja probabilidad de abandono mientras identifica aproximadamente el 77.8 % de los clientes que efectivamente presentan fuga.

---

## Principales hallazgos

- Las variables contractuales y de facturación presentan una fuerte relación con la fuga de clientes.
- El tipo de contrato y el método de pago son factores especialmente relevantes en la explicación del abandono.
- Todos los modelos desarrollados superaron ampliamente el desempeño del clasificador base.
- El árbol de decisión obtuvo la mayor sensibilidad, identificando aproximadamente el 88 % de los clientes que abandonan el servicio.
- La regresión logística mostró uno de los mejores equilibrios entre capacidad discriminativa y detección de clientes con fuga.
- LightGBM obtuvo el mejor desempeño global durante la evaluación final sobre el conjunto de prueba.

---

## Conclusiones

El proyecto permitió desarrollar un sistema de clasificación capaz de anticipar la fuga de clientes utilizando información histórica relacionada con contratos, servicios contratados y comportamiento de facturación.

El análisis exploratorio identificó que las variables contractuales y económicas contienen una parte importante de la información asociada al abandono de clientes. Estas características fueron posteriormente utilizadas para entrenar diversos algoritmos de Machine Learning, todos ellos significativamente superiores al desempeño obtenido por el modelo base.

Entre los modelos evaluados, el árbol de decisión destacó por alcanzar la mayor sensibilidad, identificando correctamente cerca del 88 % de los clientes que presentaron fuga. Por su parte, el bosque aleatorio y la regresión logística mostraron un desempeño sólido y competitivo, ofreciendo un buen equilibrio entre capacidad predictiva y detección de clientes en riesgo.

Finalmente, LightGBM fue seleccionado como modelo final tras ser evaluado sobre el conjunto de prueba, obteniendo un ROC-AUC de 0.8492 y una sensibilidad de 0.7781. Estos resultados demuestran una adecuada capacidad para generalizar sobre datos no observados previamente y confirman que el modelo puede utilizarse como herramienta de apoyo para estrategias de retención de clientes.

En términos de negocio, la capacidad de identificar de manera anticipada a los clientes con mayor riesgo de abandono permitiría implementar campañas de fidelización más efectivas, optimizar recursos comerciales y reducir las pérdidas asociadas a la fuga de usuarios.

---

## Tecnologías utilizadas

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-Learn
- LightGBM
- XGBoost
- Jupyter Notebook

---

## Estructura del repositorio

```text
Sigma-Telecom-Churn-Prediction
│
├── data/
├── notebooks/
│   └── telecom_churn_prediction.ipynb
├── images/
├── README.md
└── requirements.txt
```

---

## Autor

**Santiago Rodríguez Zaraza**
https://github.com/rodriguezzarazas01-maker
