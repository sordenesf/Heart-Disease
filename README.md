# INTRODUCCIÓN
Heart Disease es un proyecto de Machine Learning cuya finalidad es elaborar un modelo predictivo sobre el riesgo de sufrir enfermedad cardíaca en personas mayores de edad. Como insumo para el desarrollo del modelo, se han utilizado registros de encuestas realizadas por CDC como parte del Sistema de Vigilancia de Factores de Riesgo del Comportamiento (BRFSS), los cuales fueron recopilados durante el año 2022.

Los datos utilizados para el entrenamiento del modelo (bajo licencia CC0: Public Domain) pueden ser consultados desde el siguiente enlace: 
https://www.kaggle.com/datasets/kamilpytlak/personal-key-indicators-of-heart-disease/ 

# ¿QUÉ ES ENFERMDAD CARDÍACA? IMPORTANCIA DE SU DETECCIÓN A TIEMPO
Se entiende por "enfermedad cardíaca" a un variado grupo de afecciones cardíacas<sup>1</sup>:
- Enfermedad de los vasos sanguíneos, como enfermedad de las arterias coronarias
- Latidos cardíacos irregulares (arritmia)
- Problemas cardíacos de nacimiento (defectos cardíacos congénitos)
- Enfermedad del músculo cardíaco
- Enfermedad de las válvulas cardíacas

Lamentablemente, en muchos casos la Enfermedad cardíaca se manifiesta en forma silenciosa y no se diagnostica hasta que la persona experimenta signos o síntomas de un ataque cardíaco, insuficiencia cardíaca o arritmia. En este sentido, resulta de gran ayuda establecer el riesgo de enfermedad cardíaca para actuar sobre los factores de riesgo con la finalidad de prevenir enfermedad o muerte.

Aproximadamente 1 de cada 5 personas en Estados Unidos murió a causa de una enfermedad cardíaca en 2022<sup>2</sup>

# MODELO

Previo a la etapa de modelación, se estudiaron las características del conjuntos de datos buscando identificar patrones. Entre las variables que resaltan del estudio se encuentran la edad, sexo, índice de masa corporal, piezas dentales removidas, entre otras:

![Incidencia por edad y piezas dentales removidas](/img/Incidencia_por_edad_y_dientes_removidos.PNG "Incidencia por edad y piezas dentales removidas")

Los modelos propuestos fueron los siguientes:
- Regresión logística
- Decision tree
- Random Forest
- XGBoost
- LGBM

En cada uno de ellos se efectuaron pruebas con distintas configuraciones del dataset. Una vez realizadas, se seleccionó la configuración con las mejores métricas de cada uno de ellos para, posteriormente, continuar con la optimización de hiperparámetros:

|        MODELO          | Accuracy  |   Recall  | Precision | F1 score  |  ROC AUC  | Configuración |
|------------------------|-----------|-----------|-----------|-----------|-----------|---------------|
| Regresión logística    |   0,948   |   0,253   |   0,253   |   0,253   |   0,253   | Eliminación NaN |           
| Decision tree          |   0,917   |   0,284   |   0,269   |   0,276   |   0,619   | Eliminación NaN + escalamiento |
| Random Forest          |   0,947   |   0,200   |   0,597   |   0,300   |   0,596   | Imputación NaN + recorte outliers |
| XGBoost                |   0,948   |   0,239   |   0,580   |   0,338   |   0,614   | Elimincación NaN + recorte outliers + escalamiento |
| LGBM                   |   0,949   |   0,224   |   0,614   |   0,329   |   0,608   | Eliminación NaN + escalamiento |



|Modelo   |Accuracy	|Recall	|Precision	|F1	|ROC_AUC	|AUC|
|---------|----------|----------|---------|---------|---------|---------|--------|
|Regresión Logística	|  0,894	|  0,664	|  0,297	|  0,410	|  0,786	|  0,89  |
|Árbol de decisión	  |  0,924	|  0,562	|  0,378	|  0,452	|  0,754	|  0,84  |
|Random Forest	      |  0,913	|  0,590	|  0,344	|  0,434	|  0,761	|  0,87  |
|XGBoost	            |  0,924	|  0,508	|  0,368	|  0,427	|  0,728	|  0,87  |
|LightGBM	            |  0,893	|  0,660	|  0,294	|  0,407	|  0,784	|  0,89  |




# DISCLAIMER
El presente proyecto ha sido realizado con fines investigativos. Bajo ninguna circunstancia debe ser utilizado como reemplazo del consejo de su médico tratante y/o sistema de salud. Los resultados del modelo no sustituyen el juicio profesional de un médico u otro profesional de la salud calificado. Se recomienda consultar siempre con un profesional médico cualquier decisión respecto de su salud. El autor no se hace responsable por cualquier error, omisión o interpretación errónea de los resultados generados

# REFERENCIAS
1. https://www.mayoclinic.org/es/diseases-conditions/heart-disease/symptoms-causes/syc-20353118
2. https://www.cdc.gov/heart-disease/about/index.html
