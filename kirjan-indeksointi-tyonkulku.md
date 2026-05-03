# Kirjojen alus-/laivahakemistojen indeksointi — työnkulkuohje

**Tarkoitus:** Tämä ohje opastaa Claudea indeksoimaan suomalaisten
laivakirjojen alushakemistoja ja muita liitteitä luotettavasti
valokuvista. Lataa tämä tiedosto kirjan kuvien mukana, niin Claude
osaa tehdä työn samalla huolellisuudella kuin aiemmin Pakkasen
*Höyrylaivojen Suomi* (2018) ja Sipilä-Matikka-Wirrankoski *Kelluva
kulttuuriperintö* (2019) -kirjojen kanssa.

**Konteksti:** Tämä työ liittyy `laivadatan-metsastaja`-skilliin
(Santtu Ahonen, 2025–). Indeksoidut hakemistot menevät skillin
`references/`-kansioon, ja niitä käytetään `grep`illä sen jälkeen.

---

## Tavoite

Saada kirjan painetusta hakemistosta luotettava digitaalinen
sivunumeroindeksi muodossa, joka toimii yksinkertaisella
`grep`-haulla. Esimerkki tuloksesta:

```
WENNO 123, 125*
```

= aluksen WENNO tietoja löytyy kirjan sivuilta 123 ja 125, ja sivulla
125 on aluksen valokuva (tähti = kuva, jos kirjan ohjeessa niin
sanotaan).

## Periaate ennen kaikkea: älä keksi tietoa

Skillin **perusperiaate 9** sanoo: *"Älä keksi tietoa — älä vastauksissa,
eikä myöskään skilliin itseensä."* Tämä koskee erityisesti tätä
indeksointityötä:

- Jos OCR antaa numeron jonka pitäisi olla "95" mutta lukee "99", **älä
  korjaa muistivaraisesti** — tarkista visuaalisesti zoomatulla kuvalla
- Jos tähti-merkki ei näy OCR-tuloksessa, **älä lisää sitä omasta
  päästä** — tarkista kuvasta
- Jos kirjassa on painovirhe (esim. "Södern 11, 1897" Pakkasella),
  **säilytä se kirjan mukaisena** ja merkitse epäilyttäväksi
  huomautuksena, mutta älä korjaa

---

## Vaihe 1: Kuvien purkaminen ja nimeäminen

Kirjan kuvat tulevat tyypillisesti zip-tiedostona, jossa on
PXL_*.jpg-tiedostoja. Pura ja nimeä ne sivunumeron mukaan:

```bash
mkdir -p /tmp/<kirjan-lyhytnimi>-images
cd /tmp/<kirjan-lyhytnimi>-images
unzip -q /mnt/user-data/uploads/<zipin-nimi>.zip
ls *.jpg | sort
```

Sitten:

1. Selaa kuvat järjestyksessä (käytä `view`-työkalua)
2. Tunnista mikä sivu on mikä (sivunumero näkyy alanurkassa)
3. Nimeä uudelleen sivuittain:

```bash
cp PXL_20260502_053217737.jpg page-330.jpg
cp PXL_20260502_053222738.jpg page-331.jpg
# jne.
```

**Mitä etsiä kuvasta:**

- **Kansi / nimiölehti** → kirjailijat, kustantaja, ISBN, vuosi
- **Sisällysluettelo** → mikä sivu on hakemisto, mitä muita liitteitä
- **Tärkeimpiä lähteitä / Bibliografia** → erillinen lähde-indeksi
- **Alushakemisto / Laivahakemisto** → pää-indeksointityö
- **Mahdolliset erilliset listat** (museolaivat, perinnealusrekisteri jne.)
  → kysy käyttäjältä halutaanko nämä mukaan, vai onko sama tieto jo
  saatavilla muualla

---

## Vaihe 1b: Duplikaattitarkistus — onko kirja jo indeksoitu?

**Tee tämä heti kun kirja on tunnistettu** (kannesta/nimiölehdestä
saadaan kirjailija, otsikko, vuosi ja mahd. ISBN) — ennen kuin
aloitetaan varsinainen sivujen läpikäynti. Säästää tunteja työtä jos
sama kirja löytyy jo skillistä.

### Vaihe 1b.1: Tarkista nykyiset tiedostot

```bash
# 1. Tiedostonimellä (kirjan otsikon avainsana)
ls /tmp/laivadatan-metsastaja/references/ | grep -i "<otsikon-avainsana>"

# 2. Sisältöhaku ISBN:llä jos kirjassa on
grep -rl "ISBN <numero>" /tmp/laivadatan-metsastaja/references/

# 3. Sisältöhaku kirjailijan nimellä
grep -rl "<Kirjailija>" /tmp/laivadatan-metsastaja/references/

# 4. Vuoden + julkaisijan yhdistelmä jos ei muuta tunnistinta
grep -rl "<Julkaisija> <vuosi>" /tmp/laivadatan-metsastaja/references/
```

### Vaihe 1b.2: Jos ei aiempaa indeksointia — etene normaalisti

Tee Vaiheet 2–9 normaalisti uutena indeksointina. **Tarkista kuitenkin
samalla kerralla** ettei kirja ole **eri painoksessa tai eri otsikolla**
— yleisiä päällekkäisyyssyitä:

- Sama kirja toisella otsikolla (esim. ruotsinkielinen rinnakkaispainos)
- Sama tekijä, eri kirja samasta aiheesta (esim. Reijo Vallan useat
  Saimaan vesistöä käsittelevät teokset)
- Pro gradu joka on myöhemmin julkaistu kirjana
- Aineisto, johon kirja viittaa, on jo muiden kirjojen kautta skillissä
  (esim. ELKA-arkiston Lehtoniemi-aineisto kahdesta eri kirjasta)

### Vaihe 1b.3: Jos sama kirja on jo skillissä — kysy käyttäjältä

Käyttäjä päättää miten edetä. Esitä tilanne ja kolme vaihtoehtoa:

```
Löysin että <kirja> on jo skillissä:
- Tiedosto: <nykyinen-tiedostonimi>
- Indeksoitu: <kirjan tunnistetiedot, mitkä luvut/liitteet>
- Aluksia indeksissä: <määrä>
- Sivuja kirjassa indeksoitu: <esim. 104–108>

Miten haluat edetä?

a) **Päivitä olemassaolevaa** — uudet kuvat sisältävät SAMAA
   tietoa parannetussa muodossa, esim. tarkemmat OCR-luennat tai
   uusia sarakkeita. Korvaa nykyiset rivit.

b) **Laajenna olemassaolevaa** — uudet kuvat sisältävät SAMASTA
   kirjasta MUITA SIVUJA tai liitteitä joita ei vielä indeksoitu.
   Lisää uudet alukset/henkilöt nykyisiin taulukoihin
   aakkosjärjestykseen.

c) **Luo erillinen uusi tiedosto** — kyseessä on saman kirjan
   ERI PAINOS, ERI KIELI tai SAMAN SARJAN ERI OSA.
   Tiedostonimi disambiguoidaan vuosiluvulla tai
   painostunnisteella (esim. `<otsikko>-1977.md` vs.
   `<otsikko>-2018.md`).
```

### Vaihe 1b.4: Päätösvirran soveltaminen

| Tilanne | Vaihtoehto | Tiedostotoimenpide |
|---|---|---|
| Sama kirja, samat sivut, paremmat OCR | (a) Päivitä | Korvaa rivit, päivitä indeksointistatus |
| Sama kirja, eri sivut/luvut/liitteet | (b) Laajenna | Lisää rivit aakkosjärjestykseen, päivitä indeksointistatus |
| Sama tekijä + otsikko, eri painos | (c) Erillinen | Uusi tiedosto vuositunnisteella |
| Sama kirjasarja, eri osa | (c) Erillinen | Uusi tiedosto osatunnisteella (esim. `-osa-2`) |
| Käännös samasta teoksesta | (c) Erillinen | Uusi tiedosto kieli-tunnisteella jos eroavaisuuksia |
| Sama tieto eri kirjassa lainauksena | Ei toimenpiteitä | Alkuperäinen kirja on parempi lähde — älä duplikoi |

### Vaihe 1b.5: Erityistilanteet

**Yhdistäminen useampaan tiedostoon (sivuindeksi):** Joskus iso kirja
indeksoidaan useammassa erillisessä tiedostossa, jos eri liitteet
käsittelevät eri aiheita ja tutkimuskäyttö hyötyy erottelusta.
Esimerkki Krank 1990:

- `krank-1990-laivahakemisto.md` — Liite 3 (Lehtoniemen alukset)
- `krank-1990-wahl-laivatilaukset.md` — Liite 2 (Wahlin tilaukset)
- `krank-1990-lahteet.md` — Liite 1 + lähdeluettelo

Tällöin **lisätä uusi tiedosto, ei laajenna olemassaolevaa**, jos
uusi liite on sisällöllisesti erillinen kokonaisuus.

**Päivitys-laajennus -ero käytännössä:** jos kirjassa on vain yksi
hakemisto ja kuvat ovat eri sivuilta sitä — laajenna. Jos kuvat ovat
samalta sivulta tarkemmilla luennoilla — päivitä.

**Älä koskaan poista olemassaolevaa indeksointia ilman käyttäjän
nimenomaista lupaa.** Jos epäilet että nykyinen tieto on virheellistä,
merkitse rivi kommentilla, älä poista.

---

## Vaihe 2: Hakemiston selitysmerkit

Aina ensin **dokumentoi kirjan oma ohje hakemistosta**. Kirjan alkuun
tai hakemiston alkuun on yleensä painettu selitykset esim.:

- *"Mikäli aluksesta on kuva, on sivunumero merkitty tähdellä."*
- *"Versaalit nimet = nykyiset, pienet kirjaimet = entiset"*
- *"Samannimiset alukset eroteltu rakennusvuoden mukaan"*

Nämä merkitykset **vaihtelevat kirjojen välillä!** Esimerkkejä:

| Kirja | Tähden sijainti | Merkitys |
|-------|----------------|----------|
| Pakkanen 2018 (*Höyrylaivojen Suomi*) | aluksen **nimen** perässä | alustyyppi (`*` purje, `**` moottori, `***` koneeton majakkalaiva) |
| Sipilä ym. 2019 (*Kelluva kulttuuriperintö*) | **sivunumeron** perässä | aluksesta on **kuva** sillä sivulla |

**Kirjoita selitysmerkit selvästi indeksoidun tiedoston otsikkoon.**
Käyttäjä luottaa niiden olevan oikein.

---

## Vaihe 3: Sivun leikkaus sarakkeisiin

Hakemistosivut ovat tyypillisesti 2–4-sarakkeisia. Yhden ison kuvan
OCR-tulos sekoittaa sarakkeet, joten leikkaa ne erikseen:

```bash
cd /tmp/<kirjan>-images
mkdir -p columns ocr

for page in 330 331 332 333 334 335 336; do
  IMG="page-$page.jpg"
  W=$(identify -format "%w" $IMG)
  H=$(identify -format "%h" $IMG)
  COLW=$((W / N))   # N = sarakkeiden määrä, esim. 4
  WCUT=$((COLW + 50))   # 50px overlap

  for col in 1 2 3 4; do
    OFFSET=$(( (col - 1) * COLW ))
    convert "$IMG" -crop ${WCUT}x${H}+${OFFSET}+0 columns/p${page}-c${col}.jpg
    tesseract columns/p${page}-c${col}.jpg ocr/p${page}-c${col} 2>/dev/null
  done
done
```

**Vihjeitä:**

- 50 pikselin overlap pitää huolen että rivit eivät katkea
- Jos sarakeiden määrä ei ole tasajakoinen, säädä `COLW` käsin
- Pakkasella oli 7 saraketta sivulla 239 (tiivis), Kelluvalla 4
- Tarkista yksi sarake-kuva että leikkaus on oikein:
  `view columns/p330-c1.jpg`

---

## Vaihe 4: OCR-laatuvaatimukset

Tesseract toimii suomenkielenkin sanoille kohtuullisesti **ilman
suomi-kielipakettia** (pakettia ei välttämättä ole asennettuna). Mutta
tunnetut virheet:

- **Ä, Ö, Å puuttuvat usein** — luetaan A, O, A:na (esim. "Aanekoski"
  pitäisi olla "Äänekoski")
- **Tähti `*` saattaa OCR:llä lukea `%`, `+` tai jäädä kokonaan pois**
  (esim. `ASTRID 15, 115%, 116` → oikein `ASTRID 15, 115*, 116`)
- **Numerot 5/6/8/9** sekoittuvat helposti epäselvissä rivissä
- **Pieni `l`, iso `I` ja numero `1`** sekoittuvat

**Yleisimmät korjaukset (käytä sed, älä keksi):**

```bash
# Tähti-merkkien palautus
sed -i 's/, \([0-9]\+\)%/, \1*/g; s/, \([0-9]\+\)+/, \1*/g'

# Tunnetut suomenkieliset paikkanimet (lisää tarpeen mukaan)
sed -i 's/Aanekoski/Äänekoski/g'
sed -i 's/Aaransgrund/Äransgrund/g'
```

**Älä tee** liian aggressiivisia globaaleja vaihtoja, jotka voivat
muuttaa myös oikeat kohdat. Käytä mieluummin manuaalista tarkistusta.

---

## Vaihe 5: Visuaalinen tarkistus rivi riviltä

**Tämä on tärkein vaihe.** OCR ei ole koskaan 100 % oikein. Käy
jokainen sivu läpi vertaamalla OCR-tulosta kuvaan:

1. Avaa OCR-tiedosto: `cat ocr/p330-c1.txt`
2. Avaa sivun kuva: `view page-330.jpg` tai zoomattuna sarakekuva
3. Käy rivi riviltä — onko nimi oikein, ovatko kaikki numerot, onko
   tähdet paikoillaan
4. Epäselviä kohtia varten tee zoom-leikkaus:

```bash
convert page-330.jpg -crop 600x80+1340+1190 check-jokuepaily.jpg
```

5. Korjaa virheet ja merkitse epäselvät huomautuksin

**Tunnusomaiset epäilyttävät kohdat:**

- Hyvin pieni numero (3-numeroinen) keskellä riviä — ehkä OCR sekosi
- Outo numero kirjan kontekstissa (esim. sivunumero 1897 kun kirjassa
  on 240 sivua)
- Aluksen nimi joka näyttää oudolta tai jossa on omituisia merkkejä

---

## Vaihe 6: Tiedoston rakenne — aakkosjärjestys, ei sivuittain

**Tärkein periaate:** lopputulos on **aluksia/henkilöitä varten**, ei
kirjan oman sivujärjestyksen toistoa. Käyttäjä etsii useimmiten
nimellä, tyypillä tai vuosiluvulla — ei "mitä on sivulla 64".
Sivunumero on **viitetieto**, ei pääorganisaatio.

### Tiedostonimet — kirjan nimi, ei kirjailijan

Skillin konventio (4/8 hakemistoa): tiedostonimi perustuu **kirjan
otsikkoon**, ei kirjailijan sukunimeen + vuoteen.

| Hyvä | Huono |
|---|---|
| `laudamiehesta-hietaseen-laivahakemisto.md` | ~~`valta-1997-laivahakemisto.md`~~ |
| `hoyrylaivamme-1977-laivahakemisto.md` | (vuosi sallittu disambiguoinniksi) |
| `oulun-konepaja-1949-laivahakemisto.md` | (vuosi sallittu kun kirjan otsikko on yleinen) |

### Lopullisen laivahakemiston rakenne

```markdown
# <Kirjan nimi> — Laivahakemisto

**Lähde:** <viittaus>. ISBN <numero> (jos käsinkirjoitettu, **tarkista
matemaattisesti**). Sivut <X–Y>.

**Käyttö skillissä:** ...

**HUOM kirjan rakenteesta:** kirjassa [on / ei ole] erillistä
laivahakemistoa kirjan lopussa. Tämä tiedosto on koonti...

**Selitysmerkit (kirjan oman ohjeen mukaan, sivu <Z>):** ...

**Käyttö (paikallinen haku):**
\`\`\`bash
grep -in "Hietanen" references/<tiedosto>.md     # nimellä
grep -in "fregatti\|kuunari" references/<tiedosto>.md  # tyypillä
grep -in "| 1864 |" references/<tiedosto>.md     # vuoden mukaan
\`\`\`

---

## Lyhenteet

<kirjan käyttämät alustyyppilyhenteet ja yksiköt>

---

## <Tyyppi 1, esim. Purjealukset> (<vuosihaarukka>)

| Nimi | Tyyppi | Rak.v. | Koko/teho | Muuta tietoa | Sivut |
|---|---|---|---|---|---|
| **AALTO** | hinaaja | 1874 | 35 hv | <konteksti> | 35, 37, 40 |
| **ALERT** (1) | höyrylaiva | 1872 | 20 hv | <huom> | 36, 38 |
| **ALERT** (2) | hinaaja | 1899 | 25 hv | <eri alus, sama nimi> | 36, 37 |
| ...                                                              |

## <Tyyppi 2, esim. Höyrylaivat> (<vuosihaarukka>)

| Nimi | Tyyppi | Rak.v. | Koko/teho | Muuta tietoa | Sivut |
|---|---|---|---|---|---|
| ...                                                              |

## <Tyyppi 3, esim. Lotjat ja proomut> (<vuosihaarukka>)

| Nimi | Tyyppi | Rak.v. | Koko/teho | Muuta tietoa | Sivut |
|---|---|---|---|---|---|
| ...                                                              |

---

## Nimien yhteentörmäykset

<tarvittaessa: jos sama nimi useassa eri aluksessa>

| Nimi | Eri alukset |
|---|---|
| **HIETANEN** | (1) lotja 1881 — (2) jäänsärkijä 1904 — ... |

---

## Indeksointistatus

- [x] Sivu X: <mikä taulukko/luettelo>
- [x] Sivu Y: <mikä taulukko/luettelo>
```

### Pakolliset sarakkeet

Jokaisessa aakkostetussa taulukossa **on oltava** vähintään:

1. **Nimi** (lihavoitu) — pääsarake, jonka mukaan rivi aakkostetaan
2. **Tyyppi** — alustyyppi (kirjan oma terminologia, ks. lyhenteet)
3. **Rakennusvuosi** — `Rak.v.` tai vastaava
4. **Sivut** — pilkulla erotettu lista kirjan sivunumeroista joilla
   alus mainitaan. Jos useassa taulukossa, yhdistä sivuviitteet
   yhteen riviin.

Lisäksi **vähintään yksi**:
- **Koko/teho** (lästiä, brt, hv jne.) — kirjan käyttämin yksiköin
- **Muuta tietoa** — kapteeni, tilaaja, omistushistoria,
  poikkeukselliset tiedot

### Aakkostuksen yksityiskohtia

- **Skandinaaviset kirjaimet**: Ä, Ö ovat A:n ja O:n jälkeen
  (suomalainen aakkosjärjestys)
- **Lainausmerkit ja sulut** ohitetaan: `»Lokki»` aakkostetaan
  L-kirjaimen alle
- **Saman nimisten alusten erottelu**: numeroi `(1)`, `(2)` tai liitä
  rakennusvuosi nimeen erottavaksi tunnisteeksi
- **Kyrilliset nimet**: kirjoita kirjan käyttämä alkuperäinen muoto +
  latinalainen transliteraatio (esim. `**Бурлачекъ** (Burlatsok)`)

### Mihin tyyppi-jako vedetään?

Kolme tyypillistä jakoa, valitse kirjan aineiston perusteella:

| Aineisto | Suositeltu jako |
|---|---|
| Wahl-tyyppinen monipuolinen aineisto (purjeet → höyry → lotjat) | **Purjealukset** / **Höyrylaivat** / **Lotjat ja proomut** |
| Telakkakeskeinen (esim. Krank Lehtoniemi) | **Yksi taulukko** kaikille — telakka itsessään on jo yhdenmukaistava jako (jos tyyppi-sarake on selkeä, jako ei ole välttämätön) |
| Vähälukuinen (alle ~30 alusta, esim. Oulun Konepaja) | **Yksi aakkostettu taulukko**, lisäksi mahdollisesti rakennusnumero-/sivujärjestyksessä toistuva oheistaulukko |
| Henkilöhakemisto | Roolin mukaan (omistajat, kapteenit, rakennuttajat, tutkijat) — kunkin sisällä aakkosjärjestys |

### Säilytä myös kirjan oma järjestys oheistaulukkona — jos siitä on tutkimusarvoa

Kun kirjan oma listausjärjestys (rakennusnumero, kronologia,
laivakalenterivuosi) on **itse tutkimuksellinen tieto**, säilytä se
**pienempänä oheistaulukkona** aakkostetun päätaulukon jälkeen.
Esimerkkejä:

- **Oulun Konepaja**: rakennusnumerot 101–127 ovat itsenäinen
  identifioiva tunniste → oheistaulukko numerojärjestyksessä
- **Wahl 1848 / 1858 / 1887 laivakalenterit**: yksittäisen vuoden
  laivasto on tutkimuksellinen kokonaisuus → vuosi-otosten
  yhteenvetotaulukko ("aluksia 8 yhteensä, 879 lästiä, kapteenit 1848:
  Björklund, Dahlström, ...")

**Statusosa on tärkeä** — se kertoo Claudille (ja käyttäjälle) milloin
indeksointi on osittainen ja `grep`-osumattomuus voi tarkoittaa että
sivua ei ole vielä käsitelty. Statusosa noudattaa edelleen **kirjan
sivujärjestystä** (ei aakkosia) — se kertoo mistä kirjan kohdista
tieto on poimittu.

---

## Vaihe 6b: Henkilöhakemisto — sama periaate

Henkilöhakemisto noudattaa samaa periaatetta:

- **Aakkosjärjestys roolikohtaisesti**, ei sivuittain
- Rooli ensin (Omistajat, Kapteenit 1848, Kapteenit 1858, ...,
  Rakennuttajat, Tutkijat lähdeviittauksissa), sen sisällä aakkoset
- **Sivut-sarake** jokaisessa taulukossa
- Jos sama henkilö esiintyy useammassa roolissa eri vuosina (esim.
  D. Lautniemi 1858 ja 1887), **yhdistä yhdeksi riviksi** ja kirjaa
  molemmat sivut

---

## Vaihe 7: Useamman kirjan välinen yhdenmukaisuus

Jos sama alus voi olla useammassa kirjassa, käyttäjä haluaa yleensä
nähdä **kaikki lähteet samalla kerralla**. Käytä `grep -inH`-lippua
joka näyttää tiedostonimen tuloksessa. Aakkostetussa taulukko-rakenteessa
nimi on muodossa `| **Wenno** | ...`, joten `^`-ankkuri ei toimi:

```bash
# Hae aluksen nimi useasta hakemistosta yhdellä haulla
grep -inH "Wenno\|WENNO" \
  references/hoyrylaivojen-suomi-alushakemisto.md \
  references/kelluva-kulttuuriperinto-laivahakemisto.md \
  references/laudamiehesta-hietaseen-laivahakemisto.md
```

Vastaa käyttäjälle aina:
1. Mistä **kirjasta** kukin sivunumero löytyy
2. Onko aluksesta kuva (jos kirjan tähti tarkoittaa sitä)
3. Mitä erikoismerkit tarkoittavat **siinä nimenomaisessa kirjassa**

Jos sama alus on useassa kirjassa eri tiedoilla (esim. eri
rakennusvuosi, eri tyyppiluokitus), tuo ero esiin vastauksessa —
älä yritä päättää kumpi on "oikea". Käyttäjä on tutkija ja arvostaa
kaikki versiot näkyvillä.

---

## Vaihe 8: Kirjan lähdeluettelon erillinen indeksointi

Kirjoissa on yleensä erillinen "Tärkeimpiä lähteitä" tai
"Kirjallisuus"-osio. Indeksoi tämä **erillisenä tiedostona**, ei osana
laivahakemistoa:

`references/<kirjan>-lahteet.md`

Tämä auttaa käyttäjää jäljittämään aluksen tiedon **alkuperää**:
yleisteokset (kuten Pakkanen 2018) kokoavat tietoa monista
yksityiskohtaisemmista monografioista.

Jaottele lähteet kirjan oman jaottelun mukaan:
- Arkistot ja painamattomat lähteet
- Verkkosivut
- Kirjallisuus (aakkostettu kirjailijan mukaan)
- Sarjajulkaisut

---

## Vaihe 9: Skillin pakkaus ja toimitus

Kun kaikki on tehty, päivitä:

1. **`SKILL.md`** — tiedostotaulukkoon uudet `*-laivahakemisto.md` ja
   `*-lahteet.md`
2. **`references/lahteet.md`** — kirja kiitososioon, jos kirja on
   merkittävä lähde
3. **`references/hakukaavat.md`** — uusi jakso uudesta paikallisesta
   hakemistosta + päivitys yhdistelmähakuun
4. **`references/kirjallisuus.md`** (jos olemassa) — kirja viitelistaan

Pakkaa:

```bash
cd /tmp && rm -f laivadatan-metsastaja.skill
zip -r laivadatan-metsastaja.skill laivadatan-metsastaja/ > /dev/null
cp laivadatan-metsastaja.skill /mnt/user-data/outputs/
```

**Huom: Tarkista ettei tule duplikaattirakennetta.** `cp -r
/mnt/skills/user/...` luo alikansion jos kohdekansio on jo olemassa
— käytä aina `unzip` paketista.

---

## Tarkistuslista (käytä lopuksi)

- [ ] **Duplikaattitarkistus tehty** ennen indeksointia — jos kirja on
      jo skillissä, käyttäjältä kysytty miten edetä (päivitä /
      laajenna / erillinen tiedosto)
- [ ] **Tiedostonimi: kirjan otsikko, ei kirjailijan sukunimi**
      (esim. `laudamiehesta-hietaseen-*.md`, ei
      `valta-1997-*.md`)
- [ ] Kirjan tiedot otsikossa: nimi, kirjailijat, kustantaja, ISBN,
      vuosi, sivut
- [ ] **ISBN tarkistettu matemaattisesti** jos käsinkirjoitettu
      (ISBN-10 mod 11 = 0; ISBN-13 mod 10 = 0)
- [ ] **Laivahakemisto aakkosjärjestyksessä tyypeittäin** —
      ei sivuittain. Tyyppijako: purjealukset / höyrylaivat /
      lotjat-proomut tai vastaava aineiston mukaan
- [ ] **Pakolliset sarakkeet:** nimi, tyyppi, rakennusvuosi, sivut.
      Lisäksi koko/teho ja/tai muuta tietoa
- [ ] **Sivut-sarake** jokaisessa rivissä — useat sivut pilkulla
      erotettuna kun alus mainitaan useassa taulukossa
- [ ] **Henkilöhakemisto** roolikohtaisesti, kunkin roolin sisällä
      aakkoset
- [ ] **Saman nimisten alusten erottelu** numerolla `(1)`, `(2)` tai
      rakennusvuodella
- [ ] Selitysmerkit dokumentoitu **kirjan oman ohjeen mukaan**
- [ ] Jos tähti tarkoittaa eri asiaa kuin toisessa skillin kirjassa
      → varoitus näkyvästi
- [ ] Indeksointistatus näkyvissä tiedoston lopussa (kirjan
      sivujärjestyksessä, kertoo mistä kohdista tieto on poimittu)
- [ ] Visuaalinen tarkistus tehty kaikille sivuille
- [ ] Tunnetut painovirheet kirjassa **säilytetty** mutta merkitty
      huomautuksina (älä korjaa kirjan virheitä omasta päästä)
- [ ] Erillinen lähde-tiedosto luotu
- [ ] SKILL.md, lahteet.md, kirjallisuus.md, lyhenteet-ja-terminologia.md
      päivitetty (jos relevanttia uudelle kirjalle)
- [ ] **Terminologiaan EI tuotu yksityiskohtia** jotka kuuluvat
      hakemistoihin — vain perusmäärittely + viittaus oikeaan
      hakemistoon
- [ ] `grep`-haku testattu (a) nimellä (b) tyypillä (c) vuodella —
      tulokset järkeviä
- [ ] Yhdistelmähaku SKILL.md:ssä päivitetty sisältämään uusi
      hakemisto
- [ ] Pakettikoko järkevä, ei duplikaattirakennetta

---

## Esimerkki yhden kirjan indeksointityömäärästä

**Pakkanen 2018, *Höyrylaivojen Suomi*** (240 s.):
- Hakemisto 2 sivua, 7 saraketta yhteensä
- ~887 alusta
- Lähdeluettelo 1 sivu, 2 saraketta
- Aikamääre: ~yhden istunnon työ huolella

**Sipilä ym. 2019, *Kelluva kulttuuriperintö*** (336 s.):
- Hakemisto 7 sivua, 4 saraketta jokainen = 28 saraketta
- ~1800 alusta indeksoitu
- Lähdeluettelo 2 sivua, 2 saraketta
- Aikamääre: useampi istunto, sivu kerrallaan

**Yli 4 sivun hakemiston tapauksessa kannattaa harkita osittain:** tee
ensin lähdeindeksi ja A–E, jatka loput myöhemmin pala kerrallaan.
Statusosa pitää sisällön käytettävänä kesken työnkin.
