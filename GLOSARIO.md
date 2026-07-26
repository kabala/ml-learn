# Glosario y hoja de ruta de notebooks

Este archivo es el mapa de temas para dominar **aprendizaje supervisado** y
**aprendizaje no supervisado** en este repositorio. Cada fila es un tema
concreto: si ya existe un notebook que lo cubre aparece enlazado y marcado
✅; si todavía no existe, aparece marcado 🔲 con la ruta propuesta y una
frase que resume qué pregunta debería responder ese notebook cuando se cree.

Las convenciones de cómo escribir un notebook nuevo (progresión, estilo
visual, nivel de detalle) están en [AGENTS.md](AGENTS.md#estilo-de-enseñanza-para-este-alumno).

## Aprendizaje supervisado — Regresión

| Tema | Qué aprenderás | Notebook | Estado |
| --- | --- | --- | --- |
| Introducción práctica y scikit-learn | Cómo entrenar y usar una regresión lineal de verdad con `LinearRegression.fit/predict`, qué representan `coef_`/`intercept_`, y por qué otros modelos (`Ridge`, `HuberRegressor`...) comparten el mismo patrón. | [`regresion/regresion_lineal/00_introduccion_y_scikit_learn.ipynb`](notebooks/aprendizaje_supervisado/regresion/regresion_lineal/00_introduccion_y_scikit_learn.ipynb) | ✅ |
| Función de costo (MSE, MAE, RMSE, Huber) | Por qué se eleva el residuo al cuadrado, cómo comparar MSE/MAE/RMSE/Huber y cómo minimizar el costo con descenso de gradiente, viendo su trayectoria paso a paso. | [`regresion/regresion_lineal/01_funcion_de_costo.ipynb`](notebooks/aprendizaje_supervisado/regresion/regresion_lineal/01_funcion_de_costo.ipynb) | ✅ |
| Parámetros `w` y `b` | Qué representa cada parámetro de una recta, cómo cambian la predicción y el costo, y cómo se ve el mapa de costo `(w, b)`. | [`regresion/regresion_lineal/02_parametros_w_y_b.ipynb`](notebooks/aprendizaje_supervisado/regresion/regresion_lineal/02_parametros_w_y_b.ipynb) | ✅ |
| Huber Loss en profundidad | Cómo Huber combina precisión cerca de 0 con robustez lejos de 0, y cuándo preferirla sobre MSE/MAE con casos reales de outliers. | [`regresion/regresion_lineal/03_huber_loss_en_profundidad.ipynb`](notebooks/aprendizaje_supervisado/regresion/regresion_lineal/03_huber_loss_en_profundidad.ipynb) | ✅ |
| MSE en profundidad | Por qué minimizar MSE equivale a buscar la media condicional, con un ejemplo simple sin outliers y uno real (viviendas de California con valores recortados) que muestra cuándo esa propiedad ayuda y cuándo perjudica. | [`regresion/regresion_lineal/04_mse_en_profundidad.ipynb`](notebooks/aprendizaje_supervisado/regresion/regresion_lineal/04_mse_en_profundidad.ipynb) | ✅ |
| MAE en profundidad | Por qué minimizar MAE equivale a buscar la mediana condicional, con un ejemplo simple con un error de captura y el mismo dataset real de California, y por qué ninguna métrica es universalmente mejor. | [`regresion/regresion_lineal/05_mae_en_profundidad.ipynb`](notebooks/aprendizaje_supervisado/regresion/regresion_lineal/05_mae_en_profundidad.ipynb) | ✅ |
| Mínimos cuadrados vs. descenso de gradiente | Qué dos condiciones (modelo lineal en sus parámetros + costo cuadrático) permiten una fórmula cerrada, y cómo usar el atributo `n_iter_` de scikit-learn para saber, sin memorizar, si un modelo la usó o iteró. | [`regresion/regresion_lineal/06_minimos_cuadrados_vs_descenso_de_gradiente.ipynb`](notebooks/aprendizaje_supervisado/regresion/regresion_lineal/06_minimos_cuadrados_vs_descenso_de_gradiente.ipynb) | ✅ |
| Regresión lineal múltiple | Cómo se extiende `ŷ = wx + b` a varias variables de entrada, y cómo interpretar cada coeficiente por separado manteniendo las demás variables fijas. | `regresion/regresion_lineal/04_regresion_lineal_multiple.ipynb` | 🔲 |
| Features polinomiales / no lineales | Cómo capturar relaciones curvas con `PolynomialFeatures`, y cómo se ve el sobreajuste al añadir demasiado grado. | `regresion/regresion_polinomial/01_features_no_lineales.ipynb` | 🔲 |
| Regularización Ridge y Lasso | Qué es "penalizar coeficientes grandes", cómo L2 (Ridge) encoge coeficientes y L1 (Lasso) puede llevarlos a cero, visto como caminos de coeficientes. | `regresion/regularizacion/01_ridge_y_lasso.ipynb` | 🔲 |
| Métricas de regresión (R² y residuos) | Qué significa R² visualmente (varianza explicada vs. no explicada) y cómo leer un gráfico de residuos para detectar problemas del modelo. | `regresion/metricas/01_r2_y_analisis_de_residuos.ipynb` | 🔲 |
| Train/test split y validación cruzada | Por qué evaluar con los mismos datos de entrenamiento engaña, cómo funciona k-fold visualmente y cómo evitar fuga de información. | `regresion/validacion/01_train_test_split_y_validacion_cruzada.ipynb` | 🔲 |
| Sesgo, varianza y curvas de aprendizaje | Qué es subajuste vs. sobreajuste con ejemplos visuales, y cómo leer una curva de aprendizaje para diagnosticar cuál de los dos tienes. | `regresion/validacion/02_sesgo_varianza_y_overfitting.ipynb` | 🔲 |
| Pipelines y `ColumnTransformer` | Cómo encadenar preprocesamiento y modelo sin fugas de datos, aplicando transformaciones distintas a columnas numéricas y categóricas. | `regresion/pipelines/01_pipelines_y_column_transformer.ipynb` | 🔲 |
| Búsqueda de hiperparámetros | Qué es un hiperparámetro (vs. un parámetro aprendido), y cómo `GridSearchCV`/`RandomizedSearchCV` prueban combinaciones de forma sistemática. | `regresion/hiperparametros/01_grid_search_y_random_search.ipynb` | 🔲 |

## Aprendizaje supervisado — Clasificación

| Tema | Qué aprenderás | Notebook | Estado |
| --- | --- | --- | --- |
| Función de costo (log loss) | Cómo la sigmoide convierte un puntaje en probabilidad, por qué la entropía cruzada binaria mide bien esas probabilidades, y de dónde sale su gradiente `p - y`. | [`clasificacion/regresion_logistica/01_funcion_de_costo.ipynb`](notebooks/aprendizaje_supervisado/clasificacion/regresion_logistica/01_funcion_de_costo.ipynb) | ✅ |
| Frontera de decisión y regularización | Cómo se ve la frontera que separa clases en 2D, cómo se mueve al cambiar el umbral de decisión, y cómo la regularización la suaviza. | `clasificacion/regresion_logistica/02_frontera_de_decision.ipynb` | 🔲 |
| Matriz de confusión, precisión y recall | Qué son verdaderos/falsos positivos y negativos con ejemplos visuales, y por qué la exactitud sola engaña en datos desbalanceados. | `clasificacion/metricas/01_matriz_de_confusion_precision_recall.ipynb` | 🔲 |
| Curvas ROC-AUC y precisión-recall | Cómo cambian precisión y recall al mover el umbral de decisión, y cómo leer e interpretar ambas curvas para comparar modelos. | `clasificacion/metricas/02_roc_auc_y_curva_precision_recall.ipynb` | 🔲 |
| K-Vecinos más cercanos (KNN) | Cómo clasifica KNN "votando" entre vecinos, y cómo cambia la frontera de decisión al variar `k` (de una frontera irregular a una muy suave). | `clasificacion/knn/01_vecinos_cercanos.ipynb` | 🔲 |
| Árboles de decisión | Cómo un árbol elige dónde "cortar" los datos, visualizado como reglas if/else, y cómo la profundidad del árbol afecta el sobreajuste. | `clasificacion/arboles_de_decision/01_arboles_de_decision.ipynb` | 🔲 |
| Máquinas de vector soporte (SVM) | Qué es un margen máximo entre clases, visualizado en 2D, y qué hace el "truco del kernel" para separar clases que no son linealmente separables. | `clasificacion/svm/01_maquinas_de_vector_soporte.ipynb` | 🔲 |
| Naive Bayes | Cómo Naive Bayes usa probabilidades condicionales "ingenuas" (asumiendo independencia) para clasificar, con un ejemplo clásico de texto/spam. | `clasificacion/naive_bayes/01_naive_bayes.ipynb` | 🔲 |
| Ensambles: Random Forest | Cómo combinar muchos árboles "débiles" mejora la predicción, y por qué reduce el sobreajuste de un árbol individual. | `clasificacion/ensambles/01_random_forest.ipynb` | 🔲 |
| Ensambles: Gradient Boosting con XGBoost | Cómo el boosting entrena modelos en secuencia para corregir los errores del anterior, usando XGBoost (ya es dependencia del proyecto). | `clasificacion/ensambles/02_gradient_boosting_con_xgboost.ipynb` | 🔲 |
| Clases desbalanceadas | Por qué la exactitud falla cuando una clase es rara, y qué estrategias existen (pesos de clase, remuestreo, métricas adecuadas). | `clasificacion/desbalance_de_clases/01_clases_desbalanceadas.ipynb` | 🔲 |
| Interpretabilidad básica | Cómo leer la importancia de variables de un modelo entrenado, y sus límites (correlación entre variables, importancia no es causalidad). | `clasificacion/interpretabilidad/01_importancia_de_variables.ipynb` | 🔲 |

## Aprendizaje no supervisado

| Tema | Qué aprenderás | Notebook | Estado |
| --- | --- | --- | --- |
| PCA explicado visualmente | Qué significa "reducir dimensiones" con un ejemplo 2D→1D dibujado a mano, cómo se eligen las componentes principales y cuánta varianza explican. | `no_supervisado/reduccion_de_dimensionalidad/01_pca_explicado_visualmente.ipynb` | 🔲 |
| K-Means paso a paso | Cómo K-Means asigna puntos a centroides y los recalcula iterativamente, viendo la animación de convergencia y cómo elegir `k` con el método del codo. | `no_supervisado/clustering/01_kmeans_paso_a_paso.ipynb` | 🔲 |
| Clustering jerárquico | Cómo se construye un dendrograma uniendo los puntos más cercanos, y cómo "cortarlo" a distintas alturas produce distinto número de grupos. | `no_supervisado/clustering/02_clustering_jerarquico.ipynb` | 🔲 |
| DBSCAN y densidad | Cómo DBSCAN agrupa por densidad en vez de por distancia a un centroide, y por qué puede detectar formas irregulares y marcar outliers como ruido. | `no_supervisado/clustering/03_dbscan_y_densidad.ipynb` | 🔲 |
| Evaluar un clustering | Cómo medir qué tan buenos son los grupos sin tener etiquetas reales, usando el coeficiente de silueta y el método del codo (inertia). | `no_supervisado/evaluacion_exploratoria/01_como_evaluar_un_clustering.ipynb` | 🔲 |
| Detección de anomalías | Cómo Isolation Forest identifica observaciones "raras" sin etiquetas previas, y en qué se diferencia de un problema de clasificación supervisado. | `no_supervisado/deteccion_de_anomalias/01_isolation_forest_y_outliers.ipynb` | 🔲 |

## Cómo usar este glosario

- Antes de crear un notebook pendiente (🔲), revisa que la ruta y el nombre
  sigan la convención ya usada en el repo:
  `notebooks/aprendizaje_<supervisado|no_supervisado>/<tarea>/<algoritmo>/NN_tema.ipynb`.
- Al terminar un notebook, actualiza su fila a ✅ y enlázalo.
- Si surge un tema nuevo que no está aquí, añade una fila antes de crear el
  notebook — así el glosario se mantiene como la fuente de verdad del avance.
