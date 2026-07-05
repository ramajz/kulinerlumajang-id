# Coding Standards — KulinerLumajang.id

> **Status:** IMMUTABLE — AI hanya baca, tidak boleh ubah.
> **Stack:** Astro (frontend) + Laravel/Filament (backend admin) + Supabase (database)

---

## 1. File Size Limits

| Layer | Max Lines | Jika Over |
|-------|-----------|-----------|
| Controller | 1000 | Split ke service |
| Service | 800 | Split ke helper/utility |
| Model | 300 | Extract trait |
| Route file | 200 | Split per module |
| Astro component | 300 | Split ke sub-components |

## 2. Separation of Concerns

**Backend (Laravel):**
```
Controller → Service → Repository → Model
```
- Controller: HTTP handling only (validate request, call service, return response)
- Service: Business logic
- Repository: Data access (query builder/Eloquent)
- Model: Data definition + relationships

**Frontend (Astro):**
- Layout: Structure only (no business logic)
- Component: UI + minimal logic
- Page: Compose components + fetch data

## 3. Route Organization

- 1 route file per module (max 200 lines)
- Laravel: `routes/web.php` untuk admin, `routes/api.php` untuk public API
- Astro: file-based routing di `src/pages/`

## 4. Anti-Patterns (DILARANG)

- ❌ **God Controller** — 1 controller handle everything
- ❌ **Fat Model** — business logic di model
- ❌ **Deep nesting** — max 3 level if/for
- ❌ **Magic numbers** — guna constant/config
- ❌ **Hardcoded credential** — MUST `.env`
- ❌ **Copy-paste code** — extract ke shared utility

## 5. Framework Conventions

**Laravel:**
- Resource Controller untuk CRUD
- Form Request untuk validation
- Eloquent scope untuk query filter
- Filament Resource untuk admin panel

**Astro:**
- `.astro` untuk pages, `.tsx` untuk interactive components
- Frontmatter untuk data fetching
- Islands architecture — interaktif hanya di component yang butuh JS

## 6. Refactoring Checklist (Sebelum Commit)

1. File size under limit?
2. No God Controller/Fat Model?
3. No hardcoded values?
4. Separation of Concerns followed?
5. No duplicate code nearby?

## 7. Naming Conventions

| Context | Convention | Example |
|---------|-----------|---------|
| Laravel controller | PascalCase | `ListingController` |
| Laravel method | camelCase | `getFeaturedListings` |
| Database table | snake_case | `umkm_listings` |
| Astro component | PascalCase | `ListingCard.astro` |
| CSS class | BEM atau utility | `listing-card__title` |
| .env variable | UPPER_SNAKE | `XENDIT_API_KEY` |

> Untuk detail lengkap (code review questions, code smell tools, real-world examples): lihat [docs-ai repo](https://github.com/frandika06/docs-ai) `ai-rules/coding-standards/`.
