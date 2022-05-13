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

 
