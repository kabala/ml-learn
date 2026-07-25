# ML-LEARN: guía de trabajo

Este repositorio es un espacio didáctico para aprender *machine learning* de
forma progresiva, experimental y reproducible. El objetivo no es optimizar un
producto, sino entender qué problema resuelve cada técnica, cuándo falla y cómo
evaluarla con rigor.

## Alcance de aprendizaje

El contenido se organiza en módulos pequeños e independientes. La progresión
preferida es:

1. Fundamentos: Python para datos, tipos de variables, limpieza, estadística
   descriptiva, particiones y visualización.
2. Aprendizaje supervisado: regresión, clasificación, métricas, validación
   cruzada, regularización, *pipelines*, ajuste de hiperparámetros e
   interpretabilidad básica.
3. Aprendizaje no supervisado: reducción de dimensionalidad, *clustering* y
   evaluación exploratoria.
4. Temas posteriores: ensambles, detección de anomalías, series temporales y
   una introducción responsable a redes neuronales.

Cada lección debe declarar: pregunta de aprendizaje, fuente y licencia del
dataset, decisiones de preprocesamiento, método de evaluación, resultado y una
breve reflexión sobre sus límites. Priorizar datasets pequeños, públicos y
comprensibles antes de usar datos complejos.

## Principios

- Separar exploración, preparación de datos, entrenamiento y evaluación; nunca
  ajustar transformaciones con información del conjunto de prueba.
- Establecer una semilla (`random_state`) cuando corresponda y documentar las
  versiones usadas para que el resultado pueda reproducirse.
- Comparar siempre con una línea base sencilla antes de usar un modelo más
  complejo.
- Elegir las métricas según el problema y el coste de los errores, no solo por
  familiaridad. En clasificación desbalanceada, no usar exactitud como única
  métrica.
- Tratar los resultados como evidencia, no como causalidad. Comprobar sesgos,
  datos faltantes, fuga de información y posibles impactos éticos.
- Mantener el código breve, legible y orientado a explicar una idea. Las
  conclusiones deben vivir junto a las gráficas o métricas que las justifican.

## Entorno técnico

- Gestionar el proyecto exclusivamente con `uv`. Usar la versión estable más
  reciente de Python que sea compatible con todas las dependencias; antes de
  subirla, comprobarlo con `uv sync` e importaciones reales. Crear/sincronizar
  el entorno local con `uv sync` y ejecutar herramientas con `uv run ...`; no
  instalar paquetes globalmente ni activar dependencias ajenas al proyecto.
- Usar **Polars** como API principal para cargar, transformar y validar datos
  tabulares. Convertir a NumPy o pandas solo en el límite que requiera una API
  de modelado.
- Usar **scikit-learn** como base para los experimentos de aprendizaje
  supervisado y sus `Pipeline`/`ColumnTransformer` para evitar fugas de datos.
  XGBoost se reserva para comparar modelos de *gradient boosting* una vez
  exista una línea base.
- Usar **Plotly** para visualizaciones interactivas y comunicables. Toda gráfica
  debe tener título, ejes/unidades y una conclusión asociada.
- Los notebooks son para exploración y explicación; extraer funciones repetidas
  o lógica estable a módulos Python antes de reutilizarlas.

## Organización y datos

Usar, cuando el material crezca, una estructura por tema como
`01_fundamentos/`, `02_supervisado/` y `03_no_supervisado/`, con notebooks y
scripts nombrados de forma descriptiva. Guardar datasets descargados o
generados en `data/` y artefactos temporales en `artifacts/`; no versionar datos
grandes, credenciales ni información personal. Incluir instrucciones de descarga
o generación en vez de copiar material con licencia incierta.

## Comprobaciones antes de dar por terminado un cambio

1. Ejecutar `uv sync` tras cambiar dependencias.
2. Ejecutar el script o notebook afectado desde un entorno limpio cuando sea
   práctico.
3. Verificar que las particiones y métricas corresponden al objetivo didáctico.
4. Actualizar la explicación si cambian supuestos, resultados o el origen de los
   datos.
