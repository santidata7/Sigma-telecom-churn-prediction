# Sigma-Telecom-Churn-Prediction

## Descripción del proyecto

La fuga de clientes (Customer Churn) representa uno de los principales desafíos para las empresas de telecomunicaciones, ya que implica la pérdida de usuarios y la reducción de ingresos futuros. En este proyecto se desarrolló un sistema de aprendizaje automático capaz de identificar clientes con alta probabilidad de abandonar la compañía utilizando información contractual, demográfica y de los servicios contratados.

A lo largo del proyecto se realizó un proceso completo de integración de datos, análisis exploratorio, preparación de variables, tratamiento del desbalance de clases y evaluación comparativa de múltiples algoritmos de clasificación para seleccionar la alternativa con mejor capacidad predictiva.

---

## Objetivo

Desarrollar un modelo de Machine Learning capaz de predecir la fuga de clientes de una empresa de telecomunicaciones y comparar diferentes algoritmos de clasificación para identificar la solución con mejor desempeño.

---

## Conjunto de datos

La información utilizada proviene de distintas fuentes relacionadas con:

- Información contractual de los clientes.
- Servicios de internet.
- Servicios telefónicos.
- Información demográfica.
- Facturación mensual y acumulada.
- Estado de permanencia o cancelación del servicio.

Después de integrar las diferentes tablas mediante el identificador único de cliente (`customerID`), se obtuvo un conjunto consolidado compuesto por **7.043 clientes**.

---

## Metodología

### 1. Preparación de datos

- Integración de múltiples tablas.
- Conversión de tipos de datos.
- Tratamiento de valores faltantes.
- Construcción de la variable objetivo `Fuga`.
- Eliminación de variables con riesgo de fuga de información.
- Codificación de variables categóricas mediante One-Hot Encoding.
- Balanceo del conjunto de entrenamiento mediante sobremuestreo (Oversampling).

### 2. Análisis Exploratorio de Datos (EDA)

Se analizaron variables categóricas y numéricas para identificar factores asociados al abandono de clientes.

Entre las variables con mayor relación con la fuga se encontraron:

- Tipo de contrato (`Type`).
- Método de pago (`PaymentMethod`).
- Tipo de servicio de internet (`InternetService`).
- Seguridad en línea (`OnlineSecurity`).
- Soporte técnico (`TechSupport`).

También se identificaron diferencias relevantes en variables numéricas como:

- `MonthlyCharges`
- `TotalCharges`

---

### 3. Entrenamiento y evaluación de modelos

Se evaluaron distintos algoritmos de clasificación:

- DummyClassifier (Baseline)
- Decision Tree Classifier
- Logistic Regression
- Random Forest Classifier
- LightGBM
- XGBoost

Las métricas utilizadas fueron:

#### ROC-AUC

Permite medir la capacidad del modelo para diferenciar entre clientes con fuga y clientes que permanecen activos.

#### Recall (Sensibilidad)

Mide la capacidad para identificar correctamente a los clientes que efectivamente abandonan la compañía.

---

## Resultados

| Modelo | ROC-AUC | Sensibilidad |
|----------|----------:|----------:|
| DummyClassifier | 0.5000 | 0.0000 |
| Árbol de Decisión | 0.7890 | 0.8797 |
| Regresión Logística | 0.8349 | 0.7754 |
| Bosque Aleatorio | 0.8283 | 0.8315 |
| LightGBM (Prueba) | **0.8492** | **0.7781** |
| XGBoost | 0.7210 | 0.6043 |

---

## Modelo seleccionado

Tras comparar los modelos desarrollados, **LightGBM** fue seleccionado como modelo final debido a su desempeño competitivo sobre datos no utilizados durante el entrenamiento.

Resultados finales sobre el conjunto de prueba:

- **ROC-AUC:** 0.8492
- **Recall:** 0.7781

Estos resultados indican que el modelo logra distinguir adecuadamente entre clientes con alta y baja probabilidad de fuga e identifica correctamente aproximadamente el 77.8 % de los clientes que efectivamente abandonan la compañía.

---

## Principales hallazgos

- Las características contractuales y los servicios contratados presentan una fuerte relación con la fuga de clientes.
- El tipo de contrato y el método de pago son variables especialmente relevantes para explicar el abandono.
- Los modelos de Machine Learning superaron ampliamente el desempeño del clasificador base.
- El árbol de decisión obtuvo la mayor sensibilidad para detectar clientes en riesgo de abandono.
- La regresión logística mostró un equilibrio sólido entre capacidad discriminativa y detección de clientes con fuga.
- LightGBM presentó el mejor desempeño general sobre el conjunto de prueba y fue seleccionado como modelo final.

---

## Conclusiones

El proyecto demostró que es posible predecir la fuga de clientes utilizando información histórica relacionada con contratos, facturación y servicios contratados.

Durante el desarrollo se construyeron y compararon múltiples algoritmos de clasificación, todos ellos significativamente superiores al modelo base. Los resultados obtenidos evidencian que las variables disponibles contienen información suficiente para identificar patrones asociados al abandono de clientes.

El árbol de decisión destacó por su elevada sensibilidad, detectando cerca del 88 % de los casos de fuga. Por su parte, la regresión logística presentó un desempeño estable y una buena capacidad de discriminación. Finalmente, LightGBM alcanzó los mejores resultados sobre el conjunto de prueba, obteniendo un ROC-AUC de 0.8492 y una sensibilidad de 0.7781, lo que confirma su capacidad para generalizar sobre datos no vistos previamente.

Estos resultados muestran el potencial de las técnicas de aprendizaje automático como herramienta de apoyo para estrategias de retención de clientes. La identificación temprana de usuarios con alto riesgo de abandono puede contribuir al diseño de campañas de fidelización más efectivas, optimizando recursos y reduciendo la pérdida de clientes.

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
