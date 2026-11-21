# Práctica 1 · El repositorio del equipo

**Sesión 1** · Trabajo en equipo · Tiempo estimado: 1 hora

## Lo que dice la carta descriptiva

| | |
|---|---|
| **Nivel base (obligatorio)** | README del repositorio del equipo con pregunta, activo e integrantes; un commit por integrante; lectura de la sección de valor del dinero del formulario. |
| **Nivel reto (opcional)** | Repetir el ejercicio de verificación con el activo del equipo. |
| **Producto esperado y formato de entrega** | Repositorio del equipo en GitHub con README. |
| **Fecha límite** | Viernes 20 de noviembre de 2026, 23:59. |
| **Criterios de evaluación** | Repositorio funcional · README claro · Participación de cada integrante (historial de Git). |
| **Ponderación** | 5% de la calificación del módulo. |

## Nivel base, paso a paso

**Paso 1 · Elijan su activo.** Una emisora de la Bolsa Mexicana de Valores que cotice desde antes de 2016. No puede ser WALMEX: es el activo de los ejemplos de clase. Cada equipo usa un activo distinto; avisen en el grupo cuál eligieron.

**Paso 2 · Creen el repositorio.** Una persona del equipo lo crea a partir de la plantilla y agrega como colaboradores a sus compañeros y a la docente (`nana-bug`). Las instrucciones clic por clic están en la [guía de GitHub y GitHub Desktop](../../docs/guia_github_desktop.md), secciones 2 y 3.

**Paso 3 · Llenen el README.** La plantilla ya trae el README con los espacios marcados. Deben quedar llenos:

- **Pregunta del caso:** qué quieren saber de su activo, en una o dos oraciones. Ejemplo: "¿Qué tan riesgoso fue invertir en esta emisora entre 2016 y 2025, y el rendimiento compensó ese riesgo frente a CETES?"
- **Activo:** nombre de la emisora, *ticker* en Yahoo Finance (termina en `.MX`) y por qué la eligieron.
- **Integrantes:** nombre, usuario de GitHub y perfil (financiero o técnico) de cada persona.
- **Uso de inteligencia artificial:** si usaron un LLM, cuál y para qué.

**Paso 4 · Un commit por integrante.** Cada persona hace al menos un cambio al README desde su propia cuenta de GitHub (por ejemplo, escribe su propio renglón en la tabla de integrantes). Sigan la sección 5 o la sección 6 de la guía.

**Paso 5 · Lean el formulario.** Lean la sección [Valor del dinero en el tiempo](../../docs/formulario.md#valor-del-dinero-en-el-tiempo) del formulario. Es una página y es la base de la sesión 2.

## Nivel reto

Repitan con su activo el ejercicio en parejas de la sesión 1: pregunten una cifra a un LLM y verifíquenla con datos.

1. Descarguen [`01_verificacion.ipynb`](01_verificacion.ipynb) de esta carpeta y súbanlo a su repositorio, en la carpeta `notebooks/`.
2. Ábranlo en Colab, escriban en la primera celda el usuario y el nombre de su repositorio, y cambien el *ticker* por el de su activo.
3. Completen las celdas marcadas con `# Tu código aquí` y la conclusión.
4. Guarden el notebook en su repositorio (**Archivo → Guardar una copia en GitHub**).

## Cómo se entrega

No se envía ningún archivo. La entrega es el repositorio del equipo tal como esté en GitHub el viernes 20 de noviembre a las 23:59. Compartan la dirección del repositorio en el Classroom del módulo.

## Antes de entregar

- [ ] El repositorio es público y la docente (`nana-bug`) es colaboradora.
- [ ] El README tiene pregunta, activo e integrantes.
- [ ] El historial (pestaña **Commits**) muestra al menos un commit de cada integrante.
- [ ] Declararon el uso de IA en el README.

## Cómo se califica

Se revisan los tres criterios de la carta descriptiva, con el mismo peso cada uno. El nivel reto suma hasta 1 punto extra sobre 10 en esta práctica.

La solución de referencia se publica en esta misma carpeta (`solucion/`) después de la fecha límite.
