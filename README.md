# AR-FP
Aprendizaje Reforzado - Funciones de Perdida

Info sacada de: https://rubialesalberto.medium.com/data-scientist-explicaci%C3%B3n-y-diferencias-entre-m%C3%A9tricas-de-error-con-python-f7d71dbee634

### Funciones de Perdida
La funcion de perdida nos indica el coste de una prediccion, es decir
que tan lejos estubo del valor correcto

### Tipos de funciones de Perdida:

#### Funcion de Perdida Absoluta (tambien conocida como L1):
Esta funcion calcula el coste como el valor absoluto del valor real
menos el valor predicho. Como es de esperar, el coste en este caso
siempre va a ser un valor positivo. Veamos:

Si en determinado caso el valor real de 7 pero mi modelo predijo 2
el coste se calcula asi  | 7 - 2 | osea que mi coste es 5.

Si tuviera un valor real 10 y mi modelo predice -2 la ecuacion seria
asi | 7 - (-10) | lo cual seria 17, que logicamente hablando es un
error mucho peor que el caso anterior  

![f](https://user-images.githubusercontent.com/95035101/205132457-07db5766-ee5c-4631-a5c5-af1734c80d52.png)

#### Funcion de perdida del error cuadratico medio (tambien conocida como L2)
Esta funcion es parecida a L1 pero con la diferencia de que en vez de 
calcular el valor aboluto vamos a calcular el cuadrado.

Si por ejemplo nosotros tuvieramos un ejemplo en el que el valor real es 
5 y nuestra red neuronal predijo 7, nuestra funcion seria la siguiente:
(5-7)^2 que seria igual a 4.

Por otro lado si nuestra red neuronal hubiese predicho 10 la ecuacion seria asi
(5-10)^2 que seria igual a 25, lo cual es mucho peor
![f2](https://user-images.githubusercontent.com/95035101/205132488-1755f133-a7fb-4374-9b49-252c69a95231.png)

#### Funcion de perdida Pseudo-Huber
Esta es una mescla de la funcion de perdida L1 con L2 porque permite que nosotros podamos ajustar la manera en que se exageran los errores, de forma que si tenemos un delta alto se parecera al Error Cuadratico Medio pero si tenemos un delta bajo los errores seran mas pequeños y se parecera al Error Absoluto Medio.

![ddb74a0b410409d421e880aa65f57c20393f91c1](https://user-images.githubusercontent.com/95035101/205135310-192e2a55-e6f4-4379-bfe2-6aeed29c2247.svg)

Esta es una grafica comparativa entre L2, Pseudo-Huber con Delta = 1 y Pseudo-Huber con Delta = 2

![f3](https://user-images.githubusercontent.com/95035101/205135617-76402b94-79dc-4ef1-b7e8-f631aa973644.png)

#### Funcion de Perdida Logaritmo del Error Cuadratico Medio

Este algoritmo, a diferencia de los demas, penaliza mas a los errores cercanos al valor ideal, que a los lejanos.

#### Comparativa de todas las graficas

![f3](https://user-images.githubusercontent.com/95035101/205138469-2d3dd811-b853-4115-95f8-8b8c3a06f4ee.png)


### Entropia Cruzada
La entropia cruzada nos permite comparar que tan lejos estubo un vector con respecto al valor real que deberia tener el vector. Se puede expresar de la siguiente manera: 
![830e6251d7809c6ea068ba956bbfc529](https://user-images.githubusercontent.com/95035101/205139780-650ea096-9313-4c35-87d4-a4272cb1f7ee.jpg)

Cuando la entropia cruzada se utiliza como funcion de perdida de la red neuronal, p representa la correccion La respuesta, q representa el valor predicho. La entropia cruzada caracteriza la distancia entre dos distribuciones de probabilidad, es decir, cuanto menor es el valor de la entropia cruzada, mas cercanas estan las dos distribuciones de probabilidad.  
Suponga que hay un problema de tres categorias, la respuesta correcta para una muestra es (1, 0, 0) y la unica respuesta predicha para un modelo despues de la regresion de Softmax es (0.5, 0.4, 0.1). Entonces la entropia cruzada es:   
H((1, 0, 0), (0.5, 0.4, 0.1)) = - (1 * log(0.5) + 0 * log(0.4) + 0 * log(0.1)) = 0.3
Si la prediccion de otro modelo es (0.8, 0.1, 0.1), la entropia cruzada es   
H((1, 0, 0), (0.8, 0.1, 0.1)) = -(1 * log(0.8) + 0 * log(0.1) + 0 * log(0.1)) = 0.1  
Se puede concluir que la segunda respuesta predicha es mejor que la primera.


