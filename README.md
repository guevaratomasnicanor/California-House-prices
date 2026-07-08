# 🌴 California House Prices

El objetivo del proyecto es **predecir el valor medio de las viviendas en California**, utilizando variables demográficas, geográficas y socioeconómicas del censo estatal.

---

## 📊 Dataset

📦 **Fuente:** [California Housing Dataset – scikit-learn / UCI Machine Learning Repository]  
El dataset contiene información de **20.640 observaciones** sobre distritos de California, proveniente del censo de 1990.

**Variables principales:**
- `longitude` → Longitud geográfica del distrito  
- `latitude` → Latitud geográfica del distrito  
- `housing_median_age` → Edad media de las viviendas  
- `total_rooms` → Total de habitaciones  
- `total_bedrooms` → Total de dormitorios  
- `population` → Población del distrito  
- `households` → Número de hogares  
- `median_income` → Ingreso medio por hogar  
- `median_house_value` → Valor medio de la vivienda (variable objetivo)  
- `ocean_proximity` → Proximidad al océano (categoría: Inland, Near Ocean, Near Bay, Island)

---

## 🧹 Limpieza de datos y Feature Engineering

- ✅ **Imputación de nulos:** Se completaron los valores faltantes en `total_bedrooms` utilizando la mediana del distrito.  
- ⚠️ **Tratamiento de outliers:** Se eliminaron los registros con un `median_house_value` mayor o igual a u$s 500.000, debido a que el dataset original presenta un tope artificial en ese valor que genera ruido en el aprendizaje del modelo.  
- ⚙️ **Preprocesamiento:** Se aplicó escalado/normalización a las variables numéricas y encoding One-Hot para la variable categórica (`ocean_proximity`).

---

## 🔍 Precios en el mapa

<img width="823" height="686" alt="Precios de viviendas en el mapa de California" src="https://github.com/user-attachments/assets/542f2391-fa3d-4f61-b310-ec9ecc871e76" />

## 🔍 Insights Principales

* 💰 **El factor socioeconómico manda:** El ingreso medio (`median_income`) es la variable con mayor poder predictivo. Existe una fuerte correlación lineal positiva con el valor de la propiedad.
 
<img width="627" height="363" alt="Correlación Ingreso vs Precio" src="https://github.com/user-attachments/assets/977c4efd-a2d5-4f89-9ce3-72bae19f5fbb" />

* 🌊 **El efecto océano:** Las propiedades ubicadas en la costa o en zonas de bahía muestran un piso de valor significativamente más alto. Los precios caen drásticamente a medida que los distritos se adentran en el continente (Inland).

<img width="1333" height="689" alt="Distribución de precios por proximidad al océano" src="https://github.com/user-attachments/assets/f9175b67-a2bb-4c4f-ad5d-d608c964a9a5" />

---

## 🤖 Modelado Predictivo

Se evaluaron e implementaron algoritmos basados en árboles de decisión y ensambles para resolver este desafío de regresión.

🏆 **Mejor Modelo:** `XGBoost`. Logró el menor error absoluto medio (u$s 25.238 por vivienda) y el mayor coeficiente de determinación, explicando el **84% de la variabilidad** de los datos.

### 📊 Tabla de Performance

| Modelo | RMSE | MAE | MAPE | R² |
| :--- | :---: | :---: | :---: | :---: |
| **XGBoost** | **$38,995.29** | **$25,238.24** | **13.72%** | **0.8400** |
| LightGBM | $39,954.21 | $26,076.75 | 14.18% | 0.8318 |
| Random Forest | $42,259.88 | $27,200.42 | 14.61% | 0.8118 |

---

## 💼 Caso de Negocio (Business Impact)

Tener un buen $R^2$ solo es útil si se traduce en rentabilidad económica. Para validar el modelo en un entorno real, se diseñó una simulación financiera simulando la operación de una compañía **PropTech** o una firma de inversión inmobiliaria:

* **Estrategia:** Utilizar el modelo para detectar anomalías de mercado (barrios/propiedades infravaloradas por el algoritmo).
* **Supuestos Conservadores:** Se incorporaron costos de apalancamiento financiero, comisiones transaccionales y una **tasa de caída de operaciones del 25%** (1 de cada 4 negocios se cae antes del cierre).
* **Resultado:** Bajo este escenario de estrés, el Retorno Sobre la Inversión (**ROI**) proyectado se ubica sólidamente entre el **18% y el 26%**.

> 💡 **Conclusión estratégica:** Un modelo predictivo bien calibrado no representa un costo de infraestructura para el equipo de IT, sino un motor de generación de valor que mitiga el riesgo financiero y optimiza la asignación de capital.

---

## 🧰 Tecnologías utilizadas

- **Lenguaje:** Python  
- **Bibliotecas:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`, `xgboost`, `lightgbm`  
- **Técnicas aplicadas:**
  - Análisis Exploratorio de Datos (EDA) y visualización georreferenciada.  
  - Limpieza de datos, manejo de topes artificiales (outliers) e imputación.  
  - Feature Engineering y transformación de variables categóricas.  
  - Validación cruzada y optimización de hiperparámetros.  
  - Evaluación robusta mediante múltiples métricas de regresión (R², MAE, RMSE, MAPE).
