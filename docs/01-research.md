# strediskoEjAj – research (október 2026)

> Cieľ: jedno miesto po slovensky, kde si aj človek 50+ bez znalosti AI jednoducho
> objedná „oživenie fotky“, vlastnú pesničku, video blahoželanie a podobne.
> My nakúpime výpočet od AI poskytovateľov (centy) a predáme hotový výsledok
> (eurá). Rozdiel je marža.
>
> Ceny AI služieb sú v USD podľa verejných cenníkov k 9/2026 a menia sa často –
> pred spustením ich treba overiť. Právna časť nie je právna rada, je to zoznam
> vecí, ktoré treba prebrať s advokátom.

---

## 1. Zhrnutie v 10 bodoch

1. **Nápad dáva zmysel.** Vstupné náklady na jeden výstup sú 0,04 – 2 USD, slovenská
   konkurencia pýta za oživenie fotky ~2 – 15 € a za pesničku na mieru **9 – 80 €**
   (prehľad v kap. 11). Každý konkurent robí len jednu vec – **jedno miesto pre všetko
   po slovensky** zatiaľ nikto nemá. Pozor: obnovu/vyfarbenie fotky dáva ZonerAI zadarmo.
2. **Suno nemá oficiálne verejné API.** Všetky „Suno API“ sú neoficiálne obchádzky,
   porušujú podmienky Suno a môžu zo dňa na deň prestať fungovať. Na biznis to nestavať.
   Suno od 1. 7. 2026 zbiera prihlášky partnerov do pripravovaného API – **oplatí sa prihlásiť**.
3. **Oficiálne alternatívy na pesničky:** Google Lyria 3.5 (≈ 0,08 USD/pieseň),
   Mureka (≈ 0,02 – 0,07 USD/pieseň), ElevenLabs Music. Kvalitu **slovenského spevu**
   treba otestovať – nikto ju oficiálne negarantuje.
4. **Foto a video** sa najlepšie nakupuje cez agregátor **fal.ai** (jedno API, stovky modelov,
   platba len za použitie) + priamo **Google Gemini API** (Nano Banana, Lyria, Veo).
5. **„Faktúra na konci mesiaca ako Google“** – presne to robí Google Cloud (Gemini/Vertex AI).
   fal.ai je predplatený kredit s automatickým dobíjaním; faktúru po mesiaci dáva až
   firemným (enterprise) zákazníkom. Prakticky: kreditka + auto-top-up, funguje to rovnako dobre.
6. **Platby od zákazníkov:** Stripe (karta, Apple Pay, Google Pay). Pozor na pevný poplatok
   0,25 € – drobné platby pod ~3 € sa neoplatia, preto **balíčky / peňaženka**.
7. **Úložisko:** nie Google Disk (nie je na to určený), ale objektové úložisko
   (Cloudflare R2: 0,015 USD/GB/mes., stiahnutie zadarmo → 100 GB ≈ 1,5 USD/mes.).
   Výstupy držať 30 dní, potom mazať.
8. **„Výstup je náš / doživotná licencia“ nie je nepriestrelné.** Výstup AI bez tvorivého
   vkladu človeka nie je podľa autorského zákona dielo, takže sa ani „vlastniť“ nedá v
   klasickom zmysle. A fotky ľudí sú osobné údaje – súhlas s ich použitím na reklamu sa
   dá kedykoľvek odvolať. Riešenie v kap. 6.
9. **AI Act (EÚ) platí od 2. 8. 2026** – AI obsah musí byť označený (strojovo čitateľne
   + pri realistických ľuďoch aj viditeľne). Nie je to problém, len to treba mať v návrhu od začiatku.
10. **Začať malo:** 6 – 8 dlaždíc (MVP), potom pridávať. Zoznam ~35 nápadov je v kap. 3.

---

## 2. Kto sú zákazníci a čo z toho vyplýva

- **Primárne 50+**, ale veľmi často **platí niekto iný**: deti kupujú rodičom
  („daj mamke darček“), vnúčatá babke. → **Darčekové poukazy** a „pošli ako darček“ sú dôležité.
- Typické príležitosti: narodeniny, meniny (slovenský kalendár mien = ideálny marketing),
  výročia, svadby, Vianoce, Deň matiek, dušičky/spomienky na zosnulých.
- UX pravidlá:
  - veľké dlaždice s ukážkou **pred / po**, veľké písmo (min. 18 px), vysoký kontrast;
  - každý nástroj = **sprievodca na 3 kroky** (nahraj → vyber → zaplať) bez cudzích slov
    („prompt“, „model“, „render“ nikde);
  - **bez povinnej registrácie** – stačí e‑mail (prihlásenie odkazom z e‑mailu, bez hesla);
  - výsledok príde **e‑mailom / SMS** („Vaša pesnička je hotová“) – videá trvajú minúty
    a človek nemusí čakať pri počítači;
  - telefónne číslo / chat na pomoc – pre túto skupinu buduje dôveru viac ako čokoľvek iné;
  - značka „Stredisko“ evokuje „Stredisko služieb obyvateľstvu“ – retro dizajn
    (dlaždice ako okienka, pečiatky, „Vybavené!“) môže byť pre 50+ sympatický.

---

## 3. Čo všetko môžeme ponúkať

Legenda: **★ = MVP (spustiť ako prvé)**, náklad = čo zaplatíme my za 1 výstup (približne),
cena = návrh predajnej ceny s DPH.

### 3.1 Fotky

| # | Nástroj (názov dlaždice) | Čím to urobiť | Náklad | Cena (návrh) |
|---|---|---|---|---|
| 1 | ★ **Oživ starú fotku** (fotka sa pohne, usmeje, zamáva) | image‑to‑video: Kling 2.6/3.0, Seedance, Hailuo, Wan (fal.ai) | 0,20 – 0,70 USD / 5 s | 1,99 – 2,49 € (balík 5 ks 7,99 €) |
| 2 | ★ **Oprav starú fotku** (škrabance, lomy, vyblednutie) | Nano Banana Pro „restoration“, fal photo‑restoration | 0,04 – 0,15 USD | 0,99 € / zadarmo k oživeniu (ZonerAI to dáva zadarmo) |
| 3 | ★ **Vyfarbi čiernobielu fotku** | to isté ako #2 (často v jednom kroku) | 0,04 – 0,15 USD | v cene #2 / 0,99 € |
| 4 | **Zväčši a zaostri fotku** (na tlač) | upscaler (fal, Replicate – Topaz, Clarity) | 0,01 – 0,10 USD | 0,99 € |
| 5 | **Spoj ľudí na jednu fotku** (napr. starí rodičia, ktorí sa nestihli odfotiť spolu) | Nano Banana Pro / Seedream edit | 0,04 – 0,15 USD | 2,49 € |
| 6 | **Objatie / video so zosnulým** (populárny trend „hug video“) | image‑to‑video so 2 osobami | 0,30 – 0,70 USD | 3,99 € |
| 7 | **Portrét ako olejomaľba / kresba / karikatúra** | image edit modely | 0,04 – 0,15 USD | 1,49 € |
| 8 | **Profesionálna profilová fotka** (do životopisu, na Facebook) | image edit | 0,04 – 0,15 USD × 4 návrhy | 2,99 € |
| 9 | **Rodinná vianočná / sviatočná fotka** (z bežnej fotky) | image edit | ~0,15 USD | 1,99 € |
| 10 | **Odstráň niekoho / niečo z fotky**, výmena pozadia | image edit / inpainting | 0,02 – 0,15 USD | 0,99 € |
| 11 | **Omaľovánka z fotky** (pre vnúčatá) | image edit | ~0,05 USD | 0,99 € |
| 12 | **Ako by som vyzeral mladší / starší** | image edit | ~0,05 – 0,15 USD | 0,99 € (zábava) |

### 3.2 Pesničky a zvuk

| # | Nástroj | Čím to urobiť | Náklad | Cena (návrh) |
|---|---|---|---|---|
| 13 | ★ **Pesnička na mieru** (pre koho, príležitosť, pár viet o človeku, štýl: ľudovka, dychovka, šláger, pop, rock) | text: LLM (Claude/Gemini) → hudba: Lyria 3.5 / Mureka / ElevenLabs Music | 0,08 – 0,40 USD (2 verzie na výber) | 9,90 € (konkurencia 19,90 – 45 €) |
| 14 | ★ **Narodeninová / meninová pesnička** (šablóna, len meno + vek) | to isté, rýchlejší sprievodca | ~0,10 – 0,20 USD | 5,90 € |
| 15 | **Uspávanka s menom vnúčaťa** | to isté | ~0,10 USD | 3,99 € |
| 16 | **Zhudobni moju básničku** (vlastný text) | to isté | ~0,10 USD | 3,99 € |
| 17 | **Svadobná / výročná pesnička** (prémiová, dlhšia, viac verzií) | to isté + ručná kontrola textu | ~0,50 USD | 19,90 € |
| 18 | **Prečítaj text nahlas** (list, rozprávku, spomienky – pekným slovenským hlasom) | ElevenLabs v3 TTS (podporuje slovenčinu) | ~0,08 USD / 1 000 znakov | 0,99 – 1,99 € |
| 19 | **Rozprávka na dobrú noc** s menom vnúčaťa (text + hlas + 1 – 3 ilustrácie) | LLM + TTS + image | ~0,20 – 0,50 USD | 2,99 € |

### 3.3 Video

| # | Nástroj | Čím to urobiť | Náklad | Cena (návrh) |
|---|---|---|---|---|
| 20 | ★ **Video blahoželanie** (fotka oslávenca + text + hudba, krátky animovaný klip) | image‑to‑video + AI pesnička / hudba + strih (ffmpeg) | 0,50 – 1,50 USD | 4,99 € |
| 21 | **Hovoriaca fotka** (babka na fotke povie „Všetko najlepšie, Janko!“) | TTS + lip‑sync avatar: Kling Avatar 2.0 (0,04 – 0,09 USD/s), OmniHuman 1.5 (~0,13 – 0,18 USD/s) | 0,70 – 3 USD / 15 s | 5,99 – 7,99 € (konkurencia od 15 €) |
| 22 | **Spomienkové video zo fotiek** (prezentácia 10 – 30 fotiek s hudbou, jemné pohyby) | väčšinou obyčajný strih (takmer zadarmo) + AI hudba + 1 – 3 oživené fotky | 0,30 – 2 USD | 6,99 – 9,99 € |
| 23 | **Krátke video podľa popisu** („mačka hrá na harmonike na Kráľovej holi“) | text‑to‑video (Kling, Seedance, Veo) | 0,30 – 2 USD | 3,99 € |

### 3.4 Texty a „pomocník“

Toto je lacné (LLM stojí zlomky centu) a pre 50+ často **najužitočnejšie**:

| # | Nástroj | Poznámka | Cena (návrh) |
|---|---|---|---|
| 24 | ★ **Napíš blahoželanie / básničku** (veršované, vtipné, dojemné) | ideálne ako **zadarmo lákadlo** alebo súčasť pesničky | zadarmo / 0,49 € |
| 25 | **Príhovor** – svadobný, k jubileu, smútočná reč, kondolencia | vysoká hodnota pre zákazníka | 1,99 € |
| 26 | **Napíš list na úrad / reklamáciu / sťažnosť** | formálny slovenský list | 0,99 € |
| 27 | **Vysvetli mi to po ľudsky** (zmluva, list z banky, lekárska správa) | len vysvetlenie, nie rada; jasné upozornenie | 0,99 € |
| 28 | **Prelož list / dokument** (SK ⇄ EN/DE/HU/…) | | 0,99 € |
| 29 | **Prepíš nahrávku na text** (babkine rozprávanie, hlasovú správu) | Whisper / Gemini / ElevenLabs STT, centy za minútu | 0,99 € / 10 min |
| 30 | **Rodinná kronika / spomienková knižka** – rozhovor (nahrávka) → upravený text + fotky → PDF na tlač | prémiový produkt, môže byť aj s tlačou | 19 – 49 € |
| 31 | **Pozvánka na oslavu / svadbu** (text + grafika) | | 1,99 € |
| 32 | **Logo / vizitka pre živnostníka** | | 4,99 € |

### 3.5 Doplnky, ktoré zvýšia tržby

- **Darčekový poukaz** (najdôležitejšie – kupujú ho deti rodičom).
- **Tlač na fyzický produkt** – fotka na plátne, hrnček, puzzle, kalendár, vytlačená
  knižka; cez slovenskú tlačiareň alebo print‑on‑demand (Printful/Gelato). 50+ chce mať
  fotku „v ruke“, marža na tlači býva vyššia ako na AI.
- **QR kód na pohľadnicu** – vytlačená pohľadnica s QR, ktorý vedie na pesničku/video
  (podrobne v kap. 3.7).
- **Živá fotka (AR)** – vytlačená fotka, ktorá sa v mobile „rozhýbe“ (kap. 3.7).
- **Balíček „Oslava“** = pesnička + video blahoželanie + pozvánka, za zvýhodnenú cenu.

### 3.7 QR a AR – „papier, ktorý hrá“

Dobrá správa: obe veci sú **technicky lacné** (náklad na sken je prakticky nulový) a
skvele nadväzujú na to, čo už generujeme. Funguje to **bez aplikácie** – stačí fotoaparát
v mobile a prehliadač (WebAR).

#### a) QR pesnička / QR video (jednoduché, spoľahlivé – spustiť ako prvé)

- Na pohľadnici, pozvánke, fotke, obale darčeka je QR kód → otvorí stránku výsledku:
  veľké tlačidlo **▶ Prehrať**, pri pesničke **text veľkým písmom** (aj ako karaoke –
  zvýrazňuje sa riadok, ktorý sa práve spieva), tlačidlo Stiahnuť.
- QR generujeme **sami** (open‑source knižnica, zadarmo), vo vlastnej doméne
  `strediskoai.sk/q/xxxx`, s vysokou korekciou chýb, aby sa dal doň vložiť aj logo.
  **Nepoužívať cudzie „dynamické QR“ služby** – po skončení predplatného kód prestane fungovať.
- Produkty:

| Produkt | Ako | Cena (návrh) |
|---|---|---|
| QR k pesničke/videu ako PDF na vytlačenie (pohľadnica, visačka na darček) | digitálne, vytlačia si sami | +0,99 € (alebo zadarmo k objednávke) |
| **Hudobná pohľadnica** – vytlačená a poslaná poštou priamo oslávencovi | tlač + obálka + poštovné | 4,99 – 6,99 € + poštovné |
| Svadobná / jubilejná pozvánka s QR na pesničku alebo video | tlač po kusoch | podľa nákladu |
| Fotka 10×15 s QR v bielom okraji | tlač | 2,99 € |

- Doplnková možnosť: **NFC nálepka** (priloží sa mobil a pustí sa to) – 0,20 – 0,50 €/ks.
  Pre 50+ je QR zrozumiteľnejšie, NFC len ako „wow“ doplnok.

#### b) AR živá fotka („ako v Harrym Potterovi“)

Princíp: zákazník si objedná **Oživ fotku**. Vytlačíme **pôvodnú (opravenú) fotku**
a keď na ňu niekto namieri mobil, **priamo na papieri sa prehrá oživené video** –
babka sa na fotke usmeje a zamáva. Rovnako to ide s pesničkou (fotka sa pohne a hrá
k nej pesnička), s video blahoželaním na pohľadnici alebo so spomienkovým videom na
fotke zo svadby.

Ako to funguje technicky:

1. Na fotke / v jej okraji je **QR kód** → otvorí našu AR stránku pre **túto konkrétnu fotku**
   (vďaka tomu systém hľadá len jeden obrázok – je to spoľahlivejšie).
2. Stránka požiada o kameru, zákazník namieri mobil na fotku, prehliadač ju rozpozná
   (image tracking) a video „prilepí“ presne na ňu.
3. **Záchranná brzda:** ak sa AR nepodarí (starý mobil, zlé svetlo), po pár sekundách
   ukážeme veľké tlačidlo „Prehrať video“ a video sa pustí normálne na celej obrazovke.
   Pre 50+ je to kľúčové – nesmie nastať situácia „nefunguje to“.

Nástroje:

| Možnosť | Cena | Poznámka |
|---|---|---|
| **MindAR** (open‑source, MIT licencia) | zadarmo | rozpoznávanie obrázkov v prehliadači (Android aj iPhone/Safari), beží na našom serveri, žiadne poplatky za sken; „odtlačok“ obrázka (.mind súbor) sa vygeneruje raz pri objednávke. **Odporúčam.** |
| ZapWorks / Mattercraft, Blippar, ARLOOPA, Stories AR, Artivive | predplatné | hotové platformy, rýchly štart bez programovania, ale mesačné poplatky a závislosť na cudzej službe |
| 8th Wall | – | **skončil** (prístup ukončený 28. 2. 2026) – je to dobrá ukážka, prečo nestavať na cudzej platforme |

Na čo si dať pozor:

- **Staré fotky majú málo detailov a kontrastu** → horšie sa rozpoznávajú. Keďže tlačíme
  my, pridáme okolo fotky **ozdobný rámik s výrazným vzorom** (napr. ľudový ornament,
  folklórna výšivka) – ten sa rozpoznáva výborne a zároveň je to pekný dizajn a naša značka.
- Lesklý papier odráža svetlo → tlačiť na **matný** papier.
- Rozmer aspoň 10×15 cm.
- Zvuk: prehliadače nepustia video so zvukom samé od seba – vždy treba 1 ťuknutie
  („Ťuknite a namierte na fotku“). S tým treba v návode počítať.
- Kamera ide len cez **https** (to budeme mať aj tak).

Produkty a ceny (návrh):

| Produkt | Cena (návrh) |
|---|---|
| AR živá fotka – digitálne (PDF na vytlačenie doma / vo fotolabe) | +2,99 € k „Oživ fotku“ |
| AR živá fotka 10×15 vytlačená a poslaná poštou | 7,99 – 9,99 € |
| AR fotka na plátne / v rámiku (30×40) | 24,90 – 34,90 € (bežné plátno bez AR stojí 7 – 16 €) |
| AR pohľadnica s video blahoželaním | 6,99 € |
| AR fotokniha / kalendár (každá strana „ožije“) | 29 – 49 € |

Tlač: slovenský fotolab (odporúčam pre poštovné a rýchlosť) alebo print‑on‑demand
s výrobou v EÚ (Gelato, Prodigi – majú API, pošlú priamo zákazníkovi).

#### c) Pozor: vytlačený QR musí fungovať roky

Pri digitálnom výsledku stačí uchovávať 30 dní, ale **vytlačená fotka visí na stene
10 rokov** – keby kód prestal fungovať, je to sklamanie a zlá reklama.

- Pri tlačených/QR/AR produktoch **garantovať uchovanie napr. 10 rokov** (zahrnúť do ceny).
  Náklad je zanedbateľný: video 10 MB × 10 rokov na R2 ≈ 0,02 USD, sťahovanie zadarmo.
- Ukladať len výsledné video a fotku (nie originály nahraté zákazníkom) – s mazaním
  vstupov to nie je v rozpore.
- Doménu `strediskoai.sk` platiť dopredu na viac rokov a mať pravidlo, že odkazy `/q/…`
  sa nikdy nezrušia.
- Zákazník si môže výsledok kedykoľvek stiahnuť a nechať zmazať (GDPR) – potom QR
  zobrazí slušnú hlášku namiesto chyby.

#### d) Ďalšie nápady na neskôr

- **Spomienková stránka so QR** (napr. na pomník, do pamätnej knihy) – životopis, fotky,
  oživená fotka, pesnička. Existujúci trh, citlivá téma, vyžaduje veľmi taktný prístup a
  súhlas rodiny.
- **Svadobná kniha hostí** – hostia naskenujú QR na stole a nahrajú pozdrav; z nich sa
  urobí spomienkové video.
- **Rodokmeň na plagáte**, kde každá fotka po naskenovaní ožije.

### 3.6 Čo vedome NEROBIŤ (aspoň nie na začiatku)

- **Klonovanie hlasu** („hlas zosnulého dedka“) – senior je hlavný cieľ podvodov typu
  „vnuk volá, že potrebuje peniaze“; klonované hlasy sú presne nástroj týchto podvodov.
  Reputačné a právne riziko je väčšie ako zisk.
- **Zmena oblečenia / „vyzleč“, úpravy tiel**, fotky detí v čomkoľvek inom ako nevinnom
  kontexte – treba to aj technicky blokovať (moderácia vstupov aj výstupov).
- **Politici, celebrity, známe osoby** – blokovať.
- **Určovanie húb a liekov z fotky** – zdravotné riziko.
- **Pasové/dokladové fotky** – úrady AI úpravy neakceptujú.

---

## 4. Poskytovatelia (od koho nakupujeme)

### 4.1 Pesničky – kľúčová a najrizikovejšia časť

| Služba | Oficiálne API? | Cena | Komerčné použitie | Poznámka |
|---|---|---|---|---|
| **Suno** | **Nie** (len partnerský program v príprave, prihláška od 1. 7. 2026) | – | cez neoficiálne API **nezaručené** | neoficiálne „Suno API“ porušujú ToS Suno, účty sa banujú, služba môže kedykoľvek spadnúť |
| **Google Lyria 3.5** (Gemini API) | Áno | 0,08 USD / celá pieseň; 0,04 USD / 30 s klip | áno (podľa podmienok Google) | texty „v jazyku zadania“, vodoznak SynthID (pomôže s AI Actom), fakturácia cez Google Cloud |
| **Mureka** | Áno (platform.mureka.ai) | ~0,02 – 0,07 USD / pieseň | áno, plné komerčné práva na platených plánoch | text‑first prístup (dobré na texty na mieru) |
| **ElevenLabs Music** | Áno | ~0,15 – 0,40 USD / min (podľa plánu) | áno (licencovaná hudba, od plánu Starter) | oficiálne uvádza spev hlavne v EN/ES/DE/JA – slovenčinu treba otestovať |
| MiniMax Music | platené API od 20. 8. 2026 pre nových zákazníkov **nedostupné** | – | otvorená licencia s povinným uvádzaním značky | skôr nie |

**Odporúčanie:** hneď na začiatku urobiť **„slepý test“** – 3 slovenské ľudovky
(napr. *Tancuj, tancuj, vykrúcaj*, *Kopala studienku*, *Na Kráľovej holi*) a 3 texty na mieru
(narodeniny, svadba, uspávanka) vygenerovať v Lyria, Mureka a ElevenLabs a dať vypočuť 5 – 10
ľuďom 50+. Vyhráva ten, kde je **zrozumiteľná slovenská výslovnosť** (mäkčene, dĺžne,
prízvuk na prvej slabike). Systém postaviť tak, aby sa poskytovateľ dal vymeniť jedným
nastavením. Súčasne sa prihlásiť do Suno partner programu.

### 4.2 Fotky a video

- **fal.ai** – agregátor stoviek modelov (Kling, Seedance, Hailuo, Wan, Flux, Nano Banana,
  OmniHuman, upscalery, ElevenLabs…), jedno API, platba za použitie, bez paušálu.
  Predplatený kredit s auto‑dobíjaním; faktúra na konci mesiaca len pre veľkých zákazníkov.
- **Google Gemini API / Vertex AI** – Nano Banana Pro (0,134 USD/obrázok do 2K),
  Veo (video), Lyria (hudba). **Toto je presne to „Google fakturuje na konci mesiaca“** –
  Google Cloud billing účet, platba kartou alebo faktúrou.
- **Replicate** – alternatíva k fal.ai (záloha, keby fal nemal nejaký model).
- **ElevenLabs** – slovenský hlas (TTS), prepis reči (STT).
- **LLM na texty:** Claude / Gemini / GPT – texty, básničky, kontrola a úprava textov piesní
  do spievateľnej podoby, preklad do ďalších jazykov stránky. Náklad ~0,001 – 0,02 USD na úlohu.

### 4.3 Orientačné náklady (9/2026)

| Čo | Model | Cena |
|---|---|---|
| Úprava/oprava fotky | Nano Banana Pro (Google / fal) | 0,134 – 0,15 USD (2K), 0,24 – 0,30 USD (4K) |
| Oprava fotky (lacnejšie) | fal photo‑restoration | 0,04 USD |
| Video z fotky | Kling 2.6 Pro bez zvuku | 0,07 USD/s (5 s = 0,35 USD) |
| Video z fotky so zvukom | Kling 2.6 Pro / 3.0 Turbo | 0,11 – 0,17 USD/s |
| Hovoriaca fotka | Kling Avatar 2.0 Std / Pro | 0,044 / 0,087 USD/s |
| Hovoriaca fotka | OmniHuman 1.5 | ~0,13 – 0,18 USD/s (max 35 s) |
| Pieseň | Lyria 3.5 | 0,08 USD |
| Pieseň | Mureka | ~0,02 – 0,07 USD |
| Hlas (TTS) | ElevenLabs v3 | ~0,08 USD / 1 000 znakov |
| SMS na SK číslo | slovenské SMS brány | 0,033 – 0,04 € bez DPH |
| Úložisko | Cloudflare R2 | 0,015 USD/GB/mes., sťahovanie zadarmo |

---

## 5. Peniaze: ako to účtovať

### 5.1 Príklad marže – pesnička za 9,90 €

| Položka | Suma |
|---|---|
| Cena pre zákazníka (s DPH) | 9,90 € |
| − DPH 23 % (ak sme platitelia) | −1,85 € |
| − Stripe (1,5 % + 0,25 €, EHP karta) | −0,40 € |
| − AI náklad (2 verzie × Lyria + text) | −0,17 € |
| − e‑mail / SMS / úložisko | −0,05 € |
| **Hrubá marža** | **≈ 7,4 €** (~75 %) |

Aj za polovičnú cenu oproti najlacnejšej „seriózne“ vyzerajúcej konkurencii (Melodun 19,90 €)
je marža vysoká – priestor na reklamu, zľavy a darčekové poukazy.

Pri fotke za 0,99 € by Stripe zobral 0,26 € – preto **neúčtovať po jednej lacnej veci**.

### 5.2 Model platieb (odporúčanie)

- Ceny ukazovať **v eurách pri každej dlaždici** (nie v „kreditoch“ – 50+ to mätie).
- **Peňaženka:** „Nabite si 5 € / 10 € / 20 €“ (pri 20 € bonus +2 €). Z peňaženky sa
  odpočítava. Jedna platba kartou → veľa malých nákupov, poplatok 0,25 € sa rozloží.
- Drahšie veci (pesnička, video) sa dajú zaplatiť aj priamo, bez peňaženky.
- **Zadarmo na skúšku:** 1 – 2 výstupy po overení e‑mailu (alebo SMS), s vodoznakom
  „strediskoai.sk“ a v nižšom rozlíšení. Zaplatením sa odomkne plná verzia.
  Zľava/kredit za odporúčanie známemu.
- **Ochrana proti zneužitiu free verzie:** 1 free na e‑mail + telefón, limit na IP,
  CAPTCHA (Cloudflare Turnstile).

### 5.3 Platobná brána

- **Stripe** – karty, Apple Pay, Google Pay, funguje pre slovenskú firmu, 1,5 % + 0,25 €
  (bežná EHP karta). Najjednoduchšia integrácia a dobrý zákaznícky zážitok.
- Alternatívy so slovenskými/ českými bankovými tlačidlami: **GoPay, Comgate**
  (užitočné pre ľudí, ktorí nechcú zadávať kartu – platba cez internet banking).
- **Paddle / Lemon Squeezy** (Merchant of Record – vyriešia DPH za nás vo všetkých
  krajinách) stoja ~5 % + 0,50 USD. Pre začiatok na SK zbytočne drahé; zvážiť až pri
  expanzii do celej EÚ.

### 5.4 Dane a účtovníctvo (prebrať s účtovníkom!)

- **DPH na Slovensku je 23 %.**
- **Nákup služieb zo zahraničia** (fal.ai, Google, ElevenLabs sú mimo SR): aj keď firma
  nie je platiteľ DPH, pri prijatí služby od zahraničnej osoby vzniká povinnosť
  registrácie podľa **§ 7a zákona o DPH** a odvodu DPH z prijatej služby (reverse charge).
  Toto treba mať od začiatku vyriešené, inak hrozia pokuty.
- Pri predaji spotrebiteľom v iných krajinách EÚ (CZ, PL, HU…) sa po prekročení 10 000 €
  ročne platí DPH krajiny zákazníka – rieši sa cez **OSS**.
- Platby kartou cez internet **nespadajú pod eKasu**.
- Faktúry/doklady zákazníkom – Stripe vie posielať potvrdenia; na slovenské doklady
  napr. SuperFaktúra / iDoklad (majú API).

---

## 6. Právo – aby to bolo čo najpriestrelnejšie

> Pred spustením dať VOP, GDPR dokumenty a súhlasy skontrolovať advokátovi
> (cca niekoľko sto €, oplatí sa).

### 6.1 Kto „vlastní“ výstup

- Podľa **autorského zákona (185/2015 Z. z.)** je dielo výsledok tvorivej činnosti
  **fyzickej osoby**. Čisto AI výstup (bez podstatného tvorivého vkladu človeka) dielom
  zrejme nie je – **nikto ho „nevlastní“ ako autor**, ani my, ani zákazník.
- Preto vo VOP nepísať „výstup je vaším vlastníctvom“, ale:
  *„Zákazník môže výstup používať na akékoľvek osobné aj komerčné účely. Prevádzkovateľ
  si na výstup nenárokuje žiadne práva, okrem nižšie uvedených.“*
- Musíme mať **komerčné použitie povolené od poskytovateľa** (Lyria, Mureka, ElevenLabs
  áno; neoficiálne Suno API nie).

### 6.2 Naša „doživotná licencia“ na použitie výstupov

- V B2C zmluvách (so spotrebiteľmi) môže byť plošná, skrytá, neodvolateľná licencia
  považovaná za **neprijateľnú (nekalú) podmienku** – a teda neplatná.
- Ak je na výstupe **tvár človeka**, ide o **osobný údaj** (GDPR) a **ochranu osobnosti**
  (§ 11 – 12 Občianskeho zákonníka). Súhlas s použitím na reklamu sa dá **kedykoľvek odvolať**
  – „doživotná“ licencia na tvár sa zmluvou zaistiť nedá.
- **Odporúčaný spôsob:**
  - pre bežnú prevádzku si stačí vziať úzku licenciu „na poskytnutie služby“ (spracovanie,
    uloženie na 30 dní, doručenie);
  - **na reklamu / ukážky** samostatné, **dobrovoľné zaškrtávacie políčko** – ideálne
    s odmenou („Smieme vašu fotku ukázať ako vzor? Dostanete 2 € kredit.“);
  - pesničky bez osobných údajov (len text a hudba) – tu môže byť širšia licencia v poriadku,
    ale stále ako jasne viditeľná podmienka.
  - Na ukážky na hlavnej stránke radšej použiť **vlastné / vygenerované fotky** a fotky
    rodiny/známych s písomným súhlasom.

### 6.3 Fotky ľudí, zosnulí, deti

- Zákazník musí potvrdiť: *„Na fotke som ja, alebo mám súhlas osôb na nej, prípadne ide
  o mojich zosnulých blízkych.“*
- GDPR sa na zosnulých nevzťahuje, ale **ochrana osobnosti zosnulého** áno (právo majú
  manžel, deti, rodičia – § 15 OZ). Pre bežné „oživenie dedka“ vnukom je to v poriadku;
  problém je zneužitie (zosmiešnenie a pod.) → zakázať vo VOP.
- Deti: povoliť len nevinné úpravy (oprava fotky, vyfarbenie, rozprávka), automatická
  moderácia na nevhodný obsah.
- Služby veku **18+** (platí rodič/ dospelý).

### 6.4 Okamžité mazanie nahratých fotiek

- Dobrý princíp, treba ho ale dotiahnuť: fotka putuje aj k AI poskytovateľovi.
  - mať s poskytovateľmi **DPA (zmluvu o spracúvaní)** a preferovať tých, ktorí na API
    dátach netrénujú a vedia nastaviť krátke uchovávanie;
  - spresniť: *„Nahraté fotky mažeme hneď po vytvorení výsledku (najneskôr do 24 h).
    Výsledky uchovávame 30 dní, aby ste si ich mohli stiahnuť a poslať, potom ich zmažeme.“*
- **Poskytovatelia mimo EÚ** (USA, Čína) = prenos do tretej krajiny – uviesť v GDPR
  informácii, preferovať poskytovateľov s EU‑US Data Privacy Framework.
  Pri čínskych modeloch (Kling, Seedance, Hailuo) cez fal.ai beží výpočet u fal (USA),
  ale aj tak to treba v GDPR dokumentácii popísať.

### 6.5 Ľudové piesne

- **Neupravené ľudové piesne autorskej ochrane nepodliehajú** – sú voľné.
  Chránené sú **úpravy a aranžmány** konkrétnych autorov a piesne s ľudovými motívmi,
  ktorých autor je známy.
- Prakticky: zobrať **pôvodný ľudový text** (zo starých zbierok, nie z konkrétnej známej
  nahrávky či úpravy), AI z neho spraví vlastnú hudbu → ukážka je bezpečná.
  Overiť, že ide skutočne o ľudovú pieseň (nie o „zľudovelú“ pieseň známeho autora –
  napr. viaceré „ľudovky“ z 20. storočia majú autora).
- Pesničky na mieru: zakázať vo VOP texty cudzích piesní a napodobňovanie konkrétnych
  interpretov („v štýle Kollárovcov“ → „v štýle ľudovej kapely“).

### 6.6 AI Act (EÚ nariadenie 2024/1689) – čl. 50

- Od **2. 8. 2026** platia povinnosti transparentnosti:
  - AI výstupy musia byť **strojovo čitateľne označené** (metadáta C2PA / vodoznak).
    Pre systémy uvedené na trh pred 2. 8. 2026 je odklad do 2. 12. 2026, pre nové systémy
    (to sme my) platí hneď.
  - **Deepfake** (realistický obraz/zvuk/video skutočnej osoby) musí byť označený aj pre
    ľudí – kto ho zverejní.
- Riešenie: zachovať vodoznaky od poskytovateľov (napr. Google SynthID), pridávať
  C2PA/metadáta „vytvorené pomocou AI“, a do videí/fotiek malé viditeľné označenie
  („AI · strediskoai.sk“) – zároveň je to reklama.
- V rozhraní jasne písať, že ide o AI (to aj tak chceme).

### 6.7 Ochrana spotrebiteľa

- Digitálny obsah dodaný hneď = zákazník **stráca právo na odstúpenie do 14 dní**, ale len
  ak to **výslovne odsúhlasí** pred zaplatením (zaškrtávacie políčko). Bez toho môže
  do 14 dní žiadať peniaze späť.
- Aj tak odporúčam **„nepáči sa? vygenerujeme znova zadarmo“** (1×) – lacné a buduje dôveru.
- Povinné náležitosti e‑shopu: VOP, reklamačný poriadok, GDPR informácie, identifikácia
  firmy (IČO), kontakt, ARS/ODR.

---

## 7. Doručenie výsledku („pošli to rovno mamke“)

- Každý výsledok dostane **vlastnú stránku** `strediskoai.sk/d/xxxxxxx` (náhodný, neuhádnuteľný
  odkaz) s veľkým tlačidlom **Prehrať** a **Stiahnuť**.
- Pri objednávke možnosť **„Poslať darček“**: e‑mail a/alebo telefón príjemcu,
  krátky odkaz, dátum a čas doručenia (napr. ráno na meniny o 8:00).
- E‑mail: Resend / Brevo / Amazon SES (prvé tisícky e‑mailov zadarmo alebo za centy).
- SMS: slovenská SMS brána ~0,035 – 0,04 € / SMS (Notifea, smartSMS, VIPTel, Zoznam) –
  zarátať do ceny alebo 0,10 € príplatok.
- WhatsApp/Messenger: tlačidlo „Zdieľať“ s odkazom (zadarmo, telefón to vyrieši sám).
- **QR kód na vytlačenie** do pohľadnice, prípadne AR živá fotka (kap. 3.7).

### Úložisko

- Google Disk sa na toto nehodí (nie je to úložisko pre aplikácie, limity API, podmienky).
- **Cloudflare R2**: 100 GB ≈ 1,5 USD/mes., **sťahovanie zadarmo** (u AWS S3 by video
  pozerané veľa ľuďmi stálo za prenos). Prvých 10 GB zadarmo.
- Pieseň ~5 MB, video 10 s ~5 – 15 MB, fotka ~2 – 5 MB → 10 000 výstupov ≈ 50 – 100 GB.
  Pri mazaní po 30 dňoch je to zanedbateľný náklad.
- Výnimka: výsledky k tlačeným QR/AR produktom držať dlhodobo (kap. 3.7 c).

---

## 8. Technické riešenie (návrh)

- **Web:** Next.js (React) – rýchly, dobré SEO, viacjazyčnosť (next‑intl) **od prvého dňa**
  (všetky texty v súboroch `sk.json`, neskôr `cs`, `pl`, `hu`, `uk`, `ru`, `en`).
- **Databáza a prihlasovanie:** Supabase (Postgres + prihlásenie e‑mailovým odkazom) alebo
  Postgres + Auth.js. Server v EÚ (Frankfurt).
- **Úlohy na pozadí:** generovanie videa trvá 1 – 5 min → fronta úloh (napr. Inngest,
  Trigger.dev alebo vlastný worker) + webhooky od fal.ai; po dokončení e‑mail/SMS.
- **Vrstva „poskytovateľ“:** každý nástroj = konfigurácia (ktorý model, aké parametre,
  koľko stojí, akú cenu má). Výmena modelu = zmena konfigurácie, nie kódu.
  Toto je dôležité – modely sa menia každý mesiac.
- **Moderácia:** kontrola vstupnej fotky aj textu (nahota, deti, známe osoby, nenávisť) –
  väčšina poskytovateľov má vlastné filtre, plus lacný LLM/vision check.
- **Platby:** Stripe Checkout + webhooky → peňaženka v DB.
- **Hosting:** Vercel alebo Cloudflare; R2 na súbory.
- **Domény:** `strediskoai.sk` hlavná, `strediskoejaj.sk` presmerovanie (alebo veselšia
  kampaňová verzia). Zaregistrovať aj `.cz` varianty, kým sú voľné.
- **Monitoring nákladov:** každá generácia sa zapíše s nákladom → prehľad marže
  po nástrojoch; denné limity výdavkov na API (ochrana pred chybou/útokom).

---

## 9. Plán krokov

**Fáza 0 – overenie (1 – 2 týždne)**
1. Slepý test slovenských pesničiek (Lyria / Mureka / ElevenLabs), prihláška do Suno partner programu.
2. Test oživenia a opravy 20 skutočných starých rodinných fotiek na 3 – 4 video modeloch.
3. Konzultácia s účtovníkom (s.r.o. vs. živnosť, DPH § 7a) a s advokátom (VOP, GDPR).
4. Registrácia domén, firemné účty: Stripe, fal.ai, Google Cloud, ElevenLabs.

**Fáza 1 – MVP (4 – 6 týždňov)**
- 6 dlaždíc: Oživ fotku, Oprav/vyfarbi fotku, Pesnička na mieru, Narodeninová pesnička,
  Video blahoželanie, Blahoželanie/básnička (zadarmo).
- Peňaženka + priama platba, darčekové poslanie e‑mailom/SMS, stránka výsledku, mazanie po 30 dňoch.
- Slovenčina, mobil na prvom mieste (väčšina 50+ príde z Facebooku na mobile).

**Fáza 2 – rast**
- Darčekové poukazy, tlač (plátno, hrnček, pohľadnica s QR), hovoriaca fotka, spomienkové video.
- QR pesnička / hudobná pohľadnica, potom AR živá fotka (MindAR) s tlačou a poštou.
- Marketing: Facebook skupiny a reklamy na 50+, meninový kalendár („Zajtra má meniny Mária –
  darujte jej pesničku“), spolupráca s domovmi dôchodcov / Jednotou dôchodcov.

**Fáza 3 – ďalšie jazyky**
- Čeština (najmenej práce, rovnaký trh a návyky), potom maďarčina, poľština, ukrajinčina,
  angličtina. Ruštinu zvážiť (reputácia, platby).

---

## 10. Otvorené otázky na rozhodnutie

1. Firma: živnosť alebo s.r.o.? (pri GDPR a deepfake rizikách skôr s.r.o. – ručenie)
2. Ktorý poskytovateľ pesničiek – rozhodne slepý test.
3. Cenová stratégia: po prieskume (kap. 11) odporúčam byť **zhruba o polovicu lacnejší**
   ako slovenská konkurencia, ale nie najlacnejší – a súťažiť **rýchlosťou (hotové hneď,
   nie za 1 – 3 dni), jednoduchosťou a tým, že je všetko na jednom mieste**.
4. Telefonická podpora áno/nie (pre 50+ silný argument).

## 11. Konkurencia a ich ceny (prieskum 10/2026)

> Ako to vzniklo: vyhľadávanie slovenských a českých dopytov („pesnička na mieru“,
> „oživenie starej fotky“, „reštaurovanie starých fotografií cena“, „písnička na přání AI“…).
> Ceny sú z verejných stránok / úryvkov vo výsledkoch vyhľadávania k 2. 10. 2026.
> **Presné poradie na google.sk som overiť nevedel** (môj vyhľadávač nie je google.sk a
> platené reklamy nad výsledkami nevidím) – odporúčam to ručne prejsť na google.sk v
> anonymnom okne a pozrieť aj Google Ads plánovač kľúčových slov (hľadanosť).
> Kurz: 1 € ≈ 24,5 Kč.

### 11.1 Pesnička na mieru – najväčší a najdrahší trh

| Služba | Krajina | Cena | Poznámka |
|---|---|---|---|
| [tvorbapesnicky.sk](https://tvorbapesnicky.sk/) | SK | 45 € / 55 € (2 piesne) / 75 € (3) | do 48 h, až 3 – 4 min |
| [darujpesnicku.sk](https://darujpesnicku.sk/) | SK | 19,90 € (45 – 60 s) / 39,90 € (lyric video) / 79,90 € | viac úrovní |
| [tvojakord.com](https://www.tvojakord.com/) | SK | od 36,99 € | 30‑dňová garancia vrátenia |
| [joyla.sk](https://www.joyla.sk/) | SK | od 29,90 € | MP3 e‑mailom do 3 prac. dní |
| [melodun.sk](https://melodun.sk/) | SK | 19,90 € štandard, 27,89 € expres 24 h | 2 verzie na výber, 1 úprava |
| [piesenpreteba.sk](https://www.piesenpreteba.sk/) | SK | 9 € mini (~90 s) / 14 € / 19 € expres / 29 € | najlacnejšia SK „značka“ |
| [jaspravim.sk](https://www.jaspravim.sk/vasapiesen/pesnicka-na-mieru-pre-vas-o-vas-259540) | SK | od 5 € | jednotlivci na bazári služieb |
| [DarujSong.cz](https://darujsong.cz/) | CZ | 229 Kč (~9,30 €) | AI, rýchla verzia hotová za pár minút |
| [Píseňpro.mě](https://pisenpro.me/) | CZ | od 300 Kč (~12 €) | AI, ~10 min |
| [MakeSong.cz](https://makesong.cz/) | CZ | 549 Kč (~22 €) za 3 pokusy, 1. pieseň zadarmo | AI generátor v chate |
| [Slevomat](https://www.slevomat.cz/akce/2341526-pisnicky-na-prani-vytvorene-za-pomoci-ai-moznost-videa) / [Stovkomat](https://www.stovkomat.cz/ai-pisnicka-na-prani/55978/) | CZ | od 89 Kč (~3,60 €) v akcii | AI pesničky cez zľavové portály |

**Čo z toho plynie:**
- Na Slovensku sa za pesničku bežne platí **20 – 45 €** a čaká sa **1 – 3 dni**.
  Veľká časť týchto služieb s veľkou pravdepodobnosťou tiež používa AI (2 verzie na výber,
  dodanie do 24 h – typický Suno postup), len predávajú „ručnú prácu“.
- Náš náklad je ~0,20 €. **Pesnička na mieru za 9,90 € hneď na počkanie** je o polovicu
  lacnejšia ako Melodun a stále má ~75 % maržu. Prémiová (s ľudskou kontrolou textu,
  svadby, jubileá) za 19,90 €.
- V Česku je trh už lacnejší (3,60 – 12 €) – pri expanzii do CZ treba rátať s nižšou cenou.
- Konkurenti predávajú aj cez **Zľavomat/Slevomat** – to je kanál, kde sa reálne
  stretneme s cieľovkou 50+. Zvážiť kampaň.
- Doplnkové produkty konkurencie: lyric video, **magnetka s hudbou** (tvorbapesnicky.sk) –
  potvrdzuje, že fyzické produkty s QR (kap. 3.7) dávajú zmysel.

### 11.2 Oživenie fotky

| Služba | Krajina | Cena | Poznámka |
|---|---|---|---|
| [zivefotky.sk](https://zivefotky.sk/) | SK | 1 video zadarmo po registrácii, kredity od 3,95 € | priamy konkurent, 5 s video, slovensky |
| [živáfotka.cz](https://zivafotka.cz/) | CZ | 49 Kč (~2 €) za fotku (akcia) | bez registrácie |
| [fotožije.cz](https://fotozije.cz/) | CZ | ~17 Kč (~0,70 €) za animáciu v balíku, balíky od 149 Kč (~6 €) | kreditový systém |
| [FotkaAI.cz](https://fotkaai.cz/pruvodce/oziveni-fotky-video) | CZ | 10 kreditov / 5 s, 20 / 10 s | kreditový systém |
| [jaspravim.sk – obnova + oživenie](https://www.jaspravim.sk/zuzana2525/obnova-starych-fotografii-a-ozivenie-do-videa-ai-restaurovanie-266616) | SK | 5 € (obnova + bonus video), 3 fotky 13 € | dodanie do 2 dní |
| [jaspravim.sk – hovoriace AI video](https://www.jaspravim.sk/babkabozka/ozivim-vasu-fotku-vytvorim-hovoriace-ai-video-s-vlastnym-hlasom-266502) | SK | 15 € | hovoriaca fotka |
| jaspravim.sk – AI videá z fotiek | SK | 8 – 15 € | rôzni predajcovia |
| [MyHeritage Deep Nostalgia](https://www.itechguides.com/products/deep-nostalgia/) | svet | obmedzene zadarmo s vodoznakom, inak predplatné MyHeritage (~4 – 14 USD/mes.) | po anglicky, vyžaduje účet |

**Čo z toho plynie:**
- Tu je trh **lacný a už obsadený** (0,70 – 5 €). Oživenie za 1,99 € (balík 5 ks za 7,99 €)
  je konkurencieschopné; drahšie to nepôjde.
- Výhodou nie je cena, ale **balík a nadstavba**: oprava + vyfarbenie + oživenie v jednom
  kroku, objatie dvoch ľudí, hovoriaca fotka, AR živá fotka na papieri, poslanie ako darček.
- **Hovoriaca fotka** sa na jaspravim predáva za 15 € → u nás 5,99 – 7,99 € je stále výrazne lacnejšie.

### 11.3 Oprava / reštaurovanie / vyfarbenie fotky

| Služba | Cena | Poznámka |
|---|---|---|
| [ZonerAI](https://zonerai.com/sk/) (česká firma Zoner) | **zadarmo** | obnova a vyfarbenie starých fotiek, bez registrácie, aj slovensky |
| [Adobe Firefly](https://www.adobe.com/cz/products/firefly/features/ai-photo-restoration.html) | zadarmo / predplatné | |
| [upravafotky.sk](https://www.upravafotky.sk/), [fotkyobrazy.sk](https://fotkyobrazy.sk/retus-fotografie-oprava-starych-fotografii) a ďalšie ateliéry | ~1,33 – 15 € za fotku | ručná retuš podľa poškodenia |
| [adonaj.sk](https://adonaj.sk/produkt/renovacia-a-oprava-starych-fotografii/), jaspravim.sk | 4,90 – 9,90 € | renovácia, kolorizácia |

**Čo z toho plynie:** samostatná AI oprava fotky sa predávať takmer nedá (ZonerAI je
zadarmo). Dať ju **zadarmo ako lákadlo** alebo do balíka s oživením/tlačou. Platenú verziu
odlíšiť ručnou kontrolou („náš grafik to doladí“) za 4,90 € – tam je trh 5 – 15 €.

### 11.4 Video blahoželanie

- Mobilné aplikácie na „video s vlastnou tvárou“ ([App Store](https://apps.apple.com/sk/app/video-blaho%C5%BEelanie-narodenin%C3%A1m/id1500853741?l=sk)) – zadarmo, ale gýčové šablóny.
- [ShowTimes.sk](https://showtimes.sk/o-nas/) – video pozdrav od slovenskej celebrity (desiatky eur).
- **Priamy konkurent „video blahoželanie s fotkou oslávenca + vlastnou pesničkou“ som
  nenašiel** – dobrá medzera pre nás (cena 4,99 – 6,99 €).

### 11.5 AR živá fotka / QR produkty

- **Slovenského ani českého poskytovateľa AR fotky som nenašiel** (zahraničné: Stories AR,
  Artivive – po anglicky, pre umelcov a firmy). Výhoda prvého na trhu.
- Porovnanie pre cenotvorbu tlače: plátno bez AR od ~6,90 € ([onlinefotky.sk](https://www.onlinefotky.sk/fotoplatno))
  do ~15,90 € ([darcekyodsrdca.sk](https://www.darcekyodsrdca.sk/)), tlač fotky od 0,12 € ([online-fotografie.sk](https://www.online-fotografie.sk/)),
  hrnček od ~13,50 €. AR plátno za 24,90 – 34,90 € je teda prémia ~10 – 20 € za „wow“ efekt.

### 11.6 Celkové zhrnutie pozície

| Kategória | Konkurencia SK | Náš návrh | Prečo vyhráme |
|---|---|---|---|
| Pesnička na mieru | 19,90 – 45 € (1 – 3 dni) | **9,90 €**, hneď | cena + rýchlosť |
| Narodeninová pesnička (šablóna) | – | **5,90 €** | impulzívny nákup na poslednú chvíľu |
| Oživenie fotky | 0,70 – 5 € | **1,99 €** (5 ks 7,99 €) | balík s opravou, darček, AR |
| Oprava/vyfarbenie | zadarmo (ZonerAI) – 15 € | **zadarmo** k oživeniu / 4,90 € s ručnou kontrolou | lákadlo |
| Hovoriaca fotka | 15 € | **5,99 – 7,99 €** | cena |
| Video blahoželanie | – (nenašiel som) | **4,99 – 6,99 €** | nový produkt |
| AR živá fotka | – (nenašiel som) | **+2,99 €** digitálne, 7,99 – 9,99 € vytlačená | nový produkt |

---

## Zdroje

- Suno API – stav: [Music Business Worldwide](https://www.musicbusinessworldwide.com/suno-explores-developer-api-seeking-apps-that-unlock-experiences-generative-music-makes-possible-for-the-first-time/), [tunova.ai](https://tunova.ai/guides/is-there-an-official-suno-api), [AI/ML API blog – riziká neoficiálnych API](https://aimlapi.com/blog/the-suno-api-reality)
- Lyria: [OpenRouter – Lyria 3 Pro](https://openrouter.ai/google/lyria-3-pro-preview), [cellcog.ai – Lyria 3.5](https://cellcog.ai/blog/lyria-3-5/), [invideo – Lyria prehľad](https://invideo.io/blog/lyria-ai-music-generator/)
- Mureka / MiniMax / porovnanie práv: [Mureka API Platform](https://platform.mureka.ai/pricing), [apiframe – AI music API pricing](https://apiframe.ai/blog/ai-music-api-pricing-2026), [invideo – copyright porovnanie](https://invideo.io/blog/ai-music-copyright-comparison/), [fal – MiniMax Music](https://fal.ai/models/fal-ai/minimax-music)
- ElevenLabs: [API pricing](https://elevenlabs.io/pricing/api), [Music docs](https://elevenlabs.io/docs/eleven-creative/products/music), [Slovak TTS](https://elevenlabs.io/text-to-speech/slovak), [fal – Eleven v3](https://fal.ai/models/fal-ai/elevenlabs/tts/eleven-v3)
- Video/foto ceny: [fal – Kling 2.6 Pro](https://fal.ai/models/fal-ai/kling-video/v2.6/pro/image-to-video), [costgoat – Kling](https://costgoat.com/pricing/kling), [devtk.ai – video API 2026](https://devtk.ai/en/blog/ai-video-generation-pricing-2026/), [fal – photo restoration](https://fal.ai/models/fal-ai/image-editing/photo-restoration), [benchlm – Nano Banana](https://benchlm.ai/media-pricing/nano-banana), [fal pricing](https://fal.ai/pricing), [letsenhance – restoration porovnanie](https://letsenhance.io/blog/all/best-4-photo-restoration-tools/)
- Hovoriaca fotka: [evolink – OmniHuman 1.5](https://evolink.ai/omnihuman-1-5), [fal – Kling AI Avatar v2 Pro](https://fal.ai/models/fal-ai/kling-video/ai-avatar/v2/pro), [runware – lip sync](https://runware.ai/collections/best-lip-sync)
- fal billing: [fal docs – billing](https://fal.ai/docs/platform-apis/v1/account/billing), [fal docs – pricing](https://fal.ai/docs/documentation/model-apis/pricing)
- Platby: [Stripe SK pricing](https://stripe.com/en-sk/pricing), [Stripe – local payment methods SK](https://stripe.com/en-sk/pricing/local-payment-methods), [Paddle vs Lemon Squeezy](https://fungies.io/paddle-vs-lemon-squeezy/)
- Úložisko: [Cloudflare R2 pricing 2026](https://mecanik.dev/en/posts/cloudflare-r2-pricing-explained-real-costs-vs-s3-and-backblaze/)
- SMS: [Notifea](https://notifea.com/sk/sms-gateway), [VIPTel](https://www.viptel.sk/sms-brana-hromadne-sms-cez-internet), [smartSMS](https://smartsms.sk/), [Zoznam SMS brána](https://smsbrana.zoznam.sk/)
- AI Act: [Peterka Partners – čl. 50](https://blog.peterkapartners.com/article-50-of-the-ai-act-in-practice-transparency-of-ai-systems-content-labeling-and-deepfakes/), [EK – Code of Practice](https://digital-strategy.ec.europa.eu/en/policies/code-practice-ai-generated-content), [CSA – odklad do 2. 12. 2026](https://labs.cloudsecurityalliance.org/research/csa-research-note-eu-ai-act-article50-watermarking-deadline/), [Gibson Dunn – Omnibus](https://www.gibsondunn.com/eu-ai-act-omnibus-agreement-postponed-high-risk-deadlines-and-other-key-changes/)
- QR / AR: [MindAR (GitHub)](https://github.com/hiukim/mind-ar-js), [MindAR dokumentácia](https://hiukim.github.io/mind-ar-js-doc/), [Kivicube – 8th Wall shutdown](https://www.kivicube.com/post/augmented-reality-after-8th-wall-shutdown-your-2026-guide-to-the-right-webar-platform/), [ARLOOPA – 8th Wall končí](https://www.arloopa.com/blog/8th-wall-is-shutting-down-where-to-move-your-webar-projects), [Stories AR – AR pictures](https://stories-ar.com/en/ar-pictures), [webar-pamphlet – príklad „naskenuj a prehrá video“](https://github.com/arcanesoftai/webar-pamphlet)
- Ľudové piesne a autorské právo: [omediach.com – šéf SOZA o ľudových piesňach](https://www.omediach.com/radio/1234-sef-soza-sa-vyjadril-za-ktore-ludove-piesne-sa-plati-a-za-ktore-nie), [muzicka.sk – autorské práva a folklór](https://www.muzicka.sk/blog/posts/autorske-prava-a-folklorna-hudba/), [Autorský zákon 185/2015 (SOZA)](https://moja.soza.sk/cms/content/files/Autorsky_zakon_185_2015.pdf)
