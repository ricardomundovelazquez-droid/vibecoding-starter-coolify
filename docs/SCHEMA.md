# Database Schema

> Actualizar después de cada cambio. Regenerar tipos: `npx drizzle-kit generate && npx drizzle-kit migrate`

## Tablas

### users (gestionada por Auth.js + Drizzle Adapter)
| Columna | Tipo | Descripción |
|---------|------|-------------|
| id | UUID | PK |
| name | text | Nombre |
| email | text | Email único |
| emailVerified | timestamp | Verificación |
| image | text | Avatar URL |
| hashedPassword | text | Para Credentials provider |
| createdAt | timestamptz | Auto |
| updatedAt | timestamptz | Auto |

### [tu_tabla]
| Columna | Tipo | Descripción |
|---------|------|-------------|
| id | UUID | PK |
| userId | UUID | FK → users.id CASCADE |
| createdAt | timestamptz | Auto |
| updatedAt | timestamptz | Auto |

## Relaciones
```
users (1) ──── (N) [tabla]
```

## Historial de migraciones
| Fecha | Descripción |
|-------|-------------|
| | |
