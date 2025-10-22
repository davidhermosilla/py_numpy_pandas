# Análisis de la red de tiendas RetailNow

Este repositorio contiene el proyecto del máster dedicado a la cadena ficticia RetailNow. El objetivo principal es analizar ventas, inventarios y satisfacción de clientes utilizando Python, Pandas y NumPy dentro de un notebook de Jupyter.

## Estructura
- `py_numpy_pandas/analisis_red_tiendas.ipynb`: notebook principal con todo el análisis.
- `data/input/*.csv`: archivos de datos (`sales`, `inventories`, `satisfaction`).
- `docs/index.md`: documentación del proyecto.
- `requirements.txt`: dependencias de Python para reproducir el entorno.

## Requisitos y configuración
1. Instala dependencias: `python -m pip install -r requirements.txt`.
2. Abre el notebook en Visual Studio Code con el plugin de Jupyter.
3. Asegúrate de que las rutas absolutas a los CSV correspondan al entorno donde se ejecuta el notebook (se usa `/workspace/...` por defecto).

## Contenido del notebook
- Limpieza de datos (`dropna`) y verificación de estructura de DataFrames.
- Análisis de ventas: totales por tienda y producto, unidades vendidas, ingresos y estadísticas descriptivas.
- Inventarios: rotación basada en unidades vendidas y detección de inventarios críticos (<10% del stock).
- Satisfacción: cruce con ingresos y filtrado de tiendas con evaluación <60%.
- NumPy: cálculo de mediana y desviación estándar de ingresos, y simulación de proyecciones con semilla definida.

## Próximos pasos sugeridos
- Incluir visualizaciones interactivas o dashboards.
- Automatizar la actualización de los datos y el reporte en pipelines.
- Integrar pruebas sobre la consistencia de los datos y scripts de soporte.
