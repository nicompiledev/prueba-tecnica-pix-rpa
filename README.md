
# 🧪 Proceso RPA - Monitoreo de Productos E-commerce

Automatización para monitoreo de productos, registro en base de datos, generación de reportes y envío mediante formulario web.

## 🚀 Funcionalidades principales
1. Consumo de API Fake Store
2. Almacenamiento en base de datos PostgreSQL
3. Generación de reportes en Excel
4. Automatización de formulario web

## 📋 Requisitos previos (Dependencias requeridas)

- System
- System.IO
- System.Collections.Generic
- System.Linq
- System.Data
- System.Xml.Linq
- Newtonsoft.Json
- Newtonsoft.Json.Linq
- System.Globalization

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
### 🔄 Lógica de Inserción
Consulta SQL con prevención de duplicados:
```sql
@"INSERT INTO ""productos""
(""id_producto"", ""title"", ""price"", ""category"", ""description"")
VALUES (:id_producto, :title, :price::numeric, :category, :description)
ON CONFLICT (id_producto) DO NOTHING"
```

### 2. Configurar variables de entorno  
Editar el archivo `Data/Config.xlsx` con los siguientes valores:  

| Key                   | Value                                                                 |
|:----------------------|:----------------------------------------------------------------------|
| `QueueName`           | Prueba RPA                                                           |
| `ServerAddress`       | `localhost`                                                          |
| `DatabaseName`        | `fakestore`                                                          |
| `UserName`            | `postgres`                                                           |
| `UserPassword`        | `admin1234` *(🔒 contraseña de ejemplo)*                             |
| `UrlAPI`              | [https://fakestoreapi.com/products](https://fakestoreapi.com/products) |
| `UrlFormulario`       | [https://form.jotform.com/250675791629066](https://form.jotform.com/250675791629066) |
| `NombreColaborador`   | `Nicolas Santiago`                                                   |
| `ComentarioGenerico`  | Verificar resultados en la base de datos y el archivo `.json` generado. |


## 📌 Información importante

✔️ **Ubicación de archivos generados**  
   
   - Archivo JSON: `Data\Temp\rawJSON\productos_{FechaActual}.json`
   - Reporte Excel: `Data\Output\Reportes\Reporte_{FechaActual}.xlsx`  


✔️ **Captura de confirmación formulario**  
   📸 `confirmacion_formulario.png` (en `Data\Output\CapturaFormulario`) 
   

✔️ **Formulario Jotform**  
   🔗 [Enlace al formulario](https://form.jotform.com/250675791629066) *(click para acceder)*  

✔️ **Video demostrativo**  
   ▶️ [Ver video en YouTube](https://youtu.be/JoqTRKa-3ls)  *(link actualizado)*



## 🎥 Paso a Paso de ejecución del bot


![step1](https://github.com/user-attachments/assets/a5331b27-4285-415d-b491-d53a3ff40e72)

![step2](https://github.com/user-attachments/assets/e90576bb-8b10-4875-9cc0-dad351312571)

![step3](https://github.com/user-attachments/assets/b3cf30ab-2636-4e42-97f5-021887cab51e)

![step4](https://github.com/user-attachments/assets/4d124bd3-9fed-4d22-bec6-a2b21fefdd9c)

![step5](https://github.com/user-attachments/assets/d1af585a-8910-4fcf-b3c0-ea77e4b061be)

![step6](https://github.com/user-attachments/assets/59ff0f54-6423-4ea7-aa41-7cf593c9a1b6)

![step7](https://github.com/user-attachments/assets/1dddfe18-3a2a-481c-a294-3db1756cde20)

![step8](https://github.com/user-attachments/assets/bb2e607d-6df5-467e-a172-122faf7052cd)

![step9](https://github.com/user-attachments/assets/ce38fe54-dbae-45de-9f10-7119cb47fd99)






