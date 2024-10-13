# SQL Template para Vistas, Transacciones, Procedimientos y Funciones

## 1. Vistas

### Crear una Vista
```sql
-- Crear una vista para mostrar solo empleados activos
CREATE VIEW vista_empleados_activos AS
SELECT nombre, edad, puesto
FROM empleados
WHERE estado = 'activo';
```
### Consultar la vista
```sql
SELECT * FROM vista_empleados_activos;
```

### Actualizar una vista
```sql
-- Actualizar la vista para incluir empleados suspendidos
CREATE OR REPLACE VIEW vista_empleados_activos AS
SELECT nombre, edad, puesto
FROM empleados
WHERE estado IN ('activo', 'suspendido');

### Eliminar una vista
```sql
-- Eliminar la vista si ya no es necesaria
DROP VIEW vista_empleados_activos;
```

## Transacciones
```sql
-- Iniciar la transacción
START TRANSACTION;

-- Primera operación: debitar de la cuenta 1
UPDATE cuentas SET balance = balance - 100 WHERE cuenta_id = 1;

-- Segunda operación: acreditar a la cuenta 2
UPDATE cuentas SET balance = balance + 100 WHERE cuenta_id = 2;

-- Si todo sale bien, aplicar los cambios
COMMIT;

-- Si ocurre un error en cualquier parte, revertir todos los cambios
ROLLBACK;
```

## Procedimientos

### Crear un Procedimiento con Parámetros de Entrada y Salida

```sql
-- Definir delimitadores personalizados para evitar conflictos con las sentencias internas
DELIMITER $$

CREATE PROCEDURE obtener_informacion_cliente (
    IN id_cliente INT,         -- Parámetro de entrada
    OUT nombre_cliente VARCHAR(100),  -- Parámetro de salida
    OUT direccion_cliente VARCHAR(255) -- Parámetro de salida
)
BEGIN
    -- Obtener los datos del cliente según su id
    SELECT nombre, direccion 
    INTO nombre_cliente, direccion_cliente
    FROM clientes
    WHERE cliente_id = id_cliente;
END $$
```

DELIMITER ;

### LLamar a un procedimiento con parametros de salida
```sql
-- Definir variables para almacenar los valores devueltos
SET @nombre = '';
SET @direccion = '';

-- Llamar al procedimiento y capturar los valores en las variables definidas
CALL obtener_informacion_cliente(1, @nombre, @direccion);

-- Mostrar los valores obtenidos
SELECT @nombre AS Nombre, @direccion AS Dirección;
```

### Eliminar un procedimiento
```sql
-- Borrar el procedimiento cuando ya no se necesite
DROP PROCEDURE obtener_informacion_cliente;
```

## Funciones

### Crear una funcion
```sql
-- Crear una función para calcular el descuento de un producto según su precio
DELIMITER $$

CREATE FUNCTION calcular_descuento (precio DECIMAL(10, 2)) 
RETURNS DECIMAL(10, 2)
DETERMINISTIC
BEGIN
    DECLARE descuento DECIMAL(10, 2);
    
    -- Si el precio es mayor a 100, aplicar un 10% de descuento
    IF precio > 100 THEN
        SET descuento = precio * 0.10;
    ELSE
        SET descuento = 0;
    END IF;

    RETURN descuento;
END $$

DELIMITER ;
```

### Usar una funcion
```sql
-- Usar la función para obtener el descuento de un producto
SELECT nombre, calcular_descuento(precio) AS descuento
FROM productos;
```

### Eliminar una funcion
```sql
-- Borrar la función si ya no es necesaria
DROP FUNCTION calcular_descuento;
```