# CLASIFICACIÓN DE FASHION-MNIST CON SVM, RANDOM FOREST Y ÁRBOL DE DECISIÓN

Este proyecto desarrolla y compara tres modelos de clasificación supervisada aplicados al dataset Fashion-MNIST: Support Vector Machine (SVM), Random Forest y Árbol de Decisión. El objetivo es analizar su desempeño en la tarea de reconocimiento de patrones en imágenes de ropa en escala de grises.

# Descripción del Dataset

Fashion-MNIST es un conjunto de datos de Zalando que contiene 70,000 imágenes en escala de grises de 28x28 píxeles, clasificadas en 10 categorías de prendas. Se utiliza como alternativa más desafiante al clásico MNIST de dígitos escritos a mano. Cada imagen es representada como un vector de 784 valores (uint8), cargados en formato Ubytes por su eficiencia y compatibilidad con NumPy.

* t10k-images-idx3-ubyte: Archivo binario que contiene las imágenes de prueba (cada una de 28x28 píxeles). Formato original de MNIST, comprimido en bytes.
* t10k-labels-idx1-ubyte: Archivo binario con las etiquetas (labels) de las imágenes de prueba (10,000 valores entre 0–9). Contiene etiquetas de clase.
* train-images-idx3-ubyte: Archivo binario con las imágenes de entrenamiento (60,000 registros). Cada imagen es igual a la matriz 28×28, en escala de grises (0–255).
* train-labels-idx1-ubyte: Archivo binario con las etiquetas del conjunto de entrenamiento (60,000 números entre 0–9). Contiene el Texto binario estructurado.

URLs Dataset
https://storage.googleapis.com/tensorflow/tf-keras-datasets/train-labels-idx1-ubyte.gz
https://storage.googleapis.com/tensorflow/tf-keras-datasets/train-images-idx3-ubyte.gz
https://storage.googleapis.com/tensorflow/tf-keras-datasets/t10k-labels-idx1-ubyte.gz
https://storage.googleapis.com/tensorflow/tf-keras-datasets/t10k-images-idx3-ubyte.gz

# Objetivos

1. Realizar un análisis exploratorio de datos (EDA) para entender la estructura y patrones de Fashion-MNIST.
2. Entrenar modelos supervisados (SVM, Random Forest, Árbol de Decisión) y comparar su rendimiento.
3. Analizar métricas de desempeño (accuracy, recall, precision, F1-score) y matrices de confusión.
4. Documentar el proceso siguiendo buenas prácticas de código y repositorio colaborativo (GitHub).

# Estructura del repositorio

 * Notebooks/: Contiene los Jupyter Notebooks de análisis y modelado (EDA, Preprocesamiento, Modelos, Evaluación).
 * Data/: Contiene el dataset en su conjunto de pruebas y entrenamiento en formato UBytes
 * Figures/: Resultados visuales, gráficos comparativos y matrices de confusión.
 * README.md: Descripción general del proyecto.

# Metodología

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

# Resultados y comparación

        Modelo	               Accuracy       Recall      F1-score 
        ---------------------------------------------------------------
        Árbol de Decisión 	   0.81   	    0.81	        0.81	       
        SVM (RBF Kernel)	     0.85	        0.84	        0.84	        
        Random Forest          0.85	        0.85	        0.85	        

Random Forest mostró el mejor desempeño general gracias a su capacidad para combinar múltiples árboles y tener un menor costo de procesamiento frente a los otros dos modelos. El SVM logró un alto rendimiento con fronteras no lineales, mientras que el Árbol de Decisión destacó por su interpretabilidad y eficiencia en costo computacional.
     
# Ejecución del proyecto

1. Clonar el repositorio.
2. Validar dependencias con: requirements.txt.
3. Ejecutar el notebook principal: 'notebooks/Grupo_3_Caso_Práctico_RF_SVM_Tree_Comparación.ipynb'
4. Visualizar resultados en '/figures'.

# Conclusiones

El modelo Random Forest fue el más robusto, seguido de SVM, ambos superando al Árbol de Decisión individual.

El control de hiperparámetros demostró gran impacto en el rendimiento. Este proyecto evidencia cómo los modelos clásicos siguen siendo efectivos para proyectos de clasificación visual cuando se aplican buenas prácticas y análisis riguroso.

# Autores

Grupo 3 - Maestría en Inteligencia Artificial  
Oscar Parra | Jaime Sierra | Juan Miguel Velandia  
Universidad Espíritu Santo (UEES)


