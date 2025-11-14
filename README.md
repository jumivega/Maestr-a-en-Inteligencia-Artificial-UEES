# Proyectos Repositorio

En el repo se trabajaron dos proyectos de modelado, Modelos supervisados (SVM, Random Forest y Árbol de Decisión) y modelos no supervisados (K-Means y DBSCAN, PCA, T-SNE). A continuación, se relaciona la información y conclusiones correspondientes a cada proyecto.

# Clasificación de Fashion-MNIST con SVM, Random Forest y Árbol de Decisión - Supervisado

Este proyecto desarrolla y compara tres modelos de clasificación supervisada aplicados al dataset Fashion-MNIST: Support Vector Machine (SVM), Random Forest y Árbol de Decisión. El objetivo es analizar su desempeño en la tarea de reconocimiento de patrones en imágenes de ropa en escala de grises.

# Análisis de Clustering No Supervisado en Fashion MNIST

Este proyecto explora el uso de modelos de aprendizaje no supervisado para descubrir patrones y detectar outliers en un conjunto de imágenes de artículos de moda. Utilizando el dataset Fashion MNIST, se aplicaron los algoritmos K-Means y DBSCAN, acompañados de técnicas de reducción de dimensionalidad como PCA y t-SNE, con el objetivo de mejorar la visualización de un catálogo virtual y reducir errores de clasificación.

# Descripción del Dataset

Fashion-MNIST es un conjunto de datos de Zalando que contiene 70,000 imágenes en escala de grises de 28x28 píxeles, clasificadas en 10 categorías de prendas. Se utiliza como alternativa más desafiante al clásico MNIST de dígitos escritos a mano. Cada imagen es representada como un vector de 784 valores (uint8), cargados en formato Ubytes por su eficiencia y compatibilidad con NumPy.

* t10k-images-idx3-ubyte: Archivo binario que contiene las imágenes de prueba (cada una de 28x28 píxeles). Formato original de MNIST, comprimido en bytes.
* t10k-labels-idx1-ubyte: Archivo binario con las etiquetas (labels) de las imágenes de prueba (10,000 valores entre 0–9). Contiene etiquetas de clase.
* train-images-idx3-ubyte: Archivo binario con las imágenes de entrenamiento (60,000 registros). Cada imagen es igual a la matriz 28×28, en escala de grises (0–255).
* train-labels-idx1-ubyte: Archivo binario con las etiquetas del conjunto de entrenamiento (60,000 números entre 0–9). Contiene el Texto binario estructurado.

URLs Dataset
* https://storage.googleapis.com/tensorflow/tf-keras-datasets/train-labels-idx1-ubyte.gz
* https://storage.googleapis.com/tensorflow/tf-keras-datasets/train-images-idx3-ubyte.gz
* https://storage.googleapis.com/tensorflow/tf-keras-datasets/t10k-labels-idx1-ubyte.gz
* https://storage.googleapis.com/tensorflow/tf-keras-datasets/t10k-images-idx3-ubyte.gz

# Objetivos Clasificación de Fashion-MNIST con SVM, Random Forest y Árbol de Decisión

1. Realizar un análisis exploratorio de datos (EDA) para entender la estructura y patrones de Fashion-MNIST.
2. Entrenar modelos supervisados (SVM, Random Forest, Árbol de Decisión) y comparar su rendimiento.
3. Analizar métricas de desempeño (accuracy, recall, precision, F1-score) y matrices de confusión.
4. Documentar el proceso siguiendo buenas prácticas de código y repositorio colaborativo (GitHub).

# Objetivos Análisis de Clustering No Supervisado en Fashion MNIST

1. Identificar agrupaciones naturales de artículos de moda utilizando técnicas de clustering no supervisado.
2. Detectar imágenes atípicas (outliers) que podrían estar mal categorizadas.
3. Comparar el comportamiento y resultados de los modelos K-Means y DBSCAN.
4. Visualizar la estructura latente de los datos con reducción de dimensionalidad.

# Estructura de repositorio

 * Data/: Contiene el dataset en su conjunto de pruebas y entrenamiento en formato UBytes
 * Notebooks/ModelosSupervisados: Contiene el Notebook (Colab) de análisis y modelado (EDA, Preprocesamiento, Modelos, Evaluación).
 * Figures/ModelosSupervisados: Resultados visuales, gráficos comparativos y matrices de confusión.
 * Notebooks/ModelosNoSupervisados: ipynb con todo el análisis paso a paso de los modelos K-Means y DBSCAN, PCA, T-SNE.
 * Figures/ModelosNoSupervisados: Resultados visuales, gráficos comparativos y matrices de confusión.
  * README.md: Descripción general del proyecto.

# Metodología Clasificación de Fashion-MNIST con SVM, Random Forest y Árbol de Decisión

1. Análisis Exploratorio (EDA): Se verificó balance de clases, ausencia de nulos y distribución de intensidades. Se usaron histograma y boxplots para detectar correlaciones y patrones visuales.

2. Preprocesamiento: Escalado de píxeles (división por 255), aplanamiento de imágenes (784 features) y división entrenamiento/prueba (80/20).

3. Modelado:
   * Árbol de Decisión: Ajuste de hiperparametros 'max_depth' para re entrenar el modelo y controlar sobreajuste.
   * SVM: Kernel RBF, ajuste de 'C' y 'gamma' mediante GridSearchCV.
   * Random Forest: Ensamble de 120 árboles y 13 ramas, evaluación de importancia de variables.

4. Evaluación: Métricas (accuracy, precision, recall, F1), matrices de confusión y visualizaciones.
 
 * Se confirmaron datos completos, sin nulos ni inconsistencias.
 * Se visualizaron ejemplos aleatorios para validar el dominio visual.
 * Se analizó la distribución de intensidades de píxeles (0–255).

# Metodología Análisis de Clustering No Supervisado en Fashion MNIST

1. Carga y preprocesamiento de datos: Selección de muestra (20%), normalización y estandarización de píxeles

2. Reducción de dimensionalidad: PCA para compactar información y reducir ruido, t-SNE para visualización bidimensional de clústeres.
   
3. Modelos de clustering: K-Means (K=10): agrupación basada en distancias, DBSCAN: agrupación basada en densidad y detección de ruido.

4. Evaluación y visualización: Uso de métricas de silueta e inercia, visualización de resultados con t-SNE y análisis cualitativo de pureza

# Resultados y comparación modelos suspervisados

        Modelo	               Accuracy       Recall      F1-score 
        ---------------------------------------------------------------
        Árbol de Decisión 	   0.81   	    0.81	        0.81	       
        SVM (RBF Kernel)	   0.85	        0.84	        0.84	        
        Random Forest          0.85	        0.85	        0.85	        

Random Forest mostró el mejor desempeño general gracias a su capacidad para combinar múltiples árboles y tener un menor costo de procesamiento frente a los otros dos modelos. El SVM logró un alto rendimiento con fronteras no lineales, mientras que el Árbol de Decisión destacó por su interpretabilidad y eficiencia en costo computacional.

# Resultados y comparación modelos no supervisados

        Aspecto	                     K-Means                             DBSCAN 
        -----------------------------------------------------------------------------------------------
        Tipo de agrupamiento 	   Por partición (distancia)   	    Por densidad (vecindad)	     	       
        Requiere definir K	       Sí    	                        No	            
        Detección de outliers      No (todos se asignan)	        Sí (puntos etiquetados como ruido)	        
        Pureza de clústeres        Moderada a alta                  Alta en clústeres densos
        Cobertura del dataset      Completa                         Parcial (outliers excluidos)

* K-Means logró una segmentación global con clústeres que reflejan etiquetas mayoritarias.
* DBSCAN detectó clústeres densos de alta pureza y reveló outliers significativos.
* La visualización con t-SNE confirmó las estructuras y separaciones detectadas.

# Ejecución del proyecto

1. Clonar el repositorio.
2. Validar dependencias con: requirements.txt.
3. Ejecutar el notebook principal: 'notebooks/Grupo_3_Caso_Práctico_RF_SVM_Tree_Comparación.ipynb'
4. Visualizar resultados en '/figures'.

# Conclusiones Clasificación de Fashion-MNIST con SVM, Random Forest y Árbol de Decisión

* Aún con un dataset de imágenes tratado de forma “tabular” (imágenes aplanadas), los modelos clásicos de aprendizaje supervisado son capaces de lograr desempeños superiores al 80% de exactitud. Entre los modelos probados, el Random Forest emerge como el más sólido, porque combina buena precisión, estabilidad y poca sensibilidad al ruido de píxeles individuales. El SVM confirma su potencia en alta dimensión, sobre todo cuando se usa un kernel adecuado, pero su costo computacional obliga a trabajar por muestras. El Árbol de Decisión cumple el rol didáctico: permite mostrar el efecto de controlar la profundidad y visualizar reglas, pero evidencia también la necesidad de métodos de ensamble para problemas de visión.

* En este análisis con datos de Fashion-MNIST hemos constatado que los hiperparámetros influyen marcadamente en el desempeño: un SVM RBF, un gamma y un C bien ajustados supera ampliamente un SVM por defecto. Del mismo modo, un Árbol de Decisión sin podar suele sobreajustar, pero limitando max_depth mejora su capacidad de generalización. El uso de ensemble (Random Forest) demostró ser robusto: aún a muchos árboles débiles en un modelo fuerte y estable.

Hallazgos Clave

* El dataset sí tiene información útil en los píxeles: los boxplots por clase y la matriz de correlación muestran que no todos los píxeles se comportan igual; algunos cambian mucho según la prenda. Eso se relaciona con que los modelos hayan logrado buenos niveles de accuracy.

* Los modelos ensamblados (RF) manejan mejor la complejidad que el árbol simple. Esto se ve en las métricas de desempeño y en la matriz de confusión.

* SVM sigue siendo competitivo incluso con una muestra más pequeña, lo que demuestra que el kernel estuvo bien escogido.

* No hubo problema de clases desbalanceadas, así que las diferencias en las métricas se deben al modelo, no a los datos.

* Las clases visualmente parecidas siguen siendo el dolor de cabeza: todos los modelos tienen ahí sus errores. Eso podría explicarse por la limitación del dataset y al enfoque de “imagen aplanada”.

Limitaciones

* Imágenes aplanadas: al pasar de 28x28 a 784 perdemos la estructura espacial. Los modelos clásicos no “ven” que un píxel está al lado de otro. En este sentido una CNN podría hacerlo mejor.

* No pudimos entrenar el SVM con los 60.000 por temas de tiempo y costo computacional. Es posible que, con más datos y buen hardware, se acerque más o incluso supere al Random Forest.

Futuras Mejoras 

* Probar reducción de dimensionalidad (PCA) antes del SVM para que entrene más rápido y quizá con mejor generalización.

* Ajustar más el Random Forest: número de árboles (n_estimators), profundidad máxima y número de features por split.

* Probar Gradient Boosting o XGBoost: suelen mejorar unas décimas frente a RF en este tipo de problemas.

* Probar con una CNN para mostrar que el enfoque con convoluciones supera a los modelos clásicos en imágenes.

# Conclusiones Metodología Análisis de Clustering No Supervisado en Fashion MNIST

* Para la visualización de un catálogo de imágenes de moda y detección de outliers, K-Means y DBSCAN ofrecieron perspectivas complementarias. K-Means proporcionó una clasificación de todos los artículos en grupos que, en su mayoría, correspondieron a diferentes tipos de prendas, facilitando así la organización del catálogo por similitud. DBSCAN, por su parte, permitió destacar automáticamente los artículos atípicos y formó unos pocos clústeres confiables para las categorías más distintivas.

* Queda claro que no todas las clases de Fashion-MNIST son separables de forma natural bajo técnicas no supervisadas simples: ciertas prendas se traslapan en apariencia y requieren enfoques más sofisticados para diferenciarse. Aun así, combinar PCA y clustering resultó útil: PCA mejoró la velocidad y efectividad del clustering, y la inspección visual con T-SNE corroboró qué tan bien se formaron los grupos. De hecho, aplicar PCA permitió que DBSCAN encontrara más de un clúster en vez de un único clúster gigante, mostrando el valor de reducir el ruido dimensional.

* Resumiendo, K-Means es adecuado para obtener una vista general estructurada del catálogo (especialmente cuando se espera un número de categorías fijo), mientras que DBSCAN es valioso para depurar dicho catálogo identificando casos atípicos y agrupando solo lo más homogéneo. La combinación de ambos enfoques, junto con reducción de dimensionalidad y un ajuste prudente de parámetros, permite lograr una visualización más correcta del conjunto de imágenes y apoyar la limpieza del catálogo de forma fundamentada. Cada técnica tiene fortalezas y limitaciones claras, por lo que una estrategia híbrida e iterativa (apoyada en visualización y en conocimiento del dominio) resulta ser la vía más eficaz para mejorar la organización del catálogo y minimizar errores en la clasificación de sus prendas.

# Autores

Grupo 3 - Maestría en Inteligencia Artificial  
Oscar Parra | Jaime Sierra | Juan Miguel Velandia  
Universidad Espíritu Santo (UEES)

