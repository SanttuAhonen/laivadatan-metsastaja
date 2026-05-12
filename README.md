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
- Tarkistaa paikalliset hakemistot ennen verkkohakua (14 julkaisua, ~7 000+ alusmainintaa)
- Varoittaa samannimisistä aluksista (Halla I–XVII, Aallotar 1–9, Saimaa 1–6, Tornator I–IV, Ahti ×4, Kuopio ×4, Wellamo ×4…)
- Selittää Korsteenin hakemistojen lyhennejärjestelmän
- Rakentaa yhtenäisen alusprofiilipohjan viittauskäytäntöineen
- Tunnistaa lähdeketjuja — erottaa riippumattomat lähteet sitaattiketjuista
- Ohjaa vesistösiirtojen ja nimenvaihdosten jäljittämisessä
- Tulkitsee aikalaiskirjoitusasujen variantteja ja vieraskielisten nimien suomennoksia
- Selittää Suomen alusrekisterien historian (1874→), kolmen rinnakkaisen rekisterin
  rakenteen sekä mikrotonniston (alle 19 nrt) rekisteripuutteet
- Hakee mediajuttuja Yleltä, Helsingin Sanomista, Aamulehdestä, Turun Sanomista ja Savon Sanomista
- Ohjaa pro gradujen ja muiden opinnäytetöiden hakuun yliopistojen avoimista
  julkaisuarkistoista (JYX, Trepo, Helda, Doria jne.)

### Mitä taito ei korvaa

- **Alkuperäisiä kirjoja** — taito tietää minkä julkaisun miltä sivulta alus löytyy, mutta itse kirjojen leipäteksti ja kuvat eivät ole mukana
- ELKAn tutkijasalia ja alkuperäisiä arkistolähteitä
- Asiantuntijatietämystä — taito on apuväline, ei asiantuntija
- Visuaalista kuvantunnistusta ilman kontekstia
- Käsinkirjoitettujen historiallisten luetteloiden lukua — tekoäly ei pysty
  riittävällä tarkkuudella tulkitsemaan käsialaa (testattu 2026-05)

---

## Mitä skillissä on indeksoitu

Taitoon on sisällytetty **kirjojen, väitöskirjojen, gradujen, lehtien
ja telakkakirjojen omat alus-, henkilö- ja lähdehakemistot** — eli
tieto siitä, mitä alusta käsitellään missä julkaisussa ja millä
sivulla. Itse kirjojen sisältöä (leipäteksti, narratiivi, kuvat,
taulukot) ei ole indeksoitu, vaan tarvitset useimmiten vielä
alkuperäisen julkaisun. Mutta jo tieto siitä mistä etsiä säästää
tunteja kirjasto- ja antikvariaattityötä.

**Numeroina:**

- **14 indeksoitua julkaisua** — 11 kirjaa, 1 väitöskirja (Kivinen 2016),
  1 pro gradu (Koponen 1988) ja 1 telakan tilauskirjapari (Pirttiniemi /
  laivadata.fi)
- **~7 000+ alusmainintaa** yhteensä — sis. ~16 000 rivin
  Korsteeni-laivahakemisto (Uotila), Korsteenin artikkelihaku
  (Snellman, ~1 630 r.), Pakkasen 887 alusta, Sipilän ~1 800,
  Pirttiniemen 696, Karttusen ~870 ja kymmenen muuta telakka-, vesistö-
  ja yleishakemistoa
- **~2 200+ henkilöä rooleittain** — kapteenit, varustajat, telakka-
  yhtiöiden toimijat (Karttunen, Oulun Konepaja, Wahl, Nummela)
- **2 opinnäytetyön oma sisältö** indeksoituna + Laiva-lehden
  pro gradu / lisensiaatti / käsikirjoitus -bibliografia (Kivinen 2026)
- **Laiva-lehden sisällysluettelo 1/2001–1/2026** (92 lehteä)
- **9 sanomalehden hakuohjeet** — Yle, HS, Aamulehti, TS, SS,
  Etelä-Saimaa, Karjalainen, Warkauden Lehti, Iisalmen Sanomat
- **~17 verkkohakukohdetta** — Finna, digi.kansalliskirjasto.fi,
  ELKA/Astia, Kansallisarkisto, laivadata.fi, riihisaari.info ja
  yliopistojen avoimet julkaisuarkistot (JYX, Trepo, Helda, UTUPub,
  UEF, Jultika, Aaltodoc, LUTPub, Osuva, Doria, Lauda)

Yksityiskohtainen tiedostokohtainen sisältö löytyy alta
[Sisältö-osasta](#sisältö). Kunkin lähteen alkuperäiset kokoajat ja
bibliografiset tiedot on kirjattu reference-tiedostojen alkuun.

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
SKILL.md                                       — Pääohje (tästä tekoäly aloittaa)
CHANGELOG.md                                   — Versionhistoria
references/
  alusprofiili-malli.md                        — Tulostuksen vakiomuoto + viittauskäytännöt
  hakukaavat.md                                — Hakukaavojen pääindeksi
  hakukaavat-finna.md                          — Finna: URL-rakenne ja suodattimet
  hakukaavat-digi.md                           — digi.kansalliskirjasto.fi: hakukaavat
  hakukaavat-arkistot.md                       — ELKA, laivadata.fi (Pirttiniemi), Kansallisarkisto
  hakukaavat-media.md                          — Yle, HS, Aamulehti, TS, SS: hakukaavat ja URL-rakenteet
  hakukaavat-tutkimukset.md                    — Yliopistojen avoimet julkaisuarkistot (JYX, Trepo, Helda…)
  laivanrakennus-historia.md                   — Telakat, konepajat, aluksen identiteetti
  alusrekisterien-historia.md                  — Suomen alusrekisterit 1874→, mikrotonniston puutteet
  lyhenteet-ja-terminologia.md                 — Yleiset laivahistorian lyhenteet ja sanasto
  korsteeni-indeksi-lyhenteet.md               — Korsteenin omat hakemistolyhenteet
  korsteeni-osa-I.md                           — Historialliset maininnat 1986–2025
  korsteeni-osa-II.md                          — Olemassa olevien höyrylaivojen maininnat
  korsteeni-sisallysluettelo.md                — Korsteeni-lehden otsikkohaku 1986–2025
  laiva-lehti-sisallysluettelo.md              — Laiva-lehden sisällysluettelo 1/2001–1/2026
  saimaan-100-vuotishistoria-alushakemisto.md  — Karttunen 1945, alushakemisto
  saimaan-100-vuotishistoria-henkilohakemisto.md — Karttunen 1945, henkilöhakemisto
  hoyrylaivamme-1977-laivahakemisto.md         — Riimala 1977, alusluettelo
  hoyrylaivamme-1977-lahteet.md                — Riimala 1977, kirjan lähteet
  hoyrylaivojen-suomi-alushakemisto.md         — Pakkanen 2018, alushakemisto
  hoyrylaivojen-suomi-lahteet.md               — Pakkanen 2018, kirjan lähteet
  kelluva-kulttuuriperinto-laivahakemisto.md   — Sipilä ym. 2019, alushakemisto
  kelluva-kulttuuriperinto-lahteet.md          — Sipilä ym. 2019, kirjan lähteet
  isoisan-laivat-laivahakemisto.md             — Wirrankoski 2000, Päijänteen alukset
  isoisan-laivat-lahteet.md                    — Wirrankoski 2000, kirjan lähteet
  pirttiniemi-tilauskirja.md                   — Pirttiniemen kirjat I ja II, rak.no. 1–771 (~1862–1965), 696 alusta
  krank-1990-laivahakemisto.md                 — Lehtoniemen telakka 1889–1901
  krank-1990-wahl-laivatilaukset.md            — Wahl Varkaus 1882–1888
  krank-1990-lahteet.md                        — Krankin patentit ja kirjan lähteet
  koponen-1988-laivahakemisto.md               — Koponen 1988 -gradun leipätekstin alusmaininnat
  oulun-konepaja-1949-laivahakemisto.md        — Pikisaari N:o 101–127 (1903–1927)
  oulun-konepaja-1949-henkilohakemisto.md      — Toimitusjohtajat ja työntekijät
  oulun-konepaja-1949-lahteet.md               — Outakoski 1949, kirjan lähteet
  laudamiehesta-hietaseen-laivahakemisto.md    — Wahl & Co:n laivasto 1830–1909
  laudamiehesta-hietaseen-henkilohakemisto.md  — Wahlin toimijat
  laudamiehesta-hietaseen-lahteet.md           — Valta 1997, kirjan lähteet ja JyMA
  kuopion-historia-iii-laivahakemisto.md       — Nummela 1989, Kuopion alukset ja 1912-taulukko
  kuopion-historia-iii-henkilohakemisto.md     — Nummela 1989, henkilöt ja yhtiöt
  sisavesien-mikrotonnisto-laivahakemisto.md   — Kivinen 2016, Liite 6 laivannimet
  sisavesien-mikrotonnisto-paikkahakemisto.md  — Kivinen 2016, Liite 7 paikannimet
  sisavesien-mikrotonnisto-1870-laivat.md      — Kivinen 2016, Liite 2 vuoden 1870 höyrylaivat vesistöittäin
  sisavesien-mikrotonnisto-lahteet.md          — Kivinen 2016, lähdeluvun tiivistys
  kirjallisuus.md                              — ~70 teosta vesistöittäin (Kivinen 2025) + riihisaari.info
  tutkimukset.md                               — Pro gradut, lisensiaatit, käsikirjoitukset
  lahteet.md                                   — Hakulähteiden täysi katalogi
```

> **Suuret hakemistot** (Korsteeni I/II, Saimaan 100-vuotishistoria
> -alushakemisto, Kelluva kulttuuriperintö, Höyrylaivojen Suomi, Laiva-lehti
> sisällysluettelo) tutki aina ensin `grep`illä — niiden lataaminen
> kontekstiin kokonaisuudessaan on tuhlausta.

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
  pohjana taidon kirjallisuusbibliografialle, sekä *Sisävesien
  mikrotonnisto* (väitöskirja 2016) joka tarjoaa myös laajan
  arkistolähteiden tiivistyksen.
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
