
```markdown
# 🧪 Proceso RPA - Monitoreo de Productos E-commerce

Automatización para monitoreo de productos, registro en base de datos, generación de reportes y envío mediante formulario web.

## 🚀 Funcionalidades principales
1. Consumo de API Fake Store
2. Almacenamiento en base de datos PostgreSQL
3. Generación de reportes en Excel
4. Automatización de formulario web

## 📋 Requisitos previos

System
System.IO
System.Collections.Generic
System.Linq
System.Data
System.Xml.Linq
Newtonsoft.Json
Newtonsoft.Json.Linq
System.Globalization
  ```

## 🛠 Configuración de la Base de Datos

### 1. Crear base de datos y tabla
Ejecutar en PostgreSQL:
```sql
-- Crear base de datos
CREATE DATABASE fakestore
    WITH
    OWNER = postgres
    ENCODING = 'UTF8'
    LC_COLLATE = 'en-US'
    LC_CTYPE = 'en-US'
    CONNECTION LIMIT = -1;

-- Crear tabla productos
CREATE TABLE IF NOT EXISTS public.productos
(
    id integer NOT NULL DEFAULT nextval('productos_id_seq'::regclass),
    id_producto integer NOT NULL,
    title VARCHAR(255) NOT NULL,
    price NUMERIC(10,2) NOT NULL,
    category VARCHAR(255) NOT NULL,
    description TEXT,
    fecha_insercion TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    CONSTRAINT productos_pkey PRIMARY KEY (id),
    CONSTRAINT productos_id_producto_key UNIQUE (id_producto)
);
```

### 2. Configurar variables de entorno
Editar archivo `Config` con:
```ini
Key	Value
QueueName	Prueba RPA
ServerAddress	localhost
DatabaseName	fakestore
UserName	postgres
UserPassword	admin1234
UrlAPI	https://fakestoreapi.com/products
UrlFormulario	https://form.jotform.com/250675791629066
NombreColaborador	Nicolas Santiago
ComentarioGenerico	Se recomienda comprobar resultado con registros en base de datos y archivo .json

```


## 🔄 Lógica de Inserción
Consulta SQL con prevención de duplicados:
```sql
@"INSERT INTO ""productos""
(""id_producto"", ""title"", ""price"", ""category"", ""description"")
VALUES (:id_producto, :title, :price::numeric, :category, :description)
ON CONFLICT (id_producto) DO NOTHING"
```



## 📌 Entregables incluidos
- [x] Script de creación de base de datos
- [x] Enlace al formulario Jotform
- [x] Captura de confirmación de formulario
- [x] Video demostrativo (enlace)

## 🎥 Demostración

https://youtu.be/2kKgpJtXBag


```


