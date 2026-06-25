# 🩺 Predicción de Riesgo de Diabetes en la Comunidad Indígena Pima

Este repositorio contiene el desarrollo de extremo a extremo de un modelo de aprendizaje automático diseñado para la clasificación y detección temprana de diabetes utilizando variables clínicas y metabólicas.

## 📋 Definición del Problema y Contexto

La diabetes mellitus representa un desafío crítico para los sistemas de salud pública a nivel mundial. En poblaciones con alta vulnerabilidad y predisposición genética, como la comunidad de los Indios Pima, la detección tardía de esta patología incrementa exponencialmente los costos de atención médica y deteriora severamente la calidad de vida de los pacientes debido a complicaciones secundarias (cardiovasculares, renales, oftalmológicas).

**El Reto Clínico:** Las instituciones de salud operan frecuentemente bajo esquemas reactivos. El uso de herramientas predictivas basadas en Inteligencia Artificial permite transicionar hacia un modelo preventivo, identificando de manera automatizada a los pacientes con alto riesgo de desarrollar la enfermedad para priorizar su atención y seguimiento integral.

## 🎯 Objetivo SMART del Proyecto

* **Specific (Específico):** Desarrollar un modelo predictivo de clasificación binaria para determinar la presencia o ausencia de diabetes en pacientes femeninas de la comunidad Pima, utilizando variables predictoras médicas (Glucosa, Presión Arterial, IMC, Edad, entre otras).
* **Measurable (Medible):** Lograr que el modelo final obtenga un **AUC-ROC ≥ 0.83** y un **Recall (Sensibilidad) ≥ 85%** en la detección de casos positivos (pacientes con diabetes), minimizando drásticamente los Falsos Negativos.
* **Achievable (Alcanzable):** El objetivo se alcanzará mediante el análisis y preprocesamiento de la base de datos histórica de la UCI (768 instancias), implementando validación cruzada estratégica y optimización de umbrales con algoritmos de ensamble como Random Forest o XGBoost.
* **Relevant (Relevante):** Maximizar el *Recall* impacta directamente en la gestión de salud: un Falso Negativo implica un paciente enfermo que se va a casa sin tratamiento. Optimizar esta métrica previene complicaciones graves y reduce los costos operativos por hospitalizaciones de emergencia a largo plazo.
* **Time-bound (Temporal):** El ciclo completo de experimentación, optimización y diseño de la simulación de pruebas A/B se completará en un plazo máximo de **4 semanas**.

---
*Nota: Este proyecto forma parte del Reporte Técnico de Evaluación y Validación de Modelos.*
