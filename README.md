# GameStop Customer Reviews

## 1. Project description 👇

Este proyecto se centra en el análisis de un dataset en Kaggle, sobre reseñas de productos de la tienda GameStop. El objetivo es realizar un análisis detallado y clasificar los comentarios de los clientes en tres categorías: positivos, neutrales y negativos. El análisis se divide en tres secciones principales: preprocesamiento de datos, análisis exploratorio de datos y análisis de sentimientos.

# Parte I - Preprocesamiento de datos:

## 1. ¿Cómo limpiaría y preprocesaría los datos para un análisis más detallado?

1. **Eliminación de duplicados**: Remover filas duplicadas en el subset de 'review_description' para evitar comentarios repetidos.
2. **Manejo de valores nulos**: En este caso fue más fácil rellenar valores nulos por contexto (e.g., "yes" por  "Verified Purchaser" y "no" por "nan").
3. **Extracción de categorias**: Utilizar bibliotecas como `re` para obtener palabras claves de las url's.

## 2. ¿Cómo normalizarías los datos?

1. **Normalización del texto**: Convertir todo el texto a minúsculas para evitar distinciones entre palabras como "Nintendo" y "nintendo".
2. **Tokenización**: Dividir el texto en palabras individuales o tokens para obtener términos relevantes a comentarios positivos y negativos.
3. **Eliminación de stopwords**: Remover palabras comunes que no aportan valor significativo al análisis (e.g., "the", "of", "a").
4. **Lematización/Stemming**: Reducir las palabras a su forma base (e.g., "playing" a "play").
5. **Conversión de etiquetas**: Para Machine Learning, se usó LabelEncoder para convertir features en valores numéricos, usar técnicas como Min-Max Scaling o Standard Scaling 
6. **Escalado de datos**: Para Machine Learning, se usó RobustScaler para normalizar los valores entre un rango específico (e.g., entre 1 y 10 y no entre 1 y 5000).



### Preprocesamiento de Datos

Para llevar a cabo un análisis más detallado, los datos deben ser limpiados y preprocesados. Las etapas de preprocesamiento incluyen:

1. **Limpieza de Datos**: 
    - Eliminación de duplicados.
    - Manejo de valores nulos.
    - Corrección de errores tipográficos y normalización de texto (por ejemplo, convertir todo el texto a minúsculas).

2. **Normalización de Datos**: 
    - Conversión de las reseñas a un formato uniforme.
    - Tokenización de los comentarios.
    - Eliminación de stopwords (palabras comunes que no aportan valor significativo al análisis).

### Análisis Exploratorio de los Datos

El análisis exploratorio se centra en identificar los términos más frecuentes en los comentarios y analizar las diferencias entre los comentarios positivos y negativos. Esto incluye:

1. **Identificación de Términos Relevantes**:
    - Extracción de las palabras más comunes en los comentarios.
    - Análisis de la frecuencia de términos para detectar patrones significativos.

2. **Distribución de Términos**:
    - Comparación de la distribución de términos entre comentarios positivos (aquellos que recomiendan el producto) y comentarios negativos.
    - Visualización básica de los datos mediante gráficos de barras, nubes de palabras, etc.

### Análisis de Sentimientos

En esta sección, se entrenan uno o varios modelos de clasificación para categorizar los comentarios en positivos (rating 4-5), neutrales (rating 3) y negativos (rating 1-2). Las etapas incluyen:

1. **Entrenamiento de Modelos**:
    - Selección de modelos de clasificación adecuados (por ejemplo, Naive Bayes, SVM, redes neuronales).
    - Entrenamiento y validación de los modelos usando el dataset preprocesado.

2. **Métricas de Evaluación**:
    - Justificación de la métrica de evaluación seleccionada (por ejemplo, precisión, recall, F1-score).
    - Selección del modelo más adecuado para producción basado en la métrica de evaluación elegida.

Este proyecto proporciona un enfoque integral para analizar y clasificar reseñas de productos, ofreciendo insights valiosos sobre la percepción de los clientes y mejorando la capacidad de respuesta a sus comentarios.

### Diseño de la Architectura Funcional y Pipeline de Datos:

![Pipeline Architecture Design](https://github.com/AndrewBavuels/GameStop-Reviews/blob/main/images/Pipeline%20Architecture%20Draft.png)

## **2. Technology stack 💻**

### Programming language:
- [Python](https://docs.python.org/3/)

### Python Libraries:
- [pandas](https://pandas.pydata.org/docs/reference/frame.html): For data manipulation and analysis.
- [numpy](https://numpy.org/doc/stable/): For mathematical operations and array manipulation.
- [matplotlib.pyplot](https://matplotlib.org/stable/contents.html): For data visualization.
- [seaborn](https://seaborn.pydata.org/): For statistical data visualization.
- [re](https://docs.python.org/3/library/re.html): For regular expression operations.
- [nltk](https://nltk.org/): For sentiment analysis among natural language processing tasks.
- [afinn](https://pypi.org/project/afinn/): For sentiment analysis using the AFINN lexicon.
- [wordcloud](https://github.com/amueller/word_cloud): For creating word cloud visualizations.
- [sklearn](https://scikit-learn.org/stable/): For machine learning modeling and model evaluation.
- [scipy](https://docs.scipy.org/doc/scipy-1.12.0/reference/generated/scipy.stats.skewnorm.html): For scientific and technical computing.

#### Models and Evaluation Metrics:
- [xgboost](https://xgboost.readthedocs.io/en/latest/): For gradient boosting machine learning models, which are powerful for classification tasks.
- Evaluation metrics include: `mean_squared_error`, `f1_score`, `precision_score`, `recall_score`, `roc_auc_score`, `r2_score`.

#### Data Preprocessing:
- [RobustScaler](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.RobustScaler.html): For feature scaling.

#### Modeling Tools:
- [train_test_split](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.train_test_split.html): For splitting data into training and testing sets.
- [GridSearchCV](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html): For hyperparameter tuning using cross-validated grid search.

#### Distribution platform
- [Anaconda](https://www.anaconda.com/)

#### Computing environment
- [Jupyter Notebooks](https://jupyter.org/)

Dado el dataset [gamestop_product_reviews_dataset_sample](https://www.kaggle.com/datasets/thedevastator/gamestop-customer-reviews-dataset), responde a las siguientes preguntas:

# Parte I - Preprocesamiento de datos:

1. **¿Cómo limpiaría y preprocesaría los datos para un análisis más detallado?** 
2. **¿Cómo normalizarías los datos?**

En la siguiente imagen ya muestro adelanto y cuales son los valores nulos que se encuentran:

![img_1](https://github.com/AndrewBavuels/GameStop-Reviews/blob/main/images/1.png)

A partir de los urls, tambien saqué las categorías de los productos que se venden en Gamestop.

![img_2](https://github.com/AndrewBavuels/GameStop-Reviews/blob/main/images/2.png)

En paralelo, me ayudaba navegando en la misma pagína de [Gamestop](https://www.gamestop.com/)

![img_3](https://github.com/AndrewBavuels/GameStop-Reviews/blob/main/images/3.png)

![img_4](https://github.com/AndrewBavuels/GameStop-Reviews/blob/main/images/4.png)

![img_5](https://github.com/AndrewBavuels/GameStop-Reviews/blob/main/images/5.png)

![img_6](https://github.com/AndrewBavuels/GameStop-Reviews/blob/main/images/6.png)

#### Observaciones:

- La columna ['review_status'] es nuestro objetivo y consta de 1 y 0 (positivo y negativo, respectivamente)
- Los valores nulos se manejaron muy bien desde el principio, en el sentido que no se tuvieron que eliminar registros.
- Hay demasiadas columnas categóricas (13) en comparación con las 7 numéricas.
- Ver en que categorias se concentran más los reviews negativos y los positivos.
- Hacer un diagrama de pareto
-------------------------------------------------------------------------------------------------------------------------------------------------------------

# Parte II - Análisis exploratorio de los datos con NLP
1. **¿Cuáles son los términos relevantes más frecuentes en los comentarios?**  
   ¿Encuentras diferencias significativas entre la distribución de términos provenientes de comentarios positivos y negativos?  
   Para esta sección se entiende comentario positivo por aquel que termina recomendando el producto.

   ## Comentarios positivos:
   ![pos_reviews](https://github.com/AndrewBavuels/GameStop-Reviews/blob/main/images/positivos_wordcloud.png)

   ## Comentarios negativos:
   ![neg_reviews](https://github.com/AndrewBavuels/GameStop-Reviews/blob/main/images/negativos_wordcloud.png)

3. **Muestre una visualización básica de los datos**

![img_7](https://github.com/AndrewBavuels/GameStop-Reviews/blob/main/images/7.png)

   #### Observaciones:

1. el 80% de los comentarios negativos provienen del 20% de las categorias de productos (video games y consoles-hardware). Evidentemente de los productos que las personas mas compran y hacen comentarios. Esto se puede observar en la intersección de la línea verde punteada con la curva roja de los comentarios aumentados.
2. Para poner un modelo experimental de producción y sea lo mas preciso, utilizaremos la información de solo esas 2 categorias, con comentarios positivos y negativos
-------------------------------------------------------------------------------------------------------------------------------------------------------------


# Parte III. Análisis de sentimientos con ML

1. **Entrene uno o varios modelos para clasificar los comentarios en las siguientes categorías: positivos (rating 4 - 5), neutrales (rating 3) y negativos.**  
   Justifica qué métrica de evaluación has elegido para determinar el modelo que pondrías en producción.
-------------------------------------------------------------------------------------------------------------------------------------------------------------


