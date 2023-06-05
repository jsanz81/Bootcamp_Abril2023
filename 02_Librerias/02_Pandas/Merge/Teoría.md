<h1 align="center">
    Unión de Dataframes
</h1>

<div align="center">
    <img width="450" height="250" src="https://www.golinuxcloud.com/wp-content/uploads/types_joins-768x559.png" alt="Union_dataframes">
</div>

---

Pandas permite combinar filas de dos o más dataframe, 
basándose en una columna común entre ellas a las que denonimaremos `Key`, devolviendo por tanto las filas de los diferentes tablas.

## Tipos de Unión
Pandas tiene diferentes maneras de hacer esas combinaciones

<div align="center">

| Tipo de Unión  | Descripción                         |
| --------       | ------------------------------------|
| Inner Join     | Devuelve las filas donde ambos dataframe tengan un valor coincidente|
| Left Join      | Devuelve todas las filas de la primera dataframe y las filas coincidentes de la segunda dataframe            |
| Right Join     |Devuelve todas las filas de la segunda dataframe y las filas coincidentes de la primera dataframe|
| Outer Join     | Devuelve todas las filas de la primera  y segunda dataframe|
| Cross Join[^1]     | Crea el producto cartesiano de ambos dataframe|
</div>

[^1]:No recomendable hacer.

### Inner Join
Las combinaciones tipo **Inner Join** son las  más usadas.
Selecciona todas las filas de las columnas `Key` siempre y cuando haya una coincidencia entre las columnas en ambas tablas.

#### Ejemplo 1
Un Supermercado tiene en dos dataframe uno de nombres de los clientes y o otro con su fecha de ultima compra


**Clientes**
<div align="center">

| Id_Cliente  | Nombre                         | Apellido
| --------    | ------------------------------------|------------------------------------|
| 1234     | Beltrán         | García    |
| 2345     | Olga            | Bermejo   |
| 3456     | Aurora          | Siller    |
| 4567     | Saúl            | Almodóvar |
| 5678     | Ignacio         | Irin      |
</div>

**Última Compra**

<div align="center">

| Id_Cliente  | Fecha                         | Facturado
| --------       | ------------------------------------|------------------------------------|
| 4321     | 19-05-2019         | 7.532€    |
| 2345     | 25-03-2020         | 2.951€    |
| 3456     | 31-07-2020         | 4.569€    |
| 4567     | 28-02-2022         | 6.523€    |
| 7846     | 25-03-2023         | 9.632€    |
</div>

En este ejemplo la `Key` será ***Id_Cliente***.
Si se echa un vistazo rápio, se comprueba que solo 3 filas coinciden el ***Id_Cliente***.
quedando la unión como:

<div align="center">

| Id_Cliente  | Nombre | Apellido | Fecha| Facturado|
| --------    | -------|----------|------|----------|
| 2345     | Olga      | Bermejo   |25-03-2020| 2.951€    |
| 3456     | Aurora    | Siller    |31-07-2020| 4.569€    |
| 4567     | Saúl      | Almodóvar |28-02-2022| 6.523€    |
</div>

### Left Join
Las combinaciones tipo **Left Join** mantiene todas las filas del dataframe de la izquierda. Las filas del dataframe de la derecha se mostrarán si hay una coincidencia con las de la izquierda. Si existen valores en la tabla izquierda pero no en la tabla derecha, ésta mostrará como missing.

Continuemos con el [ejemplo anterior](#ejemplo-1)
#### Ejemplo 2

Se conisderará el dataframe de la izquierda el de clientes
quedando la unión como:

<div align="center">

| Id_Cliente  | Nombre | Apellido | Fecha| Facturado|
| --------    | -------|----------|------|----------|
| 1234     | Beltrán   | García    |   NaN |   NaN   |
| 2345     | Olga      | Bermejo   |25-03-2020| 2.951€    |
| 3456     | Aurora    | Siller    |31-07-2020| 4.569€    |
| 4567     | Saúl      | Almodóvar |28-02-2022| 6.523€    |
| 5678     | Ignacio   | Irin      |   NaN |   NaN   |
</div>

Se muestran todas las filas del dataframe Cliente, que es el dataframe de la izquierda. Se puede ver como Beltrán García e Ignacio Irin no tiene fecha de última compra ni facturado.

### Right Join
Las combinaciones tipo **Right Join** mantiene todas las filas del dataframe de la derecha. Las filas del dataframe de la izquierda se mostrarán si hay una coincidencia con las de la derecha. Si existen valores en la tabla derecha pero no en la tabla izquierda, ésta mostrará como missing.

Continuemos con el [ejemplo anterior](#ejemplo-1)
#### Ejemplo 3

Se conisderará el dataframe de la derecha el de Última Compra quedando la unión como:

<div align="center">

| Id_Cliente  | Nombre | Apellido | Fecha| Facturado|
| --------    | -------|----------|------|----------|
| 4321        |   NaN   |   NaN   | 19-05-2019 | 7.532€|
| 2345     | Olga      | Bermejo   |25-03-2020| 2.951€    |
| 3456     | Aurora    | Siller    |31-07-2020| 4.569€    |
| 4567     | Saúl      | Almodóvar |28-02-2022| 6.523€    |
| 7846     |   NaN |   NaN   | 25-03-2023       | 9.632€    |
</div>

Se muestran todas las filas del dataframe Última Compra, que es el dataframe de la derecha. Se puede ver como los Id_Cliente 4321 y 7846 no tiene nombre ni apellido.

### Outer Join
Las combinaciones tipo **Outer Join** mantiene todas las filas del dataframe de la izquierda y de la derecha. Si existen valores en la tabla derecha pero no en la tabla izquierda, ésta mostrará como missing y viceversa.

Continuemos con el [ejemplo anterior](#ejemplo-1)
#### Ejemplo 4

La unión Outer quedará así
<div align="center">

| Id_Cliente  | Nombre | Apellido | Fecha| Facturado|
| --------    | -------|----------|------|----------|
| 1234     | Beltrán   | García    |   NaN    |   NaN   |
| 2345     | Olga      | Bermejo   |25-03-2020| 2.951€  |
| 3456     | Aurora    | Siller    |31-07-2020| 4.569€  |
| 4567     | Saúl      | Almodóvar |28-02-2022| 6.523€  |
| 5678     | Ignacio   | Irin      |   NaN    | NaN     |
| 4321     |   NaN     | NaN       |19-05-2019| 7.532€  |
| 7846     |   NaN     | NaN       |25-03-2023| 9.632€  |
</div>

Se muestran todas las filas de ambos dataframes.

### Cross Join[^1]
Las combinaciones tipo **Cross Join** realiza un producto cartesiano entre los dataframes. No necesitará una ```Key```para realizarse.

Continuemos con el [ejemplo anterior](#ejemplo-1)
#### Ejemplo 5

La unión Cross quedará así
<div align="center">

|	Id_Cliente_x	|	Nombre	|	Apellido	|	Id_Cliente_y	|	Fecha	|	Facturado	|
|	------	|	------	|	------	|	------	|	------	|	------	|
|	1234	|	Beltrán	|	García	|	4321	|	19/05/2019	|	7.532 €	|
|	1234	|	Beltrán	|	García	|	2345	|	25/03/2020	|	2.951 €	|
|	1234	|	Beltrán	|	García	|	3456	|	31/07/2020	|	4.569 €	|
|	1234	|	Beltrán	|	García	|	4567	|	28/02/2022	|	6.523 €	|
|	1234	|	Beltrán	|	García	|	7846	|	25/03/2023	|	9.632 €	|
|	2345	|	Olga	|	Bermejo	|	4321	|	19/05/2019	|	7.532 €	|
|	2345	|	Olga	|	Bermejo	|	2345	|	25/03/2020	|	2.951 €	|
|	2345	|	Olga	|	Bermejo	|	3456	|	31/07/2020	|	4.569 €	|
|	2345	|	Olga	|	Bermejo	|	4567	|	28/02/2022	|	6.523 €	|
|	2345	|	Olga	|	Bermejo	|	7846	|	25/03/2023	|	9.632 €	|
|	3456	|	Aurora	|	Siller	|	4321	|	19/05/2019	|	7.532 €	|
|	3456	|	Aurora	|	Siller	|	2345	|	25/03/2020	|	2.951 €	|
|	3456	|	Aurora	|	Siller	|	3456	|	31/07/2020	|	4.569 €	|
|	3456	|	Aurora	|	Siller	|	4567	|	28/02/2022	|	6.523 €	|
|	3456	|	Aurora	|	Siller	|	7846	|	25/03/2023	|	9.632 €	|
|	4567	|	Saúl	|	Almodóvar	|	4321	|	19/05/2019	|	7.532 €	|
|	4567	|	Saúl	|	Almodóvar	|	2345	|	25/03/2020	|	2.951 €	|
|	4567	|	Saúl	|	Almodóvar	|	3456	|	31/07/2020	|	4.569 €	|
|	4567	|	Saúl	|	Almodóvar	|	4567	|	28/02/2022	|	6.523 €	|
|	4567	|	Saúl	|	Almodóvar	|	7846	|	25/03/2023	|	9.632 €	|
|	5678	|	Ignacio	|	Irin	|	4321	|	19/05/2019	|	7.532 €	|
|	5678	|	Ignacio	|	Irin	|	2345	|	25/03/2020	|	2.951 €	|
|	5678	|	Ignacio	|	Irin	|	3456	|	31/07/2020	|	4.569 €	|
|	5678	|	Ignacio	|	Irin	|	4567	|	28/02/2022	|	6.523 €	|
|	5678	|	Ignacio	|	Irin	|	7846	|	25/03/2023	|	9.632 €	|

</div>

Es decir, que cada fila del dataframe **Clientes** Lo unirá con cada una de las filas del dataframe **Ultima_fecha**

Puedes ver el desarrollo de python en los ficheros: 
* [Merge](https://github.com/DanielMontesSerrano/Bootcamp_Abril2023/blob/master/Librerias/Pandas/Merge/Merge.ipynb) 
* [Combinar_dataframe](https://github.com/DanielMontesSerrano/Bootcamp_Abril2023/blob/master/Librerias/Pandas/16%20Combinar%20dataframes%20(merge).ipynb)