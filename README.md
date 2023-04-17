# neumonia_identificationxrays_cnn
## Identificación de neumonía a partir de radiografías de tórax

**INTRODUCCIÓN**

_La neumonía es una infección de los pulmones causada por bacterias. El Streptococcus pneumoniae este es un organismo grampositivo que a menudo coloniza la garganta la garganta y que puede llegar hasta los pulmones._

_Un examen importante para el diagnóstico acertado de una neumonía es la radiografía de tórax, que puede mostrar áreas de opacidad (vistas como zonas blanquecinas), que representan áreas en donde se han consolidado las colonias bacterianas. La neumonía no siempre se puede apreciar en una radiografía de tórax, por ellos es importante la ayuda de una inteligencia artificial para poder identificar de manera profunda las diferencias que presentan para llegar a una identificación correcta y con ello evitar el avance de la neumonía y evitar llegar a estado de gravedad que requiera la hospitalización._

_Una identificación temprana de neumonía bacteriana a partir de una radiografía de tórax **puede evitar la hospitalización**_


INFORMACIÓN Y DATOS
https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia

**PROYECTO**

En este proyecto, la división en conjuntos de entrenamiento y prueba se realizó mediante el uso de la clase ImageDataGenerator de Keras, que permite cargar imágenes desde un directorio y aplicar una serie de transformaciones en tiempo real durante el entrenamiento del modelo.

Para la división en conjuntos de entrenamiento y prueba, se definió una carpeta principal llamada data, dentro de la cual se crearon dos subcarpetas: train y test. Las imágenes de radiografías normales y con neumonía se distribuyeron aleatoriamente en ambas subcarpetas, manteniendo la proporción original de la base de datos.

Luego, se utilizaron dos instancias de la clase ImageDataGenerator para cargar las imágenes de entrenamiento y prueba desde las subcarpetas correspondientes. Se utilizó el parámetro validation_split=0.2 para asignar el 20% de las imágenes de la carpeta de entrenamiento como conjunto de validación, y así evaluar el desempeño del modelo en un conjunto de datos no visto durante el entrenamiento.

**MODELO CNN**

La primera capa es una capa convolucional que toma la imagen de entrada y la convoluciona con 16 filtros de 3x3 para extraer características. La activación relu se aplica a cada salida de convolución para introducir no linealidad. La capa de entrada tiene una forma de (img_size, img_size, 3), lo que significa que acepta imágenes de tamaño "img_size" en escala de grises (1 canal) o RGB (3 canales).

La siguiente capa es una capa de maxpooling, que reduce el tamaño de la imagen convolucionada por un factor de 2. Esto ayuda a reducir el número de parámetros y, por lo tanto, a controlar el sobreajuste.

La capa de abandono (dropout) se utiliza para evitar el sobreajuste al desactivar aleatoriamente un porcentaje de las neuronas en la capa durante el entrenamiento.

La CNN continúa con dos capas adicionales de convolución y maxpooling, utilizando cada vez más filtros para extraer características más complejas de la imagen.

Luego, la salida de la última capa de maxpooling se aplana (flatten) para poder conectarse a una capa de neuronas completamente conectadas (Dense). Esta capa de neuronas ocultas tiene 512 neuronas y utiliza la función de activación relu.

La capa final de la CNN es una capa de salida con una sola neurona y utiliza la función de activación sigmoidal. Esta neurona representa la probabilidad de que la imagen pertenezca a la clase "PNEUMONIA" en comparación con la clase "NORMAL".






_Por Carolina Mateos Salmón_
