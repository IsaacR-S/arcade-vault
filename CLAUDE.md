# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Proyecto

Arcade Vault: plataforma para jugar online y competir por la mayor cantidad de puntos. Se desarrolla con Spec Driven Design (comandos `/spec` y `/spec-impl`), siguiendo las prácticas de https://github.com/Klerith/fernando-skills (instalado con `npx skills@latest add Klerith/fernando-skills`). Actualmente es el scaffold inicial de Create Next App (solo `app/layout.tsx` y `app/page.tsx`).

## Comandos

- `npm run dev` — servidor de desarrollo (Turbopack)
- `npm run build` / `npm run start` — build y servidor de producción
- `npm run lint` — ESLint (flat config en `eslint.config.mjs`; no hay script de tests configurado)

## Next.js: versión con cambios incompatibles

Next 16.4.2 + React 19.3. Según `AGENTS.md`, las APIs y convenciones difieren de lo que se conoce: **leer la guía relevante en `node_modules/next/dist/docs/`** (`01-app`, `02-pages`, `03-architecture`, `04-community`) antes de escribir código y respetar los avisos de deprecación.

## Arquitectura / configuración no obvia

- App Router en `app/`. El layout raíz tipa props con el helper global `LayoutProps<"/">` (sin importarlo).
- `next.config.ts` activa `cacheComponents`, `partialPrefetching` y `experimental.agentFeedback`; `cacheComponents` cambia el modelo de caché/renderizado, así que consultar la documentación antes de usar fetch/datos dinámicos.
- Tailwind CSS v4 vía `@tailwindcss/turbopack` configurado como loader de `*.css` en `next.config.ts` (no hay `tailwind.config`; los tokens se definen con `@theme inline` en `app/globals.css`, con modo oscuro por `prefers-color-scheme`).
- Fuentes Geist / Geist Mono con `next/font/google`, expuestas como variables CSS.
