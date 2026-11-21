# Guía de Google Colab

Colab es un notebook de Python que corre en el navegador. No hay que instalar nada; solo necesitas tu cuenta de Google.

## 1. Abrir el notebook de una clase

1. En el [README del repositorio](../README.md), busca la sesión en la tabla y da clic en **Abrir en Colab**.
2. En Colab, ve a **Archivo → Guardar una copia en Drive**. Se abre una pestaña nueva con tu copia: trabaja siempre ahí. Si no guardas la copia, tus cambios se pierden.
3. Corre la primera celda de código (la **celda estándar**) con el botón ▶ o con `Shift + Enter`. Tarda unos segundos: descarga el material de la clase.
4. Sigue el notebook de arriba hacia abajo. El orden importa: cada celda usa lo que definieron las anteriores.

## 2. Las tres operaciones que más vas a usar

| Qué quieres | Dónde está |
|---|---|
| Correr una celda | `Shift + Enter` |
| Empezar de cero y correr todo | **Entorno de ejecución → Reiniciar sesión y ejecutar todo** |
| Ver los archivos (por ejemplo `data/raw`) | Icono de carpeta, en la barra izquierda |

Antes de entregar cualquier práctica usa siempre **Reiniciar sesión y ejecutar todo**. Si el notebook corre completo así, le va a correr a cualquiera.

## 3. Trabajar en el repositorio de tu equipo

**Abrir un notebook de tu equipo.** En Colab: **Archivo → Abrir cuaderno → GitHub**, escribe el usuario dueño del repositorio, elige el repositorio y el notebook.

**Guardar el notebook en GitHub.** **Archivo → Guardar una copia en GitHub**. La primera vez Colab pide autorización para tu cuenta de GitHub. Elige el repositorio del equipo, escribe la ruta (por ejemplo `notebooks/02_valor_dinero.ipynb`) y un mensaje corto que diga qué cambiaste.

**La celda estándar del equipo.** Los notebooks de las prácticas empiezan con una celda donde escribes una sola vez el usuario de GitHub y el nombre del repositorio del equipo. Esa celda descarga su repositorio para que el notebook pueda usar `src/finanzas.py`.

**Si cambiaste `src/finanzas.py` y el notebook no ve el cambio:**

1. Confirma que el cambio ya está en GitHub (ábrelo en la página del repositorio).
2. En Colab: **Entorno de ejecución → Reiniciar sesión**.
3. Vuelve a correr desde la celda estándar. La celda trae los últimos cambios del repositorio.

## 4. Problemas frecuentes

| Qué ves | Qué hacer |
|---|---|
| `NameError: name '...' is not defined` | Te saltaste una celda. Usa **Reiniciar sesión y ejecutar todo**. |
| `ModuleNotFoundError: No module named 'src'` | No corriste la celda estándar, o falta escribir el usuario y el repositorio de tu equipo. |
| `ImportError: cannot import name '...'` | Esa función no está en `src/finanzas.py`, o su nombre no es exactamente el que pide la práctica. |
| `AssertionError` en una celda "Comprueba tu respuesta" | Tu respuesta al ejercicio anterior no da el valor esperado. Regresa al ejercicio. |
| La celda estándar marca error al descargar | Revisa que el usuario y el nombre del repositorio estén bien escritos y que el repositorio sea público. |
| Colab dice que la sesión se desconectó | Es normal después de un rato sin usarlo. Reconecta y usa **Ejecutar todo**. |

## 5. Tu cuenta

Usa una cuenta personal de Google. Algunas cuentas institucionales o de trabajo tienen Colab o Drive bloqueados.
