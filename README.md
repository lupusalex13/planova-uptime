# planova-uptime

Verifica la 5 minute ca Planova raspunde (API + baza, aplicatia pe tenant, pagina de prezentare).
Cand o verificare pica de 3 ori la rand, rularea iese rosie si GitHub trimite email.

Repo public: GitHub Actions e gratuit fara limita de minute doar pe repo-uri publice.
Contine doar adrese publice. Nimic secret.

## Pagina de stare (status.planova.ro)

Acelasi workflow publica pagina pe GitHub Pages (sursa: „GitHub Actions”, environment `github-pages`, domeniu `status.planova.ro`).
Preconditii, o singura data: Pages activat cu sursa „GitHub Actions”; in Cloudflare `CNAME status -> lupusalex13.github.io`, DNS only; domeniul custom setat in Settings → Pages, cu Enforce HTTPS.
Se publica doar cand se schimba starea, cand se schimba `incidente.txt` sau `pagina/`, sau o data pe ora.
Nu exista branch `gh-pages`: pagina se urca la fiecare publicare din `pagina/` + `incidente.txt` + `status.json` generat.

**In timpul unui incident:** editezi `incidente.txt` pe `main`, din GitHub (merge si de pe telefon).
Cel mai nou mesaj sus. Sabloanele (Investigam / Am identificat cauza / Rezolvat) sunt in
`planova/landing/docs/pagina-de-stare-draft.md`, sectiunea (b). Pe pagina publica nu intra nume de
clienti, date personale sau cauza tehnica detaliata. Commit-ul porneste workflow-ul, pagina se
actualizeaza in 1-2 minute. Dupa ce s-a terminat, lasi mesajul „Rezolvat” cateva zile, apoi golesti fisierul.
