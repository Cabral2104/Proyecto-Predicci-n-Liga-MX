# Liga MX: Predicción de Campeón con Machine Learning

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![Libraries](https://img.shields.io/badge/Library-Scikit--Learn%20%7C%20Pandas%20%7C%20Seaborn-green)
![Status](https://img.shields.io/badge/Status-Completed-success)

Este proyecto utiliza técnicas avanzadas de **Ciencia de Datos** y **Machine Learning** para predecir al campeón de la **Liga MX (Clausura 2026)**. A diferencia de las predicciones simples, este modelo simula el torneo completo (Fase Regular + Liguilla) 100 veces para obtener probabilidades estadísticas de éxito.

## ¿Cómo funciona?

El proyecto sigue un pipeline de datos estructurado en 4 fases:

### 1. Recolección y Limpieza de Datos
- **Fuente:** Datos históricos de `football-data.co.uk` (Temporadas 2016 - Presente).
- **Procesamiento:** Limpieza de fechas, estandarización de equipos y filtrado de datos corruptos.

### 2. Ingeniería de Características (Feature Engineering)
Para entrenar a la IA, transformamos los datos crudos en métricas de rendimiento deportivo:
- **Racha Reciente (U5):** Promedio de puntos y diferencia de goles en los últimos 5 partidos (Rolling Windows).
- **Factor de Jerarquía:** Un algoritmo personalizado que asigna un "peso histórico" a los equipos (Gigantes vs Modestos) basado en su desempeño de los últimos 2 años, corrigiendo sesgos de recencia.
- **Sabiduría del Mercado:** Incorporación de momios históricos de casas de apuestas como variable predictora.

### 3. Modelado (Random Forest)
Se entrenó un clasificador **Random Forest** (que superó a XGBoost en las pruebas de estabilidad) para predecir la probabilidad de victoria (Local/Empate/Visita) de cualquier enfrentamiento.
- **Accuracy del Modelo:** ~53% (Superando el azar del 33%).

### 4. Simulador Monte Carlo
El "Oráculo" no predice el futuro una vez, sino que simula múltiples escenarios:
1.  Genera el calendario restante "Todos contra Todos".
2.  Simula la **Fase Regular** 50 veces para definir la Tabla General.
3.  Simula la **Liguilla (Cuartos, Semis, Final)** con partidos de Ida y Vuelta 100 veces.
4.  Calcula la probabilidad porcentual de campeonato para cada equipo.

## Resultados Destacados

El modelo logró identificar correctamente la jerarquía de la liga, colocando a equipos como **América, Cruz Azul y Toluca** como los máximos contendientes, eliminando el ruido estadístico de equipos con rachas de suerte temporal.

*(Puedes ver las gráficas y las tablas de probabilidad detalladas dentro del Notebook).*

## 🛠️ Tecnologías Usadas
- **Python:** Lenguaje principal.
- **Pandas/Numpy:** Manipulación de datos y álgebra lineal.
- **Scikit-Learn:** Entrenamiento del modelo (Random Forest).
- **Seaborn/Matplotlib:** Visualización de datos (Mapas de calor y Gráficas de barras).

## Cómo ejecutarlo
1.  Abre el archivo `.ipynb` en este repositorio.
2.  Haz clic en el botón **"Open in Colab"** o descárgalo para correrlo en tu entorno local.
3.  Ejecuta las celdas secuencialmente para ver la simulación en tiempo real.

---
*Disclaimer: Este proyecto es un ejercicio académico de Ciencia de Datos y Probabilidad. El fútbol es dinámico y los resultados reales pueden variar.*
