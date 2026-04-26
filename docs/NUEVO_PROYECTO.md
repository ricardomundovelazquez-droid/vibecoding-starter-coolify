# NUEVO PROYECTO — Checklist de inicio

Sigue este checklist cada vez que empieces un proyecto nuevo desde el template.
Tacha cada paso conforme lo completes.

---

## FASE 1 — Crear el repo (GitHub, antes de abrir Cursor)

- [ ] Ir a `github.com/ricardomundovelazquez-droid/vibecoding-starter-coolify`
- [ ] Click en **"Use this template"** → **"Create a new repository"**
- [ ] Nombrar el repo nuevo (ej: `nombre-del-proyecto`)
- [ ] Click en **"Create repository"**
- [ ] Copiar la URL del repo nuevo

---

## FASE 2 — Setup local (Cursor)

- [ ] Abrir Cursor → `Ctrl+Shift+P` → Git: Clone → pegar URL del repo nuevo
- [ ] Elegir carpeta → Cursor abre el proyecto
- [ ] Abrir terminal: `` Ctrl+` ``
- [ ] Instalar dependencias: `npm install`
- [ ] Inicializar shadcn: `npx shadcn@latest init`
- [ ] Copiar env: `cp .env.example .env.local`

---

## FASE 3 — Elegir el stack (opcional pero recomendado)

- [ ] En el chat de Cursor escribir: `@architect tengo un nuevo proyecto, [describe el proyecto en 2-3 líneas]`
- [ ] Responder las preguntas del agente
- [ ] El agente genera `docs/STACK.md` con las decisiones
- [ ] Revisar y aprobar el stack

---

## FASE 4 — Configurar el contexto del proyecto

- [ ] Abrir `docs/INSTRUCTIONS.md`
- [ ] Llenar la sección **1. Información general**
- [ ] Definir los **usuarios del sistema** (sección 2)
- [ ] Activar los **módulos** que necesitas (sección 4) — quitar [ ] y poner [x]
- [ ] Activar los **providers de auth** que usarás (sección 5)
- [ ] Listar las **páginas principales** (sección 6)
- [ ] Definir las **entidades** del sistema (sección 7)

---

## FASE 5 — Variables de entorno

- [ ] En el chat de Cursor escribir: `@setup inicia la configuración de variables de entorno`
- [ ] Seguir las instrucciones del agente variable por variable
- [ ] Actualizar el checklist de variables en `docs/INSTRUCTIONS.md` (sección 9)

---

## FASE 6 — Base de datos

- [ ] Crear PostgreSQL en Coolify: New Resource → Database → PostgreSQL
- [ ] Copiar el Connection URL y pegarlo en `DATABASE_URL` del `.env.local`
- [ ] Generar migración inicial: `npx drizzle-kit generate`
- [ ] Correr migración: `npx drizzle-kit migrate`

---

## FASE 7 — Elegir design system (opcional)

Elige una opción:

**Opción A — Usar estilo de una marca:**
```bash
# Ejemplos:
curl -o docs/DESIGN.md https://getdesign.md/stripe/design-md   # Elegante, fintech
curl -o docs/DESIGN.md https://getdesign.md/linear/design-md   # Dark, minimalista
curl -o docs/DESIGN.md https://getdesign.md/notion/design-md   # Clean, workspace
```

**Opción B — Crear el tuyo:**
```bash
# El archivo ya está, solo ábrelo y edítalo:
open docs/DESIGN.md
```

**Opción C — Dejar shadcn por defecto:**
No hacer nada.

- [ ] Design system elegido o decisión de dejarlo por default

---

## FASE 8 — Primera prueba

- [ ] Correr el proyecto: `npm run dev`
- [ ] Abrir `http://localhost:3000`
- [ ] Confirmar que carga sin errores

---

## FASE 9 — Primer push al nuevo repo

```bash
git add .
git commit -m "feat: setup inicial del proyecto"
git push
```

- [ ] Push exitoso al repo nuevo (no al template)

---

## FASE 10 — Empezar a construir

- [ ] Abrir el chat de Cursor
- [ ] Escribir: `@docs/INSTRUCTIONS.md @orchestrator quiero construir [tu primer feature]`
- [ ] El orquestador coordina el resto

---

## Notas

- El template **nunca se modifica** con código de proyecto
- Los cambios al template (mejoras a los agentes, etc.) se hacen por separado
- Si encuentras un bug o mejora al template, créala en el repo del template directamente
