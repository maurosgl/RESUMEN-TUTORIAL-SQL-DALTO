# Resumen tutorial: SQL Desde Cero (SoyDalto)

SQL es el lenguaje fundamental que alimenta las bases de datos y facilita la transformación de simples conjuntos de datos en información valiosa. En un mundo impulsado por datos, el dominio de SQL es una habilidad imprescindible para quienes buscan tomar decisiones basadas en evidencia y construir soluciones robustas. 

Este manual te guiará paso a paso, desde los conceptos más básicos hasta las técnicas avanzadas que te permitirán dominar SQL con seguridad. Y lo haremos utilizando uno de los entornos más clásicos y completos para aprender bases de datos: Northwind, una base de datos que simula el funcionamiento de una compañía ficticia de importación y exportación.

A lo largo de esta guía, exploraremos cómo puedes utilizar SQL para consultar, analizar y manipular datos en un contexto empresarial realista. Ya seas un principiante absoluto o alguien con experiencia en SQL, este manual tiene algo para ti: Con ejemplos prácticos desarrollados paso a paso, desglosamos conceptos de manera accesible, asegurándonos de que cada lección esté conectada a un uso práctico en la vida real, ayudándote a entender cómo SQL puede potenciar tus proyectos y mejorar tu toma de decisiones.

¡Prepárate para sumergirte en el fascinante mundo del análisis y la gestión de datos con SQL!


## Desarrollo

### COMANDO AS
El comando AS en SQL se usa para asignar un alias (un nombre temporal) a una tabla o columna en una consulta. Esto hace que sea más fácil leer y referenciar los resultados.

```sql
SELECT * FirstName AS Nombre, LastName AS Apellido FROM Employees;
```

### ORDER BY ASC
El comando ORDER BY ASC en SQL se utiliza para ordenar los resultados de una consulta en orden ascendente (de menor a mayor).

```sql
SELECT * FROM Products
ORDER BY price ASC;
```

### ORDER BY DESC
El comando ORDER BY DESC en SQL se usa para ordenar los resultados de una consulta en orden descendente.

```sql
SELECT * FROM Products
ORDER BY price DESC;
```
### OPCIÓN NULL LAST
El comando NULL LAST en SQL se usa para que, al ordenar los resultados, los valores NULL aparezcan al final de la lista, independientemente de si el orden es ascendente (ASC) o descendente (DESC).

```sql
SELECT * FROM Products
ORDER BY ProductName ASC NULLS LAST;
```
### OPCIÓN NULL FIRST
El comando NULLS FIRST en SQL se utiliza para especificar que los valores NULL deben aparecer primero al ordenar los resultados de una consulta.

```sql
SELECT * FROM Products
ORDER BY ProductName DESC NULLS FIRST;
```
### ORDEN RANDOM
El comando ORDER BY RANDOM() en SQL se utiliza para ordenar los resultados de forma aleatoria. Es muy útil cuando deseas mostrar los registros en un orden no predecible, por ejemplo, al seleccionar elementos de manera aleatoria.

```sql
SELECT * FROM Products
ORDER BY RANDOM();
```

### ORDER BY TOMANDO DOS COLUMNAS
El comando ORDER BY en SQL se utiliza para ordenar los resultados de una consulta en función de una o más columnas. Cuando usas dos columnas, primero se ordenan los resultados por la primera columna y, si hay valores repetidos, se usan los valores de la segunda columna para ordenar esos registros.

```sql
SELECT * FROM Products
ORDER BY ProductName, SupplierID DESC;
```

### SELECCIONAR VALORES ÚNICOS Y ORDENADOS
El comando SELECT DISTINCT en SQL se utiliza para eliminar duplicados en los resultados de una consulta. Es decir, te permite obtener solo los valores únicos de una o más columnas.

```sql
SELECT DISTINCT ProductName FROM Products
ORDER BY ProductName ASC;
```

### WHERE
El comando WHERE en SQL se utiliza para filtrar los resultados de una consulta, especificando condiciones que deben cumplirse para que las filas sean incluidas en el resultado.

```sql
SELECT ProductName FROM Products
WHERE ProductID = 14;
```

### WHERE APLICADO A UN CRITERIO TIPO TEX
El comando WHERE en SQL se utiliza para filtrar los resultados de una consulta, especificando condiciones que deben cumplirse para que las filas sean incluidas en el resultado.

```sql
SELECT ProductName FROM Products
WHERE ProductName = "Tofu";
```

### WHERE EMPLEANDO >, <

```sql
SELECT * FROM Products
WHERE Price <= 40;
```

### BORRAR UN REGISTRO
El comando DELETE FROM en SQL se utiliza para eliminar registros de una tabla.

```sql
DELETE FROM Products
WHERE ProductID = 3;
```

### ACTUALIZAR UN REGISTRO
El comando UPDATE en SQL se emplea para modificar los registros existentes en una tabla. Permite cambiar uno o más valores de columnas en filas específicas.

```sql
UPDATE Products
SET Price = 97, ProductName = "Manzana"
WHERE ProductID = 9;
```

### AND
El operador AND en SQL se utiliza para combinar condiciones en una cláusula WHERE. Permite que una consulta devuelva resultados que cumplan todas las condiciones especificadas.

```sql
SELECT * FROM Customers
WHERE CustomerID >= 50 AND CustomerID <55;
```

### OR
El operador OR en SQL se utiliza para combinar condiciones en una cláusula WHERE. Permite que una fila cumpla al menos una de las condiciones especificadas, ampliando así el conjunto de resultados devueltos por la consulta.

```sql
SELECT * FROM Employees
WHERE FirstName = "Nancy" OR FirstName = "Anne";
```

### USAR AND Y OR SIMULTÁNEAMENTE
En SQL, los operadores OR y AND se utilizan para combinar condiciones en una consulta WHERE, permitiendo filtrar resultados basados en múltiples criterios.
Uso de AND:
•	AND se utiliza para asegurar que todas las condiciones especificadas sean verdaderas. Solo devuelve filas donde todas las condiciones se cumplen.
Uso de OR:
•	OR se usa para devolver filas donde al menos una de las condiciones es verdadera. Así, se cumplen más condiciones.

```sql
SELECT * FROM Products
WHERE (Price < 20 OR CategoryID = 6) AND SupplierID = 7;
```

### WHERE NOT
El comando WHERE NOT en SQL se utiliza para filtrar los resultados de una consulta, excluyendo aquellos registros que cumplen una determinada condición

```sql
SELECT * FROM Customers
WHERE NOT Country = 'USA';
```

### WHERE NOT / AND NOT

```sql
SELECT * FROM Customers
WHERE NOT Country = 'USA' AND NOT Country = 'France';
```

### WHERE / AND / AND NOT

```sql
SELECT * FROM Customers
WHERE CustomerID >= 50 AND CustomerID <55
AND NOT Country = 'Germany'
```

### LIMIT
El comando LIMIT en SQL se utiliza para restringir el número de registros devueltos por una consulta. Es especialmente útil cuando deseas obtener solo un número específico de filas de un conjunto de resultados.

```sql
SELECT * FROM Customers
WHERE CustomerID >= 50
AND NOT Country = 'Germany'
AND NOT Country = 'UK'
AND NOT Country = 'Argentina'
LIMIT 5;
```

### OPERADOR LÓGICO DISTINTO DE !=
El operador != en SQL se utiliza para comparar dos valores y verificar si son diferentes. Es un operador de desigualdad.
Uso básico:
Se utiliza en cláusulas como WHERE para filtrar registros que no cumplen con una condición específica.

```sql
SELECT * FROM Customers WHERE Country != 'USA';
```

### WHERE NOT BETWEEN
Este enfoque es útil cuando necesitas identificar registros que están fuera de un rango específico, como buscar productos que no caen dentro de un intervalo de precios, fechas, o cualquier otra métrica que estés analizando.

```sql
SELECT * FROM Products WHERE NOT Price BETWEEN 20 AND 40;
```

### FILTRO POR FECHAS

```sql
SELECT * FROM Employees WHERE BirthDate BETWEEN '1960-0-1' AND '1970-0-1';
```

### OPERADOR LIKE

El operador LIKE en SQL se utiliza para buscar patrones en columnas de tipo texto. El símbolo % es un comodín que representa cero o más caracteres en una búsqueda.
Uso básico de LIKE %:
•	LIKE 'patrón%': Encuentra valores que comienzan con "patrón".
•	LIKE '%patrón': Encuentra valores que terminan con "patrón".
•	LIKE '%patrón%': Encuentra valores que contienen "patrón" en cualquier parte.
Ejemplo:
Supongamos que tienes una tabla llamada Productos y quieres encontrar todos los productos que contienen la palabra "manzana":
sql
Copiar código
SELECT nombre_producto
FROM Productos
WHERE nombre_producto LIKE '%manzana%';
Esto devolverá todos los productos que tienen "manzana" en su nombre, sin importar su posición.
Resumen:
•	LIKE % se utiliza para realizar búsquedas flexibles en columnas de texto, facilitando la localización de coincidencias basadas en patrones.

```sql
SELECT * FROM Employees WHERE LastName LIKE '%ller';
```

### OPERADOR LIKE A% (Encuentra valores que inicien con esa cadena de texto)

```sql
SELECT * FROM Employees WHERE LastName LIKE 'B%';
```

### OPERADOR LIKE %A% (Encuentra valores que contengan lo ingresado)

```sql
SELECT * FROM Employees WHERE LastName LIKE '%B%';
```

### OPERADOR IN

```sql
SELECT * FROM Employees
WHERE LastName IN ("Fuller", "King");
```

### NOT IN

```sql
SELECT * FROM Employees
WHERE LastName NOT IN ("Fuller", "King");
```

## FUNCIONES DE AGREGACIÓN

### COUNT()

```sql
SELECT COUNT(FirstName) FROM Employees;
```

### SUM()

```sql
SELECT SUM(Price) FROM Employees;
```

### AVG()

```sql
SELECT AVG(Price) FROM Employees;
```

### ROUND

```sql
SELECT ROUND(AVG(Price),2) AS Promedio_precio FROM Products;
```

### MIN

```sql
SELECT ProductName, MIN(Price) AS precio_minimo FROM Products
WHERE ProductName IS NOT NULL;
```

### MAX

```sql
SELECT ProductName, MAX(Price) AS precio_maximo FROM Products
WHERE ProductName IS NOT NULL;
```

### GROUP BY

```sql
SELECT CategoryID, ROUND(AVG(Price)) AS promedio FROM Products
WHERE CategoryID IS NOT NULL
GROUP BY CategoryID;
```

### HAVING

```sql
SELECT CategoryID, ROUND(AVG(Price)) AS promedio FROM Products
WHERE CategoryID IS NOT NULL
GROUP BY CategoryID
HAVING promedio > 40;
```

## SUBCONSULTAS

```sql
SELECT ProductID,
  SUM(Quantity) as total_vendido,
  (SELECT Price FROM Products WHERE ProductID = OD.ProductID) AS Price,
  ROUND(SUM(Quantity) * (SELECT Price FROM Products WHERE ProductID = OD.ProductID))) AS ventas_totales
FROM [OrderDetails] OD
GROUP BY ProductID
ORDER BY ventas_totales DESC;
```

### SUBCONSULTA EN EL FROM

```sql
SELECT * FROM(
SELECT ProductID,
  SUM(Quantity) as total_vendido,
  (SELECT Price FROM Products WHERE ProductID = OD.ProductID) AS Price,
  ROUND(SUM(Quantity) * (SELECT Price FROM Products WHERE ProductID = OD.ProductID))) AS ventas_totales
FROM [OrderDetails] OD
WHERE (SELECT Price FROM Products WHERE ProductID = OD.ProductID) > 40
GROUP BY ProductID
ORDER BY ventas_totales ASC);
```
