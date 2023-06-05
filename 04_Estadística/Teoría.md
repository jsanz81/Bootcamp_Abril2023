<h1 align="center">
    Estadística
</h1>

<div align="center">
    <img width="450" height="250" src="https://cdn.euroinnova.edu.es/img/subidasEditor/8-1595978597.jpg" alt="Estadistica">
</div>

<h2 align="center">
    Resumen
</h2>

<h3 align="center">
    Fenómenos y Variables
</h3>

---

* **Fenómeno causal o determinístico**: Aquellos que presentan los mismos resultados si se realizan en idénticas condiciones.
* **Fenómenos aleatorios o estadísticos**: No se pueden predecir el resultado aunque sean conocidas las condiciones de realización.
* **Población**: Conjunto de elementos sobre los que se quiere realizar un estudio.
* **Muestra**: Subconjunto de la población que debe ser representativo. (Evitar la destrucción de la población, Rapidez, Economía y precisión)
* **Variable**: la característica de estudio.
    * **Variable Cuantitativa**: Sus diversas modalidades pueden ser medidas numéricamente.
    * **Atributos**: Variables no numéricas.
    * **Variables discretas**: toman valores aislados.
    * **Variables continuas**: Pueden tomar todos los valores de un intervalo.

<h3 align="center">
    Tablas Estadísticas
</h3>

---

* **Tablas estadísticas**: Recogen las modalidades de forma individual o agrupada en intervalos y las frecuencias absolutas de cada modalidad o intervalo.  El número de observaciones se obtiene sumando todas las frecuencias absolutas.
* **Frecuencia relativa de la modalidad o intervalo** es el cociente de la frecuencia absoluta sobre el total de observaciones.
* **Frecuencia absoluta acumulada de la modalidad o intervalo** es el número de veces que se han observado valores menores o iguales a dicha modalidad o intervalo.
* **Frecuencia relativa acumulada**: A partir de las frecuencias relativas.

* **Distribución de frecuencias**: Conjunto de valores que presentan una variable estadística junto con su frecuencia.
Diagrama de Barras: La longitud de la barra nos informa de la frecuencia con que se ha observado cada valor de la variable
<h3 align="center">
    Momentos
</h3>

---

* **Momentos**: Valores calculados a partir de la distribución de frecuencias que resumen la información relativa a alguna propiedad de la variables.
<h4 align="center">
Momentos no centrados
</h4>

Para calcular los momentos no centrados se emplea

$$a_r=\cfrac{1}{n} \times \sum_{i=1}^k (x_i^r \times n_i)$$

* **Propiedades**: El momento no centrado a_1 se conoce como media (aritmética) y $a_0$=1



<h4 align="center">
Momentos centrados
</h4>

Para calcular los momentos centrados se emplea

```math
m_r=\frac{1}{n} \times \sum_{i=1}^k \left(\left(x_i-\bar{x}\right)^r n_i\right)
```
* **Propiedades** : El momento centrado $m_2$ se conoce como la varianza. $m_0=1$, $m_1=0$. 

<h3 align="center">
Medidas de Posición
</h3>

---

Tratan de representar mediante un solo valor a un conjunto de datos y suelen tomar una posición central respecto de los mismos.
<h4 align="center">
Media Aritmética
</h4>

se define como 
```math
\bar{x}=\cfrac{1}{n} \sum_{i=1}^k x_i \times ni
```
**Propiedades**

1. Consideramos n observaciones agrupadas en s conjuntos de datos con $n_1,\ldots,n_s$ observaciones cada uno y con media $\bar{x}_1,\ldots,\bar{x}_s$, entonces la media $\bar{x}$ de n observaciones es:
```math
\bar{x} = \cfrac{\bar{x}_1 \times n_1 + \ldots + \bar{x}_s n_s}{n_1 + \ldots  + n_s}
```
2. Sufre cambios de escala y origen.

<h4 align="center">
Mediana
</h4>

Es aquel valor que divide a la muestra ordenada en dos partes iguales. Se puede calcular por interpolación

<h4 align="center">
Moda
</h4>

Es el valor que se presenta con más frecuencia. Puede haber varias modas. Para variables discretas y atributos se calcula inmediato. Variables continúas la mayor o frecuencia de las observaciones en un intervalo depende de su amplitud.


<h4 align="center">
Percentiles
</h4>

Dividen a la muestra ordenada en 100 conjuntos con igual número de observaciones. Reciben el nombre de medidas de posición no central. Forma de calculuar por interpolación.

<h3 align="center">
Medidas de Dispersión
</h3>

---
