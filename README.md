# Smart Elysium

Votación de los 12 reconocimientos **Los Dioses del Olimpo Smart Fit**. Cada persona entra con su correo corporativo de Google y vota por un nominado en cada categoría.

- **Página pública (GitHub Pages):** `index.html` presenta las categorías y lleva al enlace de votación.
- **Votación (Google Apps Script):** `apps-script/` guarda los votos en una hoja de cálculo de Google.

## Cómo funciona

| | |
|---|---|
| Quién vota | Cualquier persona con cuenta del dominio corporativo |
| Votos | 1 por persona y categoría. Se puede cambiar mientras esté abierta. Nadie puede votar por sí mismo |
| Dónde quedan | Hoja **Votos** de la hoja de cálculo |
| Quién ve el conteo | El dueño del script y los correos en **Config › organizadores** |
| Resultados | El organizador los publica: todos ven el top 3 por categoría |

## Instalación (10 minutos, una sola vez)

1. **Crea la hoja de cálculo.** En Google Drive, con tu cuenta corporativa, crea una hoja nueva llamada `Smart Elysium – Votos`.
2. **Abre Apps Script.** En la hoja: *Extensiones › Apps Script*.
3. **Copia el código.**
   - Reemplaza el contenido de `Código.gs` con [`apps-script/Code.gs`](apps-script/Code.gs).
   - *Archivo › +  › HTML*, nómbralo `Index` y pega [`apps-script/Index.html`](apps-script/Index.html).
   - *Configuración del proyecto ›* activa “Mostrar el archivo de manifiesto `appsscript.json`” y pega [`apps-script/appsscript.json`](apps-script/appsscript.json).
4. **Crea las hojas.** En el editor elige la función `setup` y pulsa *Ejecutar*. Acepta los permisos. Aparecerán las pestañas **Votos**, **Personas** y **Config**.
5. **(Opcional) Carga la lista de personas.** En **Personas** pega Nombre, Correo y Área de los colaboradores. Así aparecen en el buscador y se evita contar a la misma persona con dos nombres distintos. Si la dejas vacía, la gente escribe el nombre libremente.
6. **Agrega organizadores.** En **Config**, fila `organizadores`, escribe los correos separados por coma.
7. **Publica.** *Implementar › Nueva implementación › Aplicación web*:
   - Ejecutar como: **Yo**
   - Quién tiene acceso: **Cualquier usuario de tu dominio**

   Copia la URL que termina en `/exec`.
8. **Conecta GitHub Pages.** Pega esa URL en [`config.js`](config.js):
   ```js
   window.SMART_ELYSIUM_URL = "https://script.google.com/a/macros/.../exec";
   ```

## Durante el evento

En la parte inferior de la página de votación, los organizadores ven el **Panel del organizador**:

- **Cerrar votación** — nadie más puede votar ni cambiar su voto.
- **Publicar resultados** — guarda el top 3 de cada categoría y lo muestra a todos.
- **Reabrir / Ocultar resultados** — deshace lo anterior.

El detalle completo de votos siempre está en la hoja **Votos**.

## Actualizar el código

Si cambias algo en `apps-script/`, cópialo de nuevo al editor y usa *Implementar › Gestionar implementaciones › Editar › Nueva versión* para conservar la misma URL.
