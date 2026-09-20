Análisis de Campaña Bancaria y Segmentación de Clientes
📌 Descripción del proyecto
Este proyecto realiza un análisis completo de una campaña bancaria combinando dos fuentes de datos:
•	bank-additional.csv → información de campañas de marketing telefónico.
•	customer-details.xlsx → información demográfica y de comportamiento de clientes.
El objetivo es:
•	Limpiar y unificar ambos datasets.
•	Realizar un análisis exploratorio (EDA).
•	Detectar patrones de comportamiento.
•	Identificar segmentos de clientes con mayor probabilidad de aceptar la campaña.
•	Extraer conclusiones de negocio accionables.
•	Estructura del proyecto
•	Código
•	📦 Proyecto_Campaña_Bancaria
•	 ┣ 📂 datos
•	 ┃ ┣ bank-additional.csv
•	 ┃ ┗ customer-details.xlsx
•	 ┣ 📂 notebooks
•	 ┃ ┗ analisis_campaña.ipynb
•	 ┣ 📂 src
•	 ┃ ┗ funciones_limpieza.py
•	 ┗ 📜 README.md
🛠️ Librerías utilizadas
•	numpy
•	pandas
•	matplotlib
•	seaborn

📥 Carga de datos
Se cargan:
•	El CSV de campaña bancaria.
•	El Excel con múltiples hojas de clientes.
Se verifica estructura, tamaño y primeras filas.
🧹 Limpieza de datos
Limpieza de df_bank
•	Eliminación de duplicados.
•	Conversión de columnas numéricas.
•	Normalización de fechas (meses en español → inglés).
•	Conversión de date a formato datetime.
•	Renombrado de columna id_ → ID.
Limpieza de df_customers
•	Eliminación de duplicados por hoja.
•	Conversión de fechas (Dt_Customer).
•	Conversión de columnas numéricas: Income, Kidhome, Teenhome, NumWebVisitsMonth.
Unión de datasets
Se unen todas las hojas del Excel con el dataset bancario mediante la columna común ID.
El resultado final es un dataset consolidado:
Código
df_final.shape → (n_registros, n_columnas)
Incluye variables de campaña + variables demográficas + comportamiento digital.
🔍 Análisis Exploratorio (EDA)
1. Distribuciones básicas
Se analizan:
•	Edad
•	Duración de llamada
•	Número de contactos previos
•	Ingresos
•	Visitas web al mes
Con histogramas y KDE.
2. Correlaciones
Se genera un heatmap profesional con todas las variables numéricas.
Se añade y_bin (yes=1, no=0) para analizar correlaciones con la respuesta.
3. Relación entre variables y la respuesta
Se utilizan:
•	Boxplots
•	Violinplots
•	ANOVA
Variables clave:
•	duration → mayor discriminación.
•	campaign → correlación negativa.
•	pdays → valores extremos (999) indican no contacto previo.
•	Income, age, NumWebVisitsMonth → aportan información adicional.
4. Outliers visuales
Se analizan outliers en:
•	age
•	duration
•	campaign
•	pdays
•	previous
•	Income
•	NumWebVisitsMonth
Se observa que:
•	duration tiene outliers altos asociados a respuestas positivas.
•	campaign tiene outliers altos asociados a rechazo.
•	pdays tiene valores extremos (999) que representan “no contactado antes”.
5. Segmentación por tipo de cliente
Se crean grupos por:
•	Edad
•	Ingresos
•	Actividad digital
•	Estado civil
•	Profesión
Se analiza la tasa de respuesta por segmento.
🧠 Conclusiones de negocio
✔ Perfil del cliente con mayor probabilidad de aceptar la campaña
•	Las llamadas mas largas: la variable duración es la mas discriminante, cuanto mas tiempo permanece el cliente en la llamada, mayor es la probabilidad de conversión.
•	Edad media-alta: los grupos de edad 46-60  y +60 muestran mayor tasa d respuesta positiva.
•	Profesiones especificas: Jubilados, estudiantes y admin, tienden a responder mejor.
•	Menor numero de contactos previos (campaing): los clientes que reciben demasiadas llamadas suelen rechazar la oferta.
•	Cliente con ingresos medios-altos muestran una mayor predisposición a aceptar
✔ Variables más influyentes
•	duration → principal predictor.
•	campaign → demasiados contactos reducen probabilidad de conversión.
•	pdays → clientes nuevos responden mejor.
•	previous → historial positivo aumenta probabilidad.
✔ Recomendaciones operativas
•	Mejorar calidad del guion para aumentar duración de llamada.
•	Limitar número de contactos por cliente.
•	Priorizar segmentos de mayor respuesta.
•	Enfocar la campaña en clientes nuevos.
•	Diseñar estrategias digitales para clientes con alta actividad web.

