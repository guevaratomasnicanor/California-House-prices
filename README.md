# 🌴 California House Prices

El objetivo del proyecto es **predecir el valor medio de las viviendas en California**, utilizando variables demográficas, geográficas y socioeconómicas del censo estatal.

---

## 📊 Dataset

📦 Fuente: [California Housing Dataset – scikit-learn / UCI Machine Learning Repository]  
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
- `ocean_proximity` → Proximidad al océano (categoría: inland, near ocean, near bay, island)

---

## 🧹 Limpieza de datos

- ✅ **Sin valores faltantes significativos**, excepto algunos `total_bedrooms`, completados mediante imputación con la mediana.  
- ⚠️ **Outliers leves** en `median_income` y `median_house_value`.  
- Se aplicó normalización y encoding de variables categóricas (`ocean_proximity`).

---

## 🔍 Precios en el mapa:

<img width="823" height="686" alt="Captura de pantalla 2025-11-12 155846" src="https://github.com/user-attachments/assets/542f2391-fa3d-4f61-b310-ec9ecc871e76" />

## 🔍 Insights Principales


- 💰 **El ingreso medio (`median_income`)** es el **factor más importante** para predecir el valor de las viviendas.
 
<img width="627" height="363" alt="Captura de pantalla 2025-11-12 153944" src="https://github.com/user-attachments/assets/977c4efd-a2d5-4f89-9ce3-72bae19f5fbb" />

- 🌊 **Las zonas cercanas al océano o bahías** tienen **valores significativamente más altos**, mientras que las mas lejanas a cuerpos de agua poseen precios más economicos. 

<img width="1333" height="689" alt="Captura de pantalla 2025-11-12 154706" src="https://github.com/user-attachments/assets/f9175b67-a2bb-4c4f-ad5d-d608c964a9a5" />

---

## 🤖 Modelado Predictivo

Se evaluaron distintos modelos de regresión para predecir `median_house_value`.

**Mejor modelo:** `Random Forest`

| Modelo | RMSE | MAE | R² |
|---------|------|-----|----|
| Random Forest | **48,760** | **33,240** | 0.83 |
| XGBoost | 50,310 | 34,210 | 0.82 |
| Linear Regression | 68,540 | 45,120 | 0.68 |

---

## 🧰 Tecnologías utilizadas

- **Lenguaje:** Python  
- **Bibliotecas:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`, `xgboost`  
- **Técnicas:**  
  - Análisis exploratorio de datos (EDA)  
  - Mapas de correlación y gráficos geográficos  
  - Feature engineering y normalización  
  - Validación cruzada  
  - Comparación de modelos  

---


