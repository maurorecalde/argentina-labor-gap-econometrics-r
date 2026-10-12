# Análisis Econométrico de la Brecha Salarial y la Informalidad Laboral en Argentina (2017 - 2025)

Estudio microeconométrico aplicado sobre la Encuesta Permanente de Hogares (EPH - INDEC) para evaluar la estructura de la informalidad laboral en Argentina y su interacción con los retornos educativos en tres cortes transversales: 2017, 2021 y 2025.

---

## 📌 Preguntas de Investigación & Hipótesis

1. **Hipótesis Principal:** La penalización salarial de la informalidad se amplifica de forma no monótona a medida que se incrementa el nivel educativo.
2. **Hipótesis Complementaria 1:** La probabilidad de inserción en el mercado laboral informal se reduce consistentemente a mayor nivel educativo.
3. **Hipótesis Complementaria 2:** La informalidad laboral está concentrada de manera estructural y persistente en ramas específicas de actividad económica.

---

## 🛠️ Metodología y Estrategia Empírica

El análisis se computó considerando el diseño muestral complejo de la EPH mediante el paquete estadístico `survey` en R, ponderando por el factor de expansión de ingresos (`PONDIIO`):

* **Test de Diferencia de Medias Ponderado (Welch t-test - `svyttest`):**
  * Estimado de manera independiente sobre 18 estratos (combinación de 3 períodos temporales y 6 niveles educativos).
  * No asume igualdad de varianzas entre formales e informales, contemplando la dispersión característica de los salarios no regulados.
* **Modelo Econométrico de Ingresos (GLM Ponderado - `svyglm`):**
  * Especificación con interacción multiplicativa entre formalidad y máximo nivel educativo alcanzado.
  * Vector de controles: sexo biológico, edad y edad al cuadrado (aproximación de Mincer al ciclo de vida y rendimientos decrecientes de la experiencia laboral).
  * Ajuste por robustez y varianza en celdas muestrales reducidas.
* **Tests de Independencia Categórica (Chi-Cuadrado Ponderado - `svychisq`):**
  * Nivel educativo vs. Condición de formalidad.
  * Rama de actividad económica (clasificación agregada CAES 14 ramas vía paquete `eph`) vs. Condición de formalidad.

---

## 📊 Principales Hallazgos Empíricos

* **Estructura de la Brecha Salarial Relativa:**
  * La penalización por informalidad es estadísticamente significativa en todas las cohortes ($p < 0.001$).
  * La brecha relativa al ingreso formal se expande desde niveles bajos hasta **Superior Incompleto** (alcanzando entre un 40% y 58% según el año), pero **se comprime al 32% en el tramo Superior Completo**. Este patrón se replica de forma idéntica en 2017, 2021 y 2025.
* **Efecto de la Interacción Educativa Controlada:**
  * El modelo confirma la hipótesis con alta significancia para 2017. En 2021 la relación se mantiene con menor magnitud, mientras que en 2025 los errores estándar reflejan la inestabilidad propia del contexto de alta dispersión nominal y reducción muestral en estratos base.
* **Persistencia Estructural Sectorial:**
  * Fuerte concentración estructural en sectores puntuales: **Servicio Doméstico (73%–80%)** y **Construcción (65%–68%)** se mantienen como focos rígidos de informalidad a lo largo de los 8 años analizados, independientemente del ciclo macroeconómico.

---

## 💻 Stack Tecnológico & Paquetes

* **R Base & RStudio**
* **Librerías principales:**
  * `survey`: Modelado bajo diseño muestral complejo, varianzas robustas y ponderación poblacional.
  * `eph`: Descarga y estandarización de microdatos de la Encuesta Permanente de Hogares (INDEC).
  * `tidyverse` (`dplyr`, `ggplot2`): Manipulación y visualización de datos.

---

## 🚀 Reproducibilidad

1. Clonar el repositorio:
   ```bash
   git clone [https://github.com/maurorecalde/argentina-labor-gap-econometrics-r.git](https://github.com/maurorecalde/argentina-labor-gap-econometrics-r.git)
