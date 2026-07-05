# KulinerLumajang.id

> Directory UMKM kuliner Lumajang — daftar, cari, hubungi via WhatsApp.

## Status

🟡 MVP Development — market validation phase

## Stack

- **Frontend:** Astro + Tailwind CSS
- **Backend Admin:** Laravel + Filament
- **Database:** Supabase (PostgreSQL)
- **Payment:** Xendit
- **Deployment:** Vercel (landing page) → Coolify (full app)

## Quick Links

| Resource | Lokasi |
|----------|---------|
| AI Kontrak Kerja | `ai-rules/AGENTS.md` |
| Template Mapping | `ai-rules/README.md` |
| PRD | `~/ai-resume/Projects/kulinerlumajang-prd.md` |
| Landing Page | `~/kulinerlumajang-landing.html` |
| Domain | kulinerlumajang.id (purchased) |

## Project Structure

```
kulinerlumajang-id/
├── ai-rules/          ← IMMUTABLE — AI kontrak & template
├── apps/              ← Kode monolith (git repo)
├── planning/          ← AI output (dari planning-templates/)
├── dev-docs/          ← AI output (dari dev-docs-ai-templates/)
└── reports/           ← AI output (task reports)
```

## How to Start (for AI Agent)

1. Baca `ai-rules/AGENTS.md` (kontrak kerja)
2. Baca `ai-rules/README.md` (mapping template → output)
3. Baca `planning/PROJECT_BRIEF.md` (jika sudah ada)
4. Mulai kerja di branch `dev`, bukan `main`

## Credits

AI governance framework adapted from [docs-ai](https://github.com/frandika06/docs-ai) by frandika06.
