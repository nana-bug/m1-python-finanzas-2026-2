# Guía de GitHub y GitHub Desktop

GitHub guarda el trabajo de tu equipo y el historial de quién cambió qué. La página de GitHub y GitHub Desktop están en inglés; aquí van los nombres de los botones tal como aparecen.

## 1. Crear tu cuenta (cada integrante)

1. Entra a <https://github.com> y elige **Sign up**. Usa un correo que revises.
2. Elige un nombre de usuario profesional: lo verán futuros empleadores.

## 2. Crear el repositorio del equipo (una sola persona)

1. Entra a la plantilla: <https://github.com/nana-bug/m1-plantilla-equipo>.
2. Da clic en el botón verde **Use this template → Create a new repository**.
3. En **Repository name** escribe un nombre corto sin espacios, por ejemplo `caso-gfnorte`.
4. Elige **Public**. Así Colab puede abrir el repositorio sin contraseñas.
5. Da clic en **Create repository**.

## 3. Invitar al equipo y a la docente (la misma persona)

1. En el repositorio nuevo: **Settings → Collaborators → Add people**.
2. Agrega el usuario de GitHub de cada integrante y el de la docente: `nana-bug`.
3. Cada persona recibe un correo de invitación y debe aceptarlo.

## 4. Instalar GitHub Desktop y bajar el repositorio (cada integrante)

1. Descarga GitHub Desktop de <https://desktop.github.com> e inicia sesión con tu cuenta.
2. **File → Clone repository**, elige el repositorio del equipo y una carpeta de tu computadora. Da clic en **Clone**.

## 5. El ciclo de trabajo: bajar, cambiar, subir

Cada vez que vayas a trabajar:

1. **Fetch origin** y luego **Pull origin** (botón de arriba): trae lo que subieron tus compañeros.
2. Haz tus cambios en los archivos (por ejemplo, edita `README.md` con cualquier editor de texto).
3. En GitHub Desktop aparecen los archivos cambiados. Abajo a la izquierda escribe un resumen corto en **Summary**, por ejemplo `Agrega la pregunta del caso`.
4. Da clic en **Commit to main**.
5. Da clic en **Push origin**. Hasta que no haces *push*, tu cambio solo existe en tu computadora.

**Un commit por integrante.** En la Práctica 1 cada persona debe hacer al menos un commit desde su propia cuenta. El historial del repositorio es la evidencia de la participación de cada quien.

## 6. Otra forma de editar: directo en la página de GitHub

Para cambios pequeños no necesitas GitHub Desktop:

1. Abre el archivo en la página del repositorio (por ejemplo `src/finanzas.py`).
2. Da clic en el icono del lápiz (**Edit this file**).
3. Haz el cambio, da clic en **Commit changes**, escribe un resumen y confirma.

## 7. Si dos personas cambiaron lo mismo

GitHub Desktop avisa de un *conflict*. Para evitarlo: haz **Pull origin** antes de empezar, sube cambios pequeños y seguido, y avisa en el chat del equipo qué archivo estás editando.

## 8. Qué no se sube nunca

- Tu token de la API de Banxico ni ninguna contraseña.
- Archivos que no sean del proyecto.

La plantilla ya trae un archivo `.gitignore` que evita subir por accidente los archivos más comunes de este tipo.
