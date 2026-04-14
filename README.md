# Landing Page A/B Test — Conversion & Revenue Analysis

## Descripción del proyecto

Análisis estadístico de un experimento A/B realizado en la página de inicio (landing page) de una empresa de ecommerce. El proyecto evaluó dos versiones de la página (A y B) comparando tasa de conversión, gasto promedio por usuario convertido, comportamiento por canal de tráfico y perfil de usuario. El objetivo fue identificar qué versión genera mayor valor económico y traducir los hallazgos en recomendaciones accionables para el equipo de marketing digital.

---

## Objetivo del análisis

Determinar con evidencia estadística sólida cuál versión de la landing page debe implementarse de forma definitiva, evaluando su impacto en conversión y revenue, y segmentando el comportamiento por fuente de tráfico y tipo de usuario.

---

## Dataset utilizado

| Archivo | Filas | Columnas | Descripción |
|---|---|---|---|
| `landing_experiment.csv` | 40,000 | 9 | Registro de usuarios expuestos al experimento A/B, incluyendo versión de página, región, dispositivo, fuente de tráfico, tipo de usuario, conversión y gasto |

**Variables clave:**

| Columna | Tipo | Descripción |
|---|---|---|
| `user_id` | Categórica | Identificador único del usuario |
| `date` | Fecha | Fecha de exposición a la página |
| `landing` | Categórica | Versión de página: A (control) o B (prueba) |
| `region` | Categórica | Región geográfica del usuario |
| `dispositivo` | Categórica | Mobile o Desktop |
| `traffic_source` | Categórica | Organic, Ads, Email, Referral |
| `user_type` | Categórica | Nuevo o Recurrente |
| `converted` | Binaria | 1 = convirtió, 0 = no convirtió |
| `gasto` | Numérica | Monto gastado (0 si no convirtió) |

---

## Stack y herramientas

- **Lenguaje:** Python 3
- **Entorno:** Google Colab / Jupyter Notebook
- **Librerías:** Pandas, NumPy, Matplotlib, Seaborn, SciPy, Statsmodels

---

## Pruebas estadísticas aplicadas

| Pregunta de negocio | Prueba | p-value | Decisión |
|---|---|---|---|
| ¿El gasto promedio difiere entre A y B? | Prueba t de Student + Levene | 1.06e-20 | ✅ Rechaza H₀ |
| ¿La tasa de conversión difiere entre A y B? | Prueba Z de proporciones | 3.76e-22 | ✅ Rechaza H₀ |
| ¿La conversión depende de la fuente de tráfico? | Chi-cuadrada de independencia | 0.034 | ⚠️ Rechaza H₀ (relevancia práctica limitada) |
| ¿La conversión depende del tipo de usuario? | Chi-cuadrada de independencia | 0.474 | ❌ No rechaza H₀ |

---

## Etapas del análisis

1. **Exploración y validación de datos** — revisión de estructura, tipos de datos, duplicados, nulos, rango temporal y distribución de variables categóricas
2. **Comparación de gasto promedio (A vs B)** — prueba t de Student con verificación de varianzas mediante prueba de Levene
3. **Comparación de tasa de conversión (A vs B)** — prueba Z de proporciones con cálculo de tasas por versión
4. **Análisis de conversión por fuente de tráfico** — tabla de contingencia, verificación de supuestos y prueba Chi-cuadrada
5. **Análisis de conversión por tipo de usuario** — tabla de contingencia, verificación de supuestos y prueba Chi-cuadrada
6. **Visualización de resultados** — gráficos de barras agrupadas y apiladas para respaldar conclusiones estadísticas
7. **Insight ejecutivo** — síntesis de hallazgos con recomendaciones accionables para stakeholders no técnicos

---

## Resultados clave

| Métrica | Página A | Página B | Diferencia |
|---|---|---|---|
| Tasa de conversión | 12.57% | 15.96% | +3.38pp |
| Gasto promedio (convertidos) | $61.09 | $68.75 | +$7.66 |
| Usuarios convertidos | 2,512 | 3,194 | +682 |

---

## Hallazgos principales

- **Página B supera a A en ambas métricas clave:** mayor tasa de conversión (+3.38pp) y mayor gasto promedio por usuario convertido (+$7.66), con evidencia estadística contundente en ambos casos (p-values prácticamente cero).
- **Canal Email lidera en conversión:** con 14.99% frente al 13.79% de Organic. Sin embargo, la diferencia máxima entre canales es de apenas 1.2pp — estadísticamente significativa pero de relevancia práctica limitada.
- **El tipo de usuario no influye en la conversión:** usuarios Nuevos (14.36%) y Recurrentes (14.09%) muestran comportamiento prácticamente idéntico — no hay evidencia para segmentar estrategias por este criterio.
- **Experimento bien diseñado:** 40,000 usuarios, 28 días de duración, distribución balanceada 50/50 entre versiones y todos los supuestos estadísticos verificados.

---

## Recomendaciones de negocio

1. **Implementar página B globalmente** — la evidencia estadística en gasto promedio y tasa de conversión es sólida y consistente en ambas métricas.
2. **Priorizar inversión en canal Email** — liderazgo en tasa de conversión justifica explorar mayor inversión, evaluando previamente el costo de adquisición por canal.
3. **No segmentar por tipo de usuario** — los datos no respaldan diferencias reales en conversión entre usuarios nuevos y recurrentes; los recursos destinados a estrategias diferenciadas por este criterio no están justificados.

---

## Cómo reproducir el análisis

1. Clonar este repositorio:
   ```bash
   git clone https://github.com/gerardovazquez-DataAnalyst/ab-testing-landing-page.git
   ```
2. Abrir el notebook en Google Colab o Jupyter:
   - Desde Colab: `Archivo → Abrir notebook → GitHub` y pegar la URL del repo
   - Desde Jupyter: ejecutar `jupyter notebook` en la carpeta del proyecto
3. Verificar que `landing_experiment.csv` esté en la misma ruta que el notebook (o ajustar el `pd.read_csv()` según corresponda)
4. Ejecutar las celdas en orden secuencial

---

## Estructura del repositorio

```
ab-testing-landing-page/
│
├── Análisis_AB.ipynb            # Notebook principal con todo el análisis
├── landing_experiment.csv       # Dataset del experimento A/B
└── README.md                    # Este archivo
```

---

## Autor

**Gerardo Vázquez Cruz**  
Data Analyst  
[GitHub](https://github.com/gerardovazquez-DataAnalyst) · [LinkedIn](https://linkedin.com/in/gerardo-vazquez-dataanalyst)
