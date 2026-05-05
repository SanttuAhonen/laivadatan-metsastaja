# laivadatan-metsastaja

**Tekoälytaito vanhojen suomalaisten laivojen tiedonhakuun — botologian apuväline.**  
*An Agent Skill for researching old Finnish vessels — steamships, tugboats, log-bunchers, and motor craft. Almost all source data is in Finnish, thus the tool works best also in Finnish. Feedback on other language trials welcome.*

---

## Mikä tämä on?

`laivadatan-metsastaja` on [Agent Skills](https://agentskills.io) -muotoinen taito,
joka opettaa tekoälyavustajan (Claude tai muu yhteensopiva järjestelmä) toimimaan
botologian tutkimusapurina. Taito tietää mistä etsiä, miten lähteisiin suhtautua
ja miten rakentaa luotettava alusprofiili sirpaleisesta lähtöaineistosta.

Tyypillinen lähtötilanne: sinulla on laivan nimi, vuosiluku ja paikkakunta —
ja siitä pitäisi rakentaa kokonaiskuva. Taito ohjaa sinut oikeiden
hakemistojen, arkistojen ja lähteiden äärelle ja varoittaa tyypillisistä
karikoista (samannimiset alukset, nimenvaihdokset, OCR-virheet, sitaattiketjut).

### Mitä taito osaa

- Ehdottaa hakukaavoja Finnaan, digi.kansalliskirjasto.fi:hin, ELKAan ja laivadata.fi:hin
- Tarkistaa paikalliset hakemistot ennen verkkohakua (9 kirjaa, ~6 500+ alusmainintaa)
- Varoittaa samannimisistä aluksista (Halla I–XVII, Aallotar 1–9, Saimaa 1–6, Tornator I–IV…)
- Selittää Korsteenin hakemistojen lyhennejärjestelmän
- Rakentaa yhtenäisen alusprofiilipohjan viittauskäytäntöineen
- Tunnistaa lähdeketjuja — erottaa riippumattomat lähteet sitaattiketjuista
- Ohjata vesistösiirtojen ja nimenvaihdosten jäljittämisessä
- Tulkita aikalaiskirjoitusasujen variantteja ja vieraskielisten nimien suomennoksia
- Hakea mediajuttuja Yleltä, Helsingin Sanomista, Aamulehdestä, Turun Sanomista ja Savon Sanomista

### Mitä taito ei korvaa

- **Alkuperäisiä kirjoja** — taito tietää mistä alus löytyy ja miltä
  sivulta, mutta itse kirjojen leipäteksti ja kuvat eivät ole mukana
- ELKAn tutkijasalia ja alkuperäisiä arkistolähteitä
- Asiantuntijatietämystä — taito on apuväline, ei asiantuntija
- Visuaalista kuvantunnistusta ilman kontekstia

---

## Indeksoidut kirjat

Taitoon on sisällytetty seuraavien teosten **alus-, henkilö- ja
lähdehakemistot** — eli tieto siitä, **mitä alusta käsitellään missä
kirjassa ja millä sivulla**, sekä kirjojen omat lähdeluettelot. Itse
kirjojen sisältöä — leipätekstiä, narratiivia, kuvia, taulukoita — ei ole
indeksoitu. Botologi tarvitsee siis useimmiten vielä alkuperäisen kirjan
saadakseen kokonaiskuvan hakemastaan aluksesta.

Mutta jo tieto siitä mistä etsiä on arvokasta: se kertoo nopeasti onko
laivasta kirjoitettu, missä teoksessa, millä sivulla ja kenen aikalaisen
toimesta — säästäen tunteja kirjasto- ja antikvariaattityötä. Bibliografiset
tiedot ja kunkin aineiston alkuperäiset kokoajat löytyvät reference-
tiedostojen alusta.

### Yleishakemistot

**1. Uotila, Lasse (toim.).** *Korsteeni-laivahakemisto 1986–2025*, osat I ja II
sekä sisällysluettelo. Suomen Höyrypursiseura ry (SHPS).
- Osa I: historialliset maininnat (kadonneet ja olemassa olevat alukset), ~15 500 r.
- Osa II: olemassa olevien höyrylaivojen kaikki maininnat, ~3 500 r.

**2. Snellman, Pekka** *Korsteeni-lehden artikkelihaku 1986–2025*, ~1 600 r.
- Artikkelien kirjoittajat ja otsikot 40 vuoden ajalta.

**3. Martti Koponen / Savonlinnan museo** *Karttunen, K. I. 1945., Saimaan vesistön höyrylaivaliikenteen
100-vuotishistoria.* 
- Alushakemisto (~870 r.) ja henkilöhakemisto (~2 000 r.)
- Saimaan vanhempien alusten päälähde — yltää vuoteen 1945

**4. Riimala, Erkki (toim.) 1977.** *Höyrylaivamme.* SHPS, 2. täydennetty
painos, 112 s. ISBN 951-99140-4-8.
- Aakkosellinen kuvaluettelo (~130 alusta) + jäljellä olevien laivojen
  rekisteritieto kevään 1977 tilanteessa

**5. Pakkanen, Esko ja työryhmä 2018.** *Höyrylaivojen Suomi.* SHPS, 240 s.
- Alushakemisto sivunumeroindeksointina, 887 alusta, sekä kirjan oma lähdeluettelo

**6. Sipilä, Petri – Matikka, Hannu – Wirrankoski, Rami 2019.**
*Kelluva kulttuuriperintö — Suomen historialliset laivat.*
SLHY / Museovirasto, 336 s.
- ~1 800 alusta sivunumeroindeksointina sekä jaoteltu lähdeluettelo
  (arkistot, verkkosivut, kirjallisuus, sarjajulkaisut)

### Telakkaspesifit hakemistot

**7. Myllylä, Martti 1990.** *Albert Krank — varkautelainen laivanrakentaja.*
SHPS, 112 s.
- Lehtoniemen telakka 1889–1901 (~65 alusta), Wahl Varkaus 1882–1888
  (~50 tilausta), Krankin patentit 1883–1900

**8. Outakoski, Aslak 1949.** *Oulun Konepaja Osakeyhtiö 1873–1948.*
Kaleva (painettu 1950), 500 numeroitua kappaletta.
- Pikisaaren konepajan rakennusnumeroidut alukset N:o 101–127 (1903–1927),
  toimitusjohtajat ja pitkäaikaiset työntekijät
- Pohjanlahden laivanrakennushistorian päälähde

**9. Valta, Reijo 1997.** *Laudamiehestä Hietaseen — Paul Wahl & Co:n laivasto
ja sen toiminta 1830-luvulta vuoteen 1909.* AjanTieto 1, Gummerus Saarijärvi.
ISBN 951-97717-0-0.
- Wahlin koko laivasto 1830–1909 sekä laivakalentereiden vuosi-otokset 1835–1908
- Pohjautuu Jyväskylän maakunta-arkiston PW&CO-aineistoon

**10. Pirttiniemen telakan tilauskirjat (laivadata.fi)**
- Tilauskirja I (vanha, ~1862–) ja Tilauskirja II (1900–1965) indeksoitu
  hakemistoksi: 696 alusta, rakennusnumerot 1–771
- Sarakkeet: rak.nro, nimi, vuosi, tyyppi, tilaaja, pituus
- Avoin data (CC-lisenssi): https://www.laivadata.fi/
  — ohjeet: https://www.laivadata.fi/ohjeet/
  — kuvien rajapinta: https://www.laivadata.fi/rajapinta/
- **HUOM:** Kattaa VAIN Varkauden Pirttiniemen telakalla valmistuneet alukset
  (Paul Wahl & Co, A. Ahlström, Lehtoniemi & Taipale, myöhemmät Varkauden
  telakat). Jos laivan telakka on jo tiedossa eikä se ole Pirttiniemi,
  älä hae täältä.

### Vesistöspesifit hakemistot

**11. Wirrankoski, Raimo A. 2000** (yhteistyössä Erkki Honkasen ja Hannu
Koskisen kanssa). *Isoisän laivat — Päijänteen huviliikenteen vanhoja
ammattilaivoja.* Kopijyvä, 171 s.
- 39 pidemmän alusartikkelin hakemisto + alias-hakemisto (entiset nimet → nykyiset)
- Vuoden 2000 tilannekuva — osa aluksista on sittemmin siirtynyt muille vesistöille

### Lähdebibliografiat (eivät yksittäisiä alushakemistoja)

- **Kivinen, Jussi 2025.** *Höyrylaivakirjallisuutta.* Laiva-lehti 2/2025,
  SLHY ry — ~70 teosta vesistöittäin (`references/kirjallisuus.md`).
- **Pro gradut, lisensiaatit ja käsikirjoitukset** (Laiva 1/2026
  -bibliografia) (`references/tutkimukset.md`).
- **Hakulähteiden täysi katalogi** — verkko, arkistot, vapaakappalekirjastot,
  SoMe (`references/lahteet.md`).
- **Koposen riihisaari.info-bibliografia** — 2 609 viitettä, viittauskaavat
  ja URL-rakenne (osana `references/kirjallisuus.md`).

### Mediahakuohjeet

- **Yle, Helsingin Sanomat, Aamulehti, Turun Sanomat, Savon Sanomat**
  (`references/hakukaavat-media.md`) — hakukaavat, URL-rakenteet ja
  paywall-käytännöt viidelle suomalaiselle medialle. Sisältää aihesivun
  Yle:n höyrylaivaartikkeleille sekä Google `site:`-kaavat kaikille.
  Erityishuomio: höyrybotologi Antti Aho toimii Savon Sanomien
  toimittajana Leppävirralla.

---

## Asennus

### Anthropic Claude.ai (web tai asennettu sovellus)

1. Lataa repon zip-paketti (tuo .skill on oikeasti .zip): **Code → Download .skill**
2. Avaa Claude.ai → **Settings → Capabilities → Skills**
3. Lisää ladattu .skill eli zip-tiedosto + -napin avulla.

### Anthropic Claude Code

```bash
git clone https://github.com/SanttuAhonen/laivadatan-metsastaja \
  ~/.claude/skills/laivadatan-metsastaja
```

### Microsoft 365 Copilot Chat

Microsoft 365 Copilot Chatissa tätä skillia ei lisätä tai asenneta teknisesti, mutta sitä voidaan käyttää toimintamallina ja asiantuntijaroolina Copilotin ohjeistamiseen.
Käyttö tapahtuu pyytämällä Copilotia toimimaan Laivadatan Metsästäjän roolissa ja hyödyntämään tämän repositoryn dokumentaatiota ajattelunsa ja vastaustensa pohjana. Esimerkiksi:

*Toimi "Laivadatan Metsästäjä" ‑agenttina. Hyödynnä tämän repositoryn toimintamallia ja auta löytämään, yhdistämään ja arvioimaan laivoihin ja merenkulkuun liittyvää dataa.*

Copilotilta voi tämän jälkeen kysyä apua esimerkiksi:
- historiallisten tai nykyisten aluslähteiden löytämiseen
- eri kielillä julkaistun laivadatan tunnistamiseen
- datalähteiden luotettavuuden arviointiin
- ideoihin, mistä ja miten tietoa kannattaa etsiä

Skill toimii Copilot Chatissa prompt‑pohjaisena asiantuntijamallina, ei erillisenä agenttina, ja sen tehokkuus perustuu siihen, että Copilotille kerrotaan selkeästi tämä repository toimintakehyksenä.

#### Päivitykset

Lataa uusin .skill-versio ja korvaa aiempi tarvittaessa.

### OpenAI ChatGPT

Tämän projektin .skill-paketin voi liittää omaan GPT:hen ChatGPT:ssä.

#### Asennus
- Lataa uusin .skill-tiedosto repositorysta
- Avaa ChatGPT
- Siirry kohtaan Explore GPTs → Create
- Valitse Configure
- Lisää .skill-tiedosto GPT:hen

#### Käyttö

Tallenna GPT ja aloita käyttö – voit nyt hakea ja käsitellä laivadataa suoraan ChatGPT:ssä.

#### Päivitykset

Lataa uusin .skill-versio ja korvaa aiempi tarvittaessa.

### Muut tekoälyalustat

Taito noudattaa avointa [Agent Skills -standardia](https://agentskills.io).
`SKILL.md`-tiedosto toimii sellaisenaan muissa yhteensopivissa järjestelmissä.
Katso oman alustasi asennusohjeet.

---

## Sisältö

```
SKILL.md                                    — Pääohje (tästä tekoäly aloittaa)
references/
  alusprofiili-malli.md                     — Tulostuksen vakiomuoto + viittauskäytännöt
  hakukaavat.md                             — Hakukaavojen pääindeksi
  hakukaavat-finna.md                       — Finna: URL-rakenne ja suodattimet
  hakukaavat-digi.md                        — digi.kansalliskirjasto.fi: hakukaavat
  hakukaavat-arkistot.md                    — ELKA, laivadata.fi (Pirttiniemi), Kansallisarkisto
  hakukaavat-media.md                       — Yle, HS, Aamulehti, TS, SS: hakukaavat ja URL-rakenteet
  laivanrakennus-historia.md                — Telakat, konepajat, aluksen identiteetti
  lyhenteet-ja-terminologia.md              — Yleiset laivahistorian lyhenteet ja sanasto
  korsteeni-indeksi-lyhenteet.md            — Korsteenin omat hakemistolyhenteet
  korsteeni-osa-I.md                        — Historialliset maininnat 1986–2025
  korsteeni-osa-II.md                       — Olemassa olevien höyrylaivojen maininnat
  korsteeni-sisallysluettelo.md             — Korsteeni-lehden otsikkohaku 1986–2025
  karttunen-1945-alushakemisto.md           — Saimaan höyrylaivaliikenne, alukset
  karttunen-1945-henkilohakemisto.md        — Saimaan höyrylaivaliikenne, henkilöt
  hoyrylaivamme-1977-laivahakemisto.md      — Riimala 1977, alusluettelo
  hoyrylaivamme-1977-lahteet.md             — Riimala 1977, kirjan lähteet
  hoyrylaivojen-suomi-alushakemisto.md      — Pakkanen 2018, alushakemisto
  hoyrylaivojen-suomi-lahteet.md            — Pakkanen 2018, kirjan lähteet
  kelluva-kulttuuriperinto-laivahakemisto.md — Sipilä ym. 2019, alushakemisto
  kelluva-kulttuuriperinto-lahteet.md       — Sipilä ym. 2019, kirjan lähteet
  isoisan-laivat-laivahakemisto.md          — Wirrankoski 2000, Päijänteen alukset
  isoisan-laivat-lahteet.md                 — Wirrankoski 2000, kirjan lähteet
  pirttiniemi-tilauskirja.md                — Pirttiniemen kirjat I ja II, rak.no. 1–771 (~1862–1965), 696 alusta
  krank-1990-laivahakemisto.md              — Lehtoniemen telakka 1889–1901
  krank-1990-wahl-laivatilaukset.md         — Wahl Varkaus 1882–1888
  krank-1990-lahteet.md                     — Krankin patentit ja kirjan lähteet
  oulun-konepaja-1949-laivahakemisto.md     — Pikisaari N:o 101–127 (1903–1927)
  oulun-konepaja-1949-henkilohakemisto.md   — Toimitusjohtajat ja työntekijät
  oulun-konepaja-1949-lahteet.md            — Outakoski 1949, kirjan lähteet
  laudamiehesta-hietaseen-laivahakemisto.md — Wahl & Co:n laivasto 1830–1909
  laudamiehesta-hietaseen-henkilohakemisto.md — Wahlin toimijat
  laudamiehesta-hietaseen-lahteet.md        — Valta 1997, kirjan lähteet ja JyMA
  kirjallisuus.md                           — ~70 teosta vesistöittäin (Kivinen 2025) + riihisaari.info
  tutkimukset.md                            — Pro gradut, lisensiaatit, käsikirjoitukset
  lahteet.md                                — Hakulähteiden täysi katalogi
```

> **Suuret hakemistot** (Korsteeni I/II, Karttunen-alushakemisto) tutki aina ensin
> `grep`illä — niiden lataaminen kontekstiin kokonaisuudessaan on tuhlausta.

---

## Tausta ja kiitokset

Taito pohjaa *Laivadatan metsästäjän oppaaseen* (Santtu Ahonen, *Laiva-lehti*
4/2024) ja on kehitetty käytännön tutkimustyön pohjalta.

Erityiset kiitokset aineistojen alkuperäisille kokoajille:

- **Lasse Uotila / Suomen Höyrypursiseura ry (SHPS)** — Korsteenin
  laivahakemisto 1986–2025 (osat I ja II) 
- **Pekka Snellman / Suomen Höyrypursiseura ry (SHPS)** — Korsteenin
  artikkelihakemisto 1986–2025 
- **Martti Koponen / Savonlinnan museo** — Karttunen 1945 -teoksen alus- ja
  henkilöhakemistojen digitointi sekä laaja sisävesiliikenteen bibliografia
  (riihisaari.info, 2 609 viitettä).
- **Jussi Kivinen** — *Höyrylaivakirjallisuutta* (Laiva-lehti 2/2025),
  pohjana taidon kirjallisuusbibliografialle.
- **laivadata.fi / Suomen Höyrypursiseura ry (SHPS)** — Pirttiniemen telakan
  digitoidut tilauskirjat, avoin data (CC-lisenssi).

Hakemistoaineistojen tekijänoikeudet säilyvät niiden alkuperäisillä
oikeudenhaltijoilla — ks. tekijätiedot kunkin reference-tiedoston alussa.

---

## Kehitys ja palaute

Parannusehdotukset, korjaukset ja lisäykset ovat tervetulleita.

- **Sähköposti:** luupilotti@gmail.com — voit pyytää myös uudempaa,
  päivitettyä versiota
- **GitHub Issues:** käytä tämän repon Issues-välilehteä

Pull requestit hyväksytään harkiten — erityisesti hakukaava- ja
lähdeluettelopäivitykset ovat arvokkaita.

---

## Lisenssi

© 2026 Santtu Ahonen.

Tämä taito on lisensoitu **Creative Commons Attribution 4.0 International
(CC BY 4.0)** -lisenssillä.

Saat vapaasti:
- **jakaa** — kopioida ja levittää materiaalia missä tahansa muodossa
- **muokata** — remiksata, muuntaa ja rakentaa materiaalin päälle
- mihin tahansa tarkoitukseen, myös kaupalliseen

Ehdolla että:
- **Tekijä mainitaan** — alkuperäinen tekijä (Santtu Ahonen), lisenssi ja
  mahdolliset muutokset on ilmoitettava selkeästi. Tekijätietoja ei saa
  poistaa eikä peittää.

Lisenssin täysi teksti: https://creativecommons.org/licenses/by/4.0/legalcode

> **Huom.** CC BY 4.0 koskee taidon metodologiaa, rakennetta ja sen pohjaksi
> kirjoitettuja ohjeita. Sisällytettyjen hakemistojen tekijänoikeudet
> kuuluvat niiden alkuperäisille oikeudenhaltijoille — kunkin
> reference-tiedoston alussa on tekijätieto ja viittausohje.
