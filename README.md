# Clasificación de Fármacos con Regresión Logística

## 📝 Descripción del Proyecto

Este proyecto tiene como objetivo clasificar el tipo de fármaco adecuado para un paciente utilizando un modelo de **Regresión Logística**. Se realiza una comparación exhaustiva de los diferentes algoritmos de optimización (`solvers`) disponibles en la implementación de `LogisticRegression` de Scikit-learn para determinar cuál ofrece el mejor rendimiento en este problema de clasificación multiclase.

---

## 📊 Datos Utilizados

El conjunto de datos utilizado es `drugs.csv`, que contiene información demográfica y médica de 200 pacientes.

- **Características Predictoras:**

  - `Age`: Edad del paciente.
  - `Sex`: Sexo (F/M).
  - `BP`: Nivel de presión arterial (BAJA, NORMAL, ALTA).
  - `Cholesterol`: Nivel de colesterol (NORMAL, ALTO).
  - `Na_to_K`: Proporción de sodio a potasio en sangre.

- **Variable Objetivo:**
  - `Drug`: El tipo de fármaco recomendado (drugA, drugB, drugC, drugX, drugY).

---

## 🛠️ Técnicas y Metodología

El flujo de trabajo del proyecto se desarrolló de la siguiente manera:

### **1. Preprocesamiento de Datos**

- **Codificación de Variables Categóricas:** Las características no numéricas (`Sex`, `BP`, `Cholesterol`) se transformaron a valores numéricos utilizando `LabelEncoder`.

### **2. División del Conjunto de Datos**

- El dataset se dividió en un conjunto de **entrenamiento (80%)** y un conjunto de **prueba (20%)**.

### **3. Modelado y Comparación de Solvers**

Se entrenaron y evaluaron cinco modelos de Regresión Logística, cada uno utilizando un `solver` diferente, para identificar el más eficaz:

1.  `solver='liblinear'`
2.  `solver='lbfgs'`
3.  `solver='newton-cg'`
4.  `solver='sag'`
5.  `solver='saga'`

Para cada modelo, se analizaron su precisión global y su reporte de clasificación detallado.

---

## 📈 Resultados y Comparación

La comparación del rendimiento de cada `solver` en el conjunto de prueba arrojó los siguientes resultados de precisión (accuracy):

| Solver                    | Precisión (Accuracy) | Observaciones                                                    |
| :------------------------ | :------------------: | :--------------------------------------------------------------- |
| `liblinear`               |        0.825         | Rendimiento bajo en `drugC` (0% recall).                         |
| `lbfgs`                   |        0.850         | Mejora general, pero aún bajo rendimiento en `drugC`.            |
| **`newton-cg` (Ganador)** |      **0.950**       | **Rendimiento muy alto y equilibrado en casi todas las clases.** |
| `sag`                     |        0.700         | Rendimiento bajo, especialmente para `drugA` y `drugC`.          |
| `saga`                    |        0.725         | Rendimiento bajo, similar al de `sag`.                           |

## ⭐ Conclusión

Basado en la evaluación de las métricas, el **solver `newton-cg` fue el claro ganador**, logrando la precisión más alta con un **95%**. Este modelo no solo tuvo el mejor desempeño global, sino que también mejoró significativamente la capacidad de predicción para las clases minoritarias, como `drugC`, que los otros solvers no lograron identificar correctamente.

El modelo final con el solver `newton-cg` demostró ser una herramienta robusta y precisa para este problema de clasificación de fármacos.
