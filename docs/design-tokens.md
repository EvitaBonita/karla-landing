# design-tokens.md — Karla Logistic

## Brand barvy (canonical)

| Token           | Hex       | Použití                                      |
|-----------------|-----------|----------------------------------------------|
| `--color-red`   | `#E01020` | CTA tlačítka, akcenty, důležité bloky        |
| `--color-black` | `#181818` | Tmavé pozadí (hero, nav, kontakt sekce)      |
| `--color-gray`  | `#505050` | Tělo textu, sekundární popisky              |
| `--color-white` | `#FFFFFF` | Text na tmavém pozadí, karty                |
| `--color-light` | `#F5F5F5` | Světlé sekce (klienti), hover stavy         |
| `--color-black-90` | `#0F0F0F` | Footer pozadí                           |

## Odvozené / UI barvy (NESMÍ být mimo výše uvedené tokeny)

| Token                    | Hodnota                        | Použití                          |
|--------------------------|--------------------------------|----------------------------------|
| `--color-red-hover`      | `#C00E1C`                      | Hover stav CTA tlačítek          |
| `--color-border-dark`    | `rgba(255,255,255,0.1)`        | Okraje na tmavém pozadí          |
| `--color-border-light`   | `rgba(24,24,24,0.1)`           | Okraje na světlém pozadí         |
| `--color-text-muted-dark`| `rgba(255,255,255,0.7)`        | Muted text na tmavém pozadí      |
| `--color-overlay`        | `rgba(24,24,24,0.75)`          | Hero video scrim                 |

## Typografie

| Token                | Hodnota                          |
|----------------------|----------------------------------|
| `--font-sans`        | `'Inter', system-ui, sans-serif` |
| `--font-size-h1`     | `clamp(2.2rem, 5vw, 3.75rem)`    |
| `--font-size-h2`     | `clamp(1.75rem, 3vw, 2.5rem)`    |
| `--font-size-body`   | `1rem` (16px)                    |
| `--font-size-small`  | `0.875rem` (14px)                |
| `--font-size-label`  | `0.75rem` (12px)                 |
| `--font-weight-bold` | `700`                            |
| `--font-weight-semi` | `600`                            |
| `--line-height-body` | `1.65`                           |

## Spacing / Grid

| Token              | Hodnota     |
|--------------------|-------------|
| `--container-max`  | `72rem` (1152px) |
| `--section-py`     | `5rem` desktop, `3rem` mobile |
| `--gap-card`       | `1rem`      |
| `--radius`         | `0` (sharp cards — industriální styl) |

## Komponenty

### CTA tlačítko (primární)
- Background: `#E01020`
- Text: `#FFFFFF`
- Hover: `#C00E1C`
- Padding: `0.75rem 2rem`
- Font weight: 600
- Border-radius: 0 (sharp)

### Karta (na tmavém pozadí)
- Border: `1px solid rgba(255,255,255,0.1)`
- Background: transparent nebo `rgba(255,255,255,0.05)`

### Formulář input
- Background: `rgba(255,255,255,0.1)` (na tmavém bg)
- Border: `1px solid rgba(255,255,255,0.2)`
- Focus border: `#E01020`
- Text: `#FFFFFF`

## Tailwind konfigurace (CDN)

```js
tailwind.config = {
  theme: {
    extend: {
      colors: {
        'brand-red':   '#E01020',
        'brand-black': '#181818',
        'brand-gray':  '#505050',
      },
      fontFamily: {
        sans: ['Inter', 'system-ui', 'sans-serif'],
      },
      maxWidth: {
        container: '72rem',
      },
    }
  }
}
```
