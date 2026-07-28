# Laboratorio 1

En este laboratorio se modela la **dinámica de adopción de un protocolo de higiene** en comunidades
rurales, para una organización internacional de salud pública. La población total es constante y
se reparte en tres stocks: no adoptantes (*S*), adoptantes activos (*A*) y ex adoptantes (*R*).
El protocolo se difunde por campaña institucional y por imitación entre vecinos, mientras parte
de la comunidad lo abandona por fatiga y puede reactivarse por contacto social.

## Cómo ejecutar

Se requiere Python 3.10 o superior.

### 1. Crear el entorno virtual e instalar dependencias

```bash
git clone https://github.com/Tunchxz/CC2017-Laboratorio-1.git
cd CC2017-Laboratorio-1

python3 -m venv .venv
.venv/bin/pip install --upgrade pip
.venv/bin/pip install -r requirements.txt
```

En Windows, la ruta al ejecutable es `.venv\Scripts\` en lugar de `.venv/bin/`.

### 2. Registrar el kernel de Jupyter

```bash
.venv/bin/python -m ipykernel install --user --name cc2017-lab1 \
  --display-name "Python (CC2017 Lab 1)"
```

### 3. Abrir el notebook

```bash
.venv/bin/jupyter lab Task-3.ipynb
```

Al abrirlo, se selecciona el kernel **Python (CC2017 Lab 1)** y se ejecutan las celdas en orden
(`Run > Run All Cells`).

### Alternativa: ejecución sin interfaz

Para ejecutar el notebook de principio a fin y guardar las salidas sin abrir JupyterLab:

```bash
.venv/bin/jupyter nbconvert --to notebook --execute --inplace Task-3.ipynb
```
