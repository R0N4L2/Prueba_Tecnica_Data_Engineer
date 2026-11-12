# Prueba técnica Data Engineer — Pipeline de ventas y API REST

**En una frase:** un flujo completo de ingeniería de datos: toma un CSV de ventas con datos sucios, lo limpia, calcula métricas, detecta anomalías, lo guarda en una base SQLite y lo expone mediante una API REST.

*(Solución al reto técnico para una vacante de Data Engineer en Global Mobility Apex.)*

## Qué hace
1. **Limpieza:** cantidades faltantes → 0; precios inválidos → mediana del grupo; cálculo de `total_sales`, día de la semana y marca de "alto volumen".
2. **Métricas por categoría:** precio promedio, ingreso total y día de mayor venta.
3. **Outliers:** transacciones con cantidad a más de 2 desviaciones estándar de la media de su categoría.
4. **Almacenamiento:** SQLite con tres tablas (transacciones, métricas, outliers).
5. **API (FastAPI):**
   - `GET /sales/product` — ventas por producto (filtros por producto/categoría)
   - `GET /sales/day` — ventas por día (filtro por rango de fechas)
   - `GET /sales/category` — métricas por categoría
   - `GET /sales/outliers` — transacciones atípicas

## Archivos
- `challenge.ipynb` — solución completa (procesamiento + servidor de la API).
- `sales_dashboard.db` — base SQLite generada.

## Tecnologías
Python · pandas · NumPy · SQLite · FastAPI · Uvicorn

## Ejecutar
```bash
pip install pandas numpy fastapi uvicorn nest_asyncio
```
Abrir `challenge.ipynb`, ejecutar todas las celdas; la API queda en `http://localhost:8000`.
