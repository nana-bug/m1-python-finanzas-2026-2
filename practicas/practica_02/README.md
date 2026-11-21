# Práctica 2 · Valor del dinero en el tiempo aplicado a CETES

**Sesión 2** · Trabajo en equipo · Tiempo estimado: 1 hora (si aprovecharon el taller, menos)

## Lo que dice la carta descriptiva

| | |
|---|---|
| **Nivel base (obligatorio)** | Funciones de valor del dinero documentadas en `src/` y aplicadas a CETES. |
| **Nivel reto (opcional)** | TIR con el método de Newton-Raphson comparada con una librería. |
| **Producto esperado y formato de entrega** | Funciones en `src/` y notebook en GitHub. |
| **Fecha límite** | Viernes 27 de noviembre de 2026, 23:59. |
| **Criterios de evaluación** | Cálculos correctos · Funciones documentadas · Reproducibilidad. |
| **Ponderación** | 5% de la calificación del módulo. |

## Nivel base, paso a paso

**Paso 1 · Seis funciones en `src/finanzas.py`.** Copien al archivo `src/finanzas.py` de su repositorio las funciones que escribieron en clase. Los nombres deben ser **exactamente** estos, porque las siguientes sesiones las importan por nombre:

| Función | Fórmula | Se prueba con |
|---|---|---|
| `valor_futuro(vp, r, n, m=1)` | $VP\,(1 + r/m)^{m n}$; con `m=None`, $VP\,e^{r n}$ | 100,000 al 10%, 10 años, continua: $100{,}000\,e$ |
| `valor_presente(vf, r, n, m=1)` | $VF / (1 + r/m)^{m n}$ | 100 en 100 años al 6.1% semestral: 0.2457 |
| `tasa_efectiva(r, m)` | $(1 + r/m)^{m} - 1$ | 12% capitalizable mensual: 12.68% |
| `precio_cete(r, d, vn=10.0)` | $VN / (1 + r\,d/360)$ | Banxico, 91 días al 4.39%: 9.8902485 |
| `rendimiento_cete(p, d, vn=10.0)` | $(VN/P - 1)\,360/d$ | Banxico, de 9.8902485 a 4.39% |
| `tasa_efectiva_cete(r, d, base=360)` | $(1 + r\,d/360)^{\text{base}/d} - 1$ | 28 días al 6.20%: 6.38% |

Cada función lleva un **docstring**: el texto entre comillas triples, justo debajo de `def`, que dice qué calcula y con qué fórmula. Ejemplo:

```python
def precio_cete(r, d, vn=10.0):
    """Precio de un CETE a partir de su tasa de rendimiento: P = VN / (1 + r d/360)."""
    return vn / (1 + r * d / 360)
```

Todas las tasas van en decimales (0.062, no 6.2).

**Paso 2 · El notebook de la práctica.**

1. Descarguen [`02_valor_dinero.ipynb`](02_valor_dinero.ipynb) de esta carpeta y súbanlo a su repositorio, en `notebooks/`.
2. Ábranlo en Colab y escriban en la primera celda el usuario de GitHub y el nombre de su repositorio.
3. Corran la sección 2: las seis pruebas deben pasar sin modificar la celda.
4. Completen la sección 3 (aplicación a CETES) con los resultados de la última subasta disponible. Los publica Banco de México cada martes.

**Paso 3 · La tasa libre de riesgo en el README.** Escriban en el README de su equipo la tasa libre de riesgo que usarán todo el módulo: CETES a 28 días, la fecha de la subasta, la fuente, la tasa efectiva anual y la tasa por día hábil que calcularon en el notebook.

**Paso 4 · Suban todo.** `src/finanzas.py`, el notebook y el README deben estar en GitHub. El commit de esta semana lo hace una persona distinta a la de la semana pasada.

## Nivel reto

Agreguen a `src/finanzas.py`:

- `valor_presente_flujos(flujos, r, tiempos=None)`, vista en clase.
- `tir_newton(flujos, tiempos=None, r0=0.10, tol=1e-12, max_iter=100)`: la tasa interna de retorno con el método de Newton-Raphson.

Después completen la sección 4 del notebook: comparen su resultado con `numpy_financial.irr` y contesten la pregunta del reto.

## Cómo se entrega

La entrega es el repositorio del equipo tal como esté en GitHub el viernes 27 de noviembre a las 23:59.

## Antes de entregar

- [ ] **Entorno de ejecución → Reiniciar sesión y ejecutar todo** corre sin errores.
- [ ] Las seis pruebas pasan.
- [ ] Las seis funciones tienen docstring con su fórmula.
- [ ] El README dice qué tasa libre de riesgo eligieron, de qué subasta y de qué fuente.
- [ ] Si usaron un LLM, lo declararon en el README y pueden explicar cada línea.

## Cómo se califica

| Criterio de la carta descriptiva | Qué se revisa |
|---|---|
| Cálculos correctos | Las seis pruebas pasan y las cifras de CETES son correctas para la subasta que eligieron. |
| Funciones documentadas | Las seis funciones están en `src/finanzas.py`, con su nombre exacto y su docstring. |
| Reproducibilidad | El notebook corre de principio a fin desde cero y el README documenta la tasa libre de riesgo. |

Los tres criterios pesan lo mismo. El nivel reto suma hasta 1 punto extra sobre 10 en esta práctica.

La solución de referencia y las funciones de `src/` se publican después de la fecha límite (checkpoint 2).
