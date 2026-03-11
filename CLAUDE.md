# CLAUDE.md — Karla Logistics (CZ) B2B landing

@docs/content-source.md
@docs/design-tokens.md

## Produktový záměr (NEPORUŠIT)
- Web = firemní prezentace + konverzní landing pro kampaně.
- Primární konverze: odeslání formuláře.
- Primární CTA label všude: „Kontaktujte nás“.

Jazyk: čeština (cs-CZ). Styl: průmyslový, věcný, přehledný.

## Publikum
B2B výrobní / průmyslové firmy v CZ/PL (Moravskoslezsko + příhraničí),
které řeší paletové skladování a logistiku.

## Pravidla pro obsah (EXACT COPY — NEPORUŠIT)
- Veškerý návštěvnický text (nadpisy, odstavce, popisky sekcí, statistiky, seznam klientů)
  musí být převzat DOSLOVA z @docs/content-source.md.
- Neparafrázuj, nedoplňuj, nepřepisuj čísla, nevymýšlej benefity ani klienty.
- Canva reference nesmí přepisovat obsah (je čistě vizuální).
- Pokud něco ve @docs/content-source.md chybí, použij TODO (ne generovaný text).

Povolené „UI texty“ mimo content-source:
- labely a chybové hlášky formuláře (česky)
- stavové texty (např. „Odesílám…“, „Odesláno“)
- aria-label a přístupnostní popisky
- technické SEO labely (pokud nejsou marketingová tvrzení)

## Informační architektura
- Single-page landing s anchor navigací.
- Volitelně route /kontakt (scroll na kontakt, nebo samostatná stránka se stejným Contact blokem).

Zakázané: FAQ / Q&A sekce (nepřidávat).

Sekce (v tomto pořadí):
1) Hero (H1 + krátký podnadpis z content-source + CTA)
2) Strategická lokalita / O skladu (content-source)
3) Infrastruktura skladu (fakta ze zdroje; placeholdery ponechat jako TODO)
4) Poloha a dopravní dostupnost (fakta ze zdroje)
5) Naši klienti (POUZE co je ve zdroji)
6) Kontaktujte nás (kontakty + formulář)

## Vizuální reference a brand
- Vizuální reference (layout/styl): design/Home (1).png
- Doporučené exporty pro ladění: design/reference/landing-desktop.png, landing-mobile.png
- Brand barvy (tokeny): #E01020 (red), #181818 (black), #505050 (gray)

Vzhled:
- industriální, moderní, čistá mřížka, ostré karty, minimální stíny
- červená primárně pro CTA a důležité bloky

## Typografie a tokeny
- Používej tokeny z @docs/design-tokens.md (žádné nové barvy mimo tokeny).
- Sans-serif (Inter/System UI), výrazná typografická hierarchie, krátké odstavce.

## Přístupnost (WCAG) — must-have
- Kontrast běžného textu min. 4.5:1.
- Text přes fotografie musí mít scrim/overlay tak, aby kontrast splnil 4.5:1.
- Všechny interaktivní prvky: focus state, ovládání klávesnicí.
- Formulář: každý input má label; checkboxy mají jasné popisky.

## Výkon — must-have
- Cíl Lighthouse >= 90 (Performance + Accessibility + SEO).
- Optimalizuj obrázky (správné rozměry, komprese, lazy-loading), minimalizuj JS.

## Kontakt formulář (konverzní jádro) — must-have
Layout: vždy single-column.

Pole:
- Povinné: Název firmy, Kontaktní osoba, E-mail
- Volitelné: Telefon
- Zpráva (textarea)
- Služby (checkbox group; hodnoty/labely musí být ve @docs/content-source.md)
- Povinné: GDPR souhlas checkbox + odkaz na zásady (URL jako TODO, pokud chybí ve zdroji)

Validace:
- Inline validace (onBlur + onSubmit), chyby přímo u pole, česky.
- Server-side validace povinná (bezpečnost).
- Anti-spam: honeypot + limity délky vstupů.

Odeslání:
- Odeslat e-mail do firemní schránky: TODO CONTACT_INBOX_EMAIL
- Auto-reply odesílateli (ACK).
- Audit: uložit submittedAt + consentTextVersion (TODO definovat).

## SEO minimum
- Meta title/description z content-source (žádné nové sliby).
- OpenGraph tags.
- Sémantika: H1 jen jednou, sekce H2.

## Engineering konvence (stack-agnostic)
- Preferuj TypeScript.
- Preferuj Tailwind CSS s tokeny/design variables z @docs/design-tokens.md.
- Komponenty po sekcích (Hero, Infrastructure, Location, Clients, ContactForm).
- Texty drž v jednom zdroji (content-source), nedělej duplicitní konstanty.

## Workflow v Claude Code
- Použij /init pro start projektu a slouč návrh s tímto CLAUDE.md (nepřepisuj STRICT pravidla).
- Při problémech ověř načtené instrukce přes /memory.
- Po změnách vždy: lint + typecheck + testy + Lighthouse/axe.
- Udrž CLAUDE.md krátký; detaily patří do importovaných souborů nebo .claude/rules/.

