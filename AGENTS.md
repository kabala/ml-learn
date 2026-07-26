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

## Estilo de enseñanza para este alumno

Quien trabaja en este repositorio es un aprendiz de ML que todavía está
reforzando sus fundamentos de matemáticas y estadística, y aprende mejor de
forma **visual** que a partir de fórmulas puras. Estas directrices aplican a
todo notebook nuevo o reescrito, y complementan (no reemplazan) los
"Principios" de arriba:

- Nunca introducir una fórmula o notación matemática sin antes construir la
  intuición con una analogía cotidiana y/o una gráfica. La fórmula llega
  *después* de que el lector ya intuye qué debería pasar.
- Definir explícitamente, la primera vez que aparece, cualquier término
  matemático o estadístico usado (media, varianza, residuo, logaritmo,
  derivada/pendiente, convexidad, probabilidad, verosimilitud, cuantil,
  gradiente...), aunque parezca elemental. No asumir que el lector ya lo sabe.
- Priorizar gráficas Plotly incrementales o paso a paso (trayectorias,
  snapshots, comparaciones lado a lado, regiones sombreadas) sobre bloques de
  fórmulas o tablas. Toda fórmula relevante debe ir acompañada de al menos una
  visualización que la ilustre.
- Seguir esta progresión fija en cada notebook: motivación con un ejemplo
  cotidiano → intuición visual → formalización matemática (con cada símbolo
  explicado en prosa) → código → visualización del resultado → ideas clave →
  ejercicio de predicción (que el alumno prediga qué va a pasar *antes* de
  ejecutar la celda, no solo que la ejecute).
- Usar una paleta de color consistente entre notebooks: datos reales en
  negro, modelos o casos de comparación en colores distintos, y el resultado
  óptimo o destacado en rojo.
- Usar [GLOSARIO.md](GLOSARIO.md) como fuente de verdad de qué tema cubre cada
  notebook próximo y cuál es su objetivo de aprendizaje declarado; al terminar
  un notebook, actualizar su fila a ✅ en ese archivo.

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

Los notebooks se organizan por tema dentro de `notebooks/`, siguiendo la
convención ya en uso:
`notebooks/aprendizaje_<supervisado|no_supervisado>/<tarea>/<algoritmo>/NN_tema.ipynb`
(por ejemplo, `notebooks/aprendizaje_supervisado/regresion/regresion_lineal/01_funcion_de_costo.ipynb`).
El listado completo de temas cubiertos y pendientes, con la ruta exacta de
cada notebook, vive en [GLOSARIO.md](GLOSARIO.md) — consultarlo antes de crear
un notebook nuevo para mantener la numeración y el nombre consistentes.
Guardar datasets descargados o generados en `data/` y artefactos temporales en
`artifacts/`; no versionar datos grandes, credenciales ni información
personal. Incluir instrucciones de descarga o generación en vez de copiar
material con licencia incierta.

## Comprobaciones antes de dar por terminado un cambio

1. Ejecutar `uv sync` tras cambiar dependencias.
2. Ejecutar el script o notebook afectado desde un entorno limpio cuando sea
   práctico.
3. Verificar que las particiones y métricas corresponden al objetivo didáctico.
4. Actualizar la explicación si cambian supuestos, resultados o el origen de los
   datos.
