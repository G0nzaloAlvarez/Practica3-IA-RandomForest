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
 
 2. Cada distrito lleva a 2 personas, de ahí que puedan ganar los 2 del mismo distrito. No pueden ganar
    2 personas de distritos diferentes. Puede haber un único ganador.
 
 3. Te puedes presentar voluntario a participar (suele ser persnas que se llevan entrenando toda la vida).

 4. Los distritos altos (11,12,13) son los peores, son los mas pobres y pocas veces ganan.

 5. 

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
    - dias sobrevividos: indica el número de dias que ha sobrevivido cada uno de los participantes de la       pareja.
    - ganador: indica cuál fue la pareja ganadora de cada una de las partidas.

### **4. Obtener el fichero .arff con los hechos codificados de acuedos con las caracterisiticas anteriores**

    Para generar el fichero .arff con los datos, realizamos los siguientes pasos

    1. Bajarnosel Dataset en formato CSV y adaptarlo al formato con el que trabaja weka.
    2. En weka, ir al apartado EXPERIMENTER/ANALYSE donde abrimos nuestro fichero csv
    3. Guardamos el fichero .arff seleccionando la opcion "save"
    4. Para guardar el modelo iremos a Calsify donde seleccionamos el clasificados mejro adaptado a nuestro modelo.
    5. Exportamos el modelo usando "save model" una vez ejecutado.
    


### **5. Evaluar distintos algoritmos de aprendizaje automatico con con los datos obtenidos**

´´´
Una vez obtenido el fichero `.arff`, 
´´´
### **6.Generar en Java un objeto persistente con el algoritmo obtenido en el paso 5.**
### **7. Implementar un prototipo de aplicación que consulte el objeto persistente generado en el paso 6.**