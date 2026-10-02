# strediskoEjAj – presný postup od nuly po spustenie

> Stav k 2. 10. 2026. Pravidlá overené z verejných zdrojov (odkazy na konci).
> Nie je to právna ani daňová rada. Body označené **⚖️** treba potvrdiť s účtovníkom
> alebo advokátom. Marketing tu zámerne nie je, rieši sa až po spustení.
>
> **👤 = robíš ty**, **🤖 = robím ja (Claude)**, **👥 = účtovník / advokát**

---

## 0. Revízia: čo sa po analýze mení oproti research dokumentu

Prešiel som celý research ešte raz. Toto sú závery, ktoré ovplyvňujú postup:

1. **Najväčšie riziko je kvalita slovenského spevu.** Pesnička na mieru je produkt s
   najväčšou maržou (konkurencia 20 – 45 €, náš náklad ~0,20 €). Keď AI nebude spievať
   zrozumiteľne po slovensky, padá hlavný zdroj príjmu. **Prvý test preto robíme ešte
   pred založením firmy** (krok 1.2). Stojí do 30 € a 2 dni práce.
2. **Na začiatku nebyť platiteľom DPH.** Kým firma neprekročí obrat 50 000 € za 12 mesiacov,
   nemusí byť platiteľom DPH a predáva bez DPH. Pri pesničke za 9,90 € tak zostane
   ~9,30 € namiesto ~7,40 €. Povinná je len **registrácia podľa § 7a** (kvôli nákupu
   AI služieb zo zahraničia). ⚖️
3. **Od 17. 8. 2026 platí nový zákon o obchodnom registri.** S.r.o. sa dá založiť
   - **zjednodušene** cez štátny elektronický formulár (bez notára a advokáta, ale treba
     elektronický podpis), alebo
   - cez **advokáta / notára** (drahšie, ale nemusíš riešiť nič technické).
4. **eKasu nepotrebujeme.** Zákazníci platia vopred online kartou cez platobnú bránu.
   To podľa nového zákona o evidencii tržieb (384/2025) nie je tržba, ktorá sa eviduje v eKase.
5. **AI služby platiť firemnou kartou, nie prevodom.** S.r.o. platí transakčnú daň
   0,4 % z odchádzajúcich prevodov (max. 40 € za transakciu). Platby kartou sú
   oslobodené, za každú použitú kartu sa platí 2 € ročne.
6. **MVP zúžiť na 5 dlaždíc.** QR/AR a tlač až vo fáze 2 (tlač a pošta pridávajú
   logistiku, reklamácie a sklad). Na spustenie:
   - Pesnička na mieru (9,90 €)
   - Narodeninová / meninová pesnička (5,90 €)
   - Oživ fotku + oprava a vyfarbenie zadarmo (1,99 €, 5 ks za 7,99 €)
   - Video blahoželanie (5,99 €)
   - Blahoželanie / básnička (zadarmo, lákadlo)
7. **Dizajn od prvého dňa viacjazyčný.** Texty budú v súboroch, preklad do CZ/HU/PL
   je neskôr len preklad, nie prerábanie.

---

## 1. Fáza A – Overenie nápadu (týždeň 1, ešte bez firmy)

Cieľ: nevyhodiť 5 000 € na firmu, ak AI nespieva dobre po slovensky.

### 1.1 👤 Kúp domény (hneď dnes, ~25 €/rok za obe)

- Over voľnosť na [sk-nic.sk](https://sk-nic.sk) (WHOIS) a kúp u slovenského registrátora
  (napr. WebSupport, Active24 alebo iný akreditovaný registrátor SK‑NIC).
  - `strediskoai.sk` – hlavná
  - `strediskoejaj.sk` – presmerovanie
  - odporúčam aj `strediskoai.cz` (pre budúcu CZ verziu, ~10 €/rok)
- Kúp **na seba** (fyzická osoba). Po založení s.r.o. ich prevedieš na firmu (zmena
  držiteľa u registrátora) alebo ich necháš na sebe a firme ich prenajmeš. ⚖️
- **DNS zatiaľ nemeň**, nastavíme ho spolu v kroku 4.3.

### 1.2 👤 + 🤖 Test kvality AI (rozpočet ~30 €, platíš súkromnou kartou)

1. 👤 Založ si účty (na svoj e‑mail, neskôr ich prevedieme na firemný):
   - [Google AI Studio](https://aistudio.google.com) – Lyria 3.5 (hudba), Nano Banana (fotky). Pridaj kartu (EÚ musí byť na platenom režime).
   - [fal.ai](https://fal.ai) – video modely (Kling, Seedance, Hailuo). Nabi 10 USD.
   - [Mureka](https://platform.mureka.ai) – hudba. Najmenší balík.
   - [ElevenLabs](https://elevenlabs.io) – hudba a hlas. Free alebo Starter (~5 USD).
2. 🤖 Napíšem testovací skript. Vygeneruje:
   - 3 ľudovky (*Tancuj, tancuj*, *Kopala studienku*, *Na Kráľovej holi*) a
     3 pesničky na mieru (narodeniny 70, svadba, uspávanka), každú v 3 službách = 18 pesničiek;
   - oživenie 10 tvojich starých rodinných fotiek v 3 video modeloch.
3. 👤 Pustíš to 5 – 10 ľuďom 50+ (rodina, susedia) **naslepo** (bez názvu služby). Hodnotia:
   rozumiem textu? znie to pekne? dal by som za to 10 €?
4. **Rozhodnutie:** keď aspoň jedna hudobná služba dostane od väčšiny „áno, rozumiem a
   kúpil by som“, pokračujeme. Keď nie, MVP štartuje s fotkami a videom a pesničky
   pridáme, keď sa modely zlepšia alebo keď Suno spustí API.
5. 👤 Paralelne sa prihlás do **Suno partner programu** (formulár z LinkedIn príspevku
   Suno CPO Jacka Brodyho z 1. 7. 2026).

API kľúče **nikdy nepíš do chatu ani do kódu**. Ukážem ti, kam ich vložiť (premenné
prostredia vo Vercel / v súbore `.env.local`, ktorý sa necommituje).

---

## 2. Fáza B – Založenie s.r.o. (týždne 2 – 4)

### 2.1 👤 Rozhodnutia pred založením

| Otázka | Odporúčanie |
|---|---|
| Obchodné meno | napr. **Stredisko AI s.r.o.** Over na [orsr.sk](https://www.orsr.sk), že nikto nemá rovnaké alebo zameniteľné meno |
| Spoločníci | sám = jednoosobová s.r.o. Ak s niekým, dohodnite podiely a pravidlá **písomne** |
| Konateľ | ty |
| Základné imanie | 5 000 € (minimum). **Nie je to náklad.** Peniaze zostanú na firemnom účte a po zápise ich firma môže míňať na podnikanie (AI kredity, hosting, účtovník…) |
| Sídlo | vlastný byt (súhlas vlastníka) alebo **virtuálne sídlo** (~10 – 30 €/mes., preberajú aj poštu). Pre súkromie odporúčam virtuálne sídlo |
| Predmet podnikania | voľné živnosti (pozri 2.3) |

### 2.2 Ako založiť: dve cesty

**Cesta A – zjednodušené založenie cez štátny formulár (lacnejšie, robíš sám)**

Podmienky:
- najviac 5 spoločníkov, len peňažné vklady,
- najviac 15 voľných živností,
- správcom vkladu je konateľ,
- bez dozornej rady,
- spoločenská zmluva len zo štátneho vzoru (bez úprav na mieru).

Pre nás to všetko sedí.

Čo potrebuješ:
- **občiansky preukaz s čipom (eID)**, BOK (bezpečnostný osobný kód) a čítačku kariet,
- **kvalifikovaný elektronický podpis (KEP)**. Certifikát si nahráš do eID zadarmo
  cez aplikáciu Disig Web Signer / eID klient, prípadne na polícii.

Postup:
1. Na [slovensko.sk](https://www.slovensko.sk) → služby obchodného registra →
   **založenie s.r.o. zjednodušeným spôsobom** (elektronický formulár). V jednom
   konaní vybavíš aj živnostenské oprávnenie (voľné živnosti online = 0 €).
2. **Splatenie základného imania:** v banke otvor účet „s.r.o. v založení“ a vlož
   5 000 €. Jednoosobová s.r.o. musí mať pred zápisom splatené celé základné imanie. ⚖️
   Banka ti vydá potvrdenie, prípadne konateľ ako správca vkladu podpíše vyhlásenie
   o splatení. Prilož ho podľa pokynov vo formulári.
3. Prílohy: súhlas vlastníka nehnuteľnosti so sídlom (alebo zmluva o virtuálnom sídle),
   vyhlásenie konateľa, údaje o konečnom užívateľovi výhod (to si ty).
4. Podpíš cez KEP a zaplať **súdny poplatok 220 €**.
5. Registrový súd zapisuje rýchlo, typicky v priebehu niekoľkých pracovných dní.
   Dostaneš **IČO** a výpis z obchodného registra. **Firma vzniká dňom zápisu.**

**Cesta B – cez advokáta alebo službu na zakladanie firiem (jednoduchšie, drahšie)**

- Advokát alebo notár spíše a autorizuje spoločenskú zmluvu a podá návrh za teba.
  Od 17. 8. 2026 je to pri neštandardnej zmluve povinné.
- Cena na trhu: ~**400 – 550 € vrátane súdneho poplatku** (napr. ponuky „založenie s.r.o.
  od advokáta za 519 € s poplatkom“).
- Výhoda: nepotrebuješ čítačku ani KEP, poradia s menom aj živnosťami. Odporúčam, ak nemáš
  skúsenosti s eID. Rozdiel ~300 € je malý v porovnaní s rizikom chýb.

Pri dvoch a viac spoločníkoch odporúčam **vždy cestu B**. Advokát vám spraví zmluvu
s pravidlami, napr. čo keď niekto odíde, kto rozhoduje, vesting.

### 2.3 Voľné živnosti (predmet podnikania)

Vyber z oficiálneho zoznamu voľných živností (názvy musia sedieť presne podľa zoznamu na
slovensko.sk; toto sú návrhy):

- Počítačové služby a služby súvisiace s počítačovým spracovaním údajov
- Sprostredkovateľská činnosť v oblasti služieb
- Sprostredkovateľská činnosť v oblasti obchodu
- Kúpa tovaru na účely jeho predaja konečnému spotrebiteľovi (maloobchod) – pre tlač, poukazy, fyzické produkty
- Reklamné a marketingové služby, prieskum trhu a verejnej mienky
- Administratívne služby
- Vydavateľská činnosť (fotoknihy, kroniky v budúcnosti)

Je to max. 15, online zadarmo. Neskôr sa dajú pridať.

### 2.4 Hneď po zápise do obchodného registra (do 1 – 2 týždňov)

| # | Čo | Kde | Pozn. |
|---|---|---|---|
| 1 | **Firemný bankový účet** (účet „v založení“ sa prevedie na riadny) | banka | **Firemnú platobnú kartu** použi na AI služby (transakčná daň: karty sú oslobodené) |
| 2 | **DIČ** | finančná správa ho pridelí automaticky po zápise | skontroluj v schránke na slovensko.sk |
| 3 | **Elektronická schránka** firmy na slovensko.sk | aktivuje sa automaticky | **Pravidelne ju čítaj!** Doručené správy platia ako doručené aj keď ich neotvoríš (napr. výzvy). Nastav si e‑mailové notifikácie |
| 4 | **Elektronická komunikácia s finančnou správou** | [financnasprava.sk](https://www.financnasprava.sk) – autorizácia cez eID, alebo plnomocenstvo pre účtovníka | pre s.r.o. povinná |
| 5 | 👥 **Registrácia podľa § 7a zákona o DPH** | finančná správa (elektronicky) | **Podaj PRED prvým nákupom AI služby firmou.** Osvedčenie (IČ DPH) príde do ~7 dní. Bežná chyba: registrácia až po prvej faktúre zo zahraničia, to je už porušenie zákona. Firma sa tým **nestáva platiteľom DPH**, ale za mesiace, keď nakúpi služby zo zahraničia, podáva priznanie a odvedie DPH z týchto nákupov. ⚖️ Presný režim pre služby z USA (fal.ai, Vercel…) a z EÚ (Google Ireland, Stripe…) nastaví účtovník |
| 6 | 👥 **Účtovník** | pozri kap. 3 | zmluva + plnomocenstvo na finančnú správu |
| 7 | Sociálna / zdravotná poisťovňa | – | ak konateľ **nedostáva odmenu** a firma nemá zamestnancov, nič sa neprihlasuje. Ak budeš vyplácať odmenu konateľa, rieš s účtovníkom ⚖️ |

### 2.5 Náklady na založenie

| Položka | Cesta A | Cesta B |
|---|---|---|
| Súdny poplatok | 220 € | v cene |
| Advokát / služba | 0 € | ~300 € |
| Živnosti (online) | 0 € | 0 € |
| Čítačka kariet (ak nemáš) | ~10 – 15 € | – |
| Základné imanie (zostáva firme) | 5 000 € | 5 000 € |
| **Skutočný náklad** | **~235 €** | **~520 €** |

---

## 3. Fáza C – Účtovníctvo a dane

### 3.1 👤 Výber účtovníka (urob ešte pred založením, poradí aj so založením)

- S.r.o. musí viesť **podvojné účtovníctvo**. Odporúčam externého účtovníka (fyzická
  osoba alebo účtovnícka firma), pre malú s.r.o. **~60 – 150 €/mesiac** podľa počtu dokladov.
- Pýtaj sa:
  1. Máte skúsenosti s **e‑shopom / digitálnymi službami** a so **službami zo zahraničia (§ 7a)**?
  2. Viete spracovať **výpisy zo Stripe** (veľa malých platieb, poplatky)?
  3. Robíte cez cloudový program a môžem doklady posielať elektronicky?
  4. Čo je v cene (DPH priznania, účtovná závierka, daňové priznanie, mzdy)?
- Účtovníkovi dohodíme **mesačný export** (zoznam objednávok, výplaty Stripe, faktúry od
  AI poskytovateľov). 🤖 Do administrácie spravím tlačidlo „Export pre účtovníka“ (CSV).

### 3.2 Doklady pre zákazníkov

- Zákazník platí kartou online. Dostane e‑mailom **doklad (faktúru)**. Ako neplatiteľ
  DPH na ňom uvádzaš „nie sme platitelia DPH“.
- Riešenie: fakturačný program s API, napr. **SuperFaktúra** alebo **iDoklad**
  (~5 – 15 €/mes.). 🤖 Napojím: po zaplatení sa automaticky vystaví a pošle faktúra.
  Alternatíva: faktúry generovať priamo našou aplikáciou. Dohodnúť s účtovníkom. ⚖️
- **eKasa netreba**, lebo platby idú vopred online cez platobnú bránu (zákon 384/2025).
  Keby si niekedy predával osobne (stánok, jarmok) za hotovosť alebo kartou na termináli,
  eKasa už treba.

### 3.3 Dane a odvody – prehľad

| Čo | Pravidlo (2026) |
|---|---|
| Daň z príjmov s.r.o. | **10 %** zo zisku pri výnosoch do 100 000 € (21 % do 5 mil. €) |
| Daňová licencia (minimálna daň) | 340 € pri výnosoch do 50 000 €; **v prvom zdaňovacom období sa neplatí** |
| Dividendy (výplata zisku tebe) | zrážková daň **7 – 10 %** podľa roku, za ktorý sa zisk vypláca ⚖️; bez odvodov |
| DPH – platiteľ | povinná registrácia po prekročení **50 000 €** obratu za 12 mesiacov (pri prekročení 62 500 € v priebehu roka sa stávaš platiteľom hneď) ⚖️ |
| DPH – § 7a | registrácia pred prvým nákupom služby zo zahraničia, priznanie za mesiace s takýmto nákupom |
| Predaj do iných krajín EÚ (CZ…) | do 10 000 €/rok v celej EÚ sa platí DPH ako na Slovensku; nad 10 000 € DPH krajiny zákazníka cez **OSS** (to až pri expanzii) |
| Transakčná daň | 0,4 % z odchádzajúcich prevodov s.r.o. (max 40 €/transakcia); platby kartou oslobodené, 2 €/rok za kartu |
| eKasa | nie (len online platby vopred) |

### 3.4 Kalendár povinností (orientačne, presne nastaví účtovník)

- **Mesačne:** doklady účtovníkovi do ~10. dňa; DPH priznanie podľa § 7a do 25. dňa za
  mesiace s nákupom zo zahraničia (prakticky každý mesiac).
- **Ročne do 31. 3.:** účtovná závierka + daňové priznanie k dani z príjmov PO + zaplatenie
  dane. Lehota sa dá predĺžiť o 3 mesiace oznámením. Účtovná závierka sa ukladá do
  registra účtovných závierok.
- **Konateľ:** raz za rok rozhodnutie spoločníka o schválení závierky a rozdelení zisku
  (účtovník/advokát dá vzor).

---

## 4. Fáza D – Účty u dodávateľov (po vzniku firmy a po registrácii § 7a)

👤 Všetko zakladaj **na firmu** (IČO, IČ DPH podľa § 7a, firemný e‑mail, firemná karta).
Pri každej službe vyplň fakturačné údaje firmy, aby faktúry chodili na s.r.o.
(daňovo uznateľný náklad).

### 4.1 Firemný e‑mail

- **Google Workspace** (~7 €/používateľ/mes.) alebo Zoho Mail (lacnejšie / zadarmo pre malé tímy).
- Adresy: `info@strediskoai.sk` (zákazníci), `podpora@`, `faktury@` (na faktúry od dodávateľov,
  posielaj účtovníkovi), `admin@` (registrácie služieb).
- **Zapni dvojfaktorové overenie (2FA) všade.**

### 4.2 Zoznam účtov

| Služba | Na čo | Cena (orientačne) | Platba |
|---|---|---|---|
| **GitHub** (už máš) | kód | 0 € | – |
| **Vercel** (Pro) | hosting webu. Bezplatný plán Hobby je len na nekomerčné použitie, preto Pro | ~20 USD/mes. | karta |
| **Supabase** (Pro, región EÚ – Frankfurt) | databáza, prihlasovanie | ~25 USD/mes. | karta |
| **Cloudflare** | DNS, ochrana, úložisko R2 | ~0 – 5 USD/mes. | karta |
| **Stripe** | platby od zákazníkov | 1,5 % + 0,25 € za platbu (EHP karta) | strhne z platieb |
| **Google Cloud / AI Studio** | Lyria (hudba), Nano Banana (fotky), Veo | podľa použitia, mesačná faktúra | karta |
| **fal.ai** | video, oživenie, avatary | predplatený kredit, zapni auto‑dobíjanie (napr. 50 USD) | karta |
| **ElevenLabs** / **Mureka** | hudba / hlas (podľa výsledku testu 1.2) | od ~5 – 22 USD/mes. | karta |
| **Anthropic** (Claude API) alebo Gemini | texty, básničky, úprava textov piesní | centy za úlohu | karta |
| **Resend** (alebo Brevo) | e‑maily „Vaša pesnička je hotová“ | zadarmo do ~3 000/mes., potom ~20 USD | karta |
| **SMS brána** (napr. Notifea, smartSMS) | SMS pri darčeku | ~0,035 – 0,04 €/SMS, predplatený kredit | prevod/karta |
| **SuperFaktúra / iDoklad** | doklady zákazníkom | ~5 – 15 €/mes. | karta |
| **Sentry** | hlásenie chýb | zadarmo (malý objem) | – |

🔒 **Pri každej AI službe nastav mesačný limit výdavkov** (budget alert / hard limit),
napr. 100 USD na začiatok. Chráni pred chybou v kóde aj pred zneužitím.

### 4.3 Stripe – aktivácia (trvá pár dní, začni skôr)

1. Účet na [stripe.com](https://stripe.com) → krajina Slovensko → typ: spoločnosť (s.r.o.).
2. Údaje: IČO, sídlo, konateľ (doklad totožnosti), **konečný užívateľ výhod**, firemný IBAN.
3. Stripe pri aktivácii kontroluje web. Musia na ňom byť: obchodné podmienky, ceny,
   kontakt, sídlo a IČO, reklamačný poriadok / vrátenie peňazí, ochrana osobných údajov.
   🤖 Pripravím stránky (texty potom skontroluje advokát).
4. Zapni platobné metódy: karty, Apple Pay, Google Pay. Neskôr zvážiť aj platbu cez
   internet banking (napr. GoPay/Comgate, ak budú zákazníci chcieť).
5. Výplaty: automaticky na firemný účet (napr. týždenne).
6. Fakturačné údaje na faktúrach od Stripe = s.r.o. (poplatky Stripe sú náklad).

### 4.4 DNS a domény (spolu so mnou)

- 👤 U registrátora nastavíš nameservery na **Cloudflare** (ukážem presne kde).
- 🤖 Pripravím záznamy: web (Vercel), e‑mail (Google Workspace MX), **SPF, DKIM, DMARC**
  (aby e‑maily nepadali do spamu), presmerovanie `strediskoejaj.sk` → `strediskoai.sk`.

---

## 5. Fáza E – Právne dokumenty (týždne 3 – 6, paralelne s vývojom)

🤖 Pripravím **návrhy** všetkých textov podľa research (kap. 6). 👥 **Advokát ich skontroluje**
(rozpočet ~300 – 800 €, jednorazovo). Bez kontroly advokátom to nespúšťaj, hlavne kvôli
fotkám ľudí a licenciám.

| Dokument | Obsah (hlavné body) |
|---|---|
| **Obchodné podmienky (VOP)** | čo predávame, ceny, platba, dodanie (digitálne, hneď), **súhlas so začatím dodania a strata práva na odstúpenie** (zaškrtávacie políčko pred platbou), 1× prerobenie zadarmo, zakázané použitie (deepfake živých osôb bez súhlasu, celebrity, nahota, deti v nevhodnom kontexte, zosmiešňovanie), **práva k výstupom** (zákazník môže používať aj komerčne, my si nenárokujeme), 18+, peňaženka/kredit (ako dlho platí, vrátenie), uchovanie 30 dní |
| **Reklamačný poriadok** | ako reklamovať (e‑mail), lehoty, čo je vada pri AI výstupe |
| **Ochrana osobných údajov (GDPR)** | kto je prevádzkovateľ, aké údaje, prečo, ako dlho (vstupné fotky zmazané do 24 h, výsledky 30 dní), **zoznam sprostredkovateľov** (Google, fal.ai, ElevenLabs, Stripe, Supabase, Vercel, Cloudflare, Resend…), **prenos mimo EÚ** (USA – EU‑US Data Privacy Framework), práva dotknutých osôb, kontakt |
| **Súhlas na použitie ako ukážka** | samostatný, dobrovoľný, odvolateľný, s odmenou (napr. 2 € kredit) |
| **Cookies** | lišta len ak používame neesenciálne cookies. Odporúčam analytiku bez cookies (Plausible / Umami), potom stačí informácia |
| **Označovanie AI (AI Act čl. 50)** | text „Vytvorené pomocou umelej inteligencie“ na stránke výsledku, metadáta v súboroch, malý vodoznak vo videách/fotkách |
| **Interne (nezverejňuje sa)** | záznamy o spracovateľských činnostiach (GDPR), **zmluvy o spracúvaní (DPA)** s dodávateľmi (väčšinou sa „podpisujú“ odsúhlasením v nastaveniach účtu, uložiť PDF) |

Dôležité zákony, na ktoré sa advokát pozrie: zákon o ochrane spotrebiteľa (108/2024),
GDPR + zákon 18/2018, Občiansky zákonník (ochrana osobnosti), autorský zákon (185/2015),
AI Act (EÚ 2024/1689). Zákon o prístupnosti služieb (351/2022) sa na mikropodniky pri
službách zvyčajne nevzťahuje, ale pre 50+ prístupnosť robíme aj tak. ⚖️

Voliteľné:
- **Ochranná známka** „Stredisko AI / strediskoEjAj“ na [ÚPV SR](https://www.indprop.gov.sk).
  Poplatok rádovo stovky € (overiť aktuálny sadzobník), triedy 9, 41, 42. Odporúčam po
  overení, že projekt beží (do pár mesiacov), skôr ako ho niekto skopíruje.
- **Poistenie zodpovednosti** za škodu: lacné, prebrať s poisťovňou.

---

## 6. Fáza F – Vývoj aplikácie (týždne 2 – 7, paralelne s B – E)

Toto robím prevažne ja 🤖, ty 👤 testuješ a rozhoduješ.

### 6.1 Technológie

| Vrstva | Voľba | Prečo |
|---|---|---|
| Web | Next.js + TypeScript, Tailwind | rýchle, SEO, mobil |
| Jazyky | next‑intl, `messages/sk.json` | CZ/HU/PL neskôr len preklad |
| Databáza + prihlásenie | Supabase (EÚ), prihlásenie odkazom z e‑mailu (bez hesla) | 50+ nemusí pamätať heslá |
| Súbory | Cloudflare R2 | lacné, sťahovanie zadarmo |
| Úlohy na pozadí | fal.ai webhooky + fronta (Inngest / Trigger.dev) | video trvá minúty |
| Platby | Stripe Checkout + webhooky, peňaženka v DB | jednoduché a bezpečné |
| AI | vrstva „poskytovatelia“ – model sa mení v konfigurácii | modely sa menia každý mesiac |
| E‑maily | Resend + šablóny po slovensky | |
| Moderácia | filtre poskytovateľov + kontrola vstupu (nahota, deti, známe osoby) | AI Act, VOP |
| Monitoring | Sentry, denný report nákladov AI vs. tržby | kontrola marže |

### 6.2 Poradie práce (MVP)

1. **Kostra webu:** úvodná stránka s veľkými dlaždicami, retro „Stredisko služieb“ dizajn,
   mobil na prvom mieste, veľké písmo.
2. **Pesnička na mieru:** sprievodca 3 kroky (pre koho a príležitosť → pár viet o človeku
   a štýl → zaplatiť). Text vygeneruje LLM, zákazník ho môže **pred zaplatením prečítať
   a upraviť**. Potom 2 verzie piesne.
3. **Narodeninová pesnička** (šablóna: meno, vek, štýl).
4. **Oživ fotku** (nahraj → automatická oprava a vyfarbenie → oživenie → výsledok).
5. **Video blahoželanie** (fotka + text + hudba → strih).
6. **Blahoželanie / básnička zadarmo** (bez platby, po zadaní e‑mailu).
7. **Stránka výsledku** `strediskoai.sk/d/…` (Prehrať, Stiahnuť, Zdieľať, Poslať darček
   e‑mailom/SMS s naplánovaným časom).
8. **Platby:** Stripe, peňaženka (5/10/20 €), priama platba, doklad e‑mailom.
9. **Free skúška:** 1 výstup s vodoznakom po overení e‑mailu, ochrana proti zneužitiu.
10. **Mazanie:** vstupné fotky do 24 h, výsledky po 30 dňoch (automaticky).
11. **Administrácia:** objednávky, náklady, marža, vrátenie peňazí, export pre účtovníka.
12. **Právne stránky** + päta (IČO, sídlo, kontakt).

### 6.3 Prostredia

- **Testovacie** (`test.strediskoai.sk`): Stripe v testovacom režime (platby naoko),
  AI s nízkym limitom.
- **Ostré** (`strediskoai.sk`): po go‑live.

---

## 7. Fáza G – Testovanie (týždeň 7 – 8)

1. 🤖 Automatické testy: platba → generovanie → doručenie → mazanie; výpadok AI
   služby (vráti kredit, ospravedlní sa); dvojité kliknutie na „Zaplatiť“.
2. 👤 **Uzavretá beta: 10 – 20 ľudí 50+** (rodina, známi). Dostanú kredit zadarmo.
   Sleduj, **kde sa zaseknú**, nie čo povedia. Ideálne sedieť vedľa a nepomáhať.
3. 👤 Test na starých telefónoch (lacný Android, starší iPhone), na tablete, na počítači.
4. 👤 Skúšobný reálny nákup vlastnou kartou v ostrom režime + vrátenie peňazí.
5. 👥 Účtovník skontroluje, že doklady a export sedia.
6. 🤖 Kontrola bezpečnosti (kľúče, prístupy, limity, záloha databázy).

---

## 8. Fáza H – Go‑live checklist

**Firma a právo**
- [ ] s.r.o. zapísaná, IČO, DIČ, firemný účet a karta
- [ ] registrácia § 7a (IČ DPH) **pred** prvým firemným nákupom AI
- [ ] účtovník zazmluvnený, plnomocenstvo na finančnú správu
- [ ] VOP, reklamačný poriadok, GDPR, súhlasy skontrolované advokátom
- [ ] DPA s dodávateľmi uložené, záznamy o spracovateľských činnostiach

**Platby a doklady**
- [ ] Stripe aktivovaný, živé kľúče, webhooky overené
- [ ] automatické doklady (SuperFaktúra/iDoklad alebo vlastné) fungujú
- [ ] testovacia platba + vrátenie prebehli

**Technika**
- [ ] domény na Cloudflare, HTTPS, presmerovanie strediskoejaj.sk
- [ ] e‑maily: SPF/DKIM/DMARC, test doručenia na Gmail, Azet, Zoznam, Centrum (50+ ich používa)
- [ ] limity výdavkov na všetkých AI službách
- [ ] moderácia vstupov zapnutá, AI označenie na výstupoch
- [ ] automatické mazanie (24 h / 30 dní) overené
- [ ] záloha databázy, Sentry, denný report nákladov
- [ ] stránka funguje na mobile s veľkým písmom

**Prevádzka**
- [ ] kontakt na podporu (e‑mail; telefón áno/nie – rozhodnúť)
- [ ] postup „zákazník je nespokojný“ (prerobiť zadarmo / vrátiť peniaze)
- [ ] postup „AI služba nefunguje“ (prepnutie na záložný model)

Po odškrtnutí všetkého: **spustenie**. Prvé 2 týždne len pre známych a malé skupiny,
sledovať chyby a náklady. Potom marketing.

---

## 9. Časový plán (realisticky)

| Týždeň | 👤 Ty | 🤖 Ja | 👥 |
|---|---|---|---|
| 1 | domény, účty na test, hodnotitelia | testovací skript, výsledky testu | oslovenie účtovníka |
| 2 | rozhodnutie GO/NO‑GO, banka, sídlo, podanie s.r.o. | kostra webu, dizajn | (advokát – ak cesta B) |
| 3 | zápis firmy, § 7a, firemný e‑mail | pesnička na mieru, platby (test) | účtovník – zmluva |
| 4 | účty na firmu, Stripe aktivácia | oživenie fotky, výsledková stránka | |
| 5 | testovanie priebežných verzií | video blahoželanie, darček e‑mail/SMS | advokát dostane texty |
| 6 | | admin, export, mazanie, právne stránky | advokát vráti pripomienky |
| 7 | beta s 10 – 20 ľuďmi | opravy podľa bety | účtovník kontrola |
| 8 | ostrý test nákupu | go‑live checklist | |
| **8 – 9** | **GO‑LIVE** | | |

Hlavné zdržania bývajú: banka (KYC pri účte v založení), aktivácia Stripe a čakanie na advokáta.
Začni s nimi čo najskôr.

---

## 10. Rozpočet

### 10.1 Jednorazovo (do spustenia)

| Položka | Suma |
|---|---|
| Domény (3×, 1. rok) | ~35 € |
| Test AI (fáza A) | ~30 € |
| Založenie s.r.o. (cesta A / B) | ~235 € / ~520 € |
| Advokát – VOP, GDPR, súhlasy | ~300 – 800 € |
| AI kredity na vývoj a betu | ~100 – 150 € |
| Ochranná známka (voliteľne, neskôr) | rádovo stovky € |
| **Spolu (bez známky)** | **~700 – 1 550 €** |
| + základné imanie (zostáva firme na účte, môže ho míňať) | 5 000 € |

### 10.2 Mesačne (fixné, bez ohľadu na predaj)

| Položka | Suma |
|---|---|
| Účtovník | 60 – 150 € |
| Virtuálne sídlo | 10 – 30 € |
| Vercel Pro + Supabase Pro | ~45 € |
| Google Workspace | ~7 € |
| Fakturačný program | 5 – 15 € |
| Banka | 0 – 10 € |
| Cloudflare, Resend, Sentry | ~0 – 25 € |
| **Spolu** | **~130 – 280 €/mes.** |

Variabilné náklady (AI, Stripe, SMS) sú v cene každého predaja (kap. 5 a 11 v research).

### 10.3 Kedy sa to zaplatí

Pri marži ~9 € na pesničke (ako neplatiteľ DPH) alebo ~1,10 – 1,50 € na oživenej fotke:
- **fixné náklady pokryje ~15 – 30 pesničiek mesačne** (alebo ~90 – 250 oživených fotiek),
- jednorazové náklady sa vrátia pri ~80 – 170 predaných pesničkách.

---

## 11. Čo od teba potrebujem teraz

1. **Kúp domény** (krok 1.1).
2. **Založ účty na test** (krok 1.2): Google AI Studio, fal.ai, Mureka, ElevenLabs.
   Napíš mi, keď budú hotové. Ukážem ti, kam bezpečne vložiť kľúče.
3. Pošli mi (alebo nahraj do repozitára do priečinka `test-fotky/`, ktorý nebude verejný)
   **5 – 10 starých rodinných fotiek** na test. Len so súhlasom rodiny.
4. Rozhodni sa: **sám, alebo so spoločníkom?** A cesta **A (sám cez formulár)** alebo
   **B (advokát)**?
5. Začni hľadať **účtovníka** (otázky v 3.1).

Medzitým môžem začať písať **testovací skript** a **kostru webu**.

---

## Zdroje

- Založenie s.r.o. 2026, nový zákon o OR od 17. 8. 2026: [firmaren.sk](https://www.firmaren.sk/clanky/koniec-lacnych-eserociek-od-augusta-sa-skomplikuju-a-zdrazeju/), [podnikajte.sk](https://www.podnikajte.sk/sro/zalozenie-sro-od-17-8-2026-zmeny), [aksamec.sk – zákon 29/2026](https://www.aksamec.sk/novy-zakon-o-obchodnom-registri-2026/), [sroonline.sk – poplatky 2026](https://www.sroonline.sk/blog_clanok_zalozenie-sro-poplatky), [sroonline.sk – zjednodušené založenie](https://www.sroonline.sk/zjednodusene-zakladanie-s-r-o-prostrednictvom-vzoru-spolocenskej-zmluvy), [orsr.help](https://www.orsr.help/blog/zjednodusene-zalozenie-sro), [tkak.sk – cena od advokáta](https://www.tkak.sk/zalozenie-sro), [efektivnejsie.sk](https://www.efektivnejsie.sk/blog/spolocnost-s-r-o/novy-zakon-o-obchodnom-registri-prinasa-viacere-zmeny-bude-ucinny-od-17-augusta-2026/)
- Živnosti: [finsider.sk – voľná živnosť online zadarmo](https://www.finsider.sk/servis/ako-zalozit-zivnost-v-roku-2026-online-je-volna-zivnost-zadarmo/), [podnikajte.sk – zoznam voľných živností 2026](https://www.podnikajte.sk/zivnost/zoznam-volnych-zivnosti-2026)
- Daň z príjmov PO a daňová licencia 2026: [podnikajte.sk](https://www.podnikajte.sk/dan-z-prijmov/sadzby-dane-z-prijmov-pravnickych-osob-danova-licencia-2026), [finančná správa – minimálna daň](https://podpora.financnasprava.sk/062318-V%C5%A1eobecne-o-minim%C3%A1lnej-dani), [danovy-poradca.sk](https://www.danovy-poradca.sk/en/blog/minimalna-dan-sro-2026)
- Dividendy: [matax.sk](https://www.matax.sk/blog-dividendy-sro-2026), [Forvis Mazars](https://www.forvismazars.com/sk/sk/postrehy/publikacie-a-podujatia/viete-ze-z-danoveho-pohladu/povinnosti-pri-vyplate-dividend-v-roku-2026)
- DPH § 7a: [podnikajte.sk – postup](https://www.podnikajte.sk/dan-z-pridanej-hodnoty/postup-registracia-dph-7a-navod), [startsro blog](https://startsro.blog.pravda.sk/2026/02/18/registracia-dph-podla-%C2%A7-7a-zakona-o-dph/), [prouctovnik.sk – DPH 2026](https://prouctovnik.sk/dph-2026-kompletny-sprievodca/)
- Transakčná daň 2026: [SZRB](https://www.szrb.sk/transakcna-dan-na-slovensku-co-sa-meni-v-roku-2026-a-koho-sa-to-tyka/), [condu.sk](https://condu.sk/blog/transakcna-dan-2026-oslobodenie-zivnostnikov/)
- eKasa 2026 (zákon 384/2025): [wellbens.sk – eKasa a e‑shop](https://www.wellbens.sk/ekasa-online-platby-eshop/), [podnikajte.sk – zmeny 2026](https://www.podnikajte.sk/ekasa/zmeny-v-evidencii-trzieb-od-2026), [ekasaexpert.sk](https://ekasaexpert.sk/blog/ekasa-2026-zmeny.html)
- Stripe SK: [stripe.com/en-sk/pricing](https://stripe.com/en-sk/pricing)
