# INSTRUCTIONS.md — Contexto del Proyecto

> Este archivo es el cerebro del proyecto. Todos los agentes lo leen antes de hacer cualquier cosa.
> Llénalo al inicio del proyecto. Entre más completo, mejor trabajan los agentes.

---

## 1. Información general

- **Nombre del proyecto**: [NOMBRE]
- **Cliente / Dueño**: [NOMBRE DEL CLIENTE O "Studio Lemon — interno"]
- **Tipo de proyecto**: [Dashboard interno / App para clientes / Landing + App / Otro]
- **Descripción en una línea**: [Qué hace la app en una sola oración]
- **Descripción completa**: [2-4 párrafos explicando el problema que resuelve y cómo]

---

## 2. Usuarios del sistema

| Tipo de usuario | Qué puede hacer | Notas |
|---|---|---|
| [Ej: Administrador] | [Ej: Ver todo, editar, eliminar] | [Ej: Solo 1 usuario admin] |
| [Ej: Cliente] | [Ej: Ver sus pedidos, descargar facturas] | |

---

## 3. Stack del proyecto

> Llena esto DESPUÉS de correr @architect o de tomar la decisión del stack manualmente.

- **Framework**: Next.js 15 (App Router) ← cambiar si @architect recomienda otro
- **ORM**: Drizzle ORM
- **Base de datos**: PostgreSQL
- **Auth**: Auth.js v5
- **UI**: shadcn/ui + Magic UI
- **Deploy**: Coolify + Nixpacks

---

## 4. Módulos activos

> Pon [x] en los módulos que este proyecto SÍ usa. Los agentes ignorarán los desmarcados.

- [x] **Auth** — Login y manejo de sesiones
- [ ] **Storage** — Subida y gestión de archivos (MinIO)
- [ ] **Email** — Emails transaccionales (Resend)
- [ ] **Pagos** — Procesamiento de pagos (Stripe)
- [x] **Google OAuth** — Login con cuenta de Google
- [ ] **Tiempo real** — Notificaciones o chat en vivo

---

## 5. Providers de autenticación activos

> Solo marca los que este proyecto usará

- [x] Email + Contraseña
- [ ] Google OAuth
- [ ] Teléfono + Contraseña (OTP por SMS)
- [ ] GitHub
- [ ] Otro: ___________

---

## 6. Páginas / secciones principales

> Lista las pantallas que tendrá la app. Esto ayuda a los agentes a entender el scope.

| Ruta | Descripción | Acceso |
|---|---|---|
| `/` | [Ej: Landing page o redirect al login] | [Público / Autenticado] |
| `/dashboard` | [Ej: Panel principal] | [Autenticado] |
| `/login` | [Ej: Formulario de acceso] | [Público] |
| [agregar más...] | | |

---

## 7. Entidades principales del sistema

> Las "cosas" que la app maneja. Ayuda al agente @database a diseñar el schema.

| Entidad | Descripción |
|---|---|
| [Ej: Usuario] | [Ej: Persona que accede al sistema] |
| [Ej: Cotización] | [Ej: Presupuesto enviado a un cliente] |
| [agregar más...] | |

---

## 8. Integraciones externas

> APIs o servicios de terceros que este proyecto usa o va a usar.

| Servicio | Para qué | Status |
|---|---|---|
| [Ej: Facturapi] | [Ej: Generar CFDIs] | [Planeado / Activo] |
| [agregar más...] | | |

---

## 9. Variables de entorno

> Estado actual de la configuración. Actualiza esto conforme vayas llenando tu .env.local

| Variable | Status |
|---|---|
| DATABASE_URL | [ ] Pendiente / [x] Lista |
| AUTH_SECRET | [ ] Pendiente / [x] Lista |
| AUTH_URL | [ ] Pendiente / [x] Lista |
| GOOGLE_CLIENT_ID | [ ] Pendiente / N/A |
| GOOGLE_CLIENT_SECRET | [ ] Pendiente / N/A |
| MINIO_ENDPOINT | [ ] Pendiente / N/A |
| RESEND_API_KEY | [ ] Pendiente / N/A |

---

## 10. Convenciones del proyecto

> Reglas específicas de este proyecto. Los agentes las respetan.

- **Idioma del código**: Inglés (variables, funciones, componentes)
- **Idioma de la UI**: [Español / Inglés / Ambos]
- **Idioma de comentarios**: Español
- **Formato de fechas**: [DD/MM/YYYY o según necesidad del cliente]
- **Moneda**: [MXN / USD]
- **Zona horaria**: America/Mexico_City

---

## 11. Lo que NO debe hacer el sistema

> Límites explícitos del proyecto. Ayuda a evitar scope creep.

- [Ej: No manejar pagos (el cliente paga por transferencia)]
- [Ej: No enviar emails en esta versión]
- [agregar más...]

---

## 12. Notas adicionales para los agentes

> Cualquier cosa específica que los agentes deben saber sobre este proyecto.

[Espacio libre para notas, contexto del cliente, decisiones tomadas, etc.]
