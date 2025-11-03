# CLASIFICACIÓN DE FASHION-MNIST CON SVM, RANDOM FOREST Y ÁRBOL DE DECISIÓN

Este proyecto desarrolla y compara tres modelos de clasificación supervisada aplicados al dataset Fashion-MNIST: Support Vector Machine (SVM), Random Forest y Árbol de Decisión. El objetivo es analizar su desempeño en la tarea de reconocimiento de patrones en imágenes de ropa en escala de grises.

# Descripción del Dataset

Fashion-MNIST es un conjunto de datos de Zalando que contiene 70,000 imágenes en escala de grises de 28x28 píxeles, clasificadas en 10 categorías de prendas. Se utiliza como alternativa más desafiante al clásico MNIST de dígitos escritos a mano. Cada imagen es representada como un vector de 784 valores (uint8), cargados en formato Ubytes por su eficiencia y compatibilidad con NumPy.

# Objetivos

1. Realizar un análisis exploratorio de datos (EDA) para entender la estructura y patrones de Fashion-MNIST.
2. Entrenar modelos supervisados (SVM, Random Forest, Árbol de Decisión) y comparar su rendimiento.
3. Analizar métricas de desempeño (accuracy, recall, precision, F1-score) y matrices de confusión.
4. Documentar el proceso siguiendo buenas prácticas de código y repositorio colaborativo (GitHub).

# Estructura del repositorio

 * notebooks/: Contiene los Jupyter Notebooks de análisis y modelado (EDA, Preprocesamiento, Modelos, Evaluación).
 * data/: Contiene el dataset en su conjunto de pruebas y entrenamiento en formato UBytes
 * figures/: Resultados visuales, gráficos comparativos y matrices de confusión.
 * README.md: Descripción general del proyecto.
 * requirements.txt: Es recommendable trabajar con el dataset en formato Ubytes dada su eficiencia con respecto a NumPy.

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

        Modelo	               Accuracy      Recall           F1-score 
        --------------------------------------------------------------------------------------------------
        SVM (C=1, RBF)	        0.89 – 0.90	    0.89	        0.89	       
        Random Forest	        0.86	        0.86	        0.86	        
        Árbol de Decisión       0.81	        0.81	        0.81	        
        


# Modelos Clasificadores

SVM (Support Vector Machine)

 * Kernel: RBF.
 * Parámetro C: 1 (óptimo según validación cruzada).
 * Entrenamiento: 60 000 muestras / 10 000 de prueba.
 * Tiempo estimado: ~2.5 h CPU o ~25 min en GPU T4.
 * Ventajas: alta generalización y precisión (~0.90).
 * Desventajas: costo computacional elevado.

Árbol de Decisión

 * Hiperparámetros: max_depth=15, min_samples_split=5, min_samples_leaf=2.
 * Ventajas: interpretabilidad y rapidez de entrenamiento.
 * Desventajas: tendencia al sobreajuste y menor precisión global (~0.81).

Random Forest
 * Configuración: n_estimators=120, max_depth=13.
 * Ventajas: robustez, mayor precisión (0.86) y resistencia al ruido.
 * Desventajas: mayor demanda de memoria que un árbol simple.


# Resultados Comparativos

        Modelo	               Accuracy      Recall (macro)   F1-score (macro)    Dataset usado
        --------------------------------------------------------------------------------------------------
        SVM (C=1, RBF)	        0.89 – 0.90	    0.89	        0.89	        60 000 train / 10 000 test
        Random Forest	        0.86	        0.86	        0.86	        60 000 train / 10 000 test
        Árbol de Decisión       0.81	        0.81	        0.81	        60 000 train / 10 000 test
        

# Interpretación

 * El SVM reentrenado alcanza el mejor desempeño general, pero con alto costo de cómputo.
 * El Random Forest logra un excelente balance entre precisión y eficiencia.
 * El Árbol de Decisión es ideal cuando se requiere interpretabilidad y bajo tiempo de ejecución.


# Análisis de Costo Computacional

        Modelo	        Estrategia	                  Tiempo Estimado	            Observaciones
        ----------------------------------------------------------------------------------------------------------------
        SVM	            Reentrenamiento completo	     2.5 h CPU / 25 min GPU	      Alto costo, precisión superior (~0.90).
        Árbol	        Entrenamiento completo	         <2 min	                      Muy eficiente.
        Random Forest	120 árboles, profundidad 1       ~5 min	                      Balance ideal entre tiempo y rendimiento.

Nota: El costo del SVM crece cuadráticamente con el número de muestras; por eso se recomienda GPU o muestreo para experimentos iniciales.


# Conclusiones

 * El SVM (C=1) logra el mejor accuracy (~0.90) con el dataset completo, pero su entrenamiento requiere más recursos.
 * El Random Forest ofrece el mejor equilibrio entre rendimiento, escalabilidad y facilidad de uso.
 * El Árbol de Decisión sigue siendo una excelente alternativa en escenarios de recursos limitados o donde la interpretabilidad es clave.
 * En general, se recomienda el uso de Random Forest para proyectos de aprendizaje automático en entornos académicos y productivos.

