# /website/images/ — image drop folder

This folder is referenced by the HTML/CSS. When you generate images via Bing Image Creator (https://www.bing.com/images/create) using the prompts in `../image-prompts.md`, save them here with the filenames below. Once saved, they are picked up automatically — no further code edits required for the OG/Twitter card.

## Already wired (drop the file in, it works)

| File | Used by | Notes |
| ---- | ------- | ----- |
| `og-image.jpg` | `<meta property="og:image">` AND `<meta name="twitter:image">` on all 10 HTML pages | Open Graph + Twitter share card. **Highest priority** — generate this from prompt #10. 1200×630 recommended. |

## Ready to use after you decide to swap an SVG illustration for a photo

These are not yet referenced. The HTML currently uses inline SVG illustrations in their place (intentional — they look polished). When you want to swap one for AI-generated photography, see the "How to swap an SVG for a photo" section below.

| File | Suggested slot | Prompt # |
| ---- | -------------- | -------- |
| `hero-cad-workstation.jpg` | Home hero right column | #1 |
| `crowns-zirconia-macro.jpg` | crowns-bridges.html illustration | #2 |
| `denture-try-in-articulator.jpg` | dentures.html illustration | #3 |
| `scan-received-cad.jpg` | digital-workflow.html illustration | #4 |
| `crown-anterior-hand-mirror.jpg` | services.html illustration | #5 |
| `technician-stereomicroscope.jpg` | about.html illustration | #6 |
| `cad-laptop-design-preview.jpg` | (any) | #7 |
| `courier-handoff.jpg` | contact.html illustration | #8 |
| `about-lab-workspace.jpg` | about.html alternative | #9 |
| `surgical-guide-product.jpg` | services.html (guides anchor) | #11 |
| `material-library-wall.jpg` | (any) | #12 |

## How to swap an SVG for a photo (when you're ready)

Each illustrated page has a block like this:

```html
<section class="tight">
  <div class="container">
    <div class="illo-wrap">
      <svg class="illo" viewBox="..." role="img" aria-label="...">
        ...lots of SVG...
      </svg>
    </div>
  </div>
</section>
```

To replace the SVG with a generated photo, change the inner `<svg>...</svg>` to:

```html
<img class="illo" src="images/hero-cad-workstation.jpg"
     alt="Dental lab CAD workstation"
     loading="lazy" decoding="async"
     style="width:100%; height:auto; display:block; border-radius:8px;" />
```

Keep the `<section class="tight">`, `.container`, and `.illo-wrap` wrappers — they handle the framing, the soft gradient backdrop, the gold rule at top, and the drop shadow. Only the `<svg>` itself changes.

## Resolution targets

- OG/Twitter card (`og-image.jpg`): **1200 × 630**
- Hero photo: **2400 × 1350** (16:9), display at 1200px
- Section illustrations: **1600 × 1200** (4:3) or 1600 × 900 (16:9)
- All formats: prefer **WebP** if you can convert, else JPEG quality 85.

## Bing Image Creator caveats

- Output is usually 1024×1024 square. Crop in Preview/Photos to the target ratio.
- Bing rejects prompts mentioning "patient" / "mouth" / "blood" / etc. The prompts in `image-prompts.md` are pre-sanitized.
- Generate 4 variants per prompt, pick the strongest.
- No people's faces — the prompts already enforce this.
