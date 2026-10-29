# @contracorriente/ui

Repo: [contracorriente-ui](https://github.com/RicardoArceNCR/contracorriente-ui).
El nombre de paquete sigue siendo `@contracorriente/ui`. El renombrado del
repositorio no cambia tokens, versiones ni tags publicados. Tema WordPress y
sitio Next consumen el mismo paquete, fijado por tag.

Tokens de ContraCorriente. La fuente que se edita es el Figma. `source/dtcg/` es el export nativo de Figma (DTCG), un archivo por colección; `scripts/dtcg-to-sd.mjs` lo convierte y las listas del cliente están en `tokens.config.json`. El CSS de `build/` se genera y se versiona para que el sitio no tenga que correr Style Dictionary.

```bash
npm run verify
```

En el sitio, un solo grafo de `@import`, en este orden:

```css
@import "@contracorriente/ui/tokens.css";
@import "@contracorriente/ui/tokens-dark.css";
@import "@contracorriente/ui/theme-bridge.css";
```

`tokens-dark.css` vive bajo `.dark`. Sin esa clase, el sitio queda en claro. Las familias las carga `next/font` del sitio (`--typography-family-*`). Este paquete no trae `@font-face`.

## Trabajo con tres repos

Este paquete trabaja junto al sitio [contracorriente](https://github.com/RicardoArceNCR/contracorriente)
y las prácticas compartidas de [estudio](https://github.com/RicardoArceNCR/estudio).
En la máquina de Ricardo vive en `~/ui/contracorriente`; `~/ui` contiene
varios paquetes y no es un solo repositorio. Las rutas pueden cambiar.

Figma es la fuente de diseño. En Variables, clic derecho en cada colección
que cambió → **Export modes**; guardar el JSON en `source/dtcg/` con el
nombre de la colección (`primitivos.tokens.json`, no `Mode 1.tokens.json`),
ejecutar
`npm run verify`, revisar y commitear los exports y `build/`. El comando
verifica y genera archivos; no hace commits ni publica tags. Para consumir
un cambio en el sitio se publica una versión autorizada con tag nuevo y se
actualizan su dependencia y lockfile. Nunca mover un tag publicado.

Para una tarea de sitio, este paquete puede consultarse en lectura; para
cambiar tokens, se trabaja aquí siguiendo sus instrucciones. No editar el
CSS del sitio para reemplazar la paleta ni modificar `source/dtcg/` sin mantener su
correspondencia con Figma.

## Otro cliente

Un cliente nuevo crea su propio sitio y paquete según
[cliente-nuevo](https://github.com/RicardoArceNCR/estudio/blob/main/runbooks/cliente-nuevo.md).
No duplicar este repositorio ni su identidad. La recomendación anterior de
usar un starter queda reemplazada por el ADR 0001 de estudio y el ADR 0008
del sitio ContraCorriente. Este paquete sigue siendo exclusivo del cliente.
