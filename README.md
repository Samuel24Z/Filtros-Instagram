# Filtros de realidad aumentada usando visión por computador
Implementación de filtros de rostro de realidad aumentada usando OpenCV y Java
 
### Requerimientos previos
Para ejecutar este proyecto es necesario instalar OpenCV versión 4.6.0 en el IDE en el que se desee ejecutar.
 
### Introducción
* **Objetivo:** El objetivo de este proyecto es intentar comprender cómo funcionan los filtros de realidad aumentada usados en redes sociales, como aquellos en los que se añaden elementos personales al rostro del usuario (gafas, sombreros, etc.), así como proporcionar algunas funcionalidades que no están presentes en el paquete OpenCV 4.6 para Java.

* **Marco teórico:** Las características tipo Haar reciben su nombre debido a su similitud con las wavelets de Haar introducidas en [1]. Esta característica considera dos regiones rectangulares adyacentes en una imagen, donde se calcula la diferencia entre la suma de todos los píxeles de cada una. Las regiones adyacentes tienen el mismo tamaño y forma. También se consideran las características de 3 y 4 rectángulos [2]. En la primera, se calcula la suma de los dos rectángulos exteriores y a este valor se le resta la suma de los píxeles dentro de un rectángulo central; en la de 4 rectángulos, se calcula la diferencia entre pares diagonales de rectángulos. Las regiones mencionadas se muestran en la siguiente figura.

    ![Figura 1](/ImagenesEjemplo/Figura1.png)
    **Figura 1. Características de Haar de 2, 3 y 4 rectángulos respectivamente**

    En [2], estas características se utilizan para detectar rostros y la imagen integral se emplea para calcularlas rápidamente. En la figura 2 se muestra un ejemplo del uso de estas características, donde se mide la diferencia de intensidad entre la región de los ojos y la región de la nariz. De este modo, estas características permiten categorizar pequeñas secciones de una imagen y, en el caso de la figura 2, clasificar algunos rasgos del rostro.

    ![Figura 2](/ImagenesEjemplo/Figura2.png)
    **Figura 2. Características de Haar utilizadas en la clasificación de rasgos faciales**

    Lo anterior es importante porque nos permitirá detectar los ojos y el rostro que provienen de la imagen de la cámara y que podemos implementar a través de OpenCV usando la clase CascadeClassifier y un archivo xml que contiene un clasificador Haar previamente entrenado.

### Contribuciones añadidas a este proyecto
* Uso de la clase StretchIcon para que la imagen de la cámara se muestre completamente dentro del JLabel (y de acuerdo al tamaño del JLabel) y de esta manera simular el uso de las banderas:
    - WINDOW_KEEPRATIO
    - WND_PROP_ASPECT_RATIO
    
    descritas en https://docs.opencv.org/4.x/d0/d90/group__highgui__window__flags.html.
    
    Nota: En este momento, estas opciones no están disponibles en el paquete OpenCV 4.6 para Java.
    
    Para complementar lo descrito anteriormente, se utilizó una secuencia de procesos similar a la proporcionada por HighGui.imshow() y HighGui.waitKey() para poder redimensionar la imagen dentro del objeto JLabel y que nos permitirá visualizar la imagen de la cámara con la mejor calidad posible..

* Se ha implementado la funcionalidad de agregar lentes en el área de los ojos detectados con la ayuda de la clase CascadeClassifier.

### Referencias
* [1] Haar, A., Zur theorie der orthogonalen funktionensysteme. Mathematische Annalen, 1910.
* [2] Viola, P., Jones, M., Rapid object detection using a boosted cascade of simple features, IEEE Conf. on Computer Vision and Pattern Recognition, 2001.

***

2022 [Samuel Ramirez](https://github.com/Samuel24Z)
