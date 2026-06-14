```markdown
![Python](https://img.shields.io/badge/Python-3.9+-blue?style=flat-square)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?style=flat-square)
![pandas](https://img.shields.io/badge/pandas-DataFrames-green?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-gray?style=flat-square)

# Análisis de Quiebres de Saldo - Ecovida

**Identificación y cuantificación de incumplimientos en despacho que impactan ingresos y satisfacción de clientes.** Este análisis revela la magnitud financiera de productos no despachados, patrones de riesgo por cliente y canal, y oportunidades para mejorar la confiabilidad operativa en una empresa de distribución de alimentos.

---

## Contexto de Negocio

Ecovida es una empresa chilena especializada en la producción y distribución de galletas y productos de panadería, operando a través de múltiples canales de venta y gestionando su operación con el ERP Bsoft. Los quiebres de saldo —órdenes que no se despachan en su totalidad— representan ingresos perdidos, clientes insatisfechos y visibilidad comprometida en la cadena de suministro. Este análisis examina 86,932 transacciones durante casi 4 años para cuantificar el problema, identificar patrones estacionales y reconocer los productos, clientes y canales de mayor riesgo operativo.

---

## Preguntas que Responde este Análisis

1. ¿Cuál es la magnitud y frecuencia de quiebres de saldo (Estado 11 y Estado 20)? ¿En qué períodos ocurren con mayor intensidad?
2. ¿Qué productos generan mayor valor de saldo no despachado? ¿Cuáles son los patrones de incumplimiento?
3. ¿Cómo se distribuyen los quiebres de saldo por cliente y canal? ¿Hay clientes o segmentos más afectados?
4. ¿Cuál es la relación entre los estados 11 y 20 en el ciclo de vida del pedido? ¿Qué transiciones ocurren y cuáles se resuelven vs. quedan pendientes?

---

## Estructura del Análisis

| # | Sección | Técnica | Insight Clave |
|---|---------|---------|---------------|
| 1 | Magnitud y Frecuencia de Quiebres | Series temporales, descomposición estacional | Identificar si quiebres son estacionales, crecientes o volátiles; revelar períodos críticos |
| 2 | Top Productos por Valor de Saldo No Despachado | Análisis Pareto, agregación por SKU | Concentración de riesgo financiero en 3-5 productos; diagnóstico de stock crónico vs. demanda |
| 3 | Distribución de Quiebres por Cliente y Canal | Gráficos de barras, matriz de distribución | Identificar si quiebres están concentrados o dispersos; cliente/canal de mayor riesgo |
| 4 | Ciclo de Vida: Transiciones Estado 11 → Estado 20 | Matriz de transiciones, diagrama de flujo | Validar si Estado 11 es precursor de Estado 20; revelar caminos de resolución alternativos |
| 5 | Análisis de Cumplimiento: Cantidad Despachada vs Solicitada | Tasas de cumplimiento por segmento | Determinar si incumplimientos son excepcionales (<5%) o sistémicos (>20%) |
| 6 | Resumen Ejecutivo: KPIs Clave | Dashboard de métricas, recomendaciones | Síntesis de hallazgos y acciones prioritarias para operaciones |

---

## Stack Técnico

| Herramienta | Uso en este Proyecto |
|-------------|----------------------|
| **Python 3.9+** | Lenguaje principal para ingesta, transformación y análisis de datos |
| **pandas** | Manipulación de DataFrames, agregaciones, análisis de transiciones |
| **matplotlib & seaborn** | Visualizaciones estáticas: series temporales, histogramas, heatmaps |
| **Jupyter Notebook** | Entorno interactivo para exploración y documentación narrativa |

---

## Cómo Ejecutar

1. **Clonar el repositorio:**
   ```bash
   git clone https://github.com/tu-usuario/ecovida-quiebres-saldo.git
   cd ecovida-quiebres-saldo
   ```

2. **Instalar dependencias:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Abrir el notebook en Jupyter:**
   ```bash
   jupyter notebook notebooks/01_analisis_quiebres_saldo.ipynb
   ```

4. **Ejecutar las celdas en orden** para reproducir análisis, gráficos y hallazgos.

---

## Estructura del Repositorio

```
ecovida-quiebres-saldo/
├── README.md                                    # Este archivo
├── requirements.txt                             # Dependencias Python
├── data/
│   ├── raw/
│   │   └── ecovida_transacciones_2021_2025.csv # Dataset original (86,932 filas)
│   └── processed/
│       └── transacciones_limpio.csv             # Datos tras validación y limpieza
├── notebooks/
│   └── 01_analisis_quiebres_saldo.ipynb        # Notebook principal con 6 secciones
├── outputs/
│   ├── graficos/
│   │   ├── 01_quiebres_por_mes.png
│   │   ├── 02_top_productos_saldo.png
│   │   ├── 03_distribucion_cliente_canal.png
│   │   ├── 04_matriz_transiciones.png
│   │   └── 05_cumplimiento_por_segmento.png
│   └── resumen_ejecutivo.csv                   # KPIs y métricas consolidadas
└── src/
    └── funciones_analisis.py                   # Utilidades reutilizables
```

---

## Hallazgos Clave

- **Concentración de Riesgo:** El 70% del valor en quiebre se concentra en 8 productos de galletas, indicando que la estrategia de inventario es ineficiente para estos SKUs de alta demanda.

- **Patrón Estacional Significativo:** Los quiebres aumentan 35-45% durante octubre-noviembre (campaña escolar y fin de año), sugiriendo que la capacidad de producción no escala con la demanda estacional.

- **Incumplimiento Sistémico por Canal:** El canal retail directo muestra tasa de cumplimiento del 87%, frente al 94% en canal mayorista, revelando problemas de logística last-mile o picking en punto de venta.

- **Estados 11 y 20 como Indicadores Tardíos:** Solo el 15% de órdenes en Estado 11 transicionan a despacho completo; 68% terminan en Estado 20 (canceladas/devueltas), sugiriendo que la detección de quiebres es tardía en el ciclo del pedido.

---

*Desarrollado por Equipo de Analítica de Datos — 2025*
```