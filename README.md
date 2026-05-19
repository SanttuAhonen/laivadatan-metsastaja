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

Taito on lähdeaineistojensa takia parhaimmillaan **1980-luvun ja sitä
vanhempien alusten** parissa — erityisesti höyrylaivojen sekä nykyisten
dieselalusten, jotka ovat aiemmin kulkeneet höyryllä — historian ja
taustojen selvittelyssä. Työnkulku ja lähdekatalogi soveltuvat silti
myös muunlaisten alusten tutkimukseen, vaikka paikallinen hakemistopeitto
on niiden osalta ohuempi.

- Ehdottaa hakukaavoja Finnaan, digi.kansalliskirjasto.fi:hin, ELKAan ja laivadata.fi:hin
- Tarkistaa paikalliset hakemistot ennen verkkohakua (16 julkaisua, ~7 500+ alusmainintaa)
- Varoittaa samannimisistä aluksista (Halla I–XVII, Aallotar 1–9, Saimaa 1–6, Tornator I–IV, Ahti ×4, Kuopio ×4, Wellamo ×4…)
- Selittää Korsteenin hakemistojen lyhennejärjestelmän
- Rakentaa yhtenäisen alusprofiilipohjan viittauskäytäntöineen
- Tunnistaa lähdeketjuja — erottaa riippumattomat lähteet sitaattiketjuista
- Ohjaa vesistösiirtojen ja nimenvaihdosten jäljittämisessä
- Tulkitsee aikalaiskirjoitusasujen variantteja ja vieraskielisten nimien suomennoksia
- Selittää Suomen alusrekisterien historian (1874→), kolmen rinnakkaisen rekisterin
  rakenteen sekä mikrotonniston (alle 19 nrt) rekisteripuutteet
- Tuntee kansainväliset alusten tunnistejärjestelmät (IMO, MMSI, ITU-kutsumerkit, ENI)
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
sivulla. **Kirjojen, lehtien tai muiden julkaisujen sisältöä ei täällä
ole mukana — itse sisältöön tarvitset alkuperäisen julkaisun**. Mutta
jo tieto siitä, missä julkaisussa alus mainitaan, säästää tunteja
kirjasto- ja antikvariaattityötä.

**Numeroina:**

- **16 indeksoitua julkaisua** — 13 kirjaa, yksi väitöskirja (Kivinen 2016),
  yksi pro gradu (Koponen 1988) ja yhden telakan tilauskirjapari (Pirttiniemi /
  laivadata.fi)
- **~7 500+ alusmainintaa** yhteensä — sis. ~16 000 rivin
  Korsteeni-laivahakemisto (Uotila), Pakkasen 887 alusta, Sipilän ~1 800,
  Pirttiniemen 696, Karttusen ~870, Tuomi-Nikulan ~960 ja kymmenen muuta
  telakka-, vesistö- ja yleishakemistoa
- **~2 200+ henkilöä rooleittain** — kapteenit, varustajat, telakka-
  yhtiöiden toimijat (Karttunen, Oulun Konepaja, Wahl, Nummela)
- **2 opinnäytetyön oma sisältö** indeksoituna + Laiva-lehden
  pro gradu / lisensiaatti / käsikirjoitus -bibliografia (Kivinen 2026)
- **Laiva-lehden sisällysluettelo 1/2001–1/2026** (92 lehteä)
- **Korsteeni-lehden sisällysluettelot 1986–2025** (Snellman, ~1 630 r.)
- **9 sanomalehden hakuohjeet** — Yle, HS, Aamulehti, TS, SS,
  Etelä-Saimaa, Karjalainen, Warkauden Lehti, Iisalmen Sanomat
- **20+ verkkohakukohdetta** — Finna, digi.kansalliskirjasto.fi,
  ELKA/Astia, Kansallisarkisto, laivadata.fi, riihisaari.info ja
  yliopistojen avoimet julkaisuarkistot (JYX, Trepo, Helda, UTUPub,
  UEF, Jultika, Aaltodoc, LUTPub, Osuva, Doria, Lauda) sekä joukko
  laivaharrastajien, yhdistysten ja botologien www-sivuja ja
  keskustelufoorumeita. Sen lisäksi tietysti yleishaut verkossa.

Yksityiskohtainen tiedostokohtainen sisältö löytyy alta
[Sisältö-osasta](#sisältö). Kunkin lähteen alkuperäiset kokoajat ja
bibliografiset tiedot on kirjattu reference-tiedostojen alkuun.

---

## Asennus

### Anthropic Claude.ai (web tai asennettu sovellus)

1. **Lataa [laivadatan-metsastaja.skill](https://github.com/SanttuAhonen/laivadatan-metsastaja/raw/main/laivadatan-metsastaja.skill)** (`.skill`-tiedosto on käytännössä `.zip`-paketti) koneellesi.
2. Avaa Claude.ai → **Customize → Skills → "+" → Upload a Skill**

#### Käyttö

Voit ottaa asennetun skillin chatissa käyttöösi /-komennon avulla. Claude antaa keskustelussa tuolla /-komennolla valikon josta Laivadatan Metsästäjä on valittavissa.

#### Päivitykset

Lataa uusi `laivadatan-metsastaja.skill` Claudeen, Claude kysyy haluatko päivittää vanhan Skillin. Huomaa, että tiedostonimen pitää olla sama kuin edellisellä latauksella.

### Anthropic Claude Code

```bash
git clone https://github.com/SanttuAhonen/laivadatan-metsastaja \
  ~/.claude/skills/laivadatan-metsastaja
```

### OpenAI ChatGPT, Microsoft 365 Copilot ja muut tekoälyalustat

Agent Skills on avoin alustariippumaton standardi
([agentskills.io](https://agentskills.io)), jota yhä useammat tekoälyalustat
tukevat. Tuen toteutus ja käyttötapa kuitenkin vaihtelevat alustakohtaisesti
ja muuttuvat nopeasti. **Paras ohje on usein kysyä avustajalta itseltään**,
miten Agent Skills -muotoinen paketti otetaan käyttöön juuri sillä alustalla
ja sillä tilauksellasi.

Liitä [laivadatan-metsastaja.skill](https://github.com/SanttuAhonen/laivadatan-metsastaja/raw/main/laivadatan-metsastaja.skill) chattiviestiin ja pyydä esimerkiksi:

> *Toimi "Laivadatan Metsästäjä" -agenttina. Liitteenä on avoimen
> Agent Skills -standardin ([agentskills.io](https://agentskills.io))
> mukainen taitopaketti. Miten tämä otetaan käyttöön tällä alustalla,
> ja toimisitko sen ohjeiden mukaisesti tämän keskustelun ajan?*

Avustaja osaa tyypillisesti ohjata oman alustansa käytäntöihin — esimerkiksi
ChatGPT:llä on Skills-välilehti ja Custom GPT -knowledge-osio, ja
Microsoft 365 Copilot Coworkilla on oma `Documents/Cowork/skills/`
-kansiokäytäntö OneDrivessä.

#### Päivitykset

Lataa uusin [laivadatan-metsastaja.skill](https://github.com/SanttuAhonen/laivadatan-metsastaja/raw/main/laivadatan-metsastaja.skill) ja korvaa aiempi alustasi ohjeiden mukaisesti.

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
  vesikulkuneuvon-rekisteritiedot.md           — Traficomin korttitodistus: kentät a1–a16/b1–b5/c1–c3
  kansainvaliset-tunnistejarjestelmat.md       — IMO, MMSI, ITU-kutsumerkit, ENI
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
  hoyrymurtajien-aika-sisallys.md              — Laurell 1992, sisällysluettelo + laivanavigaatiotaulukko
  hoyrymurtajien-aika-lahteet.md               — Laurell 1992, kirjan lähteet
  punatahtisen-sotalipun-alla-laivahakemisto.md — Tuomi-Nikula 2000, takakannen alushakemisto (~960 r.)
  punatahtisen-sotalipun-alla-lahteet.md       — Tuomi-Nikula 2000, lähdeluettelo
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

---

## Tausta ja kiitokset

Taito pohjaa *Laivadatan metsästäjän oppaaseen* (Santtu Ahonen, *Laiva-lehti*
4/2024) ja on kehitetty käytännön tutkimustyön pohjalta.

Erityiset kiitokset ensimmäisten aineistojen alkuperäisille kokoajille. Aineistot 
ovat toimineet oivana inspiraationa ja lähteenä tämän skillin versioille:

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
- **laivadata.fi** — Pirttiniemen telakan
  digitoidut tilauskirjat, avoin data (CC-lisenssi).

Hakemistoaineistojen tekijänoikeudet säilyvät niiden alkuperäisillä
oikeudenhaltijoilla — ks. tekijätiedot kunkin reference-tiedoston alussa.

---

## Kehitys ja palaute

Parannusehdotukset, korjaukset, uudet hakemistot ja muut lisäykset ovat
tervetulleita. Ks. tarkemmat ohjeet [CONTRIBUTING.md](./CONTRIBUTING.md).

- **Discussions:** [github.com/SanttuAhonen/laivadatan-metsastaja/discussions](https://github.com/SanttuAhonen/laivadatan-metsastaja/discussions)
  — ensisijainen kanava kaikenlaiseen osallistumiseen
- **Sähköposti:** luupilotti@gmail.com — jos GitHub-tunnusta ei ole,
  tai voit pyytää myös uudempaa, päivitettyä versiota tätä kautta

---

## Lisenssi

© 2026 Santtu Ahonen. Lisensoitu **Creative Commons Attribution 4.0
International (CC BY 4.0)** -lisenssillä. Täysi lisenssiteksti repon
juuressa: [LICENSE](./LICENSE) (englanti) ja [LICENSE.fi](./LICENSE.fi) (suomi).

> **Huom.** CC BY 4.0 koskee taidon metodologiaa, rakennetta ja sen pohjaksi
> kirjoitettuja ohjeita. Sisällytettyjen hakemistojen tekijänoikeudet
> kuuluvat niiden alkuperäisille oikeudenhaltijoille — kunkin
> reference-tiedoston alussa on tekijätieto ja viittausohje.
