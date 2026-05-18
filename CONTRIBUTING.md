# Osallistuminen — `laivadatan-metsastaja`

Kiitos kiinnostuksesta! Tämä dokumentti kuvaa **miten** voit auttaa
taidon kehittämisessä ja **mitä** hyväksytään.

Lyhyt versio: lähetä raakamateriaali ja virheilmoitukset, älä muokattuja
taitopaketteja. Ylläpitäjä (Santtu Ahonen) kokoaa, tarkistaa ja
muotoilee aineiston taitoon sopivaan muotoon.

---

## 1. Mikä on osallistumisen periaate

Taidon arvo perustuu **lähteiden todennettavuuteen** ja **yhtenäiseen
muotoiluun**. Tästä syystä työnjako on tällä erää seuraava:

- **Sinä, osallistuja:** tuot raakamateriaalia — uusia hakemistoja,
  korjauksia, lähdetietoja, virheilmoituksia ja kehitysideoita.
- **Ylläpitäjä:** tarkistaa lähteet, muuntaa aineiston taidon
  vakiomuotoon (kolmiosainen otsikko, viittauskäytäntö,
  auktoriteettiluokitus), päivittää `CHANGELOG.md`:n ja julkaisee
  uuden taitoversion.

Tämä työnjako on tietoinen turvallisuus- ja laatuvalinta. Älä koe
sitä rajoittavaksi — se vapauttaa sinut keskittymään siihen mitä osaat
parhaiten: **lähteiden lukemiseen ja tunnistamiseen**.

---

## 2. Kanavat

Käytä aina jompaakumpaa virallista kanavaa, ei sähköpostia eikä
yksityisviestejä — paitsi jos asia on luottamuksellinen.

### 2.1 GitHub Issues

Käytä Issues-välilehteä kun haluat:

- **Ehdottaa parannusta** tai uutta ominaisuutta
- **Ilmoittaa virheestä** olemassa olevassa hakemistossa
  (väärä sivunumero, OCR-virhe, väärä vuosiluku, väärä alus)
- **Ehdottaa korjausta yksittäiseen tietoon** kun voit antaa
  todennettavan lähteen
- **Kysyä työnkulusta** tai taidon käytöstä
- **Aloittaa keskustelu** ennen isompaa kontribuutiota

Tee virheilmoituksesta käyttökelpoinen:

1. Mistä tiedostosta on kyse? (esim. `references/koponen-1988-laivahakemisto.md`)
2. Mikä rivi tai kohta?
3. Mikä on virhe?
4. Mikä on oikea tieto?
5. **Mistä lähteestä tämä todennetaan?** (sivunumero,
   arkistoviite, URL — ks. luku 4 lähdesäännöistä)

### 2.2 Pull Request — uusi raakamateriaali

Käytä Pull Requestia (PR) vain kun lähetät **uutta raakamateriaalia**,
joka on tarkoitettu lisättäväksi taitoon. Käytännössä:

- Uuden kirjan, lehden, gradun tai telakkakirjan hakemisto
- Uuden henkilöhakemiston
- Uuden vesistöhistoriikin hakemisto
- Olemassa olevan hakemiston **olennainen täydennys** (ei yksittäinen
  korjaus — ne hoidetaan Issuena)

**Pull Requestin täytyy:**

1. Lisätä tiedostoja **vain** kansioon `ehdotukset/` (luodaan tarvittaessa).
2. Olla **pelkkiä tekstitiedostoja (`.txt`)**. Ei Word-, PDF-, Excel-,
   kuva- tai muita tiedostomuotoja. Ei myöskään Markdown-muotoa (`.md`),
   vaikka tämä ohjedokumentti onkin sellainen. Perustelu alla.
3. Käyttää tiedostonimimallia `ehdotus-<kuvaava-nimi>.txt` —
   esim. `ehdotus-laiva-lehti-1985.txt` tai
   `ehdotus-pakkanen-2018-virhelista.txt`.
4. Olla yksi PR per lähde. Älä niputa useita kirjoja yhteen PR:ään.
5. Sisältää lähdetiedot luvun 3 mallin mukaan.
6. Olla **`main`-haaran päällä** ja siisti (yksi commit, selkeä viesti).

**Miksi `.txt` eikä `.md`, Word tai PDF:**

- Tekstitiedoston voi tehdä millä tahansa ohjelmalla: Windowsin
  Muistio (Notepad), Wordin "Tallenna nimellä → Pelkkä teksti",
  TextEdit Macilla, mikä tahansa puhelimen muistiinpanosovellus.
  Ei tarvitse osata uusia merkintätapoja.
- Tekstitiedoston voi avata ja tarkistaa millä tahansa ohjelmalla
  riskittä — siinä ei voi olla piilotettua sisältöä tai
  automaattisesti aktivoituvia linkkejä.
- Wordin, PDF:n tai kuvien lähettäminen tekee ylläpitäjän tarkistus-
  ja muuntotyöstä raskaampaa eikä tuo lisäarvoa välivaiheen
  aineistolle.

Jos sinulla on aineisto Wordissa tai muistiinpanoissa, tallenna se
tekstimuotoon näin:

- **Word:** Tiedosto → Tallenna nimellä → Tiedostomuoto: *Pelkkä
  teksti (.txt)*
- **Mac TextEdit:** Muoto → Muunna pelkäksi tekstiksi → Tallenna
- **Selain / muistiinpanot:** kopioi teksti ja liitä Muistioon,
  tallenna `.txt`:nä

### 2.2.1 Jos et osaa tehdä PR:ää tai tekstitiedostoa

Tämä on täysin kelvollinen tilanne. Avaa silloin **Issue** (luku 2.1),
liitä aineisto suoraan viestin sisään (kopioi-liimaa) ja kerro:

- Mikä lähde on kyseessä (kirja, lehti, gradu — täydelliset tiedot)
- Mistä olet aineiston koostanut

Ylläpitäjä tallentaa aineiston `ehdotukset/`-kansioon puolestasi
ja merkitsee sinut kontribuoijaksi.

### 2.3 Mitä PR:llä **ei** saa tehdä

PR suljetaan ilman jatkokäsittelyä jos se:

- Muokkaa tiedostoa `SKILL.md` tai mitä tahansa nykyistä
  `references/`-kansion tiedostoa
- Muokkaa tiedostoa `CHANGELOG.md`, `README.md`, `LICENSE`,
  `CONTRIBUTING.md` tai mitään `.github/`-kansion tiedostoa
- Lisää, muuttaa tai poistaa **skriptejä** (esim. `scripts/`),
  konfiguraatiotiedostoja tai työnkulkutiedostoja (`.yml`, `.yaml`)
- Lisää valmiiksi paketoidun `.skill`-tiedoston (zip)
- Lisää Markdown- (`.md`), Word- (`.docx`), PDF- tai
  taulukkolaskenta- (`.xlsx`, `.ods`) tiedostoja kontribuutioksi
- Lisää binaaritiedostoja (kuvat, ääni, videot) — käytä Issueta
  ja kuvaile mistä lähde löytyy

Korjaukset olemassa olevaan aineistoon tehdään **aina Issuen kautta**.
Ylläpitäjä päättää, miten korjaus toteutetaan ja milloin se päätyy
seuraavaan versioon.

---

## 3. Uuden raakamateriaalin malli

Lähetä uusi hakemisto **pelkkänä tekstinä**. Älä huoli muotoilusta —
ylläpitäjä muuntaa aineiston taidon vakiomuotoon. Tärkeää on että
**lähdetiedot ja sivunumerot ovat oikein**, ei se miltä tiedosto
näyttää.

Alla malli. Voit kopioida sen Notepadiin, täyttää oman aineistosi
ja tallentaa nimellä `ehdotus-<kuvaava-nimi>.txt`.

```
EHDOTUS: <julkaisun nimi>

LÄHDETIEDOT

  Tekijä(t):      Sukunimi, Etunimi (ja muut tekijät)
  Vuosi:          YYYY
  Teos:           Täydellinen nimi alaotsikkoineen
  Julkaisija:     Kustantaja, paikka
  ISBN / ISSN:    (jos saatavilla)
  Sivumäärä:      N sivua
  Hakemiston sivut: esim. s. 245-278
  Tyyppi:         kirja / lehti / pro gradu / väitöskirja /
                  telakkakirja / muu
  Auktoriteettitaso (oma arvio): 1-4
                  (ks. SKILL.md, perusperiaate 4)
  Mistä saatu:    oma hyllyni / kirjasto X / antikvariaatti /
                  digitaalinen julkaisu / arkisto


INDEKSOITU SISÄLTÖ

  Alukset, henkilöt tai paikat aakkosjärjestyksessä. Kunkin kohdalla
  sivunumero(t). Esimerkki:

  Aallotar (1881, höyrylaiva, Saimaa)
      s. 47
      s. 89
      s. 102

  Aallotar (1909, höyrylaiva, Päijänne)
      s. 47  - varustaja Y
      s. 134 - haaksirikko 1923

  Ahti I (1898, höyryhinaaja, Näsijärvi)
      s. 22
      s. 56-58

  ...


HUOMAUTUKSET

  - Mainitse epävarmuudet selkeästi: "(sivunumero epäselvä)",
    "(?)", "(nimi mahdollisesti väärin kirjattu)",
    "(samanniminen alus, ei varmuutta)"

  - Mainitse jos kirjassa on selkeitä OCR- tai painovirheitä

  - Mainitse jos sama alus esiintyy kirjassa useilla eri
    kirjoitusasuilla

  - Mainitse jos olet käyttänyt apuna tekoälyä (esim. OCR-
    tunnistus, käsialan luku, indeksointi) - älä piilota
    sitä, vaan kerro mitä työvaiheessa tehtiin tekoälyllä
    ja mitä itse tarkistit (ks. luku 4)
```

Jos sinulla on aineisto jo valmiina jossakin muodossa (taulukko,
luettelo paperilla, käsinkirjoitettu vihko), **älä murehdi mallia
liian tarkasti**. Tärkeintä on lähdetiedot ja sivunumerot.
Toimita aineisto siinä muodossa kuin se on, niin selvitetään
yhdessä loppu.

---

## 4. Lähdesäännöt

Taito noudattaa kolmea perussääntöä:

### 4.1 Jokainen tieto tarvitsee lähteen

Aluksen vuosiluku, telakka, varustaja tai mikä tahansa
yksittäistieto on jäljitettävä alkuperäiseen julkaisuun, arkistoon
tai dokumenttiin. **Aluksen perimätieto sukutarinasta ilman
varmennusta ei kelpaa** — Issue toki tervetullut, mutta merkitään
epävarmaksi kunnes lähde löytyy.

### 4.2 Tekoälyn käyttö on aina ilmoitettava

Jos olet käyttänyt apuna ChatGPT:tä, Claudea, Geminiä, Copilotia,
OCR-työkalua tai vastaavaa **missä tahansa työvaiheessa** —
hakemiston laatimisessa, käsialan tulkinnassa, OCR-virheiden
korjauksessa, kuvateksteistä lukemisessa — kerro siitä avoimesti.

Tekoälyllä tuotettu raakaindeksointi **hyväksytään** edellyttäen että:

1. Olet **itse tarkistanut** tuloksen alkuperäistä julkaisua vasten
2. **Merkitset selkeästi** kohdat joita et ole ehtinyt tarkistaa
3. Ilmoitat **mitä työkalua käytit** ja mihin vaiheeseen

Tekoälyllä tuotettua materiaalia ei käytetä taidossa **sellaisenaan**.
Se merkitään aina ihmistarkistusta odottavaksi.

### 4.3 Tekijänoikeudet pysyvät alkuperäisillä haltijoilla

Hakemistotieto (alus X mainittu sivulla Y) ei pääsääntöisesti ole
tekijänoikeudellisesti suojattua. **Älä silti lähetä kokonaisia
sivuja, kuvia tai laajoja sitaatteja** — ne kuuluvat kirjan
oikeudenhaltijalle. Lähetä **omasi laatima** hakemisto, jossa
viittaat sivuihin.

Jos epäilet, kysy Issuena ennen lähettämistä.

---

## 5. Lisenssi ja oikeudet

Lähettämällä Pull Requestin tai julkaisemalla aineiston Issueen
suostut siihen, että aineistosi julkaistaan osana taitoa
**Creative Commons Attribution 4.0 International (CC BY 4.0)**
-lisenssillä — samalla lisenssillä kuin koko taito.

Säilytät tekijyytesi aineistoon. Sinut mainitaan luvun 6 mukaisesti.

Et saa lähettää aineistoa, jonka tekijänoikeuksia et hallitse tai
joka on toisen suojaaman aineiston merkittävää kopiointia.

---

## 6. Tunnustus ja kiitokset

Tunnustusta annetaan suhteessa kontribuution laajuuteen:

### 6.1 Yksittäiset korjaukset ja täydennykset

Maininta `CHANGELOG.md`:ssä asianomaisen version yhteydessä, muodossa:

> Korjattu sivunumerot (kiitos: @käyttäjätunnus)

### 6.2 Uuden hakemiston, lähdeluettelon tai yksittäisen lehden
indeksin tuominen

Maininta **kohdetiedoston alussa** (samassa kohdassa kuin `Lähde:`)
sekä `CHANGELOG.md`:ssä. Esimerkki olemassa olevasta käytännöstä:

> Kiitokset Pekka Snellmanille (SHPS) Korsteenin artikkelihakemiston
> 1986–2025 pohjasta.

### 6.3 Merkittävä kokonaisuus

Esimerkkejä: kaikkien Laiva-lehden vuosikertojen henkilöindeksointi,
kokonaisen vesistön telakka-aineiston tuominen, satojen alusten
tasokorjaukset todennetuilla lähteillä.

Maininta:

1. README:n kiitososiossa kärkitasolla
2. Tulevassa erillisessä `CONTRIBUTORS.md`-tiedostossa
3. Mahdollisesti taidon SKILL.md:n metatiedoissa

**Huom.** Erillinen `CONTRIBUTORS.md` on suunnitteilla. README:n
nykyiset kiitokset siirretään sinne, kun tiedosto perustetaan.

### 6.4 Pseudonyymillä tai nimettömänä

Jos haluat osallistua ilman omaa nimeä, mainitse se Issuessa /
PR:ssä. Käytetään silloin GitHub-käyttäjätunnusta tai
pseudonyymiä.

---

## 7. Mitä tapahtuu lähetyksen jälkeen

1. **Kuittaus:** Issue tai PR kuitataan käsittelyyn yleensä 1–4
   viikon kuluessa. Tämä on harrastusprojekti — älä odota
   yritysohjelmiston SLA-aikoja.
2. **Tarkistus:** Ylläpitäjä lukee aineiston, vertaa olemassa olevaan,
   tarkistaa lähteet sekä kysyy täydennyksiä tarvittaessa.
3. **Mahdollinen palautus jatkotyölle:** Jos lähdetiedot puuttuvat
   tai aineisto on ristiriidassa muiden lähteiden kanssa, palautetaan
   sinulle kommentein. Tämä on normaalia, ei torjuntaa.
4. **Hyväksyntä ja muunto:** Hyväksytty aineisto muunnetaan taidon
   vakiomuotoon, lisätään `references/`-kansioon, kirjataan
   `CHANGELOG.md`:hen ja paketoidaan seuraavaan `.skill`-julkaisuun.
5. **Sulkeminen:** PR suljetaan kun aineisto on viety lopulliseen
   muotoonsa. PR:ää ei "mergetä" sellaisenaan — se toimii
   välivaiheen tallenteena.

### 7.1 Mistä syistä lähetys voidaan hylätä

- Lähdetiedot puuttuvat tai eivät vastaa todellisuutta
- Aineisto on suoraan kopioitu toisesta lähteestä ilman omaa
  käsittelyä (tekijänoikeusongelma)
- Aineisto on tekoälyn tuottamaa ilman ihmistarkistusta eikä sitä
  ilmoitettu (ks. luku 4.2)
- Aineisto ei sovi taidon sisältöprofiiliin (esim. moderni
  risteilylaivahistoria — taidon painopiste on ennen 1980-lukua
  rakennetuissa kotimaisissa aluksissa)
- Aineisto on jo taidossa eikä uusi versio tuo lisäarvoa

---

## 8. Kieli ja tyyli

- **Kieli:** suomi. Hakemistotekstien sisältö voi olla muillakin
  kielillä alkuperäisen lähteen mukaan.
- **Tyyli:** asiallinen, numeroitu tai luettelomainen, faktapohjainen.
  Vältä täytesanoja ja arvauksia.
- **Epävarmuus:** merkitään aina näkyviin sulkein "(epäselvä)",
  "(?)", "(mahd. sama alus kuin X)". Älä piilota epävarmuutta.
- **Lyhenteet:** käytä `references/lyhenteet-ja-terminologia.md`:n
  ja `references/korsteeni-indeksi-lyhenteet.md`:n mukaisia
  lyhenteitä kun mahdollista.

---

## 9. Yhteystiedot

- **Ensisijaisesti:** [GitHub Issues](https://github.com/SanttuAhonen/laivadatan-metsastaja/issues)
- **Sähköposti (luottamukselliset asiat, vanhempien versioiden
  pyytäminen):** luupilotti@gmail.com

Ylläpitäjä: **Santtu Ahonen**

---

*Tämä dokumentti on osa `laivadatan-metsastaja`-taitoa ja julkaistaan
CC BY 4.0 -lisenssillä. © 2026 Santtu Ahonen.*
