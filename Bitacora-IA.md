# Bitácora de IA

Herramienta utilizada: Claude Code (modelo Opus 5).

## Task 3

### Prompt

```text
Implementa en un Jupyter Notebook nuevo el siguiente sistema de EDOs usando únicamente NumPy.
No uses scipy.integrate, PySD ni ninguna librería de simulación: Euler y RK4 deben estar
escritos a mano.

    dS/dt = -βS - γSA/N
    dA/dt =  βS + γSA/N + εRA/N - δA
    dR/dt =  δA - εRA/N

Parámetros: N=10000, S0=9800, A0=200, R0=0, β=0.02, γ=0.3, δ=0.05, ε=0.1, T=100 semanas.

Estructura del código:

1. El campo vectorial en una función pura `derivadas(y, p)` que reciba el estado [S, A, R] y
   devuelva un arreglo de NumPy con las tres derivadas.
2. Dos integradores con firma común `(f, y0, dt, T, p) -> (t, Y)`, donde `Y` tenga forma
   (n+1, 3) para guardar la trayectoria completa y no solo el estado final.
3. Corridas de Euler con dt = 1.0, 0.5 y 0.1 semanas: gráfica de A(t) para las tres y tabla
   con S(T), A(T) y R(T) de cada una.
4. Corrida de RK4 con dt = 1.0 y tabla que compare su A(T) contra las tres corridas de Euler,
   incluyendo el número de evaluaciones del campo vectorial que costó cada una. Agrega una
   solución de referencia con un paso mucho más fino para medir el error absoluto real.
5. Una función que audite |S + A + R - N| en cada paso de cada corrida, evaluada con dos
   criterios (igualdad exacta y tolerancia de 1e-6), más una gráfica de la deriva acumulada.
```

### ¿Por qué funcionó?

Funcionó porque el prompt elimina ambigüedades desde el inicio. Las ecuaciones y parámetros se escriben directamente, evitando errores de interpretación, signos incorrectos o términos omitidos. Además, las restricciones se expresan como prohibiciones explícitas, lo que permite verificar fácilmente que no se utilicen herramientas externas.

También se fija la arquitectura del código mediante una función para el campo vectorial y una firma común para ambos integradores. Esto garantiza que las diferencias observadas provengan del método numérico y permite reutilizar las trayectorias sin volver a integrar. Asimismo, se solicita guardar la trayectoria completa para poder auditar el comportamiento paso a paso.

Finalmente, se incluye una solución de referencia con paso fino para medir el error real de cada método, en lugar de limitarse a compararlos entre sí. La auditoría de la invariante con igualdad exacta y tolerancia numérica permite distinguir entre errores de redondeo y de truncamiento.