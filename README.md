# Clasificación de intención de compra online
Test de ingreso realizado por Brenda Martinez. Este proyecto aborda un problema de clasificación binaria utilizando el dataset Online Shoppers Intention, con el objetivo de predecir la variable Revenue (intención de compra). Se realizaron análisis exploratorios, limpieza de datos, selección de características, modelado y evaluación de distintos algoritmos.

## 1. Objetivo
Desarrollar un modelo predictivo capaz de identificar usuarios con mayor probabilidad de compra en un entorno de e-commerce, optimizando el balance entre recall (no perder compradores potenciales) y precisión (evitar falsos positivos innecesarios).

## 2. Dataset
El dataset utilizado es online_shoppers_intention.csv, compuesto por:

12,330 registros

18 variables relacionadas con comportamiento de navegación, duración de visitas, tasas de rebote, páginas vistas, información temporal, entre otras.

Variable objetivo: Revenue (1 = el usuario compró, 0 = no compró)

## 3. Proceso de desarrollo
### 3.1 Análisis Exploratorio de Datos (EDA)
Identificación de tipos de variables (numéricas, categóricas, binarias).

Conversión de variables categóricas a formato numérico cuando fue necesario.

Análisis de correlaciones y detección de variables redundantes.

Evaluación de outliers (se decidió no eliminarlos por su impacto en el balance de clases).

### 3.2 Selección de características
Se evaluaron cinco configuraciones de features (set_a a set_e) eliminando columnas con baja correlación o redundancia.
El dataset final elegido fue set_d, que elimina:

Administrative, Informational, ProductRelated, Browser, TrafficType, Region, ExitRates

### 3.3 Modelos evaluados
Random Forest (Base y Tuned)

Logistic Regression

Hiperparámetros ajustados en Random Forest utilizando RandomizedSearchCV.

### 3.4 Balanceo de clases
La variable target Revenue estaba desbalanceada (~84% clase 0 vs. 16% clase 1).
Se probaron:

Baseline (sin balanceo)

Oversampling 50/50

Undersampling ~60/40

Se decidió no aplicar balanceo adicional (Baseline) por obtener el mejor F1-score y ROC AUC.

## 4. Resultados
### 4.1 Modelo final elegido
Modelo: Random Forest Tuned

Dataset: set_d

Balanceo: Sin balanceo adicional (Baseline)

### 4.2 Métricas finales en test
F1-score: 0.6635

Recall: 0.7356

Precision: 0.6043

ROC AUC: 0.9254

### 4.3 Importancia de variables
PageValues

ProductRelated_Duration

BounceRates

Month

VisitorType

## 5. Conclusiones
El modelo final logra un alto poder discriminativo (ROC AUC 0.925) y un buen equilibrio entre precision y recall (F1 0.66).

No se observó overfitting: las métricas en test son coherentes con las de validación cruzada.

El modelo es interpretable y puede priorizar acciones comerciales sobre usuarios con mayor propensión a comprar.
