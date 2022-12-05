# **Practica 3 - APRENDIZAJE AUTOMÁTICO**

## Pasos a Realizar

### **1. Elegir el Problema**

```
Para este proyecto hemos decidido escoger una serie de datos relacionados con
los "Juegos del hambre", con el fin de predecir quién será el ganador en función de una serie 
de parámetros. 

"Los juegos del hambre" es una competicion ficticia donde 24 personas de diferentes distritos del 1-12 (en orden de mejor a peor) pelean hasta la muerte hasta que hay 1 o 2  (si son del mismo distrito) ganadores.

Factores a tener en cuenta para entender quienes son los maspropensos a ganar:

 1. Los distritos mas pequeños (1,2,3...) son los mas "deportistas" y mas adinerados para entrenar y por lo tanto, con más probabilida de ganar.
 
 2. Cada distrito lleva a 2 personas, de ahí que puedan ganar los 2 del mismo distrito. No pueden ganar 2 personas de distritos diferentes. Puede haber un único ganador.
 
 3. Te puedes presentar voluntario a participar (suele ser persnas que se llevan entrenando toda la vida).

 4. Los distritos altos (11,12,13) son los peores, son los mas pobres y pocas veces ganan.

 6. La edad suele ser entre 10 y 20 de los participantes, los mas mayores tienen mas probabilidades de ganar.

 7. Asumimos que los hombres tienen mas probabilidades de exito ya que hay peleas fisicas.

 Atributos:

    Sexo: Hombre(1), Mujer(0).
    Voluntario: Si(1), No(0).
    Ganador: Si(1), No(0).


El programa recibirá una serie de parámetros, y será capaz de analizar y emitir una respuesta de 
"1" si sobrevive y gana los juegos del hambre o "0" si muere.
```


### **2. Identificar la fuente de datos**

Los datos utilizados para el aprendizaje automatico son extraidos a partir del siguiente enlace:

[https://www.kaggle.com/datasets/thedevastator/the-hunger-games-dataset-a-survival-analysis](https://www.kaggle.com/datasets/thedevastator/the-hunger-games-dataset-a-survival-analysis)
 
 Sin embargo, tuvimos que expandir nuestro dataset a mano para contar con mas registros para el análisis, añadiendo y adaptando mas de 400 nuevos registros.


### **3. Identificar las caracterisiticas relevantes de los hechos**

Para analizar y predecir los resultados hemos considerado relevantes los siguientes parámetros:

    - distrito: indica el distrito al que pertenece la pareja. En el juego habrá doce parejas, cada una perteneciente a un distrito.
    - sexo: indica el género del participante
    - edad: indica la edad del paciente
    - voluntario: Si(1), No(0).
    - rating: indica la valoración del participante
    - dias sobrevividos: indica el número de dias que ha sobrevivido cada uno de los participantes de la pareja.
    - ganador: indica cuál fue la pareja ganadora de cada una de las partidas.

### **4. Obtener el fichero .arff con los hechos codificados de acuedos con las caracterisiticas anteriores**

    Para generar el fichero .arff con los datos, realizamos los siguientes pasos

    1. Bajarnosel Dataset en formato CSV y adaptarlo al formato con el que trabaja weka.
    2. En weka, ir al apartado EXPERIMENTER/ANALYSE donde abrimos nuestro fichero csv
    3. Guardamos el fichero .arff seleccionando la opcion "save"
    4. Para guardar el modelo iremos a Calsify donde seleccionamos el clasificados mejro adaptado a nuestro modelo.
    5. Exportamos el modelo usando "save model" una vez ejecutado.
    


### **5. Evaluar distintos algoritmos de aprendizaje automatico con con los datos obtenidos**


Una vez obtenido el fichero `.arff`, Buscamos el modelo que mejor clasifique nuestros datos para ello nos vamos a fijar en el AUC, que es el area bajo la curva ROC. Además también en la Medida F ya que tiene en cuenta la precisión y la recuperacion también.


| Algoritmo            | AUC	  | F-Measure |
|:---------------------|:--------:|:---------:|
| Random Forest        | 97,1%    | 0,994     |
| J48                  | 90,8%    | 0,995     | 
| Tabla de Decisión    | 91%      | 0,995     |
| Voted Perceptron     | 71,9%    | 0,97      |
| Naive Bayes          | 96%      | 0,97      |
| BayesNet             | 97,6%    | 0,995     |

Obsermaos que el algoritmos que mejor clasifica nuestros datos es Random Forest

### **6.Generar en Java un objeto persistente con el algoritmo obtenido en el paso 5.**

Para el objeto persistente usamos el modelo obtenido de Weka. Para ejecutar este framework usamos la clase de Modelo.java ubicada en src/Modelos/Modelo.java. En esta clase encontramos el método aplicarModelo() donde recoge la informacion del modelo junto con la de los datos ubicados en training_data para encpntrar la solucción a laconsulta propuesta en el el fichero .arff de test_data

### **7. Implementar un prototipo de aplicación que consulte el objeto persistente generado en el paso 6.**  
  
    


  
  *Para llevar a cabo la comprobacion de los resultados de aprendizaje realizamos los siguientes pasos:*

1. Clonar el repositorio 
    
    ```
     git clone https://github.com/G0nzaloAlvarez/Practica3-IA-RandomForest.git
    
    ```
2. Seleccionar la consulta que quieres realizar **

```
Modificamos la clase consulta.arff en el directorio /test_data y cambiamos los parametros para ver si somos ganadores 

Ejemplo : 1,1,19,1,2,20,? 
Tiene que devolver un 1 ya que cuenta con los parametros mas favorable para salir ganador (Mejor distrito, hombre, edad, es voluntario, ranking 2 y ha sobrevivido muchos dias)
```

3. Generar el fichero jar una vez tenemos la consulta hecha y guardada. Ejecutamos el siguiente comando en la raiz del repositorio

```
$ make jar
```	

4. Ejecutar el archivo jar generado "aprendizaje.jar" y comprobamos si nuestro superviviente logra ganar los juego del hambre.

```
$ java -jar aprendizaje.jar
```


