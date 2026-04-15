# Project Instructions

> Lee este archivo primero. Referenciarlo con @INSTRUCTIONS.md al inicio de cada sesión.

## Proyecto
**Nombre:** [NOMBRE DEL PROYECTO]
**Tipo:** [SaaS / App interna / Sitio web / Herramienta]
**Descripción:** [1-2 oraciones — qué hace y para quién]
**URL producción:** [tu-dominio.com]
**Repo:** [github.com/usuario/repo]

---

## Stack — no negociable

| Capa | Tecnología |
|------|-----------|
| Framework | Next.js 15 (App Router) |
| Lenguaje | TypeScript strict |
| Estilos | Tailwind CSS v4 |
| Componentes | shadcn/ui + Magic UI |
| Base de datos | PostgreSQL (Coolify) |
| ORM | Drizzle ORM |
| Auth | Auth.js v5 (NextAuth) |
| Storage | MinIO (Coolify) |
| Deploy | Coolify en VPS — Nixpacks |
| Estado global | Zustand |
| Estado servidor | TanStack Query |
| Formularios | React Hook Form + Zod |

**Sin Supabase. Sin Vercel. Sin Figma. Todo vibecoding en VPS propio.**

---

## Estructura del proyecto

```
src/
├── app/
│   ├── (auth)/          → login, register
│   ├── (dashboard)/     → rutas protegidas
│   └── api/auth/        → Auth.js handler
├── components/
│   ├── ui/              → shadcn/ui + Magic UI + customs
│   └── [feature]/       → componentes por feature
├── lib/
│   ├── db/
│   │   ├── index.ts     → cliente Drizzle
│   │   ├── schema.ts    → tablas y tipos
│   │   └── relations.ts → relaciones
│   ├── auth/
│   │   └── index.ts     → config Auth.js
│   ├── storage/
│   │   └── index.ts     → cliente MinIO
│   └── utils.ts         → cn() y helpers
├── hooks/
├── stores/
└── types/
drizzle/                 → migraciones generadas (no editar)
```

---

## Convenciones

| Elemento | Convención |
|----------|-----------|
| Componentes | `PascalCase.tsx` |
| Hooks | `useCamelCase.ts` |
| Stores | `camelCase.store.ts` |
| Server Actions | `camelCase` en `actions.ts` |
| Tablas DB | `snake_case` plural |
| Código | inglés |
| UI copy | [IDIOMA DEL PROYECTO] |

---

## Reglas críticas

1. Verificar sesión al inicio de cada Server Action: `const session = await auth(); if (!session?.user?.id) return { error: 'No autorizado' }`
2. Sin `any` en TypeScript — nunca
3. Server Components por defecto
4. Mutaciones solo vía Server Actions
5. Inputs validados con Zod antes del DB
6. Secrets nunca con prefijo `NEXT_PUBLIC_`
7. Secrets nunca en código fuente
8. `output: 'standalone'` en next.config.ts (obligatorio para Coolify)
9. Regenerar tipos Drizzle después de cada cambio de schema

---

## Infra en Coolify

| Servicio | Tipo | Notas |
|---------|------|-------|
| App | Application (Nixpacks) | Este repositorio |
| DB | PostgreSQL | Servicio en Coolify |
| Storage | MinIO | Servicio en Coolify |

---

## Entornos

| Entorno | App | DB |
|---------|-----|----|
| local | localhost:3000 | PostgreSQL local o Docker |
| production | Coolify main branch | PostgreSQL en Coolify |

---

## MCPs activos
- **GitHub MCP** → commits y PRs
- **PostgreSQL MCP** → queries directas en desarrollo

---

## Usuarios del producto
[Describir tipos de usuario — quiénes son y qué necesitan]

---

## Estado del proyecto
- [ ] Setup inicial
- [ ] Auth (login / registro / providers)
- [ ] Feature principal
