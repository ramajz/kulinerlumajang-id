# AGENTS.md — Kontrak Kerja AI untuk KulinerLumajang.id

> **Status:** IMMUTABLE — AI hanya baca, TIDAK boleh ubah. Output AI = folder `planning/`, `dev-docs/`, `reports/`.
> **Project:** KulinerLumajang.id — directory UMKM kuliner Lumajang
> **Stack:** Astro + Laravel/Filament + Supabase + Xendit

---

## 0) Project Structure

### Git Location
**`.git/` di `apps/` (monolith).** Git commands HARUS dari dalam `apps/`:

```bash
cd apps
git status
git pull --rebase
```

❌ DILARANG `git init` di root — root BUKAN git repo

### Target Structure

```
kulinerlumajang-id/
├── ai-rules/               ← IMMUTABLE — AI hanya baca
├── apps/                    ← Kode (git repo disini)
├── planning/               ← OUTPUT dari ai-rules/planning-templates/
├── dev-docs/               ← OUTPUT dari ai-rules/dev-docs-ai-templates/
└── reports/                ← OUTPUT dari ai-rules/TASK_REPORT_TEMPLATE.md
```

### IMMUTABLE vs OUTPUT

| Area | Sifat | Oleh |
|------|-------|------|
| `ai-rules/` | IMMUTABLE | Human (copy dari template) |
| `apps/` | Kode | AI + Human |
| `planning/` | OUTPUT | AI dari planning-templates/ |
| `dev-docs/` | OUTPUT | AI dari dev-docs-ai-templates/ |
| `reports/` | OUTPUT | AI dari TASK_REPORT_TEMPLATE.md |

---

## 1) Aturan Keras

1. **DILARANG commit/push ke `main`** — AI kerja di `dev` atau `feat/*`
2. **DILARANG `git push --force`** ke main atau dev
3. **DILARANG ubah `.env`** tanpa izin eksplisit user
4. **DILARANG refactor besar** tanpa permintaan jelas
5. **WAJIB batch kecil**: 1 perubahan → 1 commit → push
6. **WAJIB baca template di `ai-rules/`** sebelum membuat file output
7. **WAJIB sinkronisasi `dev-docs/`** di setiap akhir task
8. **WAJIB ikut security standard** (ai-rules/security/) — proaktif, bukan menunggu diminta
9. **WAJIB ikut coding standards** (ai-rules/coding-standards/CODING_STANDARDS.md)
10. **DILARANG credential di file .md di dalam `apps/`** — HANYA `.env`
11. **DILARANG emoji/icon di kode** — ✅❌ hanya di checklist docs

---

## 2) Preflight Wajib (Sebelum Mulai)

```bash
cd apps
git status
git branch --show-current   # HARUS bukan main
git pull --rebase
```

Jika di main: `git checkout dev && git pull --rebase`

Checkpoint sebelum AI ubah apa pun:
```bash
cd apps && git add -A && git commit -m "chore: checkpoint before AI changes" && git push
```

---

## 3) Work Loop per Batch

### A) Rencana (maks 6 bullet)
- Apa, file target, risiko, cara verifikasi

### B) Implementasi minimal
- 1 batch = 1 fitur atau 1 fix, jangan campur

### C) Self-review
```bash
cd apps && git diff
```
Sebut: inti perubahan, file yang berubah, hal yang perlu dicek manual

### D) Commit + Push
```bash
cd apps && git add -A && git commit -m "feat: <ringkas>" && git push
```

Format commit: `feat:`, `fix:`, `refactor:`, `chore:`, `docs:`

---

## 4) Merge Policy: dev → main

```bash
cd apps
git checkout dev && git pull --rebase
git checkout main && git pull --rebase
git merge --no-commit --no-ff dev
git restore --source=HEAD --staged --worktree ../ai-rules ../dev-docs ../planning ../reports ../AGENTS.md
git commit -m "merge: dev -> main (exclude ai-rules + output folders)"
git push
```

**ai-rules/, dev-docs/, planning/, reports/ TIDAK masuk main** — hanya di dev.

---

## 5) Emergency Procedures

### Batalkan perubahan belum commit
```bash
cd apps && git reset --hard HEAD
```

### Kembali ke commit aman
```bash
cd apps && git log --oneline -20    # cari hash
git reset --hard <HASH>
```

### Jika sudah merge ke main dan rusak
```bash
cd apps && git checkout main
git revert -m 1 <MERGE_COMMIT_HASH>
git push
```

---

## 6) Output Wajib (Akhir Sesi)

AI HARUS output:
1. **Summary** (1-5 poin)
2. **Files changed** (list)
3. **Verify commands**
4. **Merge steps** (jika layak dev → main)

Jika belum aman merge: sebutkan kenapa + apa yang perlu diperbaiki.

---

## 7) Anti-Monster Rule

DILARANG file dokumentasi tumbuh tanpa batas:

| Area | Strategi |
|------|----------|
| `dev-docs/modules/` | Split per aspek (routes, controllers, models) — README hanya indeks |
| `dev-docs/ai/COMMIT_LOG.md` | Indeks saja, detail di `commit-logs/YYYY-MM-DD.md` |
| `dev-docs/ai/TASKS.md` | Task aktif saja, done >1 minggu → TASKS-ARCHIVE.md |
| `dev-docs/ai/KNOWN_ISSUES.md` | Open issues saja, resolved >2 minggu → RESOLVED.md |
| `dev-docs/CHANGELOG.md` | Tahun berjalan saja, archive per tahun |

---

## 8) Documentation Maintenance

Setiap akhir task, AI WAJIB update (bila terdampak):

| File | Kapan |
|------|-------|
| `dev-docs/ai/COMMIT_LOG.md` + `commit-logs/` | SETIAP commit+push |
| `dev-docs/ai/CURRENT_STATE.md` | Setiap selesai task |
| `dev-docs/ai/TASKS.md` | Task baru/selesai |
| `dev-docs/ai/FINAL_SYSTEM_HANDOVER.md` | Setelah push ke dev |
| `dev-docs/ai/MODULE_MAP.md` | Modul baru/berubah |
| `dev-docs/ai/VERSION.md` | Saat isi/tutup `[Unreleased]` di CHANGELOG |
| `dev-docs/CHANGELOG.md` | Setiap milestone |
| `reports/task/` | Setiap selesai push ke dev |
| `apps/README.md` | Milestone / modul signifikan — usulkan draft, user approve |

Jika tidak ada perubahan: tulis alasan eksplisit di output.

---

# END

**Reminder:**
- `main` = stabil. Semua kerja AI = `dev` / `feat/*`.
- **GIT SELALU dari `apps/`** — jangan dari root!
- **ai-rules/ = IMMUTABLE** — baca saja, jangan ubah.
