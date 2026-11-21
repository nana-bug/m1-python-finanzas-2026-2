# Módulo 1 · Aplicaciones de Python en finanzas

**Diplomado en Finanzas Cuantitativas con Python y Machine Learning** · UNAM, Facultad de Economía · Generación 2026-2

Ponente: Ilce Anahí Medina Mendoza · Sesiones: sábados de 9:00 a 13:00, en línea

Este repositorio tiene todo lo que necesitas para seguir cada clase, hacer los ejercicios y entregar cada práctica. Se actualiza cada semana.

## Empieza aquí

1. **Para seguir una clase:** busca la sesión en la tabla de abajo y da clic en **Abrir en Colab**. Luego, en Colab, usa **Archivo → Guardar una copia en Drive** y corre la primera celda.
2. **Para hacer una práctica:** abre el enunciado de la práctica en la tabla. Ahí está el paso a paso, qué se entrega y cuándo.
3. **Si es tu primera vez con estas herramientas:** lee la [guía de Colab](docs/guia_colab.md) y la [guía de GitHub y GitHub Desktop](docs/guia_github_desktop.md).

No necesitas instalar nada en tu computadora. Solo una cuenta de Google y una cuenta de GitHub.

## Sesiones, prácticas y fechas

| Sesión | Fecha | Tema | Notebook de clase | Práctica | Entrega | Solución |
|---|---|---|---|---|---|---|
| 1 | 14/11/2026 | La revolución de IA en finanzas | [Abrir en Colab](https://colab.research.google.com/github/nana-bug/m1-python-finanzas-2026-2/blob/main/notebooks/01_ia_en_finanzas/01_ia_en_finanzas.ipynb) | [Práctica 1](practicas/practica_01/README.md) | 20/11/2026, 23:59 | Después de la entrega |
| 2 | 21/11/2026 | Valor del dinero en el tiempo y CETES | [Abrir en Colab](https://colab.research.google.com/github/nana-bug/m1-python-finanzas-2026-2/blob/main/notebooks/02_valor_dinero_cetes/02_valor_dinero_cetes.ipynb) | [Práctica 2](practicas/practica_02/README.md) | 27/11/2026, 23:59 | Después de la entrega |
| 3 | 28/11/2026 | Rendimientos y riesgo | Por publicar | Práctica 3 | 04/12/2026, 23:59 | Después de la entrega |
| 4 | 05/12/2026 | Extracción de datos en bolsa | Por publicar | Práctica 4 | 08/01/2027, 23:59 | Después de la entrega |
| 5 | 09/01/2027 | Gráficas y series de tiempo | Por publicar | Práctica 5 | 15/01/2027, 23:59 | Después de la entrega |
| 6 | 16/01/2027 | Rendimiento esperado y VaR | Por publicar | Práctica 6 | 22/01/2027, 23:59 | Después de la entrega |
| 7 | 23/01/2027 | CVaR y funciones financieras propias | Por publicar | Caso aplicado | 27/01/2027, 23:59 | Después de la entrega |
| 8 | 30/01/2027 | Caso aplicado: presentaciones | Por publicar | Presentación del caso | En la sesión | No aplica |

> **Aviso:** los datos de la clase (`ipc.csv` y `walmex.csv`) todavía no están en `data/raw/`. Mientras se publican, el notebook de clase de la sesión 1 se detiene en la celda que los lee. Los enunciados de las prácticas ya están completos.

Las soluciones de cada sesión (el notebook resuelto, la solución de la práctica y las funciones de `src/`) se publican después de la fecha límite de esa práctica. Si te atrasaste una semana, con esa solución puedes ponerte al corriente y seguir.

## Qué hay en cada carpeta

| Carpeta | Qué contiene |
|---|---|
| `notebooks/` | Una carpeta por sesión, con el notebook guía de la clase |
| `practicas/` | Una carpeta por práctica, con el enunciado y el notebook para entregar |
| `src/` | Las funciones financieras del módulo. Crece cada semana, conforme se liberan las soluciones |
| `tests/` | Las pruebas de esas funciones |
| `data/raw/` | Los datos de la clase. Todo el grupo usa exactamente los mismos archivos |
| `docs/` | Formulario de notación, guías y lecturas opcionales |

Documentos que vas a consultar seguido:

- [Formulario y notación común](docs/formulario.md): todas las fórmulas del módulo, con su traducción a código.
- [Lecturas opcionales](docs/lecturas.md), con vínculo.
- [Guía de Colab](docs/guia_colab.md) y [guía de GitHub y GitHub Desktop](docs/guia_github_desktop.md).

## El caso aplicado: el repositorio de tu equipo

Cada equipo (tres o cuatro personas, con perfiles financiero y técnico) analiza durante todo el módulo **una emisora de la BMV** en su propio repositorio. Cada práctica agrega una pieza; la entrega final integra las seis y se presenta en la sesión 8.

- El repositorio del equipo se crea a partir de la [plantilla de equipo](https://github.com/nana-bug/m1-plantilla-equipo). Las instrucciones están en la [Práctica 1](practicas/practica_01/README.md).
- Los ejemplos de clase usan WALMEX; por eso ningún equipo puede elegirla.
- Este repositorio es de consulta: nadie entrega aquí. Todas las entregas se hacen en el repositorio de cada equipo.

## Evaluación

| Elementos por evaluar | Ponderación |
|---|---|
| Trabajo práctico en Python: prácticas semanales de las sesiones 1 a 6 (30% en total, en partes iguales: 5% cada una; el nivel reto suma puntos extra) | 30 |
| Trabajo práctico en Python: caso aplicado, con módulo de funciones propias y análisis del activo; integra las prácticas anteriores y se entrega antes de la sesión 8 | 30 |
| Presentación del caso aplicado por equipo (demo day, sesión 8) | 20 |
| Participación en todas las sesiones (se requiere 80% de asistencia para aprobar) | 20 |
| **Total** | **100** |

Cada práctica tiene dos niveles:

- **Nivel base:** obligatorio. Está pensado para resolverse en alrededor de una hora.
- **Nivel reto:** opcional. Suma hasta 1 punto extra sobre 10 en esa práctica; el total de las prácticas no pasa de 30%.

Los criterios de evaluación de cada práctica están en su enunciado.

## Uso de inteligencia artificial

Se permite usar LLMs (ChatGPT, Gemini, Claude y similares). A cambio, tres reglas:

1. **Cada participante debe poder explicar su código.** En cualquier momento se te puede pedir que expliques una línea de tu entrega.
2. **Toda cifra se verifica con datos.** Un número que viene de un LLM no se entrega sin comprobarlo con código.
3. **El uso se declara.** En el README de tu equipo escribe qué LLM usaron y para qué.

## Reglas de trabajo del módulo

- **Notación:** la del [formulario](docs/formulario.md). El nivel de confianza se escribe `nivel = 0.95` y la cola `cola = 1 - nivel`.
- **Datos reproducibles:** fechas fijas en toda descarga y semilla fija en todo lo aleatorio.
- **Un solo activo:** en este módulo se analiza un activo a la vez. Los portafolios son del Módulo 2 y los modelos de aprendizaje automático del Módulo 3.
- **Todo corre desde cero:** antes de entregar, usa en Colab **Entorno de ejecución → Reiniciar sesión y ejecutar todo**.

## Dónde está lo demás

Las presentaciones de cada sesión, los avisos y las calificaciones están en el Classroom del módulo y en la carpeta del curso en Google Drive.

## Licencia

El código se publica con licencia MIT ([LICENSE](LICENSE)). Los textos y notebooks, con licencia Creative Commons BY-NC-SA 4.0 ([LICENCIA_CONTENIDO.md](LICENCIA_CONTENIDO.md)).
