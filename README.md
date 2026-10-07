# TRABAJO-INTEGRADOR-FINAL-DIPLOMATURA-EN-CIENCIA-DE-DATOS-Y-ANALISIS-AVANZADO-UTN
Proyecto Final Integrador – Diplomatura en Ciencia de Datos y Análisis Avanzado (UTN FRBA). Evaluación de la tasa ajustada por riesgo de sepsis posoperatoria en hospitales de California, 2019–2023

# Evaluación de la tasa ajustada por riesgo como indicador de desempeño hospitalario

**Proyecto Final Integrador** · Diplomatura en Ciencia de Datos y Análisis Avanzado  
Universidad Tecnológica Nacional · Facultad Regional Buenos Aires · Módulo 10  
**Autor:** Lisandro Chiavassa · Octubre de 2026

## Pregunta
¿La tasa ajustada por riesgo de sepsis posoperatoria permite comparar hospitales muy distintos de manera suficientemente justa como para decidir dónde auditar?

## Dataset
- **Fuente:** *Postoperative Sepsis Outcomes for Elective Surgeries in California Hospitals*, California Department of Health Care Access and Information (HCAI), California Open Data.
- **Recurso:** Agency for Healthcare Research and Quality Postoperative Sepsis Rates 2019–2023 (CSV).
- **Licencia:** Creative Commons Attribution.
- **Enlace:** https://lab.data.ca.gov/dataset/postoperative-sepsis-outcomes-for-elective-surgeries-in-california-hospitals
- **Tamaño:** 1.475 registros, 10 variables (1.470 observaciones hospital-año de 312 hospitales tras excluir el agregado estatal).

## Archivos
- `01_NOTEBOOK_TRABAJO_INTEGRADOR_UTN_FINAL_COLAB_v12.ipynb`: notebook completo (EDA, índice de persistencia, regresiones, comparativa de modelos, evaluación y cuantificación del valor).

## Cómo ejecutarlo
**En Google Colab**
1. Descargar el CSV desde el enlace oficial y guardarlo como `2019-2023-postoperative-sepsis-rates.csv` en la raíz de Google Drive.
2. Abrir el notebook en Colab y ejecutar **Entorno de ejecución → Ejecutar todo**.
3. Autorizar el acceso a Drive cuando se solicite.

**En forma local**
1. Colocar el CSV en la misma carpeta que el notebook.
2. Instalar dependencias: `pip install pandas numpy matplotlib seaborn scipy scikit-learn xgboost plotly`
3. Ejecutar el notebook completo.

Todas las particiones y modelos usan `random_state=42` para que los resultados sean reproducibles.

## Metodología
CRISP-DM: comprensión del negocio, comprensión y preparación de datos, modelado, evaluación y propuesta de despliegue (modelo de auditoría segmentado).

## Resultados principales
- El volumen quirúrgico, por sí solo, no explica la tasa ajustada (R² en validación cruzada ≈ 0).
- El índice de persistencia separa 40 hospitales con episodios aislados de 5 con un patrón crónico Below Average.
- Comparativa de seis modelos de clasificación: se elige un árbol de decisión balanceado de profundidad 3 (balanced accuracy CV 0,588; azar 0,333).
- En hospitales de bajo volumen, la tasa anual es más inestable: se recomienda una tasa trienal.
