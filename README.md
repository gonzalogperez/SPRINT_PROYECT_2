Este notebook es la continuación del Sprint_proyect_1, donde aquí se realiza un tratamiento diferente de los datos y aplica modelos avanzados para intentar predecir el precio de las propiedades.



Transformacion de Datos

A diferencia del sprint 1, no se descartaran barrios ni zonas, tampoco los tipos de propiedades. Con esto intentaremos mejorar la precisión de nuestros modelos.

Valores Faltantes: Creamos una columna dummy por cada columna con variable categórica con valores null o nan para saber cuales fueron imputadas. Esto lo hacemos para luego poder identificar los valores que fueron imputados y aplicar filtros a partir de ellas.

Imputación de valores faltantes: para la variable bathrooms se considera que para ciertos tipos de propiedad, por lo menos tienen un baño (valor de la media), entonces se imputa con 1 u 0 dependiendo el caso. Las variables surface_covered y surface_total observamos los casos en que haya faltantes en ambos y se los imputa por la media de cada tipo de propiedad. Para el resto de los faltantes se los imputa con el valor de la otra variable considerando siempre que surface_total >= surface_covered

Detección y eliminación de Outliers Se obtienen las estadísticas de surface_covered, surface_total y price para ver el alcance de cada variable y entender si los mínimos y máximos son valores razonables ya que tenemos cierto conocimiento de la información analizada.
Como la distribución no es normal, elegimos obtener los límites para eliminar los outliers con el rango intercuartilico. También hacemos un ajuste manual de los límites ya que tenemos cierto conocimiento sobre la matería o datos analizados.

Encoding: Se selecciona las columnas categóricas que consideramos relevantes para luego convertirlas, como son variables nominales usamos get_dummies() de pandas. Aunque se aumenta la dimensionalidad, lo intentaremos compensar con PCA.

Escalado de Datos: Utilizamos Z-score para normalizar o estandarizar los datos, que es una medida de cuánto se desvía un valor del promedio, medido en desviaciones estándar. Esto solo lo aplicamos sobre las variables que no son binarias.

Generación de nuevas variables predictoras/reducción de la dimensionalidad con PCA: Se elige PCA porque nos permite obtener una nueva matríz de correlación usada para el módelo y determinar que tan bien explica la varianza de nuestros datos, pudiendo aplicar una reducción de la dimensionalidad sin perder tanta info y teniendo el control.


Machine Learning

Modelos sencillos:

LinearRegression
LinearRegression con PCA

Modelos avanzados:

DecisionTreeRegresor
DecisionTreeRegresor con PCA
DecisionTreeRegresor con PolynomialFeatures
DecisionTreeRegresor con Optimización de Hiperparametros (Random Search y CV)
DecisionTreeRegresor con Optimización de Hiperparametros (RandomForestRegressor)
DecisionTreeRegresor con Optimización de Hiperparametros (Regularización para disminuir el overfitting)
SGDRegressor
SGDRegressor con PCA


También se utiliza Clustering para entender los datos y usarlo para mejorar la predicción del modelo elegido como mejor predictor.

