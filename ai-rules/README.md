# ai-rules/ — Kontrak Kerja AI untuk KulinerLumajang.id

> **Status:** IMMUTABLE — AI TIDAK BOLEH mengubah file apapun di folder ini.
> **Versi:** v1.0-adapted (trimmed dari [docs-ai v1.4.0](https://github.com/frandika06/docs-ai))

## Cara Pakai

1. **PERTAMA KALI:** Baca `AGENTS.md` di folder ini
2. Baca file ini untuk memahami mapping template → output
3. Setiap butuh aturan: cari di sub-folder
4. Setiap butuh buat output: cari template di kolom "Template Source"

---

## Mapping: Template → Output

### `planning/` (Skenario: New Project)

| File Output | Template Source | Keterangan |
|-------------|----------------|------------|
| `planning/PROJECT_BRIEF.md` | `planning-templates/_PROJECT_BRIEF_TEMPLATE.md` | Brief project |
| `planning/prd.md` | `planning-templates/prd.md` | Product Requirements |
| `planning/architecture.md` | `planning-templates/architecture.md` | Tech stack + design |
| `planning/database.md` | `planning-templates/database.md` | ERD + schema |
| `planning/modules.md` | `planning-templates/modules.md` | Module breakdown |
| `planning/api-contract.md` | `planning-templates/api-contract.md` | API contract |
| `planning/wireframe.md` | `planning-templates/wireframe.md` | UI/UX plan |
| `planning/timeline.md` | `planning-templates/timeline.md` | Milestones |

### `dev-docs/` (Skenario: Semua)

| File Output | Template Source | Keterangan |
|-------------|----------------|------------|
| `dev-docs/CHANGELOG.md` | `CHANGELOG-template.md` | Log perubahan |
| `dev-docs/ai/START_HERE.md` | `dev-docs-ai-templates/START_HERE-template.md` | Onboarding |
| `dev-docs/ai/PROJECT_CONTEXT.md` | `dev-docs-ai-templates/PROJECT_CONTEXT-template.md` | System overview |
| `dev-docs/ai/PROJECT_MENTAL_MODEL.md` | `dev-docs-ai-templates/PROJECT_MENTAL_MODEL-template.md` | Patterns |
| `dev-docs/ai/MODULE_MAP.md` | `dev-docs-ai-templates/MODULE_MAP-template.md` | Module mapping |
| `dev-docs/ai/AGENTS.md` | `dev-docs-ai-templates/AGENTS-template.md` | Repo AI contract |
| `dev-docs/ai/CODING_RULES.md` | `dev-docs-ai-templates/CODING_RULES-template.md` | Coding conventions |
| `dev-docs/ai/CURRENT_STATE.md` | `dev-docs-ai-templates/CURRENT_STATE-template.md` | Current state |
| `dev-docs/ai/TASKS.md` | `dev-docs-ai-templates/TASKS-template.md` | Active tasks |
| `dev-docs/ai/VERSION.md` | `dev-docs-ai-templates/VERSION-template.md` | Version tracking |
| `dev-docs/ai/KNOWN_ISSUES.md` | `dev-docs-ai-templates/KNOWN_ISSUES-template.md` | Open issues |
| `dev-docs/ai/TECHNICAL_DEBT.md` | `dev-docs-ai-templates/TECHNICAL_DEBT-template.md` | Tech debt |
| `dev-docs/ai/FINAL_SYSTEM_HANDOVER.md` | `dev-docs-ai-templates/FINAL_SYSTEM_HANDOVER-template.md` | Handover doc |
| `dev-docs/ai/TASKS-ARCHIVE.md` | `TASKS-ARCHIVE-template.md` | Archived tasks |
| `dev-docs/ai/RESOLVED.md` | `RESOLVED-template.md` | Resolved issues |
| `dev-docs/ai/COMMIT_LOG.md` | `COMMIT_LOG-template.md` | Commit log index |
| `dev-docs/ai/commit-logs/YYYY-MM-DD.md` | (tanpa template — AI buat) | Daily commit log |
| `dev-docs/architecture/` | `architecture-templates/` | Architecture docs |

### `reports/` (Task Reports)

| File Output | Template Source |
|-------------|----------------|
| `reports/task/YYYY-MM-DD-{task}.md` | `TASK_REPORT_TEMPLATE.md` |

---

## Aturan Emas

1. **AI TIDAK BOLEH ubah file di `ai-rules/`** — baca, jangan tulis
2. **AI WAJIB buat folder output** saat pertama kali dibutuhkan
3. **AI WAJIB baca template** sebelum membuat/update file output
4. **Output folder di PROJECT ROOT** — paralel dengan `ai-rules/` dan `apps/`
5. **Jika ragu, baca ulang template** — template selalu utuh

---

## Bagian yang Ditunda (Copy dari docs-ai repo saat dibutuhkan)

| Bagian | Kapan Aktifkan |
|--------|---------------|
| `prod-docs-templates/` | Saat production deployment |
| `security/` Part E-Q | Saat fitur/security needs muncul |
| `operations/_templates/` | Saat ada server setup (cron, supervisor) |
| `revamp-templates/` | Saat rewrite/migration |
| `migration/` | Saat docs restructuring |
| `modules-template/_template/` (8 file) | Saat module docs detail |
| `postman/` | Saat ada external dev |
| `integrations/_template.md` | Saat ada 3rd party API |
| `decisions/` | Saat ada architecture decision |
| `testing/` | Saat ada test suite |

> Source: https://github.com/frandika06/docs-ai
