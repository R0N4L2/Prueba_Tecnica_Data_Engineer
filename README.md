A continuación te presento un ejemplo de README para el repositorio en GitHub:

---

# Prueba Técnica Data Engineer - Global Mobility Apex

Este repositorio contiene la solución al challenge propuesto para la vacante de Data Engineer en Global Mobility Apex. La solución se implementa en un Jupyter Notebook que incluye:

- **Procesamiento y limpieza de datos:** Ingesta y transformación del archivo CSV con datos de ventas, manejo de valores faltantes y errores.
- **Transformaciones y métricas agregadas:** Cálculo de total de ventas, creación de columnas derivadas (día de la semana, flag de alto volumen) y agrupación por categoría para obtener métricas (precio promedio, ingreso total, día con mayor ventas).
- **Detección de outliers:** Identificación de transacciones con cantidad mayor a 2 desviaciones estándar de la media en cada categoría.
- **Almacenamiento en SQLite:** Los datos procesados se guardan en una base de datos SQLite en tres tablas: transacciones, métricas agregadas y outliers.
- **Backend API RESTful:** Un API desarrollado con FastAPI que expone endpoints para consultar las ventas por producto, por día, las métricas agregadas por categoría y los outliers identificados.

## Estructura del Repositorio

```
├── notebook.ipynb           # Jupyter Notebook con la solución completa
├── sales_dashboard.db       # Base de datos SQLite generada (opcional, puede estar en .gitignore)
└── README.md                # Este archivo
```

## Requisitos

Asegúrate de tener instaladas las siguientes librerías:

- [pandas](https://pandas.pydata.org/)
- [numpy](https://numpy.org/)
- [fastapi](https://fastapi.tiangolo.com/)
- [uvicorn](https://www.uvicorn.org/)
- [nest_asyncio](https://pypi.org/project/nest_asyncio/)

Puedes instalarlas ejecutando:

```bash
pip install pandas numpy fastapi uvicorn nest_asyncio
```

## Uso

1. **Abrir el Notebook:**
   - Abre el archivo `notebook.ipynb` en Jupyter Notebook.
   - Ejecuta todas las celdas secuencialmente para procesar el CSV, transformar los datos y almacenar la base de datos.

2. **Ejecutar el API:**
   - En la última celda del Notebook se encuentra el código para iniciar el servidor FastAPI usando Uvicorn. 
   - Gracias a `nest_asyncio`, el servidor se ejecuta sin conflictos en el entorno de Jupyter.
   - Una vez iniciado, el API estará disponible en `http://localhost:8000`.

3. **Probar los endpoints:**
   - `GET /sales/product`: Retorna el total de ventas por producto. Se puede filtrar por nombre de producto o categoría.
   - `GET /sales/day`: Retorna el total de ventas por día, con opción de filtrar por rango de fechas.
   - `GET /sales/category`: Retorna las métricas agregadas por categoría.
   - `GET /sales/outliers`: Retorna las transacciones marcadas como outliers.

   Puedes probar estos endpoints utilizando tu navegador, cURL o Postman.

## Descripción del Challenge

El challenge consiste en desarrollar una aplicación de dashboard de ventas con los siguientes requerimientos:

- **Data Cleaning:** Reemplazar valores faltantes en `quantity` por 0, convertir valores inválidos en `price` usando la mediana del grupo, calcular `total_sales`, generar la columna `day_of_week` y marcar transacciones de alto volumen (`high_volume`).
- **Agregación y Análisis:** Agrupar los datos por categoría para calcular el precio promedio, total de ingresos y el día con mayor ventas. Además, se detectan outliers basados en la cantidad.
- **Almacenamiento:** Los datos se almacenan en una base de datos SQLite en tres tablas: transacciones, métricas agregadas y outliers.
- **Backend API:** Se desarrolla un API RESTful para exponer la información procesada y permitir consultas sobre las ventas y métricas.

## Notas

- La solución está desarrollada en Python y se ejecuta completamente en un entorno Jupyter Notebook.
- La base de datos SQLite generada (`sales_dashboard.db`) contiene los datos procesados y puede ser consultada directamente o a través del API.

## Contacto

Si tienes alguna consulta o comentario sobre esta solución, no dudes en contactarme.

---

Este README proporciona una visión completa del proyecto y te ayudará a explicar la solución en tu repositorio de GitHub.
