# Kompetansemål — Vg3 IT-utvikler (lærling, Vestfold fylkeskommune)

Official læreplan wording. **Quote verbatim in log entries** — this is the text the assessor works from, so paraphrases weaken the documentation.

Each entry has an internal ID (KM1–KM21) for referring to mål in conversation, plus typical triggers to help match real work to the right mål. The IDs are a convenience of this skill, not official numbering — write the full mål text in log entries, not "KM7".

## Quick index

| Theme | Mål |
|---|---|
| Personvern, sikkerhet, regelverk | KM1, KM8, KM13, KM17 |
| Utvikling og videreutvikling | KM2, KM3, KM10, KM19 |
| Data og integrasjoner | KM4, KM5 |
| Dokumentasjon og brukerstøtte | KM6, KM7 |
| Brukergrensesnitt | KM9 |
| Kodekvalitet, testing, feilsøking | KM11, KM15, KM16 |
| Infrastruktur | KM12 |
| Samarbeid og arbeidsliv | KM14, KM21 |
| KI og samfunn | KM18, KM20 |

---

## Personvern, sikkerhet og regelverk

**KM1** — planlegge, utvikle og dokumentere løsninger med innebygd personvern og sikkerhet
*Triggers:* privacy by design, dataminimering, hvilke persondata en løsning lagrer, sikkerhet tenkt inn fra starten, samtykke, kryptering av personopplysninger, DPIA.

**KM8** — håndtere påloggingsopplysninger på en sikker og forsvarlig måte
*Triggers:* API-nøkler, tokens, passord, hemmeligheter i kode, `.env`-filer, secrets i git-historikken, autentisering, 401/403, secret managers, rotasjon av nøkler.

**KM13** — gjøre rede for og anvende gjeldende regelverk for personvern, opphavsrett og informasjonssikkerhet i eget arbeid
*Triggers:* GDPR, personopplysningsloven, behandlingsgrunnlag, lisenser på biblioteker (MIT, GPL), opphavsrett til kode eller innhold, bruk av kode fra nettet eller fra en KI-assistent, informasjonssikkerhet i offentlig sektor.

**KM17** — behandle bedriftsinterne opplysninger på en sikker og etisk forsvarlig måte
*Triggers:* interne data, hva som kan deles eksternt eller limes inn i eksterne verktøy, tilgangsstyring, konfidensialitet, taushetsplikt, testdata basert på ekte data.

## Utvikling og videreutvikling

**KM2** — planlegge, utvikle og dokumentere løsninger som er energieffektive og bærekraftige
*Triggers:* ytelse og ressursbruk, unødvendige API-kall eller spørringer, caching for å redusere last, grønn IT, effektive algoritmer, skalering og kostnad.

**KM3** — videreutvikle en løsning for å ivareta brukernes behov
*Triggers:* endre eller utvide eksisterende funksjonalitet, brukertilbakemeldinger, brukerbehov, iterasjon på noe som finnes, refaktorering med brukernytte som mål.

**KM10** — velge og bruke relevante rammeverk og moduler til utvikling
*Triggers:* valg av rammeverk eller bibliotek, npm/pip-pakker, avhengigheter, "hvilket bibliotek bør jeg bruke", bygge selv vs. bruke noe ferdig, SvelteKit, React, .NET, Designsystemet.

**KM19** — utforske og vurdere eksisterende og nye teknologier og bransjerelevante kodespråk
*Triggers:* sammenligne teknologier eller språk, vurdere om noe nytt er verdt å ta i bruk, lære et nytt språk, teknologivalg og modenhet.

## Data og integrasjoner

**KM4** — planlegge, utvikle, sette opp og dokumentere systemer for datainnsamling, analyse og visualisering
*Triggers:* datainnsamling, logging og telemetri, dashboards, grafer og rapporter, dataanalyse, SQL-spørringer for innsikt, statistikk.

**KM5** — planlegge, utvikle, sette opp og dokumentere integrasjoner mellom ulike systemer og databaser
*Triggers:* API-integrasjon, REST/GraphQL, webhooks, databasekobling, ETL, migrering av data, systemer som skal snakke sammen, autentisering mot tredjepartstjenester, datamodell og skjema.

## Dokumentasjon og brukerstøtte

**KM6** — utvikle og bruke dokumentasjon og veiledninger
*Triggers:* skrive README, teknisk dokumentasjon, kodekommentarer, API-dokumentasjon, brukerveiledning, lese og bruke dokumentasjon for å løse noe.

**KM7** — veilede brukere i ulike oppgaver
*Triggers:* brukerstøtte, forklare noe til en sluttbruker, opplæring, brukerhenvendelse, skrive en forklaring tilpasset ikke-tekniske brukere.

## Brukergrensesnitt

**KM9** — utvikle og tilpasse brukergrensesnitt som ivaretar krav til universell utforming
*Triggers:* UU, WCAG, skjermleser, tastaturnavigasjon, kontrast, alt-tekst, semantisk HTML, ARIA, fokusrekkefølge, skjemaer og feilmeldinger, forskrift om universell utforming av IKT.

## Kodekvalitet, testing og feilsøking

**KM11** — beskrive konsekvenser av teknisk gjeld i løsninger
*Triggers:* teknisk gjeld, snarveier og hva de koster senere, refaktorering, utdaterte avhengigheter, kode ingen tør endre, vedlikeholdbarhet, "vi fikser det senere".

**KM15** — feilsøke kode og rette feil i algoritmer og kode
*Triggers:* bugs, stack traces, feilmeldinger, uventet oppførsel, debugging, kode som ikke gjør det den skal, logikkfeil, off-by-one, race conditions.

**KM16** — utforske prosesser knyttet til testing og feilsøking i utvikling av løsninger
*Triggers:* enhetstester, integrasjonstester, testdekning, testrammeverk, TDD, hvordan man tester noe systematisk, CI-kjøring av tester, QA-prosess.

*Skille mellom KM15 og KM16:* KM15 er å finne og fikse en konkret feil. KM16 er prosessen og metoden — hvordan man tester og feilsøker systematisk. Mange oppgaver treffer begge.

## Infrastruktur

**KM12** — beskrive hvilke krav som ulike løsninger stiller til infrastruktur, og hvilke muligheter og begrensninger som følger av infrastrukturen
*Triggers:* servere, hosting, sky (Azure, AWS), containere og Docker, deploy og driftsmiljø, nettverk og brannmur, miljøer (dev/test/prod), ressursbehov, begrensninger i fylkeskommunens IT-plattform.

## Samarbeid og arbeidsliv

**KM14** — bruke utviklingsstrategier og samarbeide med andre utviklere
*Triggers:* git-arbeidsflyt, branching, pull requests, kodegjennomgang, parprogramming, Scrum/Kviss/Kanban, sprintplanlegging, stand-up, konfliktløsning i kode, arbeid i team.

**KM21** — gjøre rede for hvilke krav og forventninger som stilles til et likeverdig og inkluderende yrkesfellesskap, og reflektere over hvilke plikter og rettigheter arbeidsgiver og arbeidstaker har i lærebedriften
*Triggers:* rettigheter og plikter som lærling, arbeidsmiljø, inkludering og mangfold, HMS, lærekontrakt, arbeidstid, varsling, forholdet til veileder eller faglig leder.

## Kunstig intelligens og samfunn

**KM18** — utforske konseptene maskinlæring og kunstig intelligens
*Triggers:* maskinlæring, KI-modeller, LLM-er, treningsdata, prompting, KI-verktøy i utviklingsarbeid, hvordan en modell fungerer, KI-integrasjon i en løsning.

**KM20** — reflektere over og beskrive hvordan teknologi kan misbrukes og påvirke samfunnet negativt
*Triggers:* misbruk av teknologi, overvåkning, skjevheter i algoritmer og KI, digitalt utenforskap, etiske avveininger, sikkerhetsrisiko for samfunnet, desinformasjon, konsekvenser av en løsning for sårbare brukere.
