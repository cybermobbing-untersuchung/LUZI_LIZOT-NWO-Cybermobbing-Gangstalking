# AGENTS.md — Musikforschungsprojekt: LUZI & LIZOT

> **Zweck:** Dieses Dokument beschreibt Aufbau, Ziele, Datenquellen und Arbeitsabläufe des Forschungsprojekts zu den deutschen Musikern LUZI (Yung Luzi) und LIZOT. Es dient als zentrale Orientierung für KI-Agenten und menschliche Mitarbeiter.

---

## Inhaltsverzeichnis

1. [Projektübersicht](#1-projektübersicht)
2. [Ordner- und Dateistruktur](#2-ordner--und-dateistruktur)
3. [Künstlerprofile](#3-künstlerprofile)
4. [Datenquellen & Zugangslinks](#4-datenquellen--zugangslinks)
5. [Datenerfassungsaufgaben](#5-datenerfassungsaufgaben)
6. [Agenten-Anweisungen](#6-agenten-anweisungen)
7. [Dateikonventionen & Formate](#7-dateikonventionen--formate)
8. [Erlaubte Tools & Einschränkungen](#8-erlaubte-tools--einschränkungen)
9. [Priorisierung & Roadmap](#9-priorisierung--roadmap)
10. [Qualitätssicherung](#10-qualitätssicherung)

---

## 1. Projektübersicht

### Ziel
Aufbau einer vollständigen, strukturierten Wissensdatenbank über die deutschen Musiker **LUZI** und **LIZOT** — einzeln sowie in ihrer Kollaboration miteinander. Die Daten sollen laufend aktualisiert und analysiert werden.

### Forschungsfelder
| Feld | Beschreibung |
|------|-------------|
| Diskographie | Alle Releases (Singles, EPs, Alben, Remixe) mit Metadaten |
| Songtexte | Vollständige Lyrics aller Tracks, inkl. Featuring-Angaben |
| Streaming-Daten | Spotify Streams, YouTube Views, monatliche Hörer, Abonnenten |
| Kollaborationen | Gemeinsame Tracks, Features, Remixe mit anderen Künstlern |
| Soziale Medien | Follower-Zahlen, Engagement, Plattform-Präsenz |
| Presse & News | Artikel, Interviews, Reviews, Erwähnungen |
| Erfolge & Auszeichnungen | Charts, Gold-/Platin-Zertifizierungen, Awards |
| Gemeinsame Releases | Kollaborationen zwischen LUZI & LIZOT |

---

## 2. Ordner- und Dateistruktur

```
music-research/
│
├── AGENTS.md                          ← Diese Datei (Hauptdokumentation)
├── README.md                          ← Kurzbeschreibung für neue Mitarbeiter
│
├── artists/
│   ├── LUZI/
│   │   ├── profile.md                 ← Biografie, Steckbrief, Social Links
│   │   ├── discography/
│   │   │   ├── discography.json       ← Vollständige Diskographie (maschinenlesbar)
│   │   │   ├── discography.md         ← Diskographie (lesbar, nach Jahr sortiert)
│   │   │   └── albums/
│   │   │       ├── 2021_Aus_dem_Leben_eines_Taugenichts_EP.md
│   │   │       ├── 2022_Turbolaut_Single.md
│   │   │       ├── 2023_Spargel_aus_Steglitz_EP.md
│   │   │       ├── 2023_LUZIs_Megamix.md
│   │   │       └── [weitere Releases...]
│   │   ├── lyrics/
│   │   │   ├── Drift.md
│   │   │   ├── Bass.md
│   │   │   ├── Boujee.md
│   │   │   ├── Turbolaut.md
│   │   │   ├── Vorbei.md
│   │   │   ├── Fuer_dich.md           ← feat. LIZOT
│   │   │   ├── Berlin.md
│   │   │   ├── HOT.md
│   │   │   ├── Sueechtig_nach_dir.md
│   │   │   ├── Big_City_Life.md
│   │   │   ├── Good_Life.md
│   │   │   ├── Dilara.md
│   │   │   ├── DA.md
│   │   │   ├── Film.md
│   │   │   └── [weitere Songs...]
│   │   ├── collaborations/
│   │   │   ├── collaborations.md      ← Übersicht aller Kollaborationen
│   │   │   └── by_artist/
│   │   │       ├── feat_LIZOT.md
│   │   │       ├── feat_Die_Atzen.md
│   │   │       ├── feat_Drogu.md
│   │   │       └── feat_Haegi.md
│   │   ├── social-media/
│   │   │   ├── stats_history.json     ← Zeitreihe der Follower/Listener-Daten
│   │   │   └── stats_current.md       ← Aktuellster Snapshot
│   │   └── press/
│   │       ├── index.md               ← Übersicht aller Artikel
│   │       └── articles/
│   │           └── [YYYY-MM-DD_Quelle_Titel.md]
│   │
│   └── LIZOT/
│       ├── profile.md                 ← Biografie, Steckbrief, Social Links
│       ├── discography/
│       │   ├── discography.json
│       │   ├── discography.md
│       │   └── albums/
│       │       ├── 2015_Sonnenmaedchen_Single.md
│       │       ├── 2019_Menage_A_Trois_Single.md
│       │       ├── 2020_Weekend_Single.md
│       │       ├── 2020_Like_A_Prayer_Single.md
│       │       ├── 2023_Fuer_dich_Single.md   ← feat. LUZI
│       │       └── [weitere Releases...]
│       ├── lyrics/
│       │   ├── Sonnenmaedchen.md
│       │   ├── Menage_A_Trois.md
│       │   ├── Weekend.md
│       │   ├── Like_A_Prayer.md
│       │   ├── Hurricane.md
│       │   ├── Fuer_dich.md           ← feat. LUZI
│       │   ├── Hypnotized.md
│       │   ├── Down_Under_2025.md
│       │   ├── Bad_Decisions.md
│       │   └── [weitere Songs...]
│       ├── collaborations/
│       │   ├── collaborations.md
│       │   └── by_artist/
│       │       ├── feat_LUZI.md
│       │       ├── feat_Holy_Molly.md
│       │       ├── feat_Gabry_Ponte.md
│       │       ├── feat_Blasterjaxx.md
│       │       ├── feat_Charming_Horses.md
│       │       ├── feat_KYANU.md
│       │       ├── feat_MOTi.md
│       │       └── [weitere Künstler...]
│       ├── social-media/
│       │   ├── stats_history.json
│       │   └── stats_current.md
│       └── press/
│           ├── index.md
│           └── articles/
│               └── [YYYY-MM-DD_Quelle_Titel.md]
│
├── shared/
│   ├── joint-releases/
│   │   └── Fuer_dich_2023.md          ← Detailanalyse der Kollaboration
│   ├── analytics/
│   │   ├── streaming_comparison.json  ← Vergleich beider Künstler über Zeit
│   │   ├── streaming_comparison.md
│   │   └── charts/
│   │       └── [Chartdaten nach Plattform & Zeitraum]
│   └── news/
│       ├── index.md                   ← Alle News chronologisch
│       └── articles/
│           └── [YYYY-MM-DD_*.md]
│
├── scripts/
│   ├── fetch_spotify_stats.py         ← Spotify API Scraper (monatliche Hörer, Follower)
│   ├── fetch_youtube_stats.py         ← YouTube Data API (Views, Abonnenten)
│   ├── update_stats.sh                ← Wrapper-Skript für regelmäßige Updates
│   └── README_scripts.md             ← Anleitung für die Skripte
│
└── reports/
    ├── monthly_report_template.md     ← Vorlage für monatliche Berichte
    └── [YYYY-MM_monthly_report.md]   ← Generierte Berichte
```

---

## 3. Künstlerprofile

### LUZI (Yung Luzi)

| Eigenschaft | Details |
|-------------|---------|
| **Bürgerlicher Name** | Nicht öffentlich bekannt |
| **Künstlername** | LUZI / Yung Luzi |
| **Herkunft** | Berlin-Steglitz, Deutschland |
| **Genre** | Pop, Indie-Pop, Electro-Pop, Rockeinflüsse |
| **Label** | Unabhängig (Independent) |
| **Aktiv seit** | ~2020 (Musik), vorher Social Media & Partys |
| **Spotify** | https://open.spotify.com/artist/01toP8PPkzyiQdKgyXle10 |
| **YouTube** | https://www.youtube.com/channel/UC_mX0Pg9hr3m5f3HUmwI3vQ |
| **Instagram** | https://instagram.com/yungluzi |
| **TikTok** | https://www.tiktok.com/@yungluzi1 |

**Biografie (Kurzfassung):**
LUZI wuchs in Berlin-Steglitz auf und erlangte zunächst als Social-Media-Star und Partyveranstalter auf Snapchat Bekanntheit. Während der COVID-Pandemie konzentrierte er sich auf Musik — zunächst mit Rock-Covers auf TikTok und Instagram Reels. Seine authentische Persönlichkeit (Berliner Akzent, geschminkte Augen, lackierte Fingernägel, Tattoos) und sein extrovertierter Stil machten ihn zu einer markanten Figur. Im Jahr 2021 erschienen erste eigene Songs. Seitdem veröffentlicht er regelmäßig Singles und EPs, oft in Zusammenarbeit mit anderen deutschen Künstlern.

**Spotify-Metriken (Stand: März 2026, aus öffentlicher Profilseite):**
- Monatliche Hörer: ~196.000

**Bekannte Songs:**
- Drift (2021)
- Bass (2021)
- Boujee (2021)
- Turbolaut (2022, feat. Die Atzen)
- Vorbei (2023)
- Für dich (2023, feat. LIZOT)
- Berlin (2023)
- HOT (2023)
- Big City Life (2024)
- Süchtig nach dir (2024)
- Good Life (2024)
- Dilara (2024)
- DA (2025)
- Film (2025, feat. Hägi & Drogu)

---

### LIZOT

| Eigenschaft | Details |
|-------------|---------|
| **Mitglieder** | Max Kleinschmidt (Produzent) & Patrick Art (DJ, seit Dez. 2021) |
| **Frühere Mitglieder** | Jan Sievers (2013–2019), Robin Wilhelm (2019–April 2021) |
| **Herkunft** | Deutschland (Max Kleinschmidt: Halle/Saale) |
| **Genre** | Deep House, Slap House, Dance/EDM |
| **Label** | Zeitgeist / Universal Music Germany |
| **Gegründet** | 2013 (offiziell; andere Quellen nennen 2015) |
| **Spotify** | https://open.spotify.com/artist/12A83CWwFiyXy90ScLWPIe |
| **Website** | https://lizot.de |
| **Instagram** | https://www.instagram.com/lizot_official |

**Biografie (Kurzfassung):**
LIZOT ist ein deutsches Dance-Musikprojekt, das 2013 von Max Kleinschmidt und Jan Sievers gegründet wurde. Der erste große Erfolg gelang 2015 mit "Sonnenmädchen" (feat. Charming Horses & Jason Anousheh), das direkt in die deutschen Charts einstieg. Nach mehreren Mitgliederwechseln (Jan Sievers 2019 durch Robin Wilhelm ersetzt; Robin Wilhelm im April 2021 durch Patrick Art) gelang 2020 der internationale Durchbruch mit "Weekend" (Cover von Earth & Fire) — über 120 Mio. Streams, Gold und Platin in zahlreichen Ländern. Seither gehört LIZOT mit über 750 Millionen Spotify-Gesamtstreams zu den erfolgreichsten deutschen Dance-Acts. Das Duo ist bei Universal Music unter dem Label Zeitgeist unter Vertrag.

**Spotify-Metriken (Stand: März 2026):**
- Monatliche Hörer: ~3,4 Millionen
- Gesamtstreams: über 750 Millionen (geschätzt)

**Wichtigste Songs & Auszeichnungen:**
| Song | Jahr | Streams (ca.) | Auszeichnungen |
|------|------|--------------|----------------|
| Sonnenmädchen (feat. Charming Horses, Jason Anousheh) | 2015 | — | DE Charts |
| Menage A Trois (feat. Holy Molly) | 2019 | >50 Mio. | — |
| Weekend | 2020 | >120 Mio. | 2× Platin PL, Platin NO/HU, Gold DE/SE/AT/CH/RU/CZ |
| Like A Prayer (feat. Gabry Ponte, Galwaro) | 2020 | >70 Mio. | — |
| Hurricane (feat. Blasterjaxx, Prezioso, SHIBUI) | — | >30 Mio. | Gold FR |
| Für dich (feat. LUZI) | 2023 | — | — |
| Hypnotized | 2024 | — | — |
| Down Under 2025 | 2025 | — | — |
| Bad Decisions | 2025 | — | — |
| Hardcore | 2025 | — | — |

**Wichtigste Kollaborationen:**
- Charming Horses (Sonnenmädchen, 2015)
- Holy Molly (Menage A Trois, 2019; Menage A Trois Pt. II)
- Gabry Ponte & Galwaro (Like A Prayer, 2020)
- Blasterjaxx & Prezioso (Hurricane)
- KYANU (This Is the Life)
- MOTi & Wilhelmina (Precious)
- Da Tweekaz (Invisible Friend Remix)
- LUZI (Für dich, 2023)

---

## 4. Datenquellen & Zugangslinks

### Streaming-Plattformen

| Plattform | LUZI | LIZOT |
|-----------|------|-------|
| Spotify | https://open.spotify.com/artist/01toP8PPkzyiQdKgyXle10 | https://open.spotify.com/artist/12A83CWwFiyXy90ScLWPIe |
| YouTube | https://www.youtube.com/channel/UC_mX0Pg9hr3m5f3HUmwI3vQ | (kein dedizierter Kanal bekannt) |
| Apple Music | https://music.apple.com/de/artist/luzi/1519297654 | https://music.apple.com/de/artist/lizot/888319256 |
| Deezer | https://www.deezer.com/de/artist/5611435 | https://www.deezer.com/de/artist/7393978 |

### Soziale Medien

| Plattform | LUZI | LIZOT |
|-----------|------|-------|
| Instagram | https://instagram.com/yungluzi | https://www.instagram.com/lizot_official |
| TikTok | https://www.tiktok.com/@yungluzi1 | — |
| Website | — | https://lizot.de |
| Facebook | — | https://de-de.facebook.com/djlizotofficial/ |

### Analyse-Tools & externe Datenquellen

| Tool | URL | Verwendung |
|------|-----|------------|
| Music Metrics Vault | https://www.musicmetricsvault.com/artists/lizot/12A83CWwFiyXy90ScLWPIe | LIZOT Gesamtstream-Schätzung |
| Viberate | https://www.viberate.com/artist/luzi/ | LUZI Profil & Stats |
| Shazam | https://www.shazam.com/artist/luzi/1519297654 | Diskographie-Übersicht |
| Kworb Spotify | https://kworb.net/spotify/ | Charts & Listener-Rankings |
| Songstats | https://songstats.com | Plattformübergreifende Analytics |
| YouTube Data API | https://developers.google.com/youtube/v3 | Views, Abonnenten |
| Spotify Web API | https://developer.spotify.com/documentation/web-api | Streams, Follower |
| Wikipedia (LIZOT) | https://de.wikipedia.org/wiki/Lizot | Biografie & Chartdaten |
| LIZOT About | https://lizot.de/about/ | Offizielle Biografie |

---

## 5. Datenerfassungsaufgaben

### A. Diskographie (für beide Künstler)

Für jeden Release folgende Felder erfassen und in `discography.json` eintragen:

```json
{
  "id": "luzi_001",
  "artist": "LUZI",
  "title": "Drift",
  "type": "single",
  "release_date": "2021-XX-XX",
  "featuring": [],
  "label": null,
  "spotify_id": "",
  "youtube_id": "",
  "streams_spotify": null,
  "views_youtube": null,
  "chart_positions": {},
  "certifications": [],
  "lyrics_file": "lyrics/Drift.md",
  "notes": ""
}
```

**Bekannte LUZI-Releases (chronologisch):**

| Jahr | Titel | Typ | Featuring |
|------|-------|-----|-----------|
| 2021 | Bass | Single | — |
| 2021 | Drift | Single | — |
| 2021 | Boujee | Single | — |
| 2021 | Aus dem Leben eines Taugenichts | EP | — |
| 2022 | Turbolaut | Single | Die Atzen |
| 2022 | LUZIs Megamix | Album/Mix | — |
| 2023 | Vorbei | Single | — |
| 2023 | Für dich | Single | LIZOT |
| 2023 | Berlin | Single | — |
| 2023 | HOT | Single (auch in Spargel aus Steglitz EP) | — |
| 2023 | Spargel aus Steglitz | EP | — |
| 2023 | Zur Party | Single | Die Atzen |
| 2024 | Good Life | Single | — |
| 2024 | HOT Remix | Single | Drogu |
| 2024 | Dilara | Single | — |
| 2024 | Dikkachen | Single | — |
| 2024 | Süchtig nach dir | Single | — |
| 2024 | Big City Life | Single | — |
| 2024 | Getrennt | EP | — |
| 2025 | DA | Single | — |
| 2025 | Film | Single | Hägi, Drogu |

**Bekannte LIZOT-Releases (Auswahl, chronologisch):**

| Jahr | Titel | Typ | Featuring |
|------|-------|-----|-----------|
| 2015 | Sonnenmädchen | Single | Charming Horses, Jason Anousheh |
| 2019 | Menage A Trois | Single | Holy Molly |
| 2020 | Weekend | Single | — |
| 2020 | Like A Prayer | Single | Gabry Ponte, Galwaro |
| 2021 | (Mitgliederwechsel) | — | — |
| 2022 | (mehrere Singles) | — | — |
| 2023 | Für dich | Single | LUZI |
| 2023 | Hurricane | Single | Blasterjaxx, Prezioso, SHIBUI |
| 2024 | Hypnotized | Single | — |
| 2025 | Down Under 2025 | Single | — |
| 2025 | Bad Decisions | Single | — |
| 2025 | Hardcore | Single | — |
| 2025 | Guataqui | Single | — |
| 2025 | YO TE DARÉ | Single | — |

### B. Streaming-Daten (monatlich aktualisieren)

Felder, die monatlich in `stats_history.json` gespeichert werden:

```json
{
  "date": "2026-03-20",
  "artist": "LUZI",
  "spotify": {
    "monthly_listeners": 196100,
    "followers": null,
    "top_song_streams": {}
  },
  "youtube": {
    "subscribers": null,
    "total_views": null,
    "top_video_views": {}
  },
  "instagram": {
    "followers": null,
    "following": null
  },
  "tiktok": {
    "followers": 509100,
    "likes": 27000000
  }
}
```

**Aktuell bekannte Snapshots (Stand März 2026):**

| Plattform | LUZI | LIZOT |
|-----------|------|-------|
| Spotify monatl. Hörer | ~196.000 | ~3.400.000 |
| Spotify Gesamtstreams | unbekannt | >750.000.000 |
| TikTok Follower | ~509.000 | — |
| TikTok Likes | ~27.000.000 | — |
| Instagram Follower | unbekannt (Stand 2022: ~24.000) | unbekannt |

### C. Songtexte

Für jeden Song eine Markdown-Datei anlegen nach Schema:

```markdown
# [Songtitel]

**Künstler:** LUZI [feat. ...]
**Album/EP:** [Name oder "Single"]
**Erscheinungsdatum:** YYYY-MM-DD
**Spotify-Link:** https://open.spotify.com/track/...
**YouTube-Link:** https://www.youtube.com/watch?v=...

---

## Lyrics

[Strophe 1]
...

[Chorus]
...

[Strophe 2]
...

---

**Quelle:** [z. B. Genius.com, offizielle Website]
**Zuletzt aktualisiert:** YYYY-MM-DD
```

### D. Presseartikel & News

Jeden Artikel als Markdown-Datei mit dem Namensschema `YYYY-MM-DD_Quelle_Kurztitel.md` speichern:

```markdown
# [Artikeltitel]

**Quelle:** [Publikationsname]
**URL:** [Original-URL]
**Datum:** YYYY-MM-DD
**Künstler:** LUZI / LIZOT / beide
**Kategorie:** Interview / Review / News / Chart-Meldung

---

## Zusammenfassung

[2-5 Sätze Kernaussagen des Artikels]

---

## Relevante Zitate

> "[Zitat]" — [Person/Quelle]

---

**Archiviert:** YYYY-MM-DD
```

---

## 6. Agenten-Anweisungen

### Allgemeine Regeln für Agenten

1. **Niemals halluzinieren.** Fehlende Daten werden explizit mit `null` oder `"unbekannt"` markiert, nie geschätzt oder erfunden.
2. **Quellen immer angeben.** Jeder Datenpunkt wird mit URL und Datum der Erhebung versehen.
3. **Aktuell denken.** Streaming-Zahlen und Follower-Zahlen veralten schnell — immer das Erhebungsdatum mitführen.
4. **Datenschutz respektieren.** Keine privaten Informationen über die Künstler sammeln, die nicht öffentlich zugänglich sind.
5. **Konsistente Schreibweise.** Künstlernamen immer in Großbuchstaben: **LUZI**, **LIZOT**.

### Task 1: Diskographie vervollständigen

```
Ziel: Alle Releases beider Künstler in discography.json eintragen.

Vorgehen:
1. Spotify-Profil aufrufen (Links in Abschnitt 4)
2. Apple Music / Shazam / Discogs als Kreuzreferenz nutzen
3. Jeden Release in discography.json eintragen (Schema in Abschnitt 5.A)
4. Lyrics-Datei in lyrics/ anlegen (Schema in Abschnitt 5.C)
5. discography.md als lesbare Version generieren

Priorität: HOCH
Zieldatei: artists/[KÜNSTLER]/discography/discography.json
```

### Task 2: Streaming-Daten erfassen

```
Ziel: Aktuellen Snapshot aller Plattform-Metriken erfassen.

Vorgehen:
1. Spotify-Profilseiten aufrufen → monatliche Hörer notieren
2. YouTube-Kanal (LUZI) aufrufen → Abonnenten & Views je Video
3. Instagram-Profile aufrufen → Follower
4. Daten in stats_history.json eintragen (Schema in Abschnitt 5.B)
5. stats_current.md als menschenlesbare Zusammenfassung generieren

Hinweis: Spotify-API gibt keine Track-Streams per öffentlichem Endpoint aus.
Für Schätzungen: https://www.musicmetricsvault.com nutzen.

Priorität: MITTEL
Zieldatei: artists/[KÜNSTLER]/social-media/stats_history.json
Update-Intervall: Monatlich (am 1. des Monats)
```

### Task 3: Kollaborationen dokumentieren

```
Ziel: Alle Featuring-Einträge und Remixe erfassen.

Vorgehen:
1. Diskographie nach "feat." und "with" durchsuchen
2. Für jede Kollaboration eine Datei in collaborations/by_artist/ anlegen
3. collaborations.md als Übersicht aktualisieren

Format jeder Kollaborations-Datei:
- Künstler
- Gemeinsame Tracks (mit Links & Erscheinungsdaten)
- Kontext (wann, wie kam die Zusammenarbeit zustande?)

Besondere Aufmerksamkeit: LUZI × LIZOT Kollaboration "Für dich" (2023)

Priorität: MITTEL
Zieldatei: artists/[KÜNSTLER]/collaborations/collaborations.md
```

### Task 4: Pressearchiv anlegen

```
Ziel: Alle öffentlichen Artikel, Interviews und Chartmeldungen archivieren.

Suchbegriffe (Deutsch):
- "LUZI Musiker", "Yung Luzi", "LUZI Berlin"
- "LIZOT Interview", "LIZOT Chart", "LIZOT Weekend"
- "LUZI LIZOT Für dich"

Suchbegriffe (Englisch):
- "LIZOT Weekend chart", "LIZOT platinum", "LIZOT new release"

Quellen priorisieren:
1. Offizielle Pressemitteilungen
2. Musikmagazine (Rolling Stone DE, Musikexpress, Diffus)
3. Online-Musikportale (laut.de, Genius, etc.)
4. Tageszeitungen (nur bei großen Meldungen)

Priorität: NIEDRIG (aber kontinuierlich)
Zieldatei: artists/[KÜNSTLER]/press/articles/
```

### Task 5: Monatsbericht generieren

```
Ziel: Einmal pro Monat einen Report über beide Künstler erstellen.

Inhalt des Reports:
1. Streaming-Vergleich LUZI vs. LIZOT (aktuelle Zahlen + Trend)
2. Neue Releases im vergangenen Monat
3. Chartentwicklungen
4. Neue Kollaborationen oder Ankündigungen
5. Pressehighlights

Vorlage: reports/monthly_report_template.md
Ausgabe: reports/YYYY-MM_monthly_report.md

Priorität: MITTEL
Erstellt am: 1. des Folgemonats
```

---

## 7. Dateikonventionen & Formate

### Dateinamen

- Nur Kleinbuchstaben, Unterstriche statt Leerzeichen: `fuer_dich.md`
- Jahrespräfix bei datierten Dateien: `2023_Spargel_aus_Steglitz_EP.md`
- Artikel: `YYYY-MM-DD_Quelle_Kurztitel.md` (z. B. `2024-03-15_laut_de_LUZI_interview.md`)
- Stats-Snapshots: `stats_YYYY-MM.json`

### JSON-Feldkonventionen

- Zahlen ohne Tausendertrennzeichen: `196100` (nicht `196.100`)
- Unbekannte Werte: `null` (nicht `""` oder `0`)
- Datumsformat: ISO 8601 (`YYYY-MM-DD`)
- Streams/Views immer als Integer

### Markdown-Konventionen

- H1 (`#`) nur für Dokumenttitel
- H2 (`##`) für Hauptabschnitte
- H3 (`###`) für Unterabschnitte
- Tabellen für strukturierte Daten bevorzugen
- Immer Metadaten-Block am Anfang (bei Song-Dateien)

---

## 8. Erlaubte Tools & Einschränkungen

### Erlaubt
- Web-Suche für Faktenrecherche
- Öffentliche Spotify/Apple Music/YouTube-Seiten scrapen (kein Login erforderlich)
- Spotify Web API (Rate Limits beachten)
- YouTube Data API v3 (Quota beachten: 10.000 Units/Tag)
- Genius.com für Lyrics (mit Quellenangabe)

### Einschränkungen
- **Keine kostenpflichtigen APIs** ohne vorherige Freigabe
- **Keine Passwörter oder private Credentials** in Dateien speichern → `.env`-Datei verwenden
- **Keine vollständigen Lyrics reproduzieren** ohne Urheberrechts-Clearing (nur Ausschnitte mit Quellenangabe im Research-Kontext erlaubt)
- **Keine privaten Daten** der Künstler (Adresse, Telefon, echte Namen sofern nicht selbst kommuniziert)
- **Nicht auf inoffizielle Leak-Seiten** zugreifen

### API-Konfiguration

Credentials werden in einer `.env`-Datei gespeichert (nicht ins Repo einchecken!):

```env
SPOTIFY_CLIENT_ID=your_client_id
SPOTIFY_CLIENT_SECRET=your_client_secret
YOUTUBE_API_KEY=your_api_key
```

---

## 9. Priorisierung & Roadmap

### Phase 1 — Grundaufbau (Monat 1)
- [x] AGENTS.md erstellen
- [x] Ordnerstruktur anlegen
- [x] LUZI Profil anlegen (`artists/LUZI/profile.md`)
- [x] LIZOT Profil anlegen (`artists/LIZOT/profile.md`)
- [ ] Diskographie LUZI vollständig erfassen
- [ ] Diskographie LIZOT vollständig erfassen (ab 2019, Fokus auf Hits)
- [ ] Ersten Stats-Snapshot erfassen

### Phase 2 — Anreicherung (Monat 2–3)
- [ ] Lyrics aller Haupt-Songs
- [ ] Kollaborations-Datenbank vollständig
- [ ] Pressearchiv für die letzten 12 Monate
- [ ] YouTube-Stats für LUZI-Kanal erfassen
- [ ] Ersten Monatsbericht generieren

### Phase 3 — Automatisierung (Monat 4+)
- [ ] Spotify-Stats-Skript aktivieren (`scripts/fetch_spotify_stats.py`)
- [ ] YouTube-Stats-Skript aktivieren (`scripts/fetch_youtube_stats.py`)
- [ ] Automatisches monatliches Update via Cron/Scheduler
- [ ] Streaming-Vergleichsanalyse mit Visualisierung

---

## 10. Qualitätssicherung

### Vor jedem Commit prüfen:
- [ ] Alle JSON-Dateien sind valide (mit `python -m json.tool` prüfbar)
- [ ] Keine Null-Werte ohne Kommentar
- [ ] Alle Quellenangaben vollständig
- [ ] Dateinamen entsprechen der Konvention
- [ ] Keine Credentials in Dateien

### Regelmäßige Reviews:
- **Monatlich:** Stats-Snapshot aktualisieren, neuen Releases prüfen
- **Quartalsweise:** Pressearchiv-Index aktualisieren, Diskographie auf Vollständigkeit prüfen
- **Bei neuem Release:** Sofort Eintrag in `discography.json` + Lyrics-Datei anlegen

---

*Zuletzt aktualisiert: 2026-03-20*
*Projektversion: 1.0.0*
