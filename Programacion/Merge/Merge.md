<h1 align="center">
    Unión de Dataframes
</h1>

<div align="center">
    <img width="450" height="250" src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQuJgzJfXU7JevlHCnliruZV6jmXPdrQXqfEQ&usqp=CAU" alt="pyds">
</div>

Pandas permite combinar filas de dos o más dataframe, 
basándose en una columna común entre ellas a las que denonimaremos `Key`, devolviendo por tanto las filas de los diferentes tablas.

## Tipos de Unión
Pandas tiene diferentes maneras de hacer esas combinaciones

| Tipo de Unión  | Descripción                         |
| --------       | ------------------------------------|
| Inner Join     | Devuelve las filas donde ambos dataframe tengan un valor coincidente|
| Left Join      | Devuelve todas las filas de la primera tabla y las filas coincidentes de la segunda tabla            |
| Right Join     |Devuelve todas las filas de la segunda tabla y las filas coincidentes de la primera tabla|
| Outer Join     | Devuelve todas las filas de la primera  y segunda tabla|

### Inner Join
Las combinaciones tipo **Inner Join** son las  más usadas.
Selecciona todas las filas de las columnas `Key` siempre y cuando haya una coincidencia entre las columnas en ambas tablas.

#### Ejemplo 1
Un Supermercado tiene en dos dataframe uno de nombres de los clientes y o otro con su fecha de ultima compra

**Clientes**
| Id_Cliente  | Nombre                         | Apellido
| --------    | ------------------------------------|------------------------------------|
| 1234     | Beltrán         | García    |
| 2345     | Olga            | Bermejo   |
| 3456     | Aurora          | Siller    |
| 4567     | Saúl            | Almodóvar |
| 5678     | Ignacio         | Irin      |

**Última Compra**
| Id_Cliente  | Fecha                         | Facturado
| --------       | ------------------------------------|------------------------------------|
| 4321     | 19-05-2019         | 7.532€    |
| 2345     | 25-03-2020         | 2.951€    |
| 3456     | 31-07-2020         | 4.569€    |
| 4567     | 28-02-2022         | 6.523€    |
| 7846     | 25-03-2023         | 9.632€    |

En este ejemplo la `Key` será ***Id_Cliente***.
Si se echa un vistazo rápio, se comprueba que solo 3 filas coinciden el ***Id_Cliente***.
quedando la unión como:

| Id_Cliente  | Nombre | Apellido | Fecha| Facturado|
| --------    | -------|----------|------|----------|
| 2345     | Olga      | Bermejo   |25-03-2020| 2.951€    |
| 3456     | Aurora    | Siller    |31-07-2020| 4.569€    |
| 4567     | Saúl      | Almodóvar |28-02-2022| 6.523€    |

### Left Join
Las combinaciones tipo **Left Join** mantiene todas las filas del dataframe de la izquierda. Las filas del dataframe de la derecha se mostrarán si hay una coincidencia con las de la izquierda. Si existen valores en la tabla izquierda pero no en la tabla derecha, ésta mostrará como missing.

Continuemos con el [ejemplo anterior](#ejemplo-1)
#### Ejemplo 2
Se conisderará el dataframe de la izquierda el de clientes
quedando la unión como:

| Id_Cliente  | Nombre | Apellido | Fecha| Facturado|
| --------    | -------|----------|------|----------|
| 1234     | Beltrán   | García    |   NA |   NA   |
| 2345     | Olga      | Bermejo   |25-03-2020| 2.951€    |
| 3456     | Aurora    | Siller    |31-07-2020| 4.569€    |
| 4567     | Saúl      | Almodóvar |28-02-2022| 6.523€    |
| 5678     | Ignacio   | Irin      |   NA |   NA   |

Se muestran todas las filas del dataframe Cliente, que es el dataframe de la izquierda. Se puede ver como Beltrán García e Ignacio Irin no tiene fecha de última compra ni facturado.

### Right Join
Las combinaciones tipo **Right Join** mantiene todas las filas del dataframe de la derecha. Las filas del dataframe de la izquierda se mostrarán si hay una coincidencia con las de la derecha. Si existen valores en la tabla derecha pero no en la tabla izquierda, ésta mostrará como missing.

Continuemos con el [ejemplo anterior](#ejemplo-1)
#### Ejemplo 3

**Clientes**
| Id_Cliente  | Nombre                         | Apellido
| --------    | ------------------------------------|------------------------------------|
| 1234     | Beltrán         | García    |
| 2345     | Olga            | Bermejo   |
| 3456     | Aurora          | Siller    |
| 4567     | Saúl            | Almodóvar |
| 5678     | Ignacio         | Irin      |

**Última Compra**
| Id_Cliente  | Fecha                         | Facturado
| --------       | ------------------------------------|------------------------------------|
| 4321     | 19-05-2019         | 7.532€    |
| 2345     | 25-03-2020         | 2.951€    |
| 3456     | 31-07-2020         | 4.569€    |
| 4567     | 28-02-2022         | 6.523€    |

Se conisderará el dataframe de la derecha el de Última Compra quedando la unión como:

| Id_Cliente  | Nombre | Apellido | Fecha| Facturado|
| --------    | -------|----------|------|----------|
| 4321        |   NA   |   NA   | 19-05-2019 | 7.532€|
| 2345     | Olga      | Bermejo   |25-03-2020| 2.951€    |
| 3456     | Aurora    | Siller    |31-07-2020| 4.569€    |
| 4567     | Saúl      | Almodóvar |28-02-2022| 6.523€    |
| 7846     |   NA |   NA   | 25-03-2023       | 9.632€    |

Se muestran todas las filas del dataframe Última Compra, que es el dataframe de la derecha. Se puede ver como los Id_Cliente 4321 y 7846 no tiene nombre ni apellido.


