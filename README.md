# Vibecoding Starter — Coolify Edition

Next.js 15 · PostgreSQL · Drizzle ORM · Auth.js v5 · Coolify

---

## ¿Qué es esto?

Un template para arrancar proyectos web rápido, sin configurar todo desde cero cada vez.
Incluye agentes de Cursor preconfigurados que te ayudan a elegir el stack, configurar variables y construir features.

---

## Cómo empezar un proyecto nuevo

### Paso 1 — Crear tu repo (no clonar directo)

> ⚠️ No hagas `git clone` de este repo directamente. Usa el botón de template para que tu proyecto tenga su propio repositorio separado.

1. Click en el botón verde **"Use this template"** → **"Create a new repository"**
2. Ponle nombre a tu proyecto (ej: `cotizador-cliente-x`)
3. Click en **"Create repository"**
4. Copia la URL del repo nuevo

### Paso 2 — Abrir en Cursor

1. Abrir Cursor → `Ctrl+Shift+P` → `Git: Clone` → pegar URL
2. Elegir carpeta → Cursor abre el proyecto
3. Abrir terminal: `` Ctrl+` ``
4. Instalar dependencias:

```bash
npm install
npx shadcn@latest init
cp .env.example .env.local
```

### Paso 3 — Definir el stack con el agente

En el chat de Cursor:

```
@architect tengo un nuevo proyecto: [describe qué hace la app, para quién es, y si necesita SEO]
```

El agente te hace preguntas y genera `docs/STACK.md` con las tecnologías recomendadas para ese proyecto específico. El stack no está cerrado — si Vite es mejor que Next.js para tu caso, el agente te lo dice.

### Paso 4 — Configurar variables de entorno

```
@setup inicia la configuración de variables de entorno
```

El agente lee tu `.env.example` y te guía variable por variable en español, explicando qué es cada una y de dónde obtenerla.

### Paso 5 — Llenar el contexto del proyecto

Abrir `docs/INSTRUCTIONS.md` y llenar:
- Nombre y descripción del proyecto
- Usuarios del sistema
- **Módulos activos** (marca solo los que necesitas: Auth, Storage, Email, Pagos)
- Páginas principales
- Entidades del sistema

Este archivo es lo que leen todos los agentes. Entre más completo, mejor trabajan.

### Paso 6 — Base de datos

1. Crear PostgreSQL en Coolify: **New Resource → Database → PostgreSQL**
2. Copiar el Connection URL → pegarlo en `DATABASE_URL` de tu `.env.local`
3. Correr migraciones:

```bash
npx drizzle-kit generate
npx drizzle-kit migrate
```

### Paso 7 — Elegir design system (opcional)

```bash
# Elegante, fintech (estilo Stripe)
curl -o docs/DESIGN.md https://getdesign.md/stripe/design-md

# Dark, minimalista (estilo Linear)
curl -o docs/DESIGN.md https://getdesign.md/linear/design-md

# Clean, workspace (estilo Notion)
curl -o docs/DESIGN.md https://getdesign.md/notion/design-md
```

Ver catálogo completo en: https://getdesign.md

O editar `docs/DESIGN.md` directamente con los colores de tu marca.

---

### 🎨 Skills de diseño (opcional, bajo demanda)

Estos skills le enseñan a tu agente AI principios reales de diseño. **No se activan solos** — los instalas una vez por proyecto y los invocas cuando los necesitas desde el chat de Cursor.

#### Instalar ambos skills

```bash
npx skills add pbakaus/impeccable
npx skills add emilkowalski/skill
```

---

#### Impeccable — Vocabulario de diseño + 23 comandos

**¿Para qué sirve?**
Le da a tu agente conocimiento profundo de tipografía, color, espaciado, motion y UX writing. Incluye detección de "AI slop" (patrones genéricos que genera la IA por default).

**¿Cuándo usarlo?**
- Al construir cualquier vista nueva o landing
- Cuando el diseño se ve genérico o "hecho por IA"
- Para iterar sobre UI con comandos precisos

**Comandos clave:**

```
/impeccable redo este hero         → rediseña un componente
/impeccable audit checkout         → audita problemas de diseño
/impeccable typeset                → mejora tipografía
/impeccable colorize               → trabaja la paleta de color
/impeccable teach                  → configura el contexto de diseño del proyecto
```

> 🔗 [impeccable.style](https://impeccable.style)

---

#### Emil Kowalski Skill — Animaciones y polish de UI

**¿Para qué sirve?**
Skill basado en los artículos de Emil Kowalski (autor de Sonner, Vaul). Cubre animaciones, microinteracciones, performance y criterio de diseño de alto nivel.

**¿Cuándo usarlo?**
- Al revisar o mejorar animaciones de un componente
- En la fase de polish, antes de entregar al cliente
- Cuando algo "se siente" correcto funcionalmente pero le falta vida

**Cómo invocarlo en Cursor:**

```
Usa el skill de emilkowalski para revisar las animaciones de este componente
```

> ⚠️ El propio autor recomienda usarlo puntualmente, no dejarlo siempre activo.

> 🔗 [emilkowal.ski/skill](https://emilkowal.ski/skill)

---

### Paso 8 — Primer arranque

```bash
npm run dev
# App en http://localhost:3000
```

### Paso 9 — Empezar a construir

```
@docs/INSTRUCTIONS.md @orchestrator quiero construir [describe el primer feature]
```

---

## Módulos disponibles

El template no obliga a usar todo. En `docs/INSTRUCTIONS.md` activas solo lo que necesitas:

| Módulo | Tecnología | Cuándo usarlo |
|---|---|---|
| Auth básica | Auth.js v5 | Siempre que haya login |
| Google OAuth | Auth.js v5 + Google | Cuando quieres "Entrar con Google" |
| Storage | MinIO | Solo si el proyecto sube archivos o imágenes |
| Email | Resend | Confirmaciones, notificaciones por correo |
| Pagos | Stripe | Si el proyecto cobra algo |
| AI / LLM | Groq / OpenRouter | Features con inteligencia artificial |

Los agentes solo generan código de los módulos que están activos.

---

## Agentes disponibles en Cursor

| Cuándo usarlo | Agente |
|---|---|
| Elegir el stack del proyecto | `@architect` |
| Configurar variables de entorno | `@setup` |
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

---

## Cloud Agents (tareas en segundo plano)

Cursor permite mandar tareas largas al background mientras sigues trabajando en otra cosa.

**Cómo activarlo:**
1. Cursor Settings → Cloud Agents → **"Open"** en Manage Settings
2. Conectar tu cuenta de GitHub
3. En el chat aparece el botón **"Background"** junto al de enviar

**Cuándo usarlo:**
- Features complejos que tardan varios minutos
- Cuando quieres que un agente trabaje mientras tú revisas otra cosa

---

## Stack base

| Capa | Tecnología |
|---|---|
| Framework | Next.js 15 (App Router) — o el que recomiende `@architect` |
| ORM | Drizzle ORM |
| Base de datos | PostgreSQL |
| Auth | Auth.js v5 |
| UI | shadcn/ui + Magic UI |
| Deploy | Coolify + Nixpacks |
| Estado (opcional) | Zustand |

---

## Estructura del proyecto

```
.cursor/
└── rules/
    ├── stack.mdc         → Reglas globales del stack
    ├── architect.mdc     → Elige el stack para el proyecto
    ├── setup.mdc         → Configura variables de entorno
    ├── orchestrator.mdc  → Coordina todas las tareas
    ├── ui-design.mdc     → UI con shadcn + Magic UI
    ├── database.mdc      → Drizzle ORM
    ├── auth.mdc          → Auth.js v5
    ├── storage.mdc       → MinIO
    ├── frontend.mdc      → Next.js App Router
    ├── deploy.mdc        → Coolify
    ├── auditors.mdc      → Calidad y seguridad
    ├── ux-research.mdc   → Flows y arquitectura
    └── ux-copy.mdc       → Microcopy

docs/
├── NUEVO_PROYECTO.md     → Checklist completo de inicio
├── INSTRUCTIONS.md       → Contexto del proyecto (llenar)
├── STACK.md              → Stack elegido (genera @architect)
├── PRD.md                → Qué se construye
├── DESIGN.md             → Sistema de diseño
├── SCHEMA.md             → Esquema de base de datos
└── DECISIONS.md          → Decisiones técnicas

src/
├── app/                  → Rutas (App Router)
├── components/ui/        → shadcn/ui + customs
├── lib/
│   ├── db/               → Drizzle: index, schema, relations
│   ├── auth/             → Auth.js config
│   └── storage/          → Cliente MinIO
├── hooks/
├── stores/               → Zustand
└── types/
```

---

## Deploy en Coolify

### Servicios a crear

1. **PostgreSQL** → New Resource → Database → PostgreSQL
2. **MinIO** (si el proyecto lo necesita) → New Resource → Service → MinIO
3. **Aplicación** → New Resource → Application → conectar repo → Build Pack: **Nixpacks**

### Variables de entorno en Coolify

Copiar todas las variables del `.env.example` a Coolify con los valores de producción.

### Checklist antes de deploy

- `npm run build` pasa sin errores en local
- Variables configuradas en Coolify
- `npx drizzle-kit migrate` ejecutado contra la DB de producción
- `AUTH_URL` apunta al dominio real (no localhost)
- `next.config.ts` tiene `output: 'standalone'`