# laerling-logg

Læringslogg for lærling i IT-utvikling, Vestfold fylkeskommune.
Inneholder både dagsloggene og skillene som skriver dem.

> **Dette repoet skal være privat.** Loggene beskriver arbeid i en offentlig
> virksomhet. Avklar med veileder eller faglig leder før du tar det i bruk.

## Struktur

```
laerling-logg/
├── .claude/skills/
│   ├── laerling-mentor/     # underviser, tagger kompetansemål
│   ├── start-session/       # /start-session
│   └── end-session/         # /end-session — skriver og committer loggen
├── logg/
│   └── dagslogg-YYYY-MM-DD.md
└── README.md
```

Skillene ligger i repoet slik at de er versjonert. For at de skal virke i
alle prosjekter må de også finnes under `~/.claude/skills/` — se oppsett.

## Oppsett

1. Klon repoet til `~/laerling-logg`.
2. Gjør skillene tilgjengelige personlig (velg én variant):

   **Windows, uten admin — junction:**
   ```cmd
   for %S in (laerling-mentor start-session end-session) do mklink /J "%USERPROFILE%\.claude\skills\%S" "%USERPROFILE%\laerling-logg\.claude\skills\%S"
   ```

   **macOS / Linux — symlink:**
   ```bash
   for s in laerling-mentor start-session end-session; do
     ln -s ~/laerling-logg/.claude/skills/$s ~/.claude/skills/$s
   done
   ```

   **Eller bare kopiér** mappene til `~/.claude/skills/` (enklest, men da må
   du kopiere på nytt hver gang du endrer en skill).

3. Sjekk at de er lastet: spør `Hvilke skills har du tilgang til?` i Claude Code.

## Bruk

| Kommando | Når |
|---|---|
| `/start-session` | Ved dagens start. Leser de siste loggene, spør hva som er planen. |
| `/end-session` | Ved dagens slutt. Skriver `logg/dagslogg-<dato>.md` og committer. |

Mellom disse jobber du som normalt. `laerling-mentor` sørger for at
utviklingsspørsmål blir forklart, ikke bare besvart.

## Hva som aldri skal inn i en logg

Nøkler, tokens, passord, personopplysninger, interne hostnavn, IP-adresser
eller navngitte sikkerhetssvakheter hos leverandører. Beskriv **hva du lærte**,
ikke **hvordan systemet ser ut innvendig**. `end-session` sjekker dette, men
ansvaret er ditt — git-historikk er varig.