# GameStop Customer Reviews

## 1. Project description 👇

Este proyecto se centra en el análisis de un dataset en Kaggle, sobre reseñas de productos de la tienda GameStop. El objetivo es realizar un análisis detallado y clasificar los comentarios de los clientes en tres categorías: positivos, neutrales y negativos. El análisis se divide en tres secciones principales: preprocesamiento de datos, análisis exploratorio de datos y análisis de sentimientos, descrito en la siguiente arquitectura de la pipeline de datos:

### Diseño de la Architectura Funcional y Pipeline de Datos:

![Pipeline Architecture Design](https://github.com/AndrewBavuels/GameStop-Reviews/blob/main/images/Pipeline%20Architecture%20Draft.png)

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

En la siguiente imagen ya muestro adelanto y cuales son los valores nulos que se encuentran:

![img_1](https://github.com/AndrewBavuels/GameStop-Reviews/blob/main/images/1.png)

A partir de los urls, tambien saqué las categorías de los productos que se venden en Gamestop.

![img_2](https://github.com/AndrewBavuels/GameStop-Reviews/blob/main/images/2.png)

En paralelo, me ayudaba navegando en la misma pagína de [Gamestop](https://www.gamestop.com/)

![img_3](https://github.com/AndrewBavuels/GameStop-Reviews/blob/main/images/3.png)

![img_4](https://github.com/AndrewBavuels/GameStop-Reviews/blob/main/images/4.png)

![img_5](https://github.com/AndrewBavuels/GameStop-Reviews/blob/main/images/5.png)

![img_6](https://github.com/AndrewBavuels/GameStop-Reviews/blob/main/images/6.png)

-------------------------------------------------------------------------------------------------------------------------------------------------------------

# Parte II - Análisis exploratorio de los datos con NLP

## 1. ¿Cuáles son los términos relevantes más frecuentes en los comentarios?  
   ¿Encuentras diferencias significativas entre la distribución de términos provenientes de comentarios positivos y negativos?  
   Para esta sección se entiende comentario positivo por aquel que termina recomendando el producto.

   ## Comentarios positivos:
   ![pos_reviews](https://github.com/AndrewBavuels/GameStop-Reviews/blob/main/images/positivos_wordcloud.png)

   ## Comentarios negativos:
   ![neg_reviews](https://github.com/AndrewBavuels/GameStop-Reviews/blob/main/images/negativos_wordcloud.png)

## 2. Muestre una visualización básica de los datos

![img_7](https://github.com/AndrewBavuels/GameStop-Reviews/blob/main/images/7.png)

#### Observaciones:

1. el 80% de los comentarios negativos provienen del 20% de las categorias de productos (video games y consoles-hardware). Evidentemente de los productos que las personas mas compran y hacen comentarios. Esto se puede observar en la intersección de la línea verde punteada con la curva roja de los comentarios aumentados.
2. Para poner un modelo experimental de producción y sea lo mas preciso, utilizaremos la información de solo esas 2 categorias, con comentarios positivos y negativos

-------------------------------------------------------------------------------------------------------------------------------------------------------------

# Parte III. Análisis de sentimientos con ML

## 1. Entrene uno o varios modelos para clasificar los comentarios en las siguientes categorías: positivos (rating 4 - 5), neutrales (rating 3) y negativos.**  
   Justifica qué métrica de evaluación has elegido para determinar el modelo que pondrías en producción.

Para este, solo usé las categorías con el 80% de los reviews negativos.

![img_8](https://github.com/AndrewBavuels/GameStop-Reviews/blob/main/images/8.png)

#### Data Preprocessing:
- [RobustScaler](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.RobustScaler.html): For feature scaling.

![img_9](https://github.com/AndrewBavuels/GameStop-Reviews/blob/main/images/9.png)

#### Modeling Tools:
- [train_test_split](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.train_test_split.html): For splitting data into training and testing sets.

![img_10](https://github.com/AndrewBavuels/GameStop-Reviews/blob/main/images/10.png)

#### Models and Evaluation Metrics:
- [xgboost](https://xgboost.readthedocs.io/en/latest/): For gradient boosting machine learning models, which are powerful for classification tasks.
- [GridSearchCV](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html): For hyperparameter tuning using cross-validated grid search.
- Evaluation metrics include: `mean_squared_error`, `f1_score`, `precision_score`, `recall_score`, `roc_auc_score`, `r2_score`.

![img_11](https://github.com/AndrewBavuels/GameStop-Reviews/blob/main/images/11.png)

#### Mejor modelo:

- Fitting 5 folds for each of 100 candidates, totalling 500 fits
- Mejores hiperparámetros: {'gamma': 0.1, 'learning_rate': 0.4504506741382034, 'max_depth': 3, 'n_estimators': 500}
- RMSE en datos de prueba: 0.84216610155471
- R^2 en datos de prueba: 0.509943603297751

![img_12](https://github.com/AndrewBavuels/GameStop-Reviews/blob/main/images/12.png)

#### Rating predict vs Rating actual
![img_13](https://github.com/AndrewBavuels/GameStop-Reviews/blob/main/images/13.png)

-------------------------------------------------------------------------------------------------------------------------------------------------------------

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

#### Distribution platform
- [Anaconda](https://www.anaconda.com/)

#### Computing environment
- [Jupyter Notebooks](https://jupyter.org/)



