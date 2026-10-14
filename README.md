# Predicción del rendimiento académico con WEKA

Proyecto de Asignatura de **MINERIA DE DATOS I (CLASE 2568)**
Fundación Universitaria Tecnológico Comfenalco (Cartagena).

## Objetivo
Construir modelos de clasificación en WEKA que predigan si un estudiante de
secundaria aprobará o reprobará una asignatura, a partir de sus
características personales, familiares y escolares.

## Estado del proyecto
- [x] Selección del dataset y definición del problema
- [x] Propuesta del modelo predictivo
- [x] Informe metodológico
- [x] Repositorio del prototipo y datos preparados (ARFF)
- [ ] Entrenamiento de modelos en WEKA
- [ ] Evaluación, comparación de modelos y conclusiones

## Dataset
**Student Performance** (UCI Machine Learning Repository, Cortez y Silva, 2008).
Fuente: https://archive.ics.uci.edu/dataset/320/student+performance

Se trabaja únicamente con `student-mat.csv` (asignatura de Matemáticas):
- 395 instancias y 33 atributos originales (demográficos, familiares, escolares y notas G1, G2, G3).
- Sin valores faltantes ni filas duplicadas.
- Separador de campos: punto y coma (;).

## Variable objetivo
`aprobado`, derivada de la nota final G3 (escala 0 a 20):
- **1** (aprobado): G3 mayor o igual a 10
- **0** (reprobado): G3 menor a 10

Balance de clases: 265 aprobados (67,1 %) y 130 reprobados (32,9 %).

## Preparación de los datos
Se excluyen las notas G1 y G2 (y G3, que da origen a la clase), porque su fuerte
relación con la nota final dominaría el modelo y lo haría poco útil para detectar
estudiantes en riesgo a tiempo. El resultado es `data/student-mat.arff`, con 31
atributos (30 predictores y la clase `aprobado`).

## Metodología
Se sigue CRISP-DM: comprensión del problema, comprensión de los datos,
preparación, modelado, evaluación y despliegue.

Algoritmos propuestos en WEKA: J48, Naive Bayes y Random Forest.
Validación: validación cruzada estratificada de 10 pliegues.
Métricas: exactitud, precisión, recall, F-measure, matriz de confusión, Kappa y AUC.

## Estructura del repositorio
```
README.md                Descripción del proyecto
student-mat.csv          Dataset original (asignatura de Matemáticas)
student.txt              Descripción de los atributos del dataset
student-mat.arff         Datos preparados para WEKA (sin G1 ni G2)
Propuesta_Modelo_Predictivo   Propuesta del modelo predictivo
Informe_Metodologico          Informe metodológico
```

## Cómo reproducir
1. Descargar el dataset desde el enlace de la sección Dataset.
2. Abrir WEKA Explorer y cargar `data/student-mat.arff` (la clase `aprobado` es el último atributo).
3. Ejecutar los clasificadores con validación cruzada de 10 pliegues.

## Referencias
- Cortez, P., y Silva, A. (2008). Using data mining to predict secondary school
  student performance. FUBUTEC 2008, pp. 5-12.
- Chapman, P., et al. (2000). CRISP-DM 1.0: Step-by-step data mining guide. SPSS Inc.

## Integrantes
- Victor Manuel Rocha Ramos


