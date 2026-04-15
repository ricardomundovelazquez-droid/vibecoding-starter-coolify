# Vibecoding Starter — Coolify Edition

Next.js 15 + PostgreSQL + Auth.js + MinIO + Coolify (VPS propio)

## Stack
| Capa | Tecnología |
|------|-----------|
| Framework | Next.js 15 (App Router) |
| ORM | Drizzle ORM |
| Auth | Auth.js v5 |
| Storage | MinIO |
| Deploy | Coolify (Nixpacks) |
| UI | shadcn/ui + Magic UI |

---

## Setup para proyecto nuevo

### 1. Clonar
```bash
git clone https://github.com/[tu-usuario]/vibecoding-starter-coolify.git mi-proyecto
cd mi-proyecto
git remote set-url origin https://github.com/[tu-usuario]/mi-proyecto.git
```

### 2. Instalar
```bash
npm install
npx shadcn@latest init
```

### 3. Variables de entorno
```bash
cp .env.example .env.local
# Llenar: DATABASE_URL, AUTH_SECRET, AUTH_URL, MinIO vars
```

### 4. Configurar MCPs
Editar `.cursor/mcp.json`:
- Reemplazar `TU_GITHUB_TOKEN`
- Reemplazar la URL de PostgreSQL con tu `DATABASE_URL` local

### 5. Migraciones iniciales
```bash
npx drizzle-kit generate
npx drizzle-kit migrate
```

### 6. Llenar el contexto
Editar `docs/INSTRUCTIONS.md` con el nombre, descripción y usuarios del proyecto.

### 7. Arrancar
```bash
npm run dev
```

---

## Cómo usar los agentes en Cursor

### Iniciar cualquier tarea
```
@INSTRUCTIONS.md @orchestrator quiero construir [describe el feature]
```

### Agentes disponibles
| Agente | Para qué |
|--------|----------|
| `@orchestrator` | Planear y coordinar todo |
| `@ux-research` | Flows, sitemap, personas |
| `@ui-design` | Componentes shadcn/ui + Magic UI |
| `@nextjs` | Páginas y layouts |
| `@database` | Schema Drizzle, migraciones, queries |
| `@auth` | Auth.js, providers, sesiones |
| `@storage` | MinIO — subir/obtener archivos |
| `@deploy` | Coolify, env vars, dominio |
| `@auditors` | Calidad, seguridad, TypeScript |

### Modelo
Dejar en **Auto** — maximiza duración de tokens.

---

## Deploy en Coolify

1. Crear servicio PostgreSQL en Coolify
2. Crear servicio MinIO en Coolify
3. New Application → conectar repo → Build Pack: **Nixpacks**
4. Agregar todas las variables del `.env.example`
5. Deploy → dominio → SSL automático

**Importante:** `next.config.ts` ya tiene `output: 'standalone'` configurado.
