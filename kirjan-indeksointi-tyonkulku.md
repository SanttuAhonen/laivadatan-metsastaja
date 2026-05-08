# Kirjojen alus-/laivahakemistojen indeksointi — työnkulkuohje

**Versio:** 2026.05.08.01 (versionhistoria tiedoston lopussa)

**Tarkoitus:** Tämä ohje opastaa Claudea indeksoimaan suomalaisten
laivakirjojen alushakemistoja ja muita liitteitä luotettavasti
valokuvista. Lataa tämä tiedosto kirjan kuvien mukana, niin Claude
osaa tehdä työn samalla huolellisuudella kuin aiemmin Pakkasen
*Höyrylaivojen Suomi* (2018) ja Sipilä-Matikka-Wirrankoski *Kelluva
kulttuuriperintö* (2019) -kirjojen kanssa.

**Konteksti:** Tämä työ liittyy `laivadatan-metsastaja`-skilliin
(Santtu Ahonen, 2025–). Indeksoidut hakemistot menevät skillin
`references/`-kansioon, ja niitä käytetään `grep`illä sen jälkeen.

**Tämä tiedosto EI ole skillin sisällä** — se on erillinen työkalu,
joka ladataan istuntoon vain kun uutta kirjaa indeksoidaan. Skillin
versionumero (`metadata.version` SKILL.md:ssä) ja tämän työkalun
versionumero ovat eri asioita.

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

Skillin konventio (yhdenmukaistettu 2026.05.08): kaikki kirjapohjaiset
tiedostot käyttävät **kirjan otsikkoa**, ei kirjailijan sukunimeä +
vuotta. Vuosi sallittu disambiguointiin tai kun kirjan otsikko on
yleinen.

| Hyvä | Huono |
|---|---|
| `laudamiehesta-hietaseen-laivahakemisto.md` | ~~`valta-1997-laivahakemisto.md`~~ |
| `hoyrylaivamme-1977-laivahakemisto.md` | (vuosi sallittu disambiguoinniksi) |
| `oulun-konepaja-1949-laivahakemisto.md` | (vuosi sallittu kun kirjan otsikko on yleinen) |
| `sisavesien-mikrotonnisto-laivahakemisto.md` | ~~`kivinen-2016-laivahakemisto.md`~~ |
| `saimaan-100-vuotishistoria-alushakemisto.md` | ~~`karttunen-1945-alushakemisto.md`~~ |

### Lopullisen laivahakemiston rakenne

**Yläosa noudattaa skillin standardiformaattia** (käyttöönotettu
2026.05.08): jokaisen lähdetiedoston yläosassa on kolme pakollista
merkintää: **Mikä tämä on**, **Mikä tämä EI ole**, **Lue rinnan**.

```markdown
# <Kirjan nimi> — Laivahakemisto

**Lähde:** <viittaus>. ISBN <numero> (jos käsinkirjoitettu, **tarkista
matemaattisesti**). Sivut <X–Y>.

**Mikä tämä on:** <yhden lauseen tiivistys siitä mitä tiedosto
sisältää, esim. "Pakkasen 2018 kirjan alushakemiston kopio sivuilta
239–240, ~887 alusta sivunumeroindeksointina">

**Mikä tämä EI ole:** Ei korvaa `kirjallisuus.md`:tä (yleinen
bibliografia), `tutkimukset.md`:ta (opinnäytetyöt), eikä
`lahteet.md`:tä (työnkulun yleiskatalogi). <jos tiedostolla on
muita rajauksia, ne tähän>

**Lue rinnan:** `<kirjan>-lahteet.md`, `<sukulaistiedosto-1>`,
`<sukulaistiedosto-2>` (max 3)

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

### Yläosa noudattaa standardiformaattia

Tiedoston yläosa noudattaa skillin standardiformaattia (otettu
käyttöön 2026.05.08):

```markdown
# <Kirjan nimi> — Lähdeluettelo

**Lähde:** <bibliografinen viittaus>. ISBN <numero>. Sivut <X–Y>
("<kirjan käyttämä otsikko lähdeosiolle>").

**Mikä tämä on:** <Kirjan tekijä>:n <vuosi>-kirjan oman
lähdeluettelon kopio sivuilta <X–Y> — eli mitä yksittäisiä teoksia
ja arkistoja kirja itse on lähteenä käyttänyt.

**Mikä tämä EI ole:** Ei korvaa `kirjallisuus.md`:tä (yleinen
bibliografia), `tutkimukset.md`:ta (opinnäytetyöt), eikä
`lahteet.md`:tä (työnkulun yleiskatalogi). Lähteet täällä ovat
**toissijaisia** suhteessa kirjan omaan tekstiin.

**Lue rinnan:** `<kirjan>-laivahakemisto.md`, `kirjallisuus.md`,
<sukulaiskirjojen lähdetiedostot, max 3>

<jos relevantti>**Auktoriteettiluokitus:** <tyypillinen
auktoriteettiluokituksen taso, ks. perusperiaate 4 SKILL.md:ssä>
```

**Sukulaiskirjojen valinta "Lue rinnan" -listalle**: valitse 1–3
kirjaa joiden aiheet/aikakausi/vesistö osuvat lähimmäs. Esimerkiksi:

- Päijänteen kirjat → mainitse muut Päijänne-kirjat
- Wahl-yhteyden sisältävät → mainitse Krank/Wahl-yhteyden takia
- Aikalaiskirjat (esim. 1949, 1977) → mainitse muut aikalaiset

**HUOM**: Tämä standardiformaatti **ei ole vapaaehtoinen** — sitä
käytetään systemaattisesti kaikissa skillin lähdetiedostoissa, jotta
käyttäjä ja Claude tunnistavat tiedoston roolin nopeasti yhdellä
silmäyksellä.

---

## Vaihe 9: Skillin päivitys, CHANGELOG ja pakkaus

### 9.1 Päivitä SKILL.md ja keskeiset metatiedostot

1. **`SKILL.md`** — tiedostotaulukkoon uudet `*-laivahakemisto.md` ja
   `*-lahteet.md` -rivit. Päivitä myös `metadata.version`-kenttä
   YAML-frontmatterissa (ks. CHANGELOG-osio alla).
2. **`references/lahteet.md`** — kirja kiitososioon, jos kirja on
   merkittävä lähde
3. **`references/hakukaavat.md`** (ja tarvittaessa
   `hakukaavat-arkistot.md`/`hakukaavat-finna.md`/etc.) — uusi jakso
   uudesta paikallisesta hakemistosta + päivitys yhdistelmähakuun
4. **`references/kirjallisuus.md`** — kirja viitelistaan. Tämä on
   **kasvava tiedosto**: se ei ole pelkkä Kivisen Laiva 2/2025
   -artikkelin kopio, vaan skillin yleinen julkaistujen kirjojen
   bibliografia, joka täydentyy jokaisen uuden indeksoinnin yhteydessä.
   Sijoita kirja oikean vesistön/aiheen alle, ja merkitse perään
   tarvittaessa lyhyt huomautus alkuperästä jos kirja ei ole Kivisen
   alkuperäisessä luettelossa (esim. "Lisätty 2026-XX,
   antikvariaattilöydös" tms.).
5. **`references/tutkimukset.md`** (jos kirja perustuu pro graduun
   tai sisältää viittauksia opinnäytetöihin) — sama periaate, kasvava
   tiedosto.
6. **`references/lyhenteet-ja-terminologia.md`** — jos kirja tuo
   uutta terminologiaa joka on käyttäjän/Clauden hyödyllistä tunnistaa
   skillin laajuudessa. **VAIN perusmäärittely + viittaus oikeaan
   hakemistoon**, ei yksityiskohtia jotka kuuluvat hakemistoon
   itseensä.

### 9.2 CHANGELOG-merkintä uuteen versioon

Skillin versionhallintakonventio (otettu käyttöön 2026.05.08):
**versionumero on muotoa `YYYY.MM.DD.##`**, ja sama päivämäärä saa
juoksevan ##-numeron jos sama päivä sisältää useita iteraatioita.
Saman päivän iteraatiot yhdistetään yhdeksi versioksi käyttäjän
päätöksellä.

1. **Päivitä `SKILL.md`-frontmatteri**:
   ```yaml
   metadata:
     version: 2026.MM.DD.##  # uusi versionumero
   ```

2. **Lisää uusi merkintä `CHANGELOG.md`-tiedoston yläosaan** heti
   "Versionhistoria"-otsikon ja formaatin selityksen jälkeen, ennen
   edellisiä merkintöjä. Käytä Keep a Changelog -konventiota (uusin
   ensin):

   ```markdown
   ## YYYY.MM.DD.## — <lyhyt otsikko muutoksesta>

   **Lisätty**:

   - `<kirjan>-laivahakemisto.md` (<lähde>, ~<N> alusta)
   - `<kirjan>-lahteet.md` (<lähdeluettelon laajuus>)
   - <muut uudet tiedostot>

   **Muutettu**:

   - <päivitykset olemassa oleviin tiedostoihin, esim.
     kirjallisuus.md, lahteet.md, hakukaavat.md, lyhenteet>

   **Lähteet**: <kirjan tunnistetiedot>; <eventuaaliset
   asiantuntija- tai båtologi-palautteet>; <muut alkuperälähteet>.
   ```

3. **Sähkemuotoinen tyyli**: pitkät kappaleet välttämään,
   pisteittäin, oleelliset asiat tiivisti. Vältä
   yksityiskohtaista toistoa skillin sisäisestä rakenteesta.

### 9.3 Pakkaa skill

**Käytä skill-creatorin paketointityökalua**, ei pelkkää zippaa:

```bash
rm -f /mnt/user-data/outputs/laivadatan-metsastaja.skill
cd /mnt/skills/examples/skill-creator && \
  python -m scripts.package_skill /tmp/laivadatan-metsastaja /mnt/user-data/outputs
```

Skill-creator validoi:

- YAML-frontmatterin sallitut kentät (mm. `name`, `description`,
  `metadata`, `license`)
- Tiedostorakenteen yleisen kelpoisuuden
- Pakkaa `.skill`-tiedostoksi joka voidaan asentaa Claudeen

**Jos validointi hylkää muutoksen** (esim. `version`-kenttä top-tasolla
ei ole sallittu — käytä `metadata.version`), tarkista virheviesti ja
korjaa frontmatter ennen kuin yrität uudestaan.

### 9.4 Validointitarkistus

Tarkista ennen toimitusta:

```bash
# Versionumero pakkauksessa
unzip -p /mnt/user-data/outputs/laivadatan-metsastaja.skill \
  laivadatan-metsastaja/SKILL.md | head -7

# CHANGELOG-merkintä paketissa
unzip -p /mnt/user-data/outputs/laivadatan-metsastaja.skill \
  laivadatan-metsastaja/CHANGELOG.md | head -25

# Uudet tiedostot ovat mukana
unzip -l /mnt/user-data/outputs/laivadatan-metsastaja.skill | \
  grep -E "<kirjan-lyhytnimi>"
```

Versionumeron, CHANGELOG-merkinnän ja uusien tiedostojen pitää
näkyä paketissa.

---

## Tarkistuslista (käytä lopuksi)

- [ ] **Duplikaattitarkistus tehty** ennen indeksointia — jos kirja on
      jo skillissä, käyttäjältä kysytty miten edetä (päivitä /
      laajenna / erillinen tiedosto)
- [ ] **Tiedostonimi: kirjan otsikko, ei kirjailijan sukunimi**
      (esim. `laudamiehesta-hietaseen-*.md`, ei
      `valta-1997-*.md`). Vuosi sallittu vain disambiguointiin.
- [ ] Kirjan tiedot otsikossa: nimi, kirjailijat, kustantaja, ISBN,
      vuosi, sivut
- [ ] **ISBN tarkistettu matemaattisesti** jos käsinkirjoitettu
      (ISBN-10 mod 11 = 0; ISBN-13 mod 10 = 0)
- [ ] **Standardi yläosaformaatti** kaikissa uusissa lähdetiedostoissa:
      Mikä tämä on / Mikä tämä EI ole / Lue rinnan
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
- [ ] Erillinen lähde-tiedosto luotu (yläosa standardiformaatissa)
- [ ] **`SKILL.md`** — uudet rivit lähdetiedostotaulukkoon
- [ ] **`SKILL.md` `metadata.version`** päivitetty uuteen
      `YYYY.MM.DD.##`-numeroon
- [ ] **`CHANGELOG.md`** — uusi versiomerkintä yläosaan, sähkemuotoisesti
- [ ] **`kirjallisuus.md`** — kirja lisätty (kasvava bibliografia,
      ei vain Kivisen Laiva-artikkelin kopio)
- [ ] **`tutkimukset.md`** päivitetty jos relevanttia (graduja,
      lisensiaatteja jotka kirja käyttää)
- [ ] **`lahteet.md`** ja **`hakukaavat*.md`** päivitetty jos
      relevanttia
- [ ] **Terminologiaan EI tuotu yksityiskohtia** jotka kuuluvat
      hakemistoihin — vain perusmäärittely + viittaus oikeaan
      hakemistoon
- [ ] `grep`-haku testattu (a) nimellä (b) tyypillä (c) vuodella —
      tulokset järkeviä
- [ ] Yhdistelmähaku SKILL.md:ssä päivitetty sisältämään uusi
      hakemisto
- [ ] **Skill paketoitu skill-creatorin kautta**
      (`python -m scripts.package_skill`), ei pelkällä `zip`-komennolla
- [ ] Validointitarkistus tehty (versionumero, CHANGELOG-merkintä,
      uudet tiedostot näkyvät paketissa)
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

---

## Versionhistoria

Versionumeroformaatti: `YYYY.MM.DD.##`. Saman päivän iteraatiot
yhdistetään yhdeksi versioksi. Versioidut: oleelliset ohjemuutokset,
uusien työvaiheiden lisäykset, skillin rakennemuutoksiin reagoivat
päivitykset.

Tämä työnkulkuohje on **erillinen skillistä** — se ei ole skillin
sisällä, joten skillin versionhistoria (`CHANGELOG.md`) ja tämän
työkalun versionhistoria ovat erillisiä.

---

### 2026.05.08.01 — standardi yläosaformaatti, CHANGELOG-prosessi, skill-creator-pakkaus

**Lisätty**:

- Versionumero ja versionhistoria-osio tähän työnkulkuohjeeseen
  itseensä
- Ohje **standardin yläosaformaatin** käytöstä lähdetiedostoissa
  (Mikä tämä on / Mikä tämä EI ole / Lue rinnan) — käyttöönotettu
  skillissä 2026.05.08
- Vaihe 9.2: **CHANGELOG-merkinnän** lisääminen uuden kirjan
  indeksoinnin yhteydessä, sähkemuotoinen tyyli
- Vaihe 9.1 kohta 4: maininta että `kirjallisuus.md` on **kasvava
  bibliografia**, ei pelkkä Kivisen Laiva 2/2025 -artikkelin kopio
- Vaihe 9.1 kohta 5: vastaava maininta `tutkimukset.md`:lle
- Vaihe 9.4: validointitarkistus paketin sisällöstä
  (`unzip -p`, `unzip -l`)
- Tarkistuslistaan kohdat: standardiformaatti, `metadata.version`,
  CHANGELOG, kasvavat bibliografiat, skill-creator-pakkaus,
  validointitarkistus

**Muutettu**:

- Vaihe 9 jaettu neljään alaosaan (9.1 päivitykset, 9.2 CHANGELOG,
  9.3 pakkaus, 9.4 validointi)
- Vaihe 9.3: **pakkauskomento päivitetty** `zip`-komennosta
  `python -m scripts.package_skill`-komentoon (skill-creator validoi
  YAML-frontmatterin)
- Tiedostonimikonventio (Vaihe 6 alussa): "4/8 hakemistoa"
  -maininta poistettu, koska 2026.05.08 alkaen **kaikki**
  kirjapohjaiset tiedostot käyttävät kirjan otsikkoa.
  Esimerkkitaulukkoon lisätty `sisavesien-mikrotonnisto-` ja
  `saimaan-100-vuotishistoria-` (uudet 2026.05.06–08
  yhdenmukaistuksesta)
- Vaihe 8 (lähdeluettelon indeksointi): uusi alaluku
  "Yläosa noudattaa standardiformaattia" template-koodilla
- Yläosa: lisätty maininta että tämä tiedosto **ei ole skillin
  sisällä**, ja että skillin ja tämän työkalun versionumerot ovat
  eri asioita

**Konteksti**: Skillissä otettiin 2026.05.08 käyttöön (a)
versionhallinta `CHANGELOG.md`:llä ja `metadata.version`-kentällä,
(b) standardi yläosaformaatti kaikissa 11 lähdetiedostossa,
ja (c) tiedostonimien yhdenmukaistus kirjapohjaiseksi (mm.
`karttunen-1945-*` → `saimaan-100-vuotishistoria-*`,
`kivinen-2016-*` → `sisavesien-mikrotonnisto-*`). Tämä työnkulkuohje
päivitetään vastaamaan uutta käytäntöä.

---

### Tätä aiempi versio

Aiempi versio (ennen 2026.05.08.01) ei ollut versionoitu. Se sisälsi
vaiheet 1–9 ja tarkistuslistan, mutta käytti vanhentunutta
`zip`-pakkauskomentoa eikä tuntenut standardia yläosaformaattia tai
`metadata.version`-kenttää SKILL.md:n YAML-frontmatterissa.
