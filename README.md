# ML-LEARN

Repositorio de práctica para aprender *machine learning* de forma progresiva.
Las convenciones didácticas y técnicas del proyecto están en
[AGENTS.md](AGENTS.md).

## Requisitos

- [uv](https://docs.astral.sh/uv/) instalado.
- No es necesario instalar Python manualmente: `uv` usará la versión indicada
  en `.python-version` (actualmente Python 3.14).

## Inicializar el entorno local

Desde la raíz del repositorio, ejecuta:

```powershell
uv sync
```

El comando crea —o actualiza— el entorno virtual local en `.venv` e instala las
versiones exactas registradas en `uv.lock`.

## Usar uv

No hace falta activar el entorno si se ejecutan los comandos mediante `uv run`:

```powershell
# Ejecutar el programa principal
uv run python main.py

# Abrir JupyterLab para trabajar con notebooks
uv run jupyter lab

# Ejecutar una orden o script de Python puntual
uv run python -c "import polars; print(polars.__version__)"
```

Para añadir una dependencia al proyecto:

```powershell
uv add nombre-del-paquete
uv sync
```

`uv add` actualiza `pyproject.toml` y `uv.lock`; ambos archivos deben
versionarse para que el entorno sea reproducible.

## Activación opcional

Si se prefiere trabajar con el entorno activo en PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

Después se pueden usar `python`, `jupyter lab` y demás comandos directamente.
Para salir del entorno:

```powershell
deactivate
```
