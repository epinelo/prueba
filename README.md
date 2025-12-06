## Analisis Dentix

Repositorio con el análisis de datos y modelos desarrollados para Dentix (Colombia). Contiene limpieza y preparación de datos, análisis descriptivo (univariado y bivariado), selección de variables, modelado para predicción de mora y modelado para estimar monto de desembolso, además de los reportes técnicos y ejecutivos.

Estructura general

Las carpetas principales y archivos relevantes:

Códigos/ — Scripts en R (y algunos en Python) para limpieza, análisis, selección de variables y modelado.

Correlaciones/ — Matrices y gráficas de correlación (Pearson, Eta, V de Cramér).

Univariado Numéricas/ — Gráficos y tablas descriptivas para variables numéricas.

Univariado Categóricas/ — Gráficos y tablas para variables categóricas.

LICENSE — Archivo de licencia (MIT).

HojaDeInstruccionesDentix.pdf — Alcance y requerimientos del proyecto.

ReporteCompleto.pdf — Documento técnico con detalles del análisis y modelos.

ReporteResumido.pdf — Resumen ejecutivo con hallazgos y recomendaciones.

Objetivos

Identificar variables que expliquen la probabilidad de mora y el monto aprobado.

Construir un score predictivo para clasificar franjas de mora.

Desarrollar un modelo para estimar monto de desembolso según el perfil del cliente.

Resumen del dataset

Observaciones: ~46,329 registros (datos anonimizados).

Variables: mezcla de numéricas (ingresos, activos, pasivos, monto, cuota, días de mora, score, etc.) y categóricas (región, clínica, nivel de estudios, estado civil, ocupación, tipo de vivienda, etc.).

Características relevantes: variables con concentración de ceros, desbalance en la variable objetivo (mora_franja) y presencia de outliers en variables financieras.

Metodología (pasos principales)

Preprocesamiento

Limpieza de NAs según criterio por variable.

Transformaciones (por ejemplo log) en variables con sesgo.

Creación de variables binarias para manejar zero-inflation.

Detección y tratamiento de outliers según reglas estadísticas y de negocio.

Análisis exploratorio

Estadísticas univariadas por tipo de variable.

Análisis bivariado: correlaciones, pruebas Kruskal-Wallis y chi-cuadrado según corresponda.

Visualizaciones para entender distribuciones y relaciones.

Selección de variables

Filtrado por correlación y varianza.

Reducción por PCA/MCA cuando aplica.

Selección embebida usando LASSO.

Variables finales son las que aparecen en al menos 2 de los 3 métodos anteriores.

Modelado

Clasificación para mora_franja (evaluación con Precision, Recall, F1, AUC-PR).

Regresión para monto_desembolso (MAE, RMSE, R² ajustado).

Validación cruzada y control de sobreajuste.

Variables seleccionadas (ejemplo)

Conjunto final aproximado (nominal):
actividad_economica, activos, clinica, comercial, cuota_credito, cuota_mensual, region, edad, estado_civil, estrato, gastos_sostenimiento, genero, ingresos_fijos, mora_franja, nivel_estudios, ocupacion, pasivos, personas_a_cargo, plazo, saldo_capital, saldo_vencido, score, tasa, tiempo_actividad, tiempo_residencia, tipo_contrato, tipo_vivienda, monto_desembolso, dias_mora.

(Revisar Códigos/ para la lista exacta usada en modelos.)

Resultados clave (resumen)

Se identifican al menos dos perfiles de producto (montos/plazos distintos) que requieren reglas de negocio diferenciadas.

El score crediticio es un predictor importante para mora; conviene evaluarlo con umbrales según riesgo.

El desbalance en las franjas de mora exige usar métricas y técnicas específicas (AUC-PR, remuestreo o algoritmos resistentes al desbalance).

Reducción de variables redundantes mejora estabilidad de los modelos y facilita interpretación.

Métricas usadas

Clasificación: Precision, Recall, F1-score, AUC-PR, matriz de confusión.

Regresión: MAE, RMSE, R² ajustado.

Pruebas estadísticas: Kruskal-Wallis, chi-cuadrado, correlaciones Pearson / V de Cramér.

Instrucciones para reproducir

Clonar el repositorio:

git clone https://github.com/mahuizg/AnalisisDentix.git
cd AnalisisDentix


Recomendado ejecutar en RStudio o con Rscript. Paquetes sugeridos:

install.packages(c(
  "tidyverse","data.table","janitor","ggplot2",
  "FactoMineR","factoextra","glmnet","caret",
  "randomForest","naniar","pROC","PRROC"
))


Flujo de ejecución sugerido (los nombres pueden variar; revisar Códigos/):

00_preprocessing.R — limpieza y creación de variables.

01_univariate_analysis.R — análisis univariado.

02_bivariate_correlations.R — correlaciones y pruebas.

03_feature_selection.R — selección de variables.

04_modeling_mora.R — modelos de clasificación para mora.

05_modeling_monto.R — modelos de regresión para monto.

06_evaluation_and_reports.R — métricas finales y exportación de resultados.

Ejemplo de ejecución de un script:

Rscript Códigos/00_preprocessing.R

Contribuciones

Para proponer cambios: realizar un fork, crear una rama con tus cambios, y abrir un Pull Request.

Para modificaciones grandes, abrir un issue explicando el cambio propuesto antes de empezar.

Autoría y créditos

Trabajo desarrollado por estudiantes del Tecnológico de Monterrey, Campus Querétaro, como parte del curso de métodos multivariados en ciencia de datos. Los autores y documentación completa están en los reportes incluidos.

Licencia

Revisar el archivo LICENSE en la raíz del repositorio (MIT).
