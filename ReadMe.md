# laivadatan-metsastaja

**An AI skill for researching old Finnish vessels — steamships, tugboats, log-floaters, and riveted craft.**  
*Tekoälyskilli vanhojen suomalaisten laivojen tiedonhakuun — botologian apuväline.*

---

## Mikä tämä on?

`laivadatan-metsastaja` on botologian apuri ja [Agent Skills](https://agentskills.io) -muotoinen skilli, joka opettaa
tekoälyavustajan (Claude tai muu yhteensopiva AI) toimimaan botologian
tutkimusapurina. Skilli tietää mistä etsiä, miten lähteisiin suhtautua ja
miten rakentaa luotettava alusprofiili sirpaleisesta lähtöaineistosta.

Tyypillinen lähtötilanne: sinulla on laivan nimi, vuosiluku ja paikkakunta —
ja siitä pitäisi rakentaa kokonaiskuva. Skilli ohjaa sinut oikeiden
hakemistojen, arkistojen ja lähteiden äärelle.

### Skilli osaa muun muassa

- Ehdottaa hakukaavoja Finnaan, digi.kansalliskirjasto.fi:hin, ELKAan ja laivadata.fi:hin
- Varoittaa samannimisistä aluksista (Halla I–XVII, Aallotar 1–9, Saimaa 1–6…)
- Selittää Korsteenin hakemistojen lyhennejärjestelmän
- Rakentaa yhtenäisen alusprofiilipohjan viittauskäytäntöineen
- Tunnistaa lähdeketjuja — erottaa riippumattomat lähteet sitaattiketjuista
- Ohjata vesistösiirtojen ja nimenvaihdosten jäljittämisessä

### Mitä skilli ei korvaa

- ELKAn tutkijasalia
- Alkuperäisiä arkistolähteitä
- Korsteenin ja Laiva-lehden omia hakemistoja (ne löydät SHPS:ltä)
- Asiantuntijatietämystä — skilli on apuväline, ei asiantuntija

---

## Asennus

### Claude.ai (web)

1. Lataa tämä repo zip-pakettina: **Code → Download ZIP**
2. Avaa Claude.ai → **Settings → Capabilities → Skills**
3. Lisää ladattu zip-tiedosto

### Claude Code

```bash
# Kloonaa repo suoraan skills-hakemistoon
git clone https://github.com/SINUN-KÄYTTÄJÄTUNNUS/laivadatan-metsastaja ~/.claude/skills/laivadatan-metsastaja
```

### Muut AI-alustat

Skilli noudattaa avointa [Agent Skills -standardia](https://agentskills.io).
`SKILL.md`-tiedosto toimii sellaisenaan muissa yhteensopivissa järjestelmissä.
Katso oman alustasi asennusohjeet.

---

## Sisältö

```
SKILL.md                        — Skillin pääohje (tästä AI aloittaa)
references/
  lahteet.md                    — Hakulähteiden täysi katalogi
  kirjallisuus.md               — Julkaistu kirjallisuus vesistöittäin (~70 teosta)
  hakukaavat.md                 — Hakukaavojen pääindeksi
  hakukaavat-finna.md           — Finna-hakujen URL-rakenne ja suodattimet
  hakukaavat-digi.md            — Digitaalinen kansalliskirjasto: hakukaavat
  hakukaavat-arkistot.md        — ELKA, laivadata.fi, Kansallisarkisto
  alusprofiili-malli.md         — Vakiomuoto alusprofiilille + viittauskäytännöt
  laivanrakennus-historia.md    — Taustaperusteet: telakat, konepajat, identiteetti
  lyhenteet.md                  — Korsteenin ja yleiset laivastolyheneet
  tutkimukset.md                — Pro gradut ja käsikirjoitukset vesistöittäin
```

> **Huom.** Korsteenin hakemistot (osat I ja II) ja Karttunen 1945
> -aineistot eivät sisälly tähän julkiseen repoon — ne kuuluvat
> alkuperäisille oikeudenhaltijoille. Ota yhteyttä
> [Suomen Höyrypursiseuraan](https://www.steamship.fi) (SHPS) ja
> [Savonlinnan museoon](https://www.savonlinna.fi/museo).

---

## Tausta ja kiitokset

Skilli pohjaa *Laivadatan metsästäjän oppaaseen* (Santtu Ahonen, 2025) ja
on kehitetty käytännön tutkimustyön pohjalta.

Erityiset kiitokset aineistojen alkuperäisille kokoajille:

- **Lasse Uotila / Suomen Höyrypursiseura ry (SHPS)** — Korsteenin
  laivahakemisto 1986–2024 (osat I ja II) sekä Korsteenin
  sisällysluettelon kokoaminen
- **Martti Koponen / Savonlinnan museo** — Karttunen 1945 -teoksen
  alus- ja henkilöhakemistojen digitointi sekä laaja
  sisävesiliikenteen bibliografia (riihisaari.info, 2609 viitettä)
- **Jussi Kivinen** — *Höyrylaivakirjallisuutta* (Laiva-lehti 2/2025),
  pohjana skillin kirjallisuusbibliografialle

Alkuperäiset hakemistot ja niiden tekijänoikeudet säilyvät
oikeudenhaltijoillaan.

---

## Kehitys ja palaute

Parannusehdotukset, korjaukset ja lisäykset ovat tervetulleita.

- **Sähköposti:** luupilotti@gmail.com
- **GitHub Issues:** käytä tämän repon Issues-välilehteä

Pull requestit hyväksytään harkiten — erityisesti hakukaava- ja
lähdeluettelopäivitykset ovat arvokkaita.

---

## Lisenssi

© 2025 Santtu Ahonen.

Tämä skilli on lisensoitu **Creative Commons Attribution 4.0 International
(CC BY 4.0)** -lisenssillä.

Saat vapaasti:
- **jakaa** — kopioida ja levittää materiaalia missä tahansa muodossa
- **muokata** — remiksata, muuntaa ja rakentaa materiaalin päälle
- mihin tahansa tarkoitukseen, myös kaupalliseen

Ehdolla että:
- **Tekijä mainitaan** — alkuperäinen tekijä (Santtu Ahonen), lisenssi ja
  mahdolliset muutokset on ilmoitettava selkeästi. Tekijätietoja ei saa
  poistaa eikä peittää.

Lisenssin täysi teksti:
https://creativecommons.org/licenses/by/4.0/legalcode

> Huom. CC BY 4.0 koskee skillin metodologiaa ja rakennetta.
> Korsteenin hakemistojen ja Karttunen 1945 -aineistojen oikeudet
> kuuluvat niiden alkuperäisille oikeudenhaltijoille.
