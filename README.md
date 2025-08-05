# Proyecto: Telecom X - Etapa 2 - Machine Learning para Churn de Clientes  
**Repositorio:** `ml_churn`

---

## Índice 📋  
1. Descripción del proyecto  
2. Acceso al proyecto  
3. Etapas del proyecto  
4. Descripción de los datos  
5. Resultados y conclusiones  
6. Tecnologías utilizadas  
7. Agradecimientos  
8. Desarrollador del proyecto  

---

## 1. Descripción del proyecto 📚  
Se implementaron modelos supervisados de Machine Learning para predecir cancelaciones de clientes en una empresa de telecomunicaciones. Se aplicó preprocesamiento, análisis de multicolinealidad y optimización de hiperparámetros.  
El modelo final fue seleccionado priorizando el **Recall**, buscando minimizar falsos negativos. Finalmente, se validó su uso con un pipeline productivo sobre datos sintéticos.

---



---

## 2. Etapas del proyecto 📝  
- Importación de librerías  
- Preprocesamiento: Encoding, normalización, correlación  
- Modelado: Árboles, regresión, SVM, KNN, XGBoost  
- Evaluación: Métricas, sobreajuste/subajuste, importancia de variables  
- Simulación en entorno productivo con pipeline  

---

## 3. Descripción de los datos 📊  
Se integraron dos datasets (`preprocessed_TelecomX_data.json`, `clientes_altovalor_abandonan.json`) con 7152 registros.  
Variables: 19 predictoras y 1 objetivo (Churn).  
Se aplicó balanceo con **NearMiss v3** (reducción) y **SMOTENC** (simulación).  
Transformaciones específicas por tipo de modelo:

- Árboles: One-hot encoding, sin escalado  
- Modelos lineales: One-hot (drop='first'), escalado con RobustScaler  
- KNN: One-hot (drop='if_binary'), escalado con RobustScaler  
- Objetivo (Churn): Label Encoding (`Yes`→1, `No`→0)  

---

## 4. Resultados y conclusiones ✍️  

**Modelos evaluados:**  
- Random Forest  
- Logistic Regression  
- XGBoost  
- SVM  
- KNN (descartado por bajo Recall)

**Métricas destacadas (Recall ≥ 0.85 con umbral modificado):**

| Modelo               | Recall | Precision | F1-score | AUC    |
|----------------------|--------|-----------|----------|--------|
| **Random Forest**    | 0.862  | 0.4914    | 0.6259   | 0.8326 |
| Logistic Regression  | 0.862  | 0.4539    | 0.5947   | 0.8137 |
| XGBoost              | 0.855  | 0.4695    | 0.6062   | 0.8188 |
| SVM                  | 0.862  | 0.4571    | 0.5974   | 0.8073 |

**Modelo campeón:**  
**Random Forest**, por mayor capacidad de generalización y menor tasa de falsos positivos al alcanzar Recall ≥ 0.85.

**Importancia de variables:**  
Visualizada en `RandomForest_importancias`, complementada con coeficientes de regresión logística para interpretar dirección e impacto.

**Pipeline productivo:**  
Recibe JSON con datos crudos y genera:

- `mode='production'`: Probabilidad y etiqueta de churn.  
- `mode='monitor'`: Métricas y log de ejecución.

---

## 5. Tecnologías utilizadas 🛠️  
- Python + Jupyter Notebook  
- Git & GitHub  

---

## 6. Agradecimientos 🤝  
Gracias a **Oracle** y **Alura LATAM** por brindar los recursos de capacitación para el desarrollo de este proyecto.

---

## 7. Desarrollador del proyecto 👷  

| **Milan yb** | Data Scientist Junior |  
📫 milanyb@gmail.com | 💻 LinkedIn  
