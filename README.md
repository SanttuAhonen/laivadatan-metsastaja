# laivadatan-metsastaja

**Tekoälytaito vanhojen suomalaisten laivojen tiedonhakuun, botologian apuväline.**  
*An Agent Skill for researching old Finnish vessels: steamships, tugboats, log-bunchers and motor craft. Almost all source data is in Finnish, so the tool works best in Finnish. Feedback on other language trials is welcome.*

Versiotiedot ja muutokset: `CHANGELOG.md` paketin sisällä.

---

## Mikä tämä on?

`laivadatan-metsastaja` on [Agent Skills](https://agentskills.io) -muotoinen taito,
joka opettaa tekoälyavustajan (Claude tai muu yhteensopiva järjestelmä) toimimaan
botologian tutkimusapurina. Taito tietää, mistä etsiä, miten lähteisiin suhtautua
ja miten rakentaa luotettava alus- tai henkilöprofiili sirpaleisesta lähtöaineistosta.

Tyypillinen lähtötilanne: sinulla on laivan nimi, vuosiluku ja paikkakunta,
ja niistä pitäisi rakentaa kokonaiskuva. Taito ohjaa oikeiden hakemistojen,
arkistojen ja lähteiden äärelle ja varoittaa tyypillisistä karikoista, kuten
samannimisistä aluksista, nimenvaihdoksista, OCR-virheistä ja sitaattiketjuista.

### Mitä taito osaa

Taito on lähdeaineistojensa takia parhaimmillaan **1980-luvun ja sitä
vanhempien alusten** parissa, erityisesti höyrylaivojen ja nykyisten
dieselalusten, jotka ovat aiemmin kulkeneet höyryllä. Työnkulku ja
lähdekatalogi soveltuvat myös muiden alusten tutkimukseen, vaikka paikallinen
hakemistopeitto on niiden osalta ohuempi.

- Tarkistaa paikalliset hakemistot ennen verkkohakua (18 julkaisua, noin 9 000 alusmainintaa)
- Tekee haut suoraan selainikkunassa: Finna, digi.kansalliskirjasto.fi, ELKA ja laivadata.fi, ilman käsin tehtävää välivaihetta
- Tunnistaa telakan nimen perusteella: lähteiden kirjoitusasut, yhtiöiden nimenmuutokset ja samannimiset telakat (esim. kaksi eri *Helsingin Laivatelakkaa*, kaksi *Viipurin konepajaa*)
- Tuntee Suomen telakoiden ja laivoja rakentaneiden konepajojen historian 1830-luvulta nykypäivään: yhtiöketjut, toimintavuodet, alusluettelot ja arkistot
- Erottaa rungon rakentajan, kokoamispaikan ja koneen valmistajan sekä korjaus- ja talvehtimismerkinnät rakennuspaikasta
- Varoittaa samannimisistä aluksista (Halla I–XVII, Aallotar 1–9, Saimaa 1–6, Tornator I–IV, Ahti ×4, Kuopio ×4, Wellamo ×4…)
- Selittää Korsteenin hakemistojen lyhennejärjestelmän
- Rakentaa yhtenäisen alus- tai henkilöprofiilin viittauskäytäntöineen (henkilöprofiili: laivurin, kapteenin, konemiehen tai muun laivaväen ura)
- Erottaa riippumattomat lähteet sitaattiketjuista ja kirjaa ristiriitaiset tiedot rinnakkain lähteineen
- Ohjaa vesistösiirtojen ja nimenvaihdosten jäljittämisessä
- Tulkitsee aikalaiskirjoitusasujen variantteja ja vieraskielisten nimien suomennoksia
- Selittää alusten mittojen merkinnät ja mittaustavat (miksi saman aluksen pituus vaihtelee lähteittäin)
- Selittää Suomen alusrekisterien historian (1874→), kolmen rinnakkaisen rekisterin
  rakenteen sekä mikrotonniston (alle 19 nrt) rekisteripuutteet
- Tuntee kansainväliset alusten tunnistejärjestelmät (IMO, MMSI, ITU-kutsumerkit, ENI)
- Ohjaa pro gradujen ja muiden opinnäytteiden hakuun yliopistojen avoimista
  julkaisuarkistoista (JYX, Trepo, Helda, Doria jne.)

### Lähdekuri

Jokainen hakemistotiedosto sisältää vain oman lähteensä tiedot. Toisen lähteen
tietoa tai arviota lähteen oikeellisuudesta ei lisätä lähdetiedostoon, vaikka
lähteet olisivat ristiriidassa. Vertailu ja ristiriidat kirjataan erikseen
telakkaselvityksiin ja alusprofiileihin, jolloin tiedon alkuperä säilyy.

### Mitä taito ei korvaa

- **Alkuperäisiä julkaisuja:** taito tietää, minkä julkaisun miltä sivulta alus löytyy, mutta kirjojen leipäteksti ja kuvat eivät ole mukana
- ELKAn tutkijasalia ja alkuperäisiä arkistolähteitä
- Asiantuntijatietämystä: taito on apuväline, ei asiantuntija
- Visuaalista kuvantunnistusta ilman kontekstia
- Käsinkirjoitettujen historiallisten luetteloiden lukua: tekoäly ei pysty
  tulkitsemaan käsialaa riittävällä tarkkuudella (testattu 2026-05)

---

## Mitä skillissä on indeksoitu

Taitoon on sisällytetty **kirjojen, väitöskirjan, opinnäytteiden, lehtien
ja telakan tilauskirjojen alus-, henkilö- ja lähdehakemistot** eli tieto
siitä, mitä alusta käsitellään missä julkaisussa ja millä sivulla.
**Julkaisujen sisältöä ei ole mukana; sisältöön tarvitset alkuperäisen
julkaisun.** Jo tieto siitä, missä alus mainitaan, säästää tunteja
kirjasto- ja antikvariaattityötä.

**Numeroina:**

- **18 indeksoitua julkaisua:** 12 kirjaa, yksi väitöskirja (Kivinen 2016),
  yksi pro gradu (Koponen 1988), yksi lisensiaattityö (Koponen 2001),
  Korsteeni- ja Laiva-lehden hakemistot sekä Pirttiniemen telakan
  tilauskirjat (laivadata.fi)
- **Noin 9 000 alusmainintaa,** joista suurimmat: Korsteenin laivahakemisto
  (Uotila, noin 16 000 riviä), Sipilä ym. noin 1 800, *Navis Fennica 4*
  995, Tuomi-Nikula noin 960, Pakkanen 887, Karttunen noin 870,
  Pirttiniemi 696 ja *Teollinen höyrylaivanrakennus* noin 530
- **Noin 2 200 henkilöä rooleittain:** kapteenit, varustajat ja
  telakkayhtiöiden toimijat (Karttunen, Oulun Konepaja, Wahl, Nummela)
- **Suomen telakkahistoria:** 45 telakan tai konepajan luettelo,
  nimimuotohakemisto, monitulkintaiset nimet ja 13 aluetiedostoa
  (Helsinki, Turku, Varkaus, Savonlinna, Kymijoen vesistö, Tampere,
  Viipuri, Porvoo, muut telakat, pienet rakennuspaikat, moottorikausi,
  ulkomaiset rakentajat, alusluettelot ja arkistot), noin 2 700 riviä.
  Telakkatiedot on ristiintarkistettu lisensiaattityötä *Teollinen
  höyrylaivanrakennus Suomessa 1833–1959* (2001) ja aikalaislehtiä vasten.
- **Laiva-lehden sisällysluettelo 1/2001–2/2026** (93 merkintää)
- **Korsteeni-lehden sisällysluettelot 1986–2025** (Snellman, noin 1 630 riviä)
- **Opinnäytebibliografia:** pro gradut, lisensiaattityöt ja käsikirjoitukset
  (Kivinen 2026 ja muut)
- **9 sanomalehden hakuohjeet:** Yle, HS, Aamulehti, TS, SS,
  Etelä-Saimaa, Karjalainen, Warkauden Lehti, Iisalmen Sanomat
- **Yli 20 verkkohakukohdetta:** Finna, digi.kansalliskirjasto.fi,
  ELKA/Astia, Kansallisarkisto, laivadata.fi, riihisaari.info ja
  yliopistojen avoimet julkaisuarkistot (JYX, Trepo, Helda, UTUPub,
  UEF, Jultika, Aaltodoc, LUTPub, Osuva, Doria, Lauda) sekä
  laivaharrastajien, yhdistysten ja botologien sivuja ja
  keskustelufoorumeita. Lisäksi yleishaut verkossa.

**Korsteeni-hakemisto on keskeneräinen.** Telakkatiedostojen Korsteeni-viitteet,
jotka on paikannettu hakemiston kautta, on merkitty `[K-hak]`. Ne tarkistetaan,
kun hakemiston korjattu versio valmistuu.

Tiedostokohtainen sisältö löytyy alta [Sisältö-osasta](#sisältö). Kunkin lähteen
kokoajat ja bibliografiset tiedot on kirjattu hakemistotiedostojen alkuun.

---

## Asennus

### Anthropic Claude.ai (web tai asennettu sovellus)

1. **Lataa [laivadatan-metsastaja.skill](https://github.com/SanttuAhonen/laivadatan-metsastaja/raw/main/laivadatan-metsastaja.skill)** koneellesi (`.skill`-tiedosto on käytännössä `.zip`-paketti).
2. Avaa Claude.ai → **Customize → Skills → "+" → Upload a Skill**

#### Käyttö

Asennetun skillin saa chatissa käyttöön /-komennolla. Claude näyttää valikon,
josta Laivadatan Metsästäjä on valittavissa.

#### Päivitykset

Lataa uusi `laivadatan-metsastaja.skill` Claudeen, niin Claude kysyy, haluatko
päivittää vanhan skillin. Tiedostonimen pitää olla sama kuin edellisellä
latauksella.

### Anthropic Claude Code

Pura `laivadatan-metsastaja.skill` (zip) kansioon `~/.claude/skills/`:

```bash
curl -L -o laivadatan-metsastaja.skill \
  https://github.com/SanttuAhonen/laivadatan-metsastaja/raw/main/laivadatan-metsastaja.skill
unzip laivadatan-metsastaja.skill -d ~/.claude/skills/
```

### OpenAI ChatGPT, Microsoft 365 Copilot ja muut tekoälyalustat

Agent Skills on avoin alustariippumaton standardi
([agentskills.io](https://agentskills.io)), jota yhä useammat tekoälyalustat
tukevat. Tuen toteutus ja käyttötapa vaihtelevat alustoittain ja muuttuvat
nopeasti. **Paras ohje on usein kysyä avustajalta itseltään,** miten Agent
Skills -muotoinen paketti otetaan käyttöön juuri sillä alustalla ja sillä
tilauksella.

Liitä [laivadatan-metsastaja.skill](https://github.com/SanttuAhonen/laivadatan-metsastaja/raw/main/laivadatan-metsastaja.skill) chattiviestiin ja pyydä esimerkiksi:

> *Toimi "Laivadatan Metsästäjä" -agenttina. Liitteenä on avoimen
> Agent Skills -standardin ([agentskills.io](https://agentskills.io))
> mukainen taitopaketti. Miten tämä otetaan käyttöön tällä alustalla,
> ja toimisitko sen ohjeiden mukaisesti tämän keskustelun ajan?*

Avustaja osaa tyypillisesti ohjata oman alustansa käytäntöihin. Esimerkiksi
ChatGPT:llä on Skills-välilehti ja Custom GPT -knowledge-osio, ja
Microsoft 365 Copilot Coworkilla on oma `Documents/Cowork/skills/`
-kansiokäytäntö OneDrivessä.

#### Päivitykset

Lataa uusin [laivadatan-metsastaja.skill](https://github.com/SanttuAhonen/laivadatan-metsastaja/raw/main/laivadatan-metsastaja.skill) ja korvaa aiempi alustasi ohjeiden mukaisesti.

---

## Sisältö

```
SKILL.md                                       Pääohje (tästä tekoäly aloittaa)
CHANGELOG.md                                   Versionhistoria
references/
  Työnkulku ja mallit
  alusprofiili-malli.md                        Aluksen profiilin vakiomuoto ja viittauskäytännöt
  henkiloprofiili-malli.md                     Henkilön (laivuri, kapteeni, konemies, mestari…) profiilin vakiomuoto
  tunnistus-valokuvasta.md                     Aluksen tunnistaminen valokuvasta: työnkulku ja karikot
  hakukaavat.md                                Hakukaavojen pääindeksi
  hakukaavat-finna.md                          Finna: URL-rakenne, suodattimet, telakan arkistohaku
  hakukaavat-kansalliskirjasto.md              digi.kansalliskirjasto.fi: hakukaavat ja XLSX-massatyönkulku
  hakukaavat-arkistot.md                       ELKA, laivadata.fi, Kansallisarkisto, telakkahistorian lähteet
  hakukaavat-media.md                          Yle, HS, Aamulehti, TS, SS: hakukaavat ja URL-rakenteet
  hakukaavat-tutkimukset.md                    Yliopistojen avoimet julkaisuarkistot (JYX, Trepo, Helda…)

  Taustatieto
  laivanrakennus-historia.md                   Laivanrakennuksen kehitys, koneet, aluksen identiteetti
  alusrekisterien-historia.md                  Suomen alusrekisterit 1874→, mikrotonniston puutteet
  vesikulkuneuvon-rekisteritiedot.md           Traficomin korttitodistus: kentät a1–a16/b1–b5/c1–c3
  kansainvaliset-tunnistejarjestelmat.md       IMO, MMSI, ITU-kutsumerkit, ENI
  alusten-mittojen-merkinnat-ja-mittaustavat.md  Mittatyypit ja mittojen vertailu
  lyhenteet-ja-terminologia.md                 Laivahistorian lyhenteet ja sanasto

  Telakkahistoria
  suomen-telakat.md                            Keskustiedosto: tunnistus nimien perusteella, telakkaluettelo,
                                               nimimuotohakemisto, monitulkintaiset nimet, henkilöt
  telakat/helsinki.md                          Hietalahti, Ullanlinna, Stenberg, Kone ja Silta ym.
  telakat/turku.md                             Crichton, Vulcan, Crichton-Vulcan, Pansio, Perno ym.
  telakat/varkaus.md                           Pirtinniemi (Wahl, Ahlström) ja Lehtoniemi
  telakat/savonlinna.md                        Savonniemi, Lypsyniemi, Laitaatsilta, Pääskyniemi ym.
  telakat/kymijoki.md                          Päijänne ja Kymijoen vesistö: Väinölä, Heinola, Vähä-Äiniö ym.
  telakat/tampere.md                           Tampella, Tammelan konepaja, Dunderberg, Onkiniemi ym.
  telakat/viipuri.md                           Wiborgs Mekaniska Verkstad, Gallén, Kaksoissaari ym.
  telakat/porvoo.md                            Porvoon Konepaja, Borgå Båtvarf ym.
  telakat/muut-telakat.md                      Oulu, Kemi, Pori, Puhos, Kuopio, Kotka, Lappeenranta
  telakat/pienet-rakennuspaikat.md             Pienet telakat, veistämöt ja rakennuspaikat
  telakat/moottorikausi.md                     Moottorikauden telakat ja sotakorvaukset
  telakat/ulkomaiset.md                        Ulkomaiset rakentajat, yleiskatsaus
  telakat/alusluettelot-ja-arkistot.md         Mistä kunkin telakan alusluettelo ja arkisto löytyy

  Lehtien hakemistot
  korsteeni-indeksi-lyhenteet.md               Korsteenin hakemistolyhenteet
  korsteeni-osa-I.md                           Korsteeni: historialliset maininnat 1986–2025
  korsteeni-osa-II.md                          Korsteeni: olemassa olevien höyrylaivojen maininnat
  korsteeni-sisallysluettelo.md                Korsteeni-lehden otsikkohaku 1986–2025
  laiva-lehti-sisallysluettelo.md              Laiva-lehden sisällysluettelo 1/2001–2/2026

  Kirjojen ja opinnäytteiden hakemistot
  saimaan-100-vuotishistoria-alushakemisto.md  Karttunen 1945, alushakemisto
  saimaan-100-vuotishistoria-henkilohakemisto.md  Karttunen 1945, henkilöhakemisto
  hoyrylaivamme-1977-laivahakemisto.md         Riimala 1977, alusluettelo
  hoyrylaivamme-1977-lahteet.md                Riimala 1977, kirjan lähteet
  hoyrymurtajien-aika-sisallys.md              Laurell 1992, sisällysluettelo ja laivanavigaatiotaulukko
  hoyrymurtajien-aika-lahteet.md               Laurell 1992, kirjan lähteet
  punatahtisen-sotalipun-alla-laivahakemisto.md  Tuomi-Nikula 2000, alushakemisto (noin 960 r.)
  punatahtisen-sotalipun-alla-lahteet.md       Tuomi-Nikula 2000, lähdeluettelo
  hoyrylaivojen-suomi-alushakemisto.md         Pakkanen 2018, alushakemisto
  hoyrylaivojen-suomi-lahteet.md               Pakkanen 2018, kirjan lähteet
  kelluva-kulttuuriperinto-laivahakemisto.md   Sipilä ym. 2019, alushakemisto
  kelluva-kulttuuriperinto-lahteet.md          Sipilä ym. 2019, kirjan lähteet
  navis-fennica-4-laivahakemisto.md            Navis Fennica 4 (1995), 995 laivannimeä
  navis-fennica-4-lahteet.md                   Navis Fennica 4, lähteet ja sanasto
  isoisan-laivat-laivahakemisto.md             Wirrankoski 2000, Päijänteen alukset
  isoisan-laivat-lahteet.md                    Wirrankoski 2000, kirjan lähteet
  pirttiniemi-tilauskirja.md                   Pirttiniemen tilauskirjat I ja II, rak.nrot 1–771 (n. 1862–1965), 696 alusta
  krank-1990-laivahakemisto.md                 Myllylä 1990, Lehtoniemen telakka 1889–1901
  krank-1990-wahl-laivatilaukset.md            Myllylä 1990, Wahl Varkaus 1882–1888
  krank-1990-lahteet.md                        Myllylä 1990, Krankin patentit ja kirjan lähteet
  rautaisten-hoyryalusten-rakennus-1988-laivahakemisto.md  Koponen 1988 (pro gradu), leipätekstin alusmaininnat
  teollinen-hoyrylaivanrakennus-2001-laivahakemisto.md     Koponen 2001 (lisensiaattityö), alukset sivuittain
  oulun-konepaja-1949-laivahakemisto.md        Outakoski 1949, Pikisaari N:o 101–127 (1903–1927)
  oulun-konepaja-1949-henkilohakemisto.md      Outakoski 1949, toimitusjohtajat ja työntekijät
  oulun-konepaja-1949-lahteet.md               Outakoski 1949, kirjan lähteet
  laudamiehesta-hietaseen-laivahakemisto.md    Valta 1997, Wahl & Co:n laivasto 1830–1909
  laudamiehesta-hietaseen-henkilohakemisto.md  Valta 1997, Wahlin toimijat
  laudamiehesta-hietaseen-lahteet.md           Valta 1997, kirjan lähteet ja JyMA
  kuopion-historia-iii-laivahakemisto.md       Nummela 1989, Kuopion alukset ja 1912-taulukko
  kuopion-historia-iii-henkilohakemisto.md     Nummela 1989, henkilöt ja yhtiöt
  sisavesien-mikrotonnisto-laivahakemisto.md   Kivinen 2016, liite 6, laivannimet
  sisavesien-mikrotonnisto-paikkahakemisto.md  Kivinen 2016, liite 7, paikannimet
  sisavesien-mikrotonnisto-1870-laivat.md      Kivinen 2016, liite 2, vuoden 1870 höyrylaivat vesistöittäin
  sisavesien-mikrotonnisto-lahteet.md          Kivinen 2016, lähdeluvun tiivistys

  Bibliografiat ja lähdekatalogi
  kirjallisuus.md                              Noin 70 teosta vesistöittäin (Kivinen 2025) ja riihisaari.info
  tutkimukset.md                               Pro gradut, lisensiaattityöt, käsikirjoitukset
  lahteet.md                                   Hakulähteiden täysi katalogi
```

---

## Tausta ja kiitokset

Taito pohjaa *Laivadatan metsästäjän oppaaseen* (Santtu Ahonen, *Laiva-lehti*
4/2024) ja on kehitetty käytännön tutkimustyön pohjalta.

Erityiset kiitokset aineistojen alkuperäisille kokoajille. Aineistot ovat
toimineet inspiraationa ja lähteenä tämän skillin versioille:

- **Lasse Uotila / Suomen Höyrypursiseura ry (SHPS):** Korsteenin
  laivahakemisto 1986–2025 (osat I ja II)
- **Pekka Snellman / Suomen Höyrypursiseura ry (SHPS):** Korsteenin
  artikkelihakemisto 1986–2025
- **Martti Koponen / Savonlinnan museo:** Karttunen 1945 -teoksen alus- ja
  henkilöhakemistojen digitointi sekä laaja sisävesiliikenteen bibliografia
  (riihisaari.info, 2 609 viitettä)
- **Jussi Kivinen:** *Höyrylaivakirjallisuutta* (Laiva-lehti 2/2025),
  pohjana taidon kirjallisuusbibliografialle, sekä *Sisävesien
  mikrotonnisto* (väitöskirja 2016), joka tarjoaa myös laajan
  arkistolähteiden tiivistyksen
- **Jarmo Koponen:** *Rautaisten höyryalusten rakennus Varkauden
  Lehtoniemen ja Pirttiniemen telakoilla 1862–1931 (–1951)* (pro gradu,
  Jyväskylän yliopisto 1988) ja *Teollinen höyrylaivanrakennus Suomessa
  1833–1959* (lisensiaattityö, Oulun yliopisto 2001), telakkahistorian
  ristiintarkistuksen perusta. Lisensiaattityötä ei jaeta; skillissä on
  vain alusten nimet, vuodet, telakat ja sivunumerot.
- **laivadata.fi:** Pirttiniemen telakan digitoidut tilauskirjat, avoin
  data (CC-lisenssi)

Hakemistoaineistojen tekijänoikeudet säilyvät niiden alkuperäisillä
oikeudenhaltijoilla. Tekijätiedot ovat kunkin hakemistotiedoston alussa.

---

## Kehitys ja palaute

Parannusehdotukset, korjaukset, uudet hakemistot ja muut lisäykset ovat
tervetulleita. Tarkemmat ohjeet: [CONTRIBUTING.md](./CONTRIBUTING.md).

- **Discussions:** [github.com/SanttuAhonen/laivadatan-metsastaja/discussions](https://github.com/SanttuAhonen/laivadatan-metsastaja/discussions),
  ensisijainen kanava kaikenlaiseen osallistumiseen
- **Sähköposti:** luupilotti@gmail.com, jos GitHub-tunnusta ei ole.
  Tätä kautta voi pyytää myös uudempaa, päivitettyä versiota.

---

## Lisenssi

© 2026 Santtu Ahonen. Lisensoitu **Creative Commons Attribution 4.0
International (CC BY 4.0)** -lisenssillä. Täysi lisenssiteksti repon
juuressa: [LICENSE](./LICENSE) (englanti) ja [LICENSE.fi](./LICENSE.fi) (suomi).

> **Huom.** CC BY 4.0 koskee taidon metodologiaa, rakennetta ja sen pohjaksi
> kirjoitettuja ohjeita. Sisällytettyjen hakemistojen tekijänoikeudet
> kuuluvat niiden alkuperäisille oikeudenhaltijoille. Kunkin
> hakemistotiedoston alussa on tekijätieto ja viittausohje.
