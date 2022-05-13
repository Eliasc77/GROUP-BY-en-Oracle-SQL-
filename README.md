# GROUP-BY-en-Oracle-SQL-
#### group by especifica q una consulta devuelve una lista que esta agrupada por una  o mas columnaas es decir al momento de ejecutar una consulta utilizando la funcion GROUP BY en el resultado veremos una agrupacion en una columna especifica de la cantidad de registros consultados en dicha sentencia.

```sql
  create table visitantes(
  nombre varchar2(30),
  edad number(2),
  sexo char(1) default 'f',
  domicilio varchar2(30),
  ciudad varchar2(20) default 'Cordoba',
  telefono varchar2(11),
  mail varchar2(30) default 'no tiene',
  montocompra number(6,2)
 );

 insert into visitantes
  values ('Susana Molina',35,default,'Colon 123',default,null,null,59.80);
 insert into visitantes
  values ('Marcos Torres',29,'m',default,'Carlos Paz',default,'marcostorres@hotmail.com',150.50);
 insert into visitantes
  values ('Mariana Juarez',45,default,default,'Carlos Paz',null,default,23.90);
 insert into visitantes (nombre, edad,sexo,telefono, mail)
  values ('Fabian Perez',36,'m','4556677','fabianperez@xaxamail.com');
 insert into visitantes (nombre, ciudad, montocompra)
  values ('Alejandra Gonzalez','La Falda',280.50);
 insert into visitantes (nombre, edad,sexo, ciudad, mail,montocompra)
  values ('Gaston Perez',29,'m','Carlos Paz','gastonperez1@gmail.com',95.40);
 insert into visitantes
  values ('Liliana Torres',40,default,'Sarmiento 876',default,default,default,85);
 insert into visitantes
  values ('Gabriela Duarte',21,null,null,'Rio Tercero',default,'gabrielaltorres@hotmail.com',321.50);
 
 ```
 
 ```sql
 select * from visitantes;
 ```
 
 | nombre            | edad           |   sexo   |  domicilio   |  ciudad   |  telefono  |  mail  | mmontocompra |
 | ------------------|:----------------:|----------------:| ---------:| -----------:| ------------------:| --------:| ----------:|
 | Susana Molina | 35 |  f |Colon 123 | cordoba | (null)| (null)|  59.8   |
 | Marcos Torres | 29 | m   |(null) | Carlos Paz | (null)|marcostorres@hotmail.com| 150.5 |
 | Mariana Juarez | 45|  f  | (null) | Carlos Paz | (null)| no tiene|  23.9 |
 | Fabian Perez | 36|  m   | (null) | cordoba | 4556677| fabianperez@xaxamail.com'|   (null) |
 | Alejandra Gonzalez | (null) |  f  | (null) | La Falda | (null)| no tiene|  280.50  |
 | Gaston Perez| 29 |  m   | (null)  | Carlos Paz | (null)| gastonperez1@gmail.com|   95.40  |
 | Liliana Torres | 40 |  f  | Sarmiento 876 | cordoba | (null)| no tiene|  85  |
 | Gabriela Duarte | 21 |  (null) | (null) | Rio Tercero | (null)| gabrielaltorres@hotmail.com|  321.50  |

___
 
 ```sql
select ciudad, count(*)
from visitantes
group by ciudad;
```

|CIUDAD | COUNT(**) | 
|:------| ---------:|
|La falda | 1|
|Rio Tercero | 1|
|Cordoba | 3|
|Carlos Paz| 3|

#### nos mostrara cuantos registros fueron insertados en el campo ciudad y agrupados por ciudad

 ```sql
select ciudad, count(telefono) as "numero de telefonos"
from visitantes
group by ciudad;
```

|CIUDAD | numero de telefonos | 
|:------| ---------:|
|La falda | 0|
|Rio Tercero | 0|
|Cordoba | 1|
|Carlos Paz| 0|

#### nos mostrara los registros de telefonos agrupados x ciudad.
___

```sql
select sexo, sum(montocompra) as "total comprado " from visitantes
group by sexo;
```
|sexo | total comprado | 
|:------| ---------:|
|(null) | 321.5|
|f | 449.2|
|m | 245.9|

#### se muestra los montos comprados segun el sexo, se mostrara null ya que en el campo null existen registros de monto de compra.

>si no queremos que se muestre el null utilizamo la clausula  IS NOT NULL

```SQL
select sexo, sum(montocompra) as "total comprado "
from visitantes
where sexo is not null
group by sexo;
```
|sexo | total comprado | 
|:------| ---------:|
|f | 449.2|
|m | 245.9|

____
#### con group by tambien funciona agrupando varios campos
```sql
select sexo,  ciudad, max(montocompra) as "Mayor", min(montocompra) as "Menor"
from visitantes
group by sexo,ciudad;
```

|sexo | ciudad | Mayor | Menor |
|:------|---------:| ---------:| ---------:|
|m | Carlos Paz|  150.5 |  95.4 |
|f | Carlos Paz| 23.9 | 23.9|
|(null) | Rio Tercero| 321.5 | 321.5 |
|f | Cordoba | 85 |  59.8 |
|f | La Falda | 280.5 | 280.5| 
|m | Cordoba | (null ) |(null ) |

####  OJO :  cuando se utiliza la funcion GROUP BY se debe agrupar por tantos campos se coloque al principio del select y en el mismo orden.
