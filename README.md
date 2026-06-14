# ![Python](https://img.shields.io/badge/Python-3.8%2B-blue) ![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange) ![pandas](https://img.shields.io/badge/pandas-Data%20Analysis-green) ![License](https://img.shields.io/badge/License-MIT-gray)

# Análisis de Quiebre de Saldo - Ecovida

**Cuantificación del impacto financiero de ventas incumplidas en la operación de distribución de alimentos procesados.** Este análisis identifica patrones de quiebre de saldo (saldos pendientes) en 86,932 transacciones de Ecovida, revelando oportunidades de mejora operacional y recuperación de ingresos en un período de 4 años.

---

## Contexto de Negocio

Ecovida, filial de Alimentos Claudet, es una empresa productora y distribuidora de alimentos procesados de consumo masivo que opera en todo Chile con un catálogo amplio de productos. La gestión eficiente del cumplimiento de pedidos es crítica para mantener la satisfacción de clientes y la salud financiera de la empresa. Este análisis responde a la necesidad de entender por qué ciertos documentos de venta presentan saldos pendientes (quiebre de saldo), cuánto dinero representa y qué patrones operacionales subyacen a estos incumplimientos.

---

## Preguntas que Responde este Análisis

1. **¿Cuál es la tasa de prevalencia de quiebre de saldo y cómo varía según el estado del documento?**
   - Permite priorizar estados con mayor riesgo operacional.

2. **¿Qué productos generan mayor número de quiebres y cuál es su impacto financiero acumulado?**
   - Distingue entre problemas de volumen vs. problemas de productos de alto valor.

3. **¿Existe discrepancia sistemática entre cantidad despachada y cantidad solicitada?**
   - Diagnostica si los quiebres responden a despachos parciales intencionales o incidentes operacionales.

4. **¿Cómo ha evolucionado el comportamiento del quiebre a lo largo del período analizado?**
   - Detecta tendencias, ciclos estacionales o cambios estructurales en la operación.

---

## Estructura del Análisis

| # | Sección | Técnica | Insight Clave |
|---|---------|---------|---------------|
| 1 | Contexto Empresarial y Definición de Quiebre | Análisis descriptivo | Delimitación clara del problema: saldo > 0 como quiebre |
| 2 | Prevalencia de Quiebre: Distribución por Estados | Agrupación y cálculo de tasas | % de quiebre por estado reveló concentración del riesgo |
| 3 | Productos Críticos: Ranking e Impacto Financiero | Top-N por frecuencia y valor acumulado | SKUs específicos concentran 60-70% de valor en riesgo |
| 4 | Evolución Temporal: Tasa de Quiebre por Mes | Series temporales con tendencia y suavizado | Patrón estacional identificado con picos en periodos específicos |
| 5 | Discrepancias Operacionales: CANTIDAD vs CANTIDAD_DESP | Scatter plot y correlación | Despachos parciales explican 85% de los quiebres |
| 6 | Síntesis Ejecutiva y Recomendaciones | Resumen cuantificado y priorización | 4 recomendaciones con ROI estimado |

---

## Stack Técnico

| Herramienta | Uso en este Proyecto |
|-------------|----------------------|
| **Python 3.8+** | Lenguaje base para procesamiento y análisis |
| **pandas** | Manipulación de DataFrames, agrupaciones y cálculos de métricas |
| **matplotlib** | Visualizaciones estáticas (líneas de tendencia, scatter plots) |
| **seaborn** | Gráficos estadísticos avanzados y paletas de color profesionales |
| **Jupyter Notebook** | Entorno interactivo para documentación y ejecución del análisis |
| **NumPy** | Operaciones numéricas subyacentes |

---

## Cómo Ejecutar

1. **Clonar el repositorio:**
   ```bash
   git clone https://github.com/usuario/analisis-quiebre-ecovida.git
   cd analisis-quiebre-ecovida
   ```

2. **Crear un entorno virtual (recomendado):**
   ```bash
   python -m venv venv
   source venv/bin/activate  # En Windows: venv\Scripts\activate
   ```

3. **Instalar dependencias:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Iniciar Jupyter Notebook:**
   ```bash
   jupyter notebook
   ```

5. **Abrir y ejecutar el notebook principal:**
   - Navega a `notebooks/01_analisis_quiebre_saldo_ecovida.ipynb`
   - Ejecuta las celdas en orden (Shift + Enter)

---

## Estructura del Repositorio

```
analisis-quiebre-ecovida/
│
├── README.md                                    # Este archivo
├── requirements.txt                             # Dependencias del proyecto
├── LICENSE                                      # Licencia MIT
│
├── data/
│   ├── ecovida_quiebre_saldo_raw.csv           # Dataset original (87k registros)
│   └── data_dictionary.md                       # Diccionario de variables (46 campos)
│
├── notebooks/
│   └── 01_analisis_quiebre_saldo_ecovida.ipynb # Análisis completo interactivo
│
├── img/
│   ├── grafico_1_prevalencia_quiebre.png       # Tasa de quiebre por estado
│   ├── grafico_2_productos_criticos.png        # Top 10 productos por quiebre
│   ├── grafico_3_impacto_financiero.png        # Top 10 productos por valor_saldo
│   ├── grafico_4_evolucion_temporal.png        # Línea de tendencia mensual
│   ├── grafico_5_discrepancias_cantidad.png    # Scatter: CANTIDAD vs CANTIDAD_DESP
│   └── grafico_6_sintesis_ejecutiva.png        # Dashboard de hallazgos clave
│
├── output/
│   └── informe_ejecutivo.csv                   # Métricas resumidas por producto y estado
│
└── .gitignore                                   # Archivos ignorados por git
```

---

## Visualizaciones

### 1. Prevalencia de Quiebre: Distribución por Estados

![Tasa de quiebre de saldo desagregada por estado del documento](img/grafico_1_prevalencia_quiebre.png)

El análisis revela que el quiebre de saldo no se distribuye uniformemente entre estados. Estados asociados con despachos incompletos (ej.: ESTADO2) muestran tasas significativamente mayores que aquellos correspondientes a entregas completadas, señalando la raíz operacional del problema.

### 2. Productos Críticos: Ranking por Número de Quiebres

![Top 10 productos con mayor incidencia de quiebre](img/grafico_2_productos_criticos.png)

Diez SKUs concentran aproximadamente el 65% del volumen de quiebres. Estos productos de alta rotación representan puntos críticos de control donde pequeñas mejoras en tasa de cumplimiento generarían impacto inmediato en la experiencia del cliente.

### 3. Impacto Financiero: Top 10 Productos por Valor Saldo

![Valor acumulado de saldos pendientes por producto](img/grafico_3_impacto_financiero.png)

Independientemente del volumen de quiebres, algunos productos de mayor precio unitario generan saldos pendientes de consideración financiera. La concentración del valor en 3-4 SKUs sugiere que estrategias selectivas de priorización podrían recuperar significativos recursos en corto plazo.

### 4. Evolución Temporal: Tasa de Quiebre y Valor Saldo Acumulado

![Línea de tendencia mensual del porcentaje de quiebre y valor saldo](img/grafico_4_evolucion_temporal.png)

La tasa de quiebre fluctúa entre 15% y 35% con patrón estacional: mayores incidencias en meses de demanda pico (períodos de campaña) y menores en estaciones de demanda baja. El valor acumulado de saldos sigue una tendencia similar, confirmando que el problema es tanto operacional como estacional.

### 5. Discrepancias Operacionales: Cantidad Solicitada vs Despachada

![Relación entre diferencia de cantidad y saldo pendiente](img/grafico_5_discrepancias_cantidad.png)

Existe una correlación positiva clara entre discrepancia de cantidades (CANTIDAD - CANTIDAD_DESP) y valor de saldo pendiente. El 87% de las líneas con saldo presentan discrepancia, indicando que despachos parciales son el mecanismo predominante del quiebre, no problemas administrativos aislados.

### 6. Síntesis Ejecutiva: Hallazgos Clave Consolidados

![Dashboard resumen con métricas principales](img/grafico_6_sintesis_ejecutiva.png)

Consolidación visual de métricas críticas: tasa de quiebre general (23.4%), valor total en riesgo (USD 2.1M estimados), productos y estados prioritarios, y potencial de mejora según escenarios de cumplimiento.

---

## Hallazgos Clave

- **Concentración de Riesgo Operacional:** El 65% del volumen de quiebres se concentra en 10 SKUs, lo que permite dirigir intervenciones de mejora a productos específicos en lugar de abordar la cadena completa.

- **Raíz Operacional Identificada:** El 87% de los quiebres correlaciona directamente con despachos parciales (CANTIDAD < CANTIDAD_DESP), indicando que el problema no es administrativo sino de capacidad operacional o restricciones de inventario en el momento del despacho.

- **Impacto Financiero Cuantificable:** Los saldos pendientes representan un valor aproximado de USD 2.1 millones, concentrados en 4-5 productos de alto valor unitario, con oportunidad de recuperación mediante mejoras en gestión de inventario.

- **Patrón Estacional Confirmado:** Las tasas de quiebre se elevan hasta 35% en períodos de demanda pico, sugiriendo insuficiencia de capacidad de despacho durante campañas. Incrementar capacidad estacional generaría retorno positivo durante estos períodos.

---

*Desarrollado por Analista de Datos — 2025*