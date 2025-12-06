# Análisis Dentix

Repositorio con el análisis de datos y modelos desarrollados para Dentix (Colombia). Contiene limpieza y preparación de datos, análisis descriptivo (univariado y bivariado), gráficos y visualizaciones, selección de variables y modelos de predicción.

## Estructura general

- `Códigos/` — Scripts en R y Python para limpieza, análisis, visualización, selección de variables y modelado.

- `Correlaciones/` — Gráficos de correlaciones, varianzas y distribuciones por y entre variables. 

- `Univariado Numéricas/` — Gráficos para variables numéricas.

- `Univariado Categóricas/` — Gráficos para variables categóricas.

## Objetivos

1. Realizar un diagnóstico profundo de los factores que explican distintas variables como la probabilidad de mora y las diferencias entre clientes y clínicas de Dentix.
2. Realizar una segmentación de clientes buscando perfiles de alto, mediano y bajo riesgo.
3. Desarrollar modelos predictivos para estimar monto de desembolso según el perfil del cliente.
4. Generar propuestas para maximizar la rentabilidad del negocio de Dentix.

## Resumen del dataset

- Observaciones: 46,329 registros (datos anonimizados).
- Variables:
    - Numéricas: ingresos_fijos, activos, pasivos, cuota_credito,cuota_mensual, saldo_capital, saldo_vencido, dias_mora, score, monto_desembolso, plazo, tasa,
    - Categóricas: nivel_estudios, estado_civil, tipo_vivienda, estrato, actividad_económica, tipo_contrato, ocupacion, genero, clinica, comercial, region, lugar_nacimiento, mora_franja 
edad, tiempo_residencia, tiempo_actividad, personas_a_cargo

## Metodología 

### Preprocesamiento

- Limpieza de NAs según criterio por variable.
- Transformaciones (por ejemplo log) en variables con sesgo.
- Creación de variables binarias para manejar zero-inflation.
- Detección y tratamiento de outliers según reglas estadísticas y de negocio.

### Análisis exploratorio

- Estadísticas univariadas por tipo de variable.
- Análisis bivariado: correlaciones, pruebas Kruskal-Wallis, chi-cuadrado y MANOVA según corresponda.
- Visualizaciones para entender distribuciones y relaciones.

### Selección de variables

- Filtrado por correlación y varianza.
- Reducción por PCA y MCA.
- Selección usando LASSO.
- Las variables finales son las que aparecen en al menos 2 de los 3 métodos anteriores.

### Modelado

- Clasificación para mora_franja.
- Regresión para monto_desembolso.
- Validación cruzada y control de sobreajuste.

## Resultados clave 

- Se identificaron 6 perfiles diferentes dentro de la clientela de Dentix.
- Dentix puede aumentar los montos ofrecidos, ofrecer plazos más largos o mejorar las tasas a los clientes del perfil 6 (empleados padres de familia).
- Sobreestimación de clientes en el perfil 5 (empleados independientes con mal score) los cuales cuentan con un riesgo crítico. Establecer umbrales de score más altos.
- Cálculo de score interno para evaluación de clientes en la asignaciñon de montos credicticios y tasas según comportamientos y características de los clientes que son capturadas por el score externo.

## Métricas usadas

- Pearson
- Tasa de correlación Eta
- V de Cramér
- Prueba de hipótesis de Chi cuadrada
- Z-test
- Mann-Whitney
- Precision
- Recall
- F1 score
- AUC-PR
- Matriz de confusión
- MAE
- RMSE
- R2 ajustado

## Conclusiones

Este proyecto permitió construir una visión integral del comportamiento credicticio de los clientes de Dentix, generando un análsis de datos completo y la creación de modelos predictivos. A lo largo del proyecto, se identificaron insights importantes que nos permitieron proponer soluciones potenciales para la rentabilidad de Dentix. 
