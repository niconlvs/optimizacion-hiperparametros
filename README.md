# Optimización de Hiperparámetros con Random Forest

## Descripción
Optimización de hiperparámetros de un `RandomForestClassifier` para clasificar la ocupación de clientes usando GridSearchCV y RandomizedSearchCV.

## Estructura del repositorio

- 10_Optimizacion_Hiperparametros.ipynb # Cuaderno Jupyter con todo el flujo
- random_forest_final_model.pkl # Modelo serializado
- LICENSE # Licencia MIT
- README.md # Este archivo


## Datos utilizados
- **Origen:**  
  `https://raw.githubusercontent.com/niconlvs/ModelosML/main/transacciones.csv`  
- **Variables predictoras:**  
  - Numéricas: `TransactionAmount`, `CustomerAge`, `LoginAttempts`, `AccountBalance`  
  - One-hot: `TransactionType_*`, `Channel_*`  
- **Variable objetivo:** `CustomerOccupation`

## Pasos principales
1. **Carga y preprocesamiento**  
   - Lectura del CSV  
   - Escalado de numéricas (StandardScaler) y codificación de categóricas (OneHotEncoder)  
2. **Definición de modelo**  
   - `RandomForestClassifier(random_state=42)`  
   - Selección de hiperparámetros a optimizar:  
     `n_estimators`, `max_depth`, `min_samples_split`  
3. **GridSearchCV** (5 folds)  
   - Parámetros probados ≥3 valores c/u  
   - **Mejor score:** 0.8053  
   - **Mejores params:** `{'n_estimators': 500, 'max_depth': 10, 'min_samples_split': 10}`  
4. **RandomizedSearchCV** (25 iteraciones, 5 folds)  
   - Espacio de búsqueda ≥5 valores c/u  
   - **Mejor score:** 0.8057  
   - **Mejores params:** `{'n_estimators': 100, 'max_depth': 10, 'min_samples_split': 15}`  
5. **Reentrenamiento final**  
   - Con los parámetros de RandomizedSearchCV  
   - **Accuracy final:** 0.8057  
   - Serialización en `random_forest_final_model.pkl`

## ▶️ Cómo reproducir
```bash
git clone https://github.com/niconlvs/optimizacion-hiperparametros.git
cd optimizacion-hiperparametros
pip install -r requirements.txt    # (genera tu propio requirements con pip freeze)
jupyter notebook 10_Optimizacion_Hiperparametros.ipynb
```
## 📈 Resultados obtenidos
- **GridSearchCV**:  
  - Mejor score: 0.8053  
  - Parámetros: `{'n_estimators': 500, 'max_depth': 10, 'min_samples_split': 10}`  
- **RandomizedSearchCV**:  
  - Mejor score: 0.8057  
  - Parámetros: `{'n_estimators': 100, 'max_depth': 10, 'min_samples_split': 15}`  
- **Modelo final**: accuracy 0.8057 en todo el conjunto.


##📜 Licencia
Este proyecto está bajo la Licencia MIT. Consulta el archivo LICENSE para más detalles.

