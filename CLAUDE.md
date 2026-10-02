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
- **MVP = 5 dlaždíc:** Pesnička na mieru 9,90 € · Narodeninová/meninová pesnička 5,90 € ·
  Oživ fotku 1,99 € (5 ks 7,99 €; oprava + vyfarbenie zadarmo) · Video blahoželanie 5,99 € ·
  Blahoželanie/básnička zadarmo.
- Fáza 2: hovoriaca fotka, darčekové poukazy, QR pesnička / hudobná pohľadnica,
  AR živá fotka (MindAR), tlač. Marketing až po spustení.
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
- [ ] Fáza A: domény, testovacie účty (Google AI Studio, fal.ai, Mureka, ElevenLabs),
      testovací skript + slepý test slovenských pesničiek a oživenia fotiek
- [ ] Fáza B: založenie s.r.o.
- [ ] Fáza F: vývoj MVP (ešte nezačatý – v repozitári je zatiaľ len dokumentácia)

## Pravidlá

- API kľúče a heslá nikdy do kódu ani do chatu – len premenné prostredia
  (`.env.local` v `.gitignore`, Vercel env).
- Vývojová vetva: `claude/busy-goldberg-b30nws`.
- Ceny a právne/daňové údaje sa menia – pri použití uviesť dátum a zdroj, overovať.
