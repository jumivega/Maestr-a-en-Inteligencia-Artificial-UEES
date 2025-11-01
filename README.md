# Maestr-a-en-Inteligencia-Artificial-UEES
Trabajos asociados a las asignaturas de la Maestría en IA - Grupo 3
Integrantes:  Juan Miguel Velandia, Jaime Alberto Sierra, Oscar Mauricio Parra

RESUMEN DEL PROBLEMA

El problema central consiste en clasificar imágenes de prendas de vestir del catálogo de Zalando utilizando técnicas de aprendizaje supervisado, empleando el conjunto de datos Fashion-MNIST.

Este dataset contiene 70,000 imágenes en escala de grises de 28x28 píxeles (60,000 para entrenamiento y 10,000 para prueba), donde cada imagen pertenece a una de 10 categorías de ropa (camiseta, pantalón, suéter, vestido, zapato, etc.). Cada fila del dataset representa una imagen convertida a un vector de 784 valores de intensidad de píxeles (0–255).

Objetivo del análisis:
Desarrollar, entrenar y comparar distintos modelos de clasificación (Árboles de Decisión, Random Forest y SVM) para determinar cuál de ellos logra una mejor precisión y desempeño al identificar correctamente las prendas de vestir a partir de sus características visuales.

En resumen, el proyecto busca evaluar la capacidad de tres algoritmos clásicos de Machine Learning para resolver un problema de clasificación multiclase de imágenes.

METODOLOGÍA UTILIZADA

El proyecto sigue una metodología estructurada de aprendizaje supervisado, aplicada paso a paso para desarrollar, entrenar y comparar distintos modelos de clasificación. Esta metodología es la base de la mayoría de los proyectos de Machine Learning (ML) y busca garantizar resultados precisos y reproducibles.

A continuación, se describe cada etapa utilizada en el proyecto:

1. Recolección y exploración de los datos:
Se parte del conjunto de datos Fashion-MNIST, que contiene imágenes en escala de grises de diferentes prendas de vestir (camisetas, zapatos, bolsos, etc.). Cada imagen de 28x28 píxeles se transforma en una fila con 784 valores numéricos, y una etiqueta (de 0 a 9) que indica el tipo de prenda.

En esta etapa se revisa:
    •	Estructura y dimensiones del dataset.
    •	Balance de clases (que todas las categorías estén representadas).
    •	Muestras visuales para confirmar que las imágenes se leen correctamente.

2. Preparación y preprocesamiento de datos:
Antes de entrenar los modelos, los datos deben estar limpios y en el formato adecuado. Se aplicaron las siguientes transformaciones:

    •	Normalización: Se escalan los valores de los píxeles de 0–255 a 0–1, lo que mejora la estabilidad de los algoritmos.
    •	División del dataset: Se separan los datos en dos conjuntos:
        - Entrenamiento (60,000 imágenes) → se usa para enseñar al modelo.
        - Prueba (10,000 imágenes) → se usa para evaluar el rendimiento final.
    •	Verificación de calidad: Se asegura que no haya valores faltantes ni duplicados.

    Este paso garantiza que los modelos aprendan patrones reales y no ruido.

3. Entrenamiento de modelos:
En esta fase se aplican tres algoritmos de clasificación con el mismo conjunto de datos para comparar su desempeño:

    - Árbol de Decisión: Divide los datos en reglas simples de “si-entonces” hasta llegar a una predicción. Fácil de interpretar.
    - Random Forest: Combina muchos árboles para mejorar la precisión y reducir errores. Es robusto y confiable.
    - SVM (Máquina de Vectores de Soporte): Encuentra la mejor frontera que separa las clases en el espacio de datos. Muy preciso, pero más costoso de          entrenar.

    Cada modelo se entrena con el conjunto de entrenamiento (X_train, y_train) y se evalúa con el conjunto de prueba (X_test, y_test).

4. Evaluación del rendimiento:
Para medir qué tan bien funciona cada modelo, se utilizan métricas cuantitativas:

    •	Accuracy (Precisión): porcentaje de aciertos del modelo.
    •	Matriz de confusión: muestra cuántas imágenes fueron clasificadas correctamente y cuáles se confundieron.
    •	Tiempo de entrenamiento: ayuda a evaluar la eficiencia computacional.

    Estas métricas permiten comparar de forma objetiva el desempeño entre modelos.

5. Comparación y selección del modelo óptimo:
Una vez entrenados los tres modelos, se analizan los resultados:

    •	Árbol de Decisión: interpretación clara, pero tiende a sobreajustarse.
    •	Random Forest: excelente equilibrio entre precisión y estabilidad.
    •	SVM: precisión alta, pero mayor demanda de cómputo.

El Random Forest se identifica como el modelo más equilibrado y recomendable para producción, por combinar alta precisión, buena generalización y tiempos de ejecución razonables.

6. Iteración y mejora continua:
Finalmente, se propone una fase iterativa donde se pueden:

    •	Ajustar hiperparámetros.
    •	Refinar características.
    •	Volver a entrenar los modelos.

    Este ciclo de mejora es esencial en cualquier proyecto de Machine Learning, ya que permite optimizar resultados con base en nuevas métricas o datos adicionales.





