# ai-rules/security/ — Keamanan untuk KulinerLumajang.id

> **Status:** IMMUTABLE — AI TIDAK BOLEH mengubah file apapun di folder ini.
> **Scope:** MVP KulinerLumajang.id — directory app dengan payment (Xendit).

## Bagian yang Aktif (WAJIB AI baca & terapkan proaktif)

| Part | File | Priority | Keterangan |
|------|------|----------|------------|
| **A** | `part-a-credential-management.md` | P0 | `.env` mandatory, credential boundary — WAJIB |
| **B** | `part-b-http-security-headers.md` | P1 | CSP, HSTS, X-Frame-Options — WAJIB saat deploy |
| **C** | `part-c-authentication-authorization.md` | P1 | Auth buat admin panel (Filament) — WAJIB |
| **D** | `part-d-input-validation-output-sanitization.md` | P0 | Validasi form listing, sanitization — WAJIB |
| **I** | `part-i-security-pre-merge-checklist.md` | P1 | Checklist sebelum merge ke main — WAJIB |

## Bagian yang Ditunda (Nanti saat production)

| Part | Topik | Kapan Aktifkan |
|------|-------|---------------|
| E | Code security standards | Saat ada SAST/DAST pipeline |
| F | Auth flow documentation | Saat auth system lebih kompleks |
| G | Guards, roles, permissions | Saat ada multi-role (admin, premium user, etc) |
| H | Sensitive operations | Saat ada 2FA, audit trail |
| J | Incident response | Saat production live |
| K | Data protection & privacy | Saat ada GDPR/data policy |
| L | Backup & DR security | Saat production + backup setup |
| M | Container deployment | Saat pakai Docker production |
| N-Q | WebSocket, GraphQL, Network, Monitoring | Saat fitur tersebut ada |

## Aturan Khusus KulinerLumajang.id

1. **Xendit API key** — HANYA di `.env`, DILARANG hardcode. Referensi di kode: `process.env.XENDIT_API_KEY`
2. **Supabase URL + key** — HANYA di `.env`. Public anon key boleh di frontend, service_role key HANYA di backend `.env`
3. **Admin panel (Filament)** — Auth WAJIB. Default Filament auth atau custom guard
4. **Form listing UMKM** — Validasi WAJIB: nama, kategori, kontak, foto (MIME + size limit)
5. **WhatsApp link** — Validasi nomor WA format Indonesia

> Untuk bagian ditunda: copy dari [docs-ai repo](https://github.com/frandika06/docs-ai) saat dibutuhkan.
