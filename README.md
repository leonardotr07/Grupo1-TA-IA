#  Clasificación de distritos del Perú según su nivel de daño por huaicos mediante algoritmos de ML supervisado



Este repositorio contiene el proyecto final del curso \*\*Inteligencia Artificial (1INF24)\*\* de la Pontificia Universidad Católica del Perú (PUCP). El estudio compara tres algoritmos de aprendizaje automático supervisado para clasificar los 1 834 distritos del Perú según su nivel de daño por huaicos (Bajo, Medio y Alto) en el periodo 2015-2020, a partir de su historial de emergencias 2003-2014, su región natural y su altitud.



## Integrantes



- Polino Rojas, Merari — 20267545

- Tueros Rodriguez, Leonardo — 20231671

- La Torre Chavesta, Enger Fabricio — 20233642

- Romero Luna, Binny Benigna — 20233905



## Descripción del proyecto



El Perú enfrenta un Niño Costero de magnitud extraordinaria y el Gobierno declaró en emergencia a 1 380 distritos. Esta medida no establece un orden de prioridad, por lo que los gobiernos regionales y locales deben decidir dónde intervenir primero. El proyecto propone un criterio basado en datos: clasificar los distritos según el daño histórico que han sufrido por huaicos, para apoyar la priorización preventiva.



El dataset final contiene **1 834 distritos**, **cero valores nulos** en las variables de entrada y tres clases: **Bajo (1 626)**, **Medio (104)** y **Alto (104)**. La etiqueta se construye con un índice de daño de 2015-2020 que combina damnificados, fallecidos y viviendas destruidas; el número de huaicos se excluye del índice porque un huaico sin pérdidas no constituye daño (377 de los 585 distritos con huaicos en 2015-2020 no registraron damnificados, fallecidos ni viviendas destruidas). Las variables de entrada provienen del periodo 2003-2014 para evitar fuga de información.



## Modelos evaluados



- K-Nearest Neighbors (KNN)

- Árbol de Decisión

- Regresión Logística

- Clasificador base (predice siempre la clase mayoritaria, Bajo)



## Principales resultados



La **Regresión Logística** y un **Árbol de Decisión muy regularizado** (profundidad 3 y al menos 300 casos por hoja) empataron en el mejor desempeño: F1 macro de 0,354 y 0,351 en test, y ambos detectaron **11 de los 31 distritos Alto** del conjunto de prueba. **KNN fue el más débil** (F1 macro de 0,297 en test), sin superar al clasificador base. La prueba t corregida de Nadeau y Bengio, con corrección de Holm, no encontró diferencias significativas entre los modelos. La hipótesis (que KNN y Árbol superarían a la Regresión) se **rechaza**.



El análisis de ablación mostró que **quitar la geografía reduce drásticamente el recall de Alto** (de 0,398 a 0,116 en la Regresión), aunque sube el F1 macro: un F1 más alto no implica un mejor modelo cuando el objetivo es detectar los distritos de mayor daño. La priorización medida con AUC-PR (0,063–0,072) está apenas por encima del azar (0,056), lo que indica que los modelos identifican un grupo amplio de distritos con más riesgo, pero no sirven para un ranking fino.



## Estructura del repositorio



```text

proyecto/

   Grupo1-TA-Notebook.ipynb

   dataset\_distritos\_v3.csv

   Grupo1-TA-Final.pdf



