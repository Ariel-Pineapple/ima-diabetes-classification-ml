# 🩺 Predicción de Riesgo de Diabetes en la Comunidad Indígena Pima
**Reporte Técnico de Evaluación, Validación e Impacto en el Negocio** *Desarrollado por: Luis Vázquez — Especialista en IA y Soluciones Tecnológicas*

---

## 📋 1. Definición del Problema y Contexto

La diabetes mellitus representa un desafío crítico para los sistemas de salud pública a nivel mundial. En poblaciones con alta vulnerabilidad y predisposición genética, como la comunidad de los Indios Pima, la detección tardía de esta patología incrementa exponencialmente los costos de atención médica y deteriora severamente la calidad de vida de los pacientes debido a complicaciones secundarias (cardiovasculares, renales, oftalmológicas).

**El Reto Clínico:** Las instituciones de salud operan frecuentemente bajo esquemas reactivos. El uso de herramientas predictivas basadas en Inteligencia Artificial permite transicionar hacia un modelo preventivo, identificando de manera automatizada a los pacientes con alto riesgo de desarrollar la enfermedad para priorizar su atención y seguimiento integral.

## 🎯 2. Objetivo SMART del Proyecto

* **Specific (Específico):** Desarrollar un modelo predictivo de clasificación binaria para determinar la presencia o ausencia de diabetes en pacientes femeninas de la comunidad Pima, utilizando variables predictoras médicas (Glucosa, Presión Arterial, IMC, Edad, entre otras).
* **Measurable (Medible):** Lograr que el modelo final obtenga un **AUC-ROC ≥ 0.83** y un **Recall (Sensibilidad) ≥ 85%** en la detección de casos positivos (pacientes con diabetes), minimizando drásticamente los Falsos Negativos.
* **Achievable (Alcanzable):** El objetivo se alcanzará mediante el análisis y preprocesamiento de la base de datos histórica de la UCI (768 instancias), aplicando una validación cruzada estratificada y optimización de umbrales con algoritmos de ensamble (Random Forest).
* **Relevant (Relevante):** Maximizar el *Recall* impacta directamente en la gestión de salud: un Falso Negativo implica un paciente enfermo que se va a casa sin tratamiento. Optimizar esta métrica previene complicaciones graves y reduce los costos operativos por hospitalizaciones de emergencia a largo plazo.
* **Time-bound (Temporal):** El ciclo completo de experimentación, optimización y diseño de la simulación de pruebas A/B se completará en un plazo máximo de **4 semanas**.

---

## 📊 3. Tablero Visual de Resultados y Comparación con Baseline

Para justificar la complejidad técnica del modelo avanzado (**Random Forest**), se estableció una **Regresión Logística** como modelo *Baseline*. A continuación, se presenta la evaluación comparativa en el set de prueba independiente.

### 📉 Comparación de Modelos (Curva ROC)
El modelo avanzado demuestra un poder de discriminación significativamente superior al de la línea base, expandiendo el Área Bajo la Curva ($AUC$) de manera notable.

![Comparación de Modelos](notebooks/comparacion_modelos.png)

### 🎯 Ajuste de Umbral Operativo e Interpretación de la Matriz de Confusión
Operando bajo el umbral estándar de $0.5$, el modelo omitía un volumen peligroso de pacientes enfermas. Al desplazar el umbral probabilístico hacia un enfoque preventivo optimizado, logramos capturar la gran mayoría de los casos positivos, reduciendo los Falsos Negativos a su mínima expresión.

![Matriz de Confusión Optimizada](notebooks/matriz_confusion_optima.png)

### 🔍 Interpretación de los Cuadrantes Clínicos:
* **Verdaderos Positivos (VP):** Pacientes diabéticas correctamente identificadas. Permite iniciar un tratamiento metabólico inmediato.
* **Falsos Positivos (FP):** Pacientes sanas clasificadas en riesgo. El costo asociado es marginal (estudios clínicos de confirmación secundarios), lo cual es totalmente aceptable para el negocio frente al riesgo de omisión.
* **Falsos Negativos (FN):** Pacientes enfermas no detectadas. **El peor escenario clínico y financiero.** Reducido drásticamente gracias al ajuste de umbral.

---

## 🚀 4. Evidencia de Experimentos y Validación Cruzada

Para garantizar la estabilidad del modelo ante fluctuaciones en los datos de entrada y mitigar el riesgo de sobreajuste (*overfitting*), el modelo avanzado fue evaluado mediante **Validación Cruzada Estratificada ($5\text{-}Folds$)** sobre el conjunto de entrenamiento.

| Métrica Evaluada | Media Obtenida (CV) | Desviación Estándar ($\sigma$) | Estado vs. Objetivo SMART |
| :--- | :---: | :---: | :---: |
| **AUC-ROC** | **0.8354** | ± 0.0215 | **Superado** (Meta ≥ 0.83) |
| **Recall (Sensibilidad)** | **0.8620** | ± 0.0340 | **Superado** (Meta ≥ 0.85 con ajuste) |
| **Accuracy (Exactitud)** | 0.7634 | ± 0.0180 | Informativo |

*Nota: La baja desviación estándar ($\le 0.03$) confirma la consistencia y robustez del algoritmo ante diferentes subconjuntos de pacientes.*

---

## 🧪 5. Análisis de Pruebas A/B e Impacto en el Negocio

Para validar la efectividad de la solución antes de su despliegue en producción, se ejecutó una simulación estadística de una **Prueba A/B** con un flujo de 1,000 pacientes de la comunidad:
* **Grupo A (Control - 500 pacientes):** Evaluación asistida por el método tradicional / Baseline.
* **Grupo B (Tratamiento - 500 pacientes):** Evaluación asistida por el Modelo Optimizado de Random Forest.

![Resultados de la Prueba A/B](notebooks/resultado_prueba_ab.png)

### 📈 Validación Estadística (Proportions Z-Test):
* **Estadístico Z:** 4.1524
* **p-valor:** 0.000016
* **Decisión:** Al ser el $p\text{-valor} < 0.05$, **se rechaza categóricamente la Hipótesis Nula ($H_0$)**.

**Justificación de Impacto Financiero y Clínico:** El incremento en la tasa de detección del **60.0% al 86.0%** se traduce en que, de cada 175 pacientes con diabetes real en la muestra, el modelo optimizado rescata a **45 pacientes adicionales** que habrían sido enviadas a casa sin diagnóstico bajo el esquema tradicional. Para una institución como Laboratorios Licon, esto mitiga el costo de tratamientos críticos crónicos a largo plazo y optimiza el retorno de inversión ($ROI$) en infraestructura de medicina preventiva.

---

## 🏁 6. Conclusiones

1. **Cumplimiento de Objetivos:** El proyecto alcanzó con éxito las métricas estipuladas en el objetivo SMART, consolidando un $AUC\text{-}ROC$ de 0.835 y un $Recall$ superior al 85% mediante el ajuste dinámico del umbral de decisión.
2. **Justificación del Enfoque:** La priorización del *Recall* sobre el *Accuracy* o la *Precisión* demostró ser la estrategia matemáticamente correcta para resolver un problema del sector salud, donde la omisión de un diagnóstico conlleva un costo humano y financiero crítico.
3. **Siguientes Pasos:** Se recomienda integrar este script de experimentación en un pipeline formal de MLOps para monitorear la degradación del modelo (*data drift*) a medida que se incorporen nuevos registros clínicos de la región.
