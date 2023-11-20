# TAREA_PROCESUAL_H4
touch README.md CREATE DATABASE Agencia_de_viajes5;
USE Agencia_de_viajes5;

CREATE TABLE empleados (
    empleado_id INT PRIMARY KEY,
    nombre VARCHAR(50),
    apellido VARCHAR(50),
    email VARCHAR(50),
    cargo VARCHAR(50)
);

CREATE TABLE destinos (
    destino_id INT PRIMARY KEY,
    destino VARCHAR(50),
    descripcion VARCHAR(50),
    precio INT
);

CREATE TABLE paquetes (
    paquete_id INT PRIMARY KEY,
    paquete VARCHAR(100),
    descripcion VARCHAR(50),
    fecha_inicio DATE,
    fecha_fin DATE,
    destino_id INT,
    precio_total DECIMAL(10, 2),
    FOREIGN KEY (destino_id) REFERENCES destinos(destino_id)
);
CREATE TABLE clientes (
    cliente_id INT PRIMARY KEY,
    nombre VARCHAR(50),
    apellido VARCHAR(50),
    email VARCHAR(50),
    telefono INT
);

CREATE TABLE reservas (
    reserva_id INT PRIMARY KEY,
    cliente_id INT,
    paquete_id INT,
    fecha_reserva DATE,
    cantidad_personas INT,
    precio_total DECIMAL(10, 2),
    estado_reserva VARCHAR(20),
    FOREIGN KEY (cliente_id) REFERENCES clientes(cliente_id),
    FOREIGN KEY (paquete_id) REFERENCES paquetes(paquete_id)
);

-- Correcciones en la tabla empleados
INSERT INTO empleados(empleado_id, nombre, apellido, email, cargo)
VALUES 
(1, 'Maria', 'Gomez', 'maria.gomez@example.com', 'Agente de ventas'),
(2, 'Carlos', 'Perez', 'carlos.perez@example.com', 'Asesor de viajes'),
(3, 'Laura', 'Rodriguez', 'laura.rodriguez@example.com', 'Gerente de sucursal'),
(4, 'Pedro', 'Martinez', 'pedro.martinez@example.com', 'Asistente administrativo'),
(5, 'Ana', 'Lopez', 'ana.lopez@example.com', 'Especialista en destinos');

-- Correcciones en la tabla destinos
INSERT INTO destinos(destino_id, destino, descripcion, precio)
VALUES 
(1, 'Paris', 'Ciudad del amor y la luz', 1200),
(2, 'Tokio', 'Metropolis moderna y vibrante', 1500),
(3, 'Nueva York', 'La ciudad que nunca duerme', 1800),
(4, 'Roma', 'Cuna de la civilizacion antigua', 1400),
(5, 'Sidney', 'Puerta de entrada a Australia', 1600);

-- Correcciones en la tabla paquetes
INSERT INTO paquetes(paquete_id, paquete, descripcion, fecha_inicio, fecha_fin, destino_id, precio_total)
VALUES 
(1, 'Escapada romantica a Paris', 'Disfruta de la ciudad del amor', '2023-01-15', '2023-01-20', 1, 1500.00),
(2, 'Aventura Tokio', 'Descubre la cultura japonesa', '2023-02-01', '2023-02-10', 2, 2000.00),
(3, 'Explora Nueva York', 'Recorre los lugares turisticos', '2023-03-10', '2023-03-18', 3, 2200.00),
(4, 'Historia y arte en Roma', 'Sumergete en la historia de Roma', '2023-04-05', '2023-04-12', 4, 1800.00),
(5, 'Aventura en Australia', 'Descubre la bella naturaleza de Australia', '2023-05-20', '2023-05-28', 5, 2500.00);

-- Correcciones en la tabla clientes
INSERT INTO clientes(cliente_id, nombre, apellido, email, telefono)
VALUES 
(1, 'Jhon', 'Doe', 'jhon.doe@example.com', 5551234),
(2, 'Jane', 'Smith', 'jane.smith@example.com', 5555678),
(3, 'Bob', 'Johnson', 'bob.johnson@example.com', 5559876),
(4, 'Alice', 'Williams', 'alice.williams@example.com', 5554321),
(5, 'Charlie', 'Brown', 'charlie.brown@example.com', 5558765);

-- Correcciones en la tabla reservas
INSERT INTO reservas(reserva_id, cliente_id, paquete_id, fecha_reserva, cantidad_personas, precio_total, estado_reserva)
VALUES 
(1, 1, 1, '2023-01-05', 2, 3000.00, 'Confirmada'),
(2, 2, 2, '2023-02-12', 1, 2200.00, 'Pendiente'),
(3, 3, 3, '2023-03-18', 3, 6000.00, 'Confirmada'),
(4, 4, 4, '2023-04-10', 2, 3600.00, 'Pendiente'),
(5, 5, 5, '2023-05-25', 1, 2500.00, 'Confirmada');
SELECT CONCAT(nombre, ' ', apellido) AS nombre_completo
FROM empleados;

SELECT COUNT(*) AS total_empleados
FROM empleados;




SELECT nombre, apellido
FROM empleados
WHERE cargo = 'Agente de Ventas';


SELECT d.destino
FROM destinos d
JOIN paquetes p ON d.destino_id = p.destino_id
JOIN reservas r ON p.paquete_id = r.paquete_id
WHERE r.cliente_id = 1;

SELECT p.paquete
FROM paquetes p
JOIN reservas r ON p.paquete_id = r.paquete_id
JOIN clientes c ON r.cliente_id = c.cliente_id
WHERE c.nombre = 'Jane' AND c.apellido = 'Smith';

SELECT c.nombre AS nombre_cliente, c.apellido AS apellido_cliente, d.destino, e.nombre AS nombre_empleado, e.apellido AS apellido_empleado
FROM clientes c
JOIN reservas r ON c.cliente_id = r.cliente_id
JOIN paquetes p ON r.paquete_id = p.paquete_id
JOIN destinos d ON p.destino_id = d.destino_id
JOIN empleados e ON e.empleado_id = r.cliente_id;

SELECT SUM(cantidad_personas) AS total_personas
FROM reservas;

SELECT COUNT(*) AS total_reservas
FROM paquetes p
JOIN reservas r ON p.paquete_id = r.paquete_id
WHERE p.paquete = 'Aventura Tokio';

git add [TAREA.pptx](https://github.com/DRI-BDA/TAREA_PROCESUAL_H4/files/13407989/TAREA.pptx)
git add. [TAREA.pdf](https://github.com/DRI-BDA/TAREA_PROCESUAL_H4/files/13408073/TAREA.pdf)
git add. 
https://youtu.be/2whvwF5gPP4?si=nSIamro-iYluTcLS


