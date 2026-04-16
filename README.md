# Vibecoding Starter — Coolify Edition

Next.js 15 · PostgreSQL · Drizzle ORM · Auth.js v5 · MinIO · Coolify (VPS propio)

---

## Stack

| Capa | Tecnología |
|------|-----------|
| Framework | Next.js 15 (App Router) |
| ORM | Drizzle ORM |
| Auth | Auth.js v5 |
| Storage | MinIO |
| Deploy | Coolify + Nixpacks |
| UI | shadcn/ui + Magic UI + DESIGN.md |

---

## Inicio rápido

### Paso 1 — Clonar el starter

```bash
git clone https://github.com/[tu-usuario]/vibecoding-starter-coolify.git mi-proyecto
cd mi-proyecto
git remote set-url origin https://github.com/[tu-usuario]/mi-proyecto.git
```

### Paso 2 — Instalar dependencias

```bash
npm install
npx shadcn@latest init
```

Cuando shadcn pregunte por el estilo base, elige el que más se acerque a tu diseño (puedes cambiarlo después con el DESIGN.md).

### Paso 3 — Variables de entorno

```bash
cp .env.example .env.local
```

Abrir `.env.local` y llenar:
- `DATABASE_URL` — string de conexión PostgreSQL
- `AUTH_SECRET` — ejecutar `openssl rand -base64 32` y pegar el resultado
- `AUTH_URL` — tu dominio o `http://localhost:3000` para desarrollo
- Variables de MinIO — las obtienes del panel de Coolify al crear el servicio

### Paso 4 — Elegir el sistema de diseño (DESIGN.md)

Tienes tres opciones:

**Opción A — Usar el estilo de una marca existente**

Elige la marca que más se parece a la estética que quieres y ejecuta:

```bash
# Stripe — morado elegante, fintech premium
curl -o docs/DESIGN.md https://getdesign.md/stripe/design-md

# Linear — dark, minimalista, herramienta de productividad
curl -o docs/DESIGN.md https://getdesign.md/linear/design-md

# Vercel — blanco y negro, precisión, developer tools
curl -o docs/DESIGN.md https://getdesign.md/vercel/design-md

# Notion — clean, editorial, workspace
curl -o docs/DESIGN.md https://getdesign.md/notion/design-md

# Airbnb — cálido, coral, fotografía
curl -o docs/DESIGN.md https://getdesign.md/airbnb/design-md

# Apple — espacio en blanco premium, SF Pro
curl -o docs/DESIGN.md https://getdesign.md/apple/design-md

# Spotify — verde vibrante en dark, música
curl -o docs/DESIGN.md https://getdesign.md/spotify/design-md

# Shopify — dark cinematic, neon verde
curl -o docs/DESIGN.md https://getdesign.md/shopify/design-md
```

Ver catálogo completo de 55+ marcas en: https://getdesign.md

**Opción B — Crear tu propio design system**

El archivo `docs/DESIGN.md` ya viene con un template vacío de 9 secciones. Ábrelo y llena los colores, tipografía, spacing y componentes de tu marca.

```bash
# Ya está en el repo, solo abrir y editar:
open docs/DESIGN.md
```

**Opción C — Dejar shadcn por defecto**

No hacer nada. shadcn/ui y Magic UI funcionan perfectamente sin DESIGN.md. Puedes agregar uno después cuando tengas claro el estilo.

### Paso 5 — Configurar MCPs en Cursor

Abrir `.cursor/mcp.json` y reemplazar:
- `TU_GITHUB_TOKEN` — crear en github.com → Settings → Developer settings → Personal access tokens
- La URL de PostgreSQL — usar tu `DATABASE_URL` local

```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "ghp_tu_token_aqui"
      }
    },
    "postgres": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-postgres", "postgresql://user:pass@localhost:5432/dbname"]
    }
  }
}
```

### Paso 6 — Migraciones iniciales

```bash
npx drizzle-kit generate
npx drizzle-kit migrate
```

### Paso 7 — Llenar el contexto del proyecto

Abrir `docs/INSTRUCTIONS.md` y llenar los campos marcados con `[CORCHETES]`:
- Nombre del proyecto
- Tipo y descripción
- Usuarios del producto

Este archivo es el contexto principal que leen los agentes. Sin él trabajan a ciegas.

### Paso 8 — Arrancar

```bash
npm run dev
# App en http://localhost:3000
```

---

## Cómo trabajar con los agentes en Cursor

### Iniciar cualquier tarea

```
@docs/INSTRUCTIONS.md @orchestrator quiero construir [describe el feature]
```

El orquestador crea el plan completo y activa los agentes en el orden correcto.

### Cuando hay UI involucrada — incluir el DESIGN.md

```
@docs/INSTRUCTIONS.md @docs/DESIGN.md @orchestrator quiero construir [feature con UI]
```

Con el DESIGN.md en el contexto, el agente de UI genera componentes que respetan tu sistema de diseño desde el primer componente.

### Catálogo de agentes

| Cuándo usarlo | Agente |
|---------------|--------|
| Planear y coordinar cualquier tarea | `@orchestrator` |
| Definir flows, sitemap, personas | `@ux-research` |
| Componentes UI, design system | `@ui-design` |
| Copy, CTAs, errores, empty states | `@copy` |
| Páginas y layouts Next.js | `@nextjs` |
| Schema, migraciones, queries (Drizzle) | `@database` |
| Auth.js, providers, sesiones | `@auth` |
| MinIO — subir y gestionar archivos | `@storage` |
| Server Actions, Route Handlers | `@api` |
| Coolify, env vars, dominio | `@deploy` |
| Revisión de calidad al terminar | `@auditors` |

### Modelo recomendado

Dejar en **Auto** — Cursor elige el modelo según la complejidad.
Esto maximiza la duración de tus tokens.

---

## Cómo cambiar el design system

Puedes cambiar el DESIGN.md en cualquier momento del proyecto:

```bash
# Descargar otro
curl -o docs/DESIGN.md https://getdesign.md/linear/design-md

# Luego pedirle al agente que actualice los tokens
@docs/DESIGN.md @ui-design actualiza globals.css con los nuevos tokens
```

El agente actualiza `src/app/globals.css` y todos los componentes nuevos usarán el nuevo sistema. Los componentes existentes se actualizan si se lo pides explícitamente.

---

## Deploy en Coolify

### Servicios a crear en Coolify

1. **PostgreSQL** — New Resource → Database → PostgreSQL
   - Guardar las credenciales generadas

2. **MinIO** — New Resource → Service → MinIO
   - Acceder al panel en el puerto 9001
   - Crear un bucket y generar access key/secret key

3. **Aplicación** — New Resource → Application
   - Conectar el repositorio de GitHub
   - Build Pack: **Nixpacks** (detección automática)
   - Agregar todas las variables del `.env.example`
   - Domain → tu dominio → Enable SSL

### Variables de entorno en Coolify

Copiar todas las variables del `.env.example` a Coolify (Settings → Environment Variables) con los valores reales de producción:

```
DATABASE_URL       → string de conexión al PostgreSQL de Coolify
AUTH_SECRET        → generar nuevo con: openssl rand -base64 32
AUTH_URL           → https://tu-dominio.com (sin trailing slash)
MINIO_ENDPOINT     → nombre del servicio MinIO en Coolify
...
```

### Checklist antes de hacer deploy

- [ ] `npm run build` pasa sin errores en local
- [ ] `.env.example` tiene todas las variables necesarias
- [ ] Variables configuradas en Coolify
- [ ] `npx drizzle-kit migrate` ejecutado contra la DB de producción
- [ ] `AUTH_URL` apunta al dominio correcto (no localhost)
- [ ] Bucket de MinIO creado y configurado
- [ ] `next.config.ts` tiene `output: 'standalone'`

---

## Estructura de archivos

```
.cursor/
├── mcp.json              → MCPs: GitHub + PostgreSQL
└── rules/                → Agentes (no modificar)
    ├── stack.mdc         → Reglas globales del stack (siempre activo)
    ├── orchestrator.mdc  → PM que coordina todo
    ├── ui-design.mdc     → UI con shadcn + Magic UI + DESIGN.md
    ├── database.mdc      → Drizzle ORM
    ├── auth.mdc          → Auth.js v5
    ├── storage.mdc       → MinIO
    ├── frontend.mdc      → Next.js App Router
    ├── deploy.mdc        → Coolify
    ├── auditors.mdc      → Calidad, seguridad, TypeScript
    ├── ux-research.mdc   → Flows y arquitectura de info
    └── ux-copy.mdc       → Microcopy e i18n
docs/
├── INSTRUCTIONS.md       → Contexto del proyecto (LLENAR)
├── PRD.md                → Qué se construye (LLENAR)
├── DESIGN.md             → Sistema de diseño (ELEGIR O CREAR)
├── SCHEMA.md             → Esquema DB (actualizar con migraciones)
└── DECISIONS.md          → Decisiones técnicas
drizzle/                  → Migraciones generadas (no editar)
src/
├── app/                  → Rutas (App Router)
├── components/ui/        → shadcn/ui + Magic UI + customs
├── lib/
│   ├── db/               → Drizzle: index.ts, schema.ts, relations.ts
│   ├── auth/             → Auth.js config
│   └── storage/          → Cliente MinIO
├── hooks/
├── stores/               → Zustand
└── types/
```
