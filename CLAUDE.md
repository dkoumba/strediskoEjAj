# strediskoEjAj – kontext projektu pre Claude

Tento súbor sa načíta automaticky v každom novom chate. Udržuj ho aktuálny:
po každom dôležitom rozhodnutí alebo dokončenom kroku uprav sekcie **Rozhodnutia**
a **Stav**.

## O projekte

- Web s jednoduchými AI službami **po slovensky** na jednom mieste (oživenie fotky,
  pesnička na mieru, video blahoželanie…), primárne pre ľudí **50+**.
- Biznis: sprostredkovateľ. Nakupujeme AI výpočet (centy) a predávame hotový výsledok (eurá).
- Domény: `strediskoai.sk` (hlavná), `strediskoejaj.sk` (presmerovanie), neskôr `.cz`.
- Jazyky: najprv SK, neskôr CZ, HU, PL, UK, EN (RU zvážiť).
- Majiteľ komunikuje po slovensky → odpovedaj po slovensky, jednoducho, bez žargónu.

## Dokumenty (zdroj pravdy)

- `docs/01-research.md` – research: ponuka služieb a ceny, poskytovatelia AI, platby,
  právo, QR/AR, konkurencia a jej ceny (kap. 11).
- `docs/02-postup-od-zalozenia-po-spustenie.md` – presný postup: založenie s.r.o.,
  účtovníctvo, dane, účty u dodávateľov, právne dokumenty, vývoj, testovanie,
  go‑live checklist, rozpočet. **Pri rozpore platí 02.**
- Nové zistenia a rozhodnutia zapisuj do týchto dokumentov (nie len do chatu) a commitni.

## Rozhodnutia (stav 2. 10. 2026)

- Forma: **s.r.o.** (otvorené: sám/so spoločníkom; formulár vs. advokát).
- Na začiatku **neplatiteľ DPH**, len registrácia **§ 7a** pred prvým nákupom AI zo zahraničia.
- eKasa netreba (len online platby vopred). AI služby platiť firemnou kartou (transakčná daň).
- **MVP = 6 dlaždíc:** Pesnička na mieru 9,90 € · Narodeninová/meninová pesnička 5,90 € ·
  Oživ fotku 1,99 € (5 ks 7,99 €; oprava + vyfarbenie zadarmo) · Video blahoželanie 5,99 € ·
  **Smiešne videá** (lip‑sync: rozprávajúce zvieratko 3,99 €, vtipný pozdrav z fotky 4,99 €,
  tancujúca fotka 3,99 €, spievajúca fotka +3,99 € k pesničke / balík 12,90 €) ·
  Blahoželanie/básnička zadarmo.
- Smiešne videá: **zákaz politikov a známych osôb** (VOP + potvrdenie súhlasu + filter
  verejných osôb + kontrola textu + vodoznak AI + „Nahlásiť zneužitie“ + logy). Firma môže
  niesť zodpovednosť aj sama (research 6.9) – VOP musí skontrolovať advokát.
- Dodávateľov (Google, fal…) žalovať nemôžeme – ich podmienky hovoria, že **my odškodňujeme
  ich** za zneužitie našimi zákazníkmi. Rovnakú ochranu si spravíme sami (research 6.10):
  VOP so zodpovednosťou a odškodnením zo strany zákazníka, všetky súhlasy ukladať ako dôkaz
  (kto, kedy, IP, verzia VOP), smiešne videá s ľuďmi **len platené** (identifikovateľný
  zákazník), free skúška len pri zvieratkách, s.r.o. + poistenie zodpovednosti
  (cyber + media) od spustenia.
- Fáza 2: „Ty v scéne“, „Prerob svoje video“ (len vlastné videá; research 3.8, 6.8),
  hovoriaca fotka, darčekové poukazy, QR pesnička / hudobná pohľadnica,
  AR živá fotka (MindAR), tlač. Marketing až po spustení.
- **Modely: kvalita na prvom mieste** (rozdiel pár centov nerieši). Aktuálny výber
  (research kap. 12, 10/2026): oprava fotky MAI‑Image‑2.6 / Seedream 5.0 Pro,
  oživenie a video MiniMax H3 / Gemini Omni Flash, hlas Eleven v4, lip‑sync VEED Fabric /
  sync‑3, pohyb Kling 3.0 Motion Control, hudba podľa slepého testu (ElevenLabs Music v2 /
  Lyria 3.5 / Mureka). Rebríčky (Artificial Analysis, Arena.ai) kontrolovať raz za štvrťrok.
- **Nepoužívať neoficiálne Suno API.** Hudba: Lyria 3.5 / Mureka / ElevenLabs. Výber
  rozhodne slepý test slovenského spevu. Suno partner program – prihlásiť sa.
- Nerobiť: klonovanie hlasu, úpravy tiel/nahota, celebrity/politici, huby/lieky z fotky.
- Vstupné fotky mazať do 24 h, výsledky po 30 dňoch (tlačené QR/AR produkty dlhodobo).
- Ceny zobrazovať v eurách (nie kredity), peňaženka 5/10/20 €.

## Plánovaná technika

Next.js + TypeScript + Tailwind, next‑intl (`messages/sk.json`), Supabase (EÚ),
Cloudflare R2 + DNS, Vercel Pro, Stripe Checkout + peňaženka, fal.ai + Google Gemini API
(+ ElevenLabs/Mureka), Resend, SMS brána, Sentry. AI modely ako konfigurácia
(vymeniteľné bez zmeny kódu). Moderácia vstupov, označenie AI výstupov (AI Act čl. 50).
UX pre 50+: veľké dlaždice, veľké písmo, sprievodca na 3 kroky, prihlásenie e‑mailovým
odkazom, výsledok príde e‑mailom/SMS.

## Stav

- [x] Research, prieskum konkurencie, postup po go‑live (docs 01, 02)
- [ ] Fáza A: domény, testovacie účty (Google AI Studio, fal.ai, OpenRouter, Mureka, ElevenLabs),
      testovací skript + slepý test slovenských pesničiek a oživenia fotiek
- [ ] Fáza B: založenie s.r.o.
- [ ] Fáza F: vývoj MVP (ešte nezačatý – v repozitári je zatiaľ len dokumentácia)

## Pravidlá

- API kľúče a heslá nikdy do kódu ani do chatu – len premenné prostredia
  (`.env.local` v `.gitignore`, Vercel env).
- Vývojová vetva: `claude/busy-goldberg-b30nws`.
- Ceny a právne/daňové údaje sa menia – pri použití uviesť dátum a zdroj, overovať.
