# COMPARATIVA Y SELECCIÓN DE CLASIFICADORES: SVM, RANDOM FOREST Y ÁRBOL DE DECISIÓN APLICADOS AL DATASET FASHION-MNIST

Proyecto de Maestría en Inteligencia Artificial — Asignatura: Aprendizaje Automático
Integrantes:  Juan Miguel Velandia, Jaime Alberto Sierra, Oscar Mauricio Parra


# Descripción General

Este proyecto tiene como objetivo comparar, analizar y seleccionar el mejor clasificador supervisado entre tres modelos:

•	SVM (Support Vector Machine)
•	Random Forest (Bosque Aleatorio)
•	Árbol de Decisión (Decision Tree)

Los modelos fueron entrenados sobre el conjunto Fashion-MNIST, que contiene imágenes de prendas de vestir en escala de grises (28×28 píxeles).
Se realiza un análisis integral que incluye exploración de datos, preprocesamiento, entrenamiento, comparación de métricas y análisis de costo computacional.


# Objetivos del Proyecto

1.	Entrenar tres clasificadores supervisados sobre el dataset Fashion-MNIST.
2.	Evaluar su rendimiento con métricas de clasificación: Accuracy, Recall y F1-score.
3.	Analizar los costos de cómputo y escalabilidad de cada modelo.
4.	Determinar cuál modelo ofrece el mejor equilibrio entre precisión y eficiencia.
5.	Aplicar buenas prácticas colaborativas mediante GitHub.


# Dataset: Fashion-MNIST

•	Tamaño: 70 000 imágenes (60 000 entrenamiento / 10 000 prueba).
•	Formato: Escala de grises (28×28 píxeles).
•	Clases: 10 categorías balanceadas (camiseta, pantalón, abrigo, zapato, etc.).
•	Fuente: Zalando Research.

Dataset ampliamente utilizado como benchmark moderno en aprendizaje automático y visión por computadora.


# Análisis Exploratorio de Datos (EDA)

•	Se verificó el balance de clases (~6 000 imágenes por categoría).
•	Se confirmaron datos completos, sin nulos ni inconsistencias.
•	Se visualizaron ejemplos aleatorios para validar el dominio visual.
•	Se analizó la distribución de intensidades de píxeles (0–255).

Ejemplo de visualización:

        plt.figure(figsize=(6,6))
        for i in range(9):
            plt.subplot(3,3,i+1)
            plt.imshow(X_train[i].reshape(28,28), cmap='gray')
            plt.title(y_train[i])
        plt.show()

# Preprocesamiento

•	Aplanamiento: conversión de cada imagen a vector de 784 características.
•	Normalización: división por 255 para escalar valores entre [0,1].
•	División 80/20: separación estratificada entrenamiento/prueba.
•	Reentrenamiento del SVM: uso completo del dataset (60 000 train / 10 000 test).


# Modelos Clasificadores

SVM (Support Vector Machine)

•	Kernel: RBF.
•	Parámetro C: 1 (óptimo según validación cruzada).
•	Entrenamiento: 60 000 muestras / 10 000 de prueba.
•	Tiempo estimado: ~2.5 h CPU o ~25 min en GPU T4.
•	Ventajas: alta generalización y precisión (~0.90).
•	Desventajas: costo computacional elevado.

Árbol de Decisión

•	Hiperparámetros: max_depth=15, min_samples_split=5, min_samples_leaf=2.
•	Ventajas: interpretabilidad y rapidez de entrenamiento.
•	Desventajas: tendencia al sobreajuste y menor precisión global (~0.81).

Random Forest
•	Configuración: n_estimators=120, max_depth=13.
•	Ventajas: robustez, mayor precisión (0.86) y resistencia al ruido.
•	Desventajas: mayor demanda de memoria que un árbol simple.


# Resultados Comparativos

        Modelo	               Accuracy      Recall (macro)   F1-score (macro)    Dataset usado
        --------------------------------------------------------------------------------------------------
        SVM (C=1, RBF)	        0.89 – 0.90	    0.89	        0.89	        60 000 train / 10 000 test
        Random Forest	        0.86	        0.86	        0.86	        60 000 train / 10 000 test
        Árbol de Decisión       0.81	        0.81	        0.81	        60 000 train / 10 000 test
        

#cInterpretación

• El SVM reentrenado alcanza el mejor desempeño general, pero con alto costo de cómputo.
• El Random Forest logra un excelente balance entre precisión y eficiencia.
• El Árbol de Decisión es ideal cuando se requiere interpretabilidad y bajo tiempo de ejecución.


# Análisis de Costo Computacional

        Modelo	        Estrategia	                  Tiempo Estimado	            Observaciones
        ----------------------------------------------------------------------------------------------------------------
        SVM	            Reentrenamiento completo	     2.5 h CPU / 25 min GPU	      Alto costo, precisión superior (~0.90).
        Árbol	        Entrenamiento completo	         <2 min	                      Muy eficiente.
        Random Forest	120 árboles, profundidad 1       ~5 min	                      Balance ideal entre tiempo y rendimiento.

Nota: El costo del SVM crece cuadráticamente con el número de muestras; por eso se recomienda GPU o muestreo para experimentos iniciales.


# Conclusiones

• El SVM (C=1) logra el mejor accuracy (~0.90) con el dataset completo, pero su entrenamiento requiere más recursos.
• El Random Forest ofrece el mejor equilibrio entre rendimiento, escalabilidad y facilidad de uso.
• El Árbol de Decisión sigue siendo una excelente alternativa en escenarios de recursos limitados o donde la interpretabilidad es clave.
• En general, se recomienda el uso de Random Forest para proyectos de aprendizaje automático en entornos académicos y productivos.

