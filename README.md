# Lacre

Cartas selladas en el tiempo. Frontend editorial con React, Vite y Tailwind CSS.

## Desarrollo

Requiere Node.js 22 y npm.

```sh
npm ci
npm run dev
```

```sh
npm run build
npm run preview
```

## Cloudflare

Este repositorio está preparado para desplegarse como un Worker de Cloudflare con Wrangler.

| Ajuste | Valor |
| --- | --- |
| Rama de producción | `main` |
| Framework | React (Vite) |
| Comando de compilación | `npm run build` |
| Comando de despliegue | `npx wrangler deploy` o `npm run deploy` |
| Directorio de assets | `dist` |
| Node.js | `22` (definido en `.node-version`) |

La configuración de `wrangler.jsonc` usa `not_found_handling: "single-page-application"`, por lo que las rutas de React como `/c/demo-sellada` y `/c/demo-abierta` funcionan al abrirse directamente.

## Rutas

- `/`: escribir y sellar una carta.
- `/c/demo-sellada`: ejemplo sellado con contador, copiar enlace y recordatorio de calendario.
- `/c/demo-abierta`: ejemplo desbloqueado con apertura animada.
- `/c/[id]`: cartas creadas en el dispositivo.

## Almacenamiento

Esta versión usa `localStorage`. Las cartas permanecen en el navegador y origen donde se crearon. Los enlaces a cartas personales no recuperan su contenido desde otro dispositivo. Cambiar de dominio o borrar los datos del navegador tampoco migra ni conserva las cartas.

El sellado es una restricción de interfaz, no cifrado ni custodia segura: el contenido sigue accesible en el almacenamiento del navegador. Un backend será necesario para compartir cartas entre dispositivos y controlar realmente su apertura.
