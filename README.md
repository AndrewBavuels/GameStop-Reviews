# Prueba Práctica – Data Scientist

## GLOBAL ALUMNI 

 ### Functional architecture design:

![Pipeline Architecture Design](Pipeline%20Architecture.jpg)

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


