# RetailNow Store Network Analysis

## Proyecto
- Objetivo: analizar ventas, inventarios y satisfacción de clientes para la cadena ficticia RetailNow.
- Entorno: notebook `py_numpy_pandas/analisis_red_tiendas.ipynb` ejecutado en Visual Studio Code con el complemento de Jupyter.
- Lenguaje y librerías: Python 3.12, Pandas, NumPy y pathlib para rutas absolutas.

## Preparación del entorno
- Requisitos: `python3 -m pip install pandas numpy jupyter`.
- Ejecuta `code -r py_numpy_pandas/analisis_red_tiendas.ipynb` o abre el notebook desde VS Code > Jupyter.
- Asegúrate de que los CSV estén disponibles mediante rutas absolutas (`/workspace/sales.csv`, `/workspace/inventories.csv`, `/workspace/satisfaction.csv`). En este repositorio los archivos fuente se encuentran en `data/input` por si necesitas copiarlos.

## Fuentes de datos
- `sales.csv`: `ID_Tienda`, `Producto`, `Cantidad_Vendida`, `Precio_Unitario`, `Fecha_Venta`.
- `inventories.csv`: `ID_Tienda`, `Producto`, `Stock_Disponible`, `Fecha_Actualización`.
- `satisfaction.csv`: `ID_Tienda`, `Satisfacción_Promedio`, `Fecha_Evaluación`.
- Cada archivo se carga con `pd.read_csv(...).dropna()` para eliminar registros incompletos antes del análisis.

## Flujo de análisis en el notebook
- **Preparación**: conversión de columnas numéricas, creación de `ventas_totales` (ingresos por transacción) y agregados básicos.
- **Ventas**:
  - Totales por tienda y producto (`groupby(['ID_Tienda', 'Producto'])`).
  - Totales por tienda (`groupby('ID_Tienda')`) y descritos con `.describe()`.
  - Métricas adicionales de unidades vendidas (tablas `unidades_tienda_producto`, `unidades_por_tienda`, `unidades_por_producto`).
- **Inventarios**:
  - Unión `inventarios` + `unidades_tienda_producto` para obtener rotación en unidades.
  - Cálculo de `rotacion_inventario` y `porcentaje_vendido`; filtrado de `inventario_critico` (<10%).
- **Satisfacción**:
  - Cruce de ingresos con `satisfaccion` para identificar tiendas bajo 60%.
  - Tabla `tiendas_baja_satisfaccion` como punto de partida para recomendaciones.
- **NumPy**:
  - Conversión de ingresos a `ndarray` (`ventas_totales_tienda`) y cálculo de `np.median` y `np.std(ddof=1)`.
  - Simulación `np.random.normal` (12 periodos) para proyecciones con semilla 42 y resumen estadístico.
- **Conclusiones**: sección final del notebook resume riesgos de inventario y satisfacción, y sugiere líneas de acción.

## Cómo ejecutar y revisar resultados
- Ejecuta todas las celdas en orden (`Run All`) después de confirmar las rutas absolutas.
- Revisa las salidas tabulares para:
  - Ventas/inventarios por tienda.
  - `inventario_critico` y `tiendas_baja_satisfaccion`.
  - Estadísticos NumPy (`mediana_np`, `desviacion_np`) y `resumen_proyecciones`.

## Próximos pasos sugeridos
- Añadir visualizaciones (por ejemplo, barras de ventas por tienda o heatmaps de rotación).
- Exportar tablas clave a CSV o dashboards para reportes gerenciales.
- Automatizar actualizaciones con nuevas fechas de ventas mediante pipelines o scripts adicionales.
