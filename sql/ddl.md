# Hoja de Trucos Completa de SQL

## 1. Crear, Actualizar, Borrar, Insertar

### Crear tabla
```sql
CREATE TABLE nombre_tabla (
    id INT PRIMARY KEY AUTO_INCREMENT,
    nombre VARCHAR(100) NOT NULL,
    edad INT CHECK (edad > 0)
);
```
### Claves primarias y foraneas
```sql
CREATE TABLE pedidos (
    id INT auto_increment,
    cliente_id INT,
    PRIMARY KEY(id),
    FOREIGN KEY (cliente_id) REFERENCES clientes(id)
);
```

### insertar datos
```sql
INSERT INTO nombre_tabla (nombre, edad)
VALUES ('Juan', 30), ('Maria', 25);
```

### Actualizar datos
```sql
UPDATE nombre_tabla
SET edad = 31
WHERE id = 1;
```

### Borrar datos
```sql
DELETE FROM nombre_tabla
WHERE id = 1;
```

### Truncar una tabla (elimina todos los registros, más rápido que DELETE)
```sql
TRUNCATE TABLE nombre_tabla;
```

## 2. Carga de Datos desde Archivo Externo

### Cargar datos desde un archivo CSV en MySQL
```sql
LOAD DATA INFILE '/ruta/del/archivo.csv'
INTO TABLE nombre_tabla
FIELDS TERMINATED BY ',' 
LINES TERMINATED BY '\n'
IGNORE 1 LINES;
```

### Cargar datos desde archivo CSV en PostgreSQL
```sql
COPY nombre_tabla FROM '/ruta/del/archivo.csv' DELIMITER ',' CSV HEADER;
```

## 3. Funciones de Agregación
### SUM, AVG, COUNT, MIN, MAX
```sql
SELECT 
    SUM(edad), 
    AVG(edad), 
    COUNT(*), 
    MIN(edad), 
    MAX(edad)
FROM nombre_tabla;
```

### GROUP_CONCAT (MySQL) o STRING_AGG (PostgreSQL) para concatenar valores
```sql
SELECT GROUP_CONCAT(nombre) 
FROM nombre_tabla;
```

```sql
SELECT STRING_AGG(nombre, ', ') 
FROM nombre_tabla;
```

## 4. WHERE (Condiciones)
### Filtrar datos con condiciones múltiples
```sql
SELECT * 
FROM nombre_tabla
WHERE edad > 25 AND nombre = 'Juan';
```

### Usar operadores IN, BETWEEN, LIKE
```sql
SELECT * 
FROM nombre_tabla
WHERE edad BETWEEN 20 AND 30;

SELECT * 
FROM nombre_tabla
WHERE nombre LIKE 'J%';

SELECT * 
FROM nombre_tabla
WHERE nombre IN ('Juan', 'Maria');
```

### Usar subconsultas en WHERE
```sql
SELECT * 
FROM nombre_tabla
WHERE edad > (SELECT AVG(edad) FROM nombre_tabla);
```

## 5. Agrupamiento, Ordenamiento, Límite, Offset, Having
### Agrupamiento
```sql
SELECT nombre, COUNT(*)
FROM nombre_tabla
GROUP BY nombre;
```

### Ordenar resultados
```sql
SELECT * 
FROM nombre_tabla
ORDER BY edad DESC;
```

### Limite y desplazamiento
```sql
SELECT * 
FROM nombre_tabla
ORDER BY edad
LIMIT 10 OFFSET 5;
```

### Having: Condiciones tras agrupamiento
```sql
SELECT nombre, COUNT(*)
FROM nombre_tabla
GROUP BY nombre
HAVING COUNT(*) > 1;
```

## 6. ENUM y Conjuntos
### Campos enum
```sql
CREATE TABLE empleados (
    id INT PRIMARY KEY,
    nombre VARCHAR(100),
    estado ENUM('activo', 'inactivo', 'suspendido')
);
```

### Conjuntos
```sql
CREATE TABLE dias_trabajo (
    id INT PRIMARY KEY,
    dias SET('Lunes', 'Martes', 'Miercoles', 'Jueves', 'Viernes')
);
```

## 7. Joins
### Inner join
```sql
SELECT *
FROM tabla1
INNER JOIN tabla2 ON tabla1.id = tabla2.id;
```

### Left join
```sql
SELECT *
FROM tabla1
LEFT JOIN tabla2 ON tabla1.id = tabla2.id;

### Right join
```sql
SELECT *
FROM tabla1
RIGHT JOIN tabla2 ON tabla1.id = tabla2.id;
```

### Full outer join
```sql
SELECT *
FROM tabla1
FULL OUTER JOIN tabla2 ON tabla1.id = tabla2.id;
```

### CROSS JOIN (producto cartesiano)
```sql
SELECT *
FROM tabla1
CROSS JOIN tabla2;
```

### 8. Variables Temporales
#### Declarar e iniciar una variable
```sql
SET @variable_temporal = 100;
```

#### Usar la variable
```sql
SELECT nombre
FROM nombre_tabla
WHERE edad > @variable_temporal;
```

## 9. Volcado de Datos en Archivos Externos (mysqldump)
### Exportar base de datos completa
```sql
mysqldump -u usuario -p nombre_base_datos > backup.sql
```

### Exportar una sola tabla
```sql
mysqldump -u usuario -p nombre_base_datos nombre_tabla > backup_tabla.sql
```

### Restaurar una base de datos
```sql
mysql -u usuario -p nombre_base_datos < backup.sql
```

## 10. Indices
### Crear indices
```sql
CREATE INDEX idx_nombre ON nombre_tabla (nombre);
```

### Crear un indice unico
```sql
CREATE UNIQUE INDEX idx_nombre_unico ON nombre_tabla (nombre);
```

### Crear un indice compuesto
```sql
CREATE INDEX idx_compuesto ON nombre_tabla (nombre, edad);
```

### Borrar un indice
```sql
DROP INDEX idx_nombre ON nombre_tabla;

### Ver indice en una tabla
```sql
SHOW INDEX FROM nombre_tabla;
```

## 14. Funciones de Ventana (Window Functions)
### Uso de ROW_NUMBER y RANK
```sql
SELECT nombre, edad, 
    ROW_NUMBER() OVER (ORDER BY edad DESC) AS numero_fila,
    RANK() OVER (ORDER BY edad DESC) AS rango
FROM nombre_tabla;
```

## Comentarios
```sql
-- Comentario de una sola línea

/*
  Comentario
  multilínea
*/
```