# SectorCare Email Design Specification
*Reusable prompt + verification table for Claude Code*

---

## PART 1 — REUSABLE GENERATION PROMPT

Copy this prompt into Claude Code to regenerate or create new emails:

---

```
You are generating HTML marketing emails for SectorCare (sectorcare.com.au), an Australian mobility equipment retailer and registered NDIS provider. Use the exact design system below. All emails must be table-based HTML compatible with Outlook, Gmail, and Apple Mail. No external CSS. All styles inline except the <style> block for @media.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
BRAND IDENTITY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Brand name: SectorCare (one word, capital S and C)
Tagline: Move with confidence
NDIS: Registered NDIS provider — mention as text, never as a badge
Phone: 02 9172 5607
Email: sales@sectorcare.com.au
Hours: Mon – Fri, 9am – 5pm AEST
Website: https://sectorcare.com.au/
Privacy: https://www.sectorcare.com.au/privacy

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
COLOR PALETTE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Brand Blue (primary accent):  #3A9AD9
Dark Navy (headings):         #111e2d
Deep Black (footer bg):       #06141b
Navy 2 (icon circles):        #233543
Gray Text (body copy):        #475666
Light Gray (muted text):      #96a3ac
Light BG (email outer / contact section): #f5f7fa
Border:                       #e4e8ed
White (card/content bg):      #FFFFFF

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TYPOGRAPHY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Primary font stack:
  'Opposans','SF Pro Display',-apple-system,BlinkMacSystemFont,'Segoe UI',Arial,sans-serif

Monospace (promo codes only):
  'Courier New',Courier,monospace

Font sizes:
  Utility bar text:       10px / color #475666
  Header subtitle:         9px / color #3A9AD9 / letter-spacing 3px / uppercase
  H1 (hero headline):     34px / weight 700 / color #111e2d (dark part) + #3A9AD9 (blue part)
  H1 mobile:              26px (via .hh class @media)
  Body copy:              13px / color #475666 / line-height 1.72–1.75
  Section label eyebrow:   9px / color #3A9AD9 / letter-spacing 2.5px / uppercase
  Feature tile title:     10px / weight 700 / color #111e2d / letter-spacing 0.3px
  Feature tile body:       9px / color #475666 / line-height 1.6
  CTA button:             11px / weight 700 / uppercase / letter-spacing 1.5px / color #FFFFFF
  Category card title:    10px / weight 700 / color #111e2d / uppercase / letter-spacing 0.5px
  Category card body:      9px / color #475666 / line-height 1.6
  Category button:         9px / weight 700 / uppercase / letter-spacing 1px
  Product name:           16px / weight 700 / color #111e2d
  Product price:          20px / weight 700 / color #3A9AD9
  Contact label:          10px / weight 700 / color #111e2d
  Contact phone:          13px / weight 700 / color #111e2d
  Contact email:          11px / weight 700 / color #111e2d
  Contact hours:           9px / color #475666
  NDIS line (contact):     9px / weight 700 / color #3A9AD9 / letter-spacing 1.5px / uppercase
  Promo code:             22px / weight 700 / color #FFFFFF / letter-spacing 6px / monospace
  Promo terms:             9px / color #475666 / letter-spacing 1px / uppercase
  Footer legal:            9px / color #475666 / line-height 1.7 / letter-spacing 0.5px
  Footer links:            9px / color #96a3ac / underline

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
LAYOUT & SPACING
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Email max-width: 600px (class .ew)
Outer wrapper bg: #f5f7fa, padding 20px top / 28px bottom
Card: white bg, box-shadow 0 2px 16px rgba(0,0,0,0.10)
Content horizontal padding: 40px desktop (class .mp → 20px mobile)
Section dividers: border-bottom: 1px solid #e4e8ed between all sections
Header border: border-bottom: 3px solid #3A9AD9 (accent stripe below logo)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
RESPONSIVE (MOBILE)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Breakpoint: max-width 600px
Classes used in @media block:
  .ew  → width 100%
  .mp  → padding-left/right 20px
  .pc  → product card: 100% width, display block, border-right none, border-bottom 1px solid #e4e8ed
  .cc  → contact column: 100% width, display block, border-right none, padding-bottom 14px
  .hh  → H1: font-size 26px
  .fc  → feature tile: (no override needed, handled by .pc logic)
  .pl  → padding-left override (optional)
  .pr  → padding-right override (optional)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SECTION STRUCTURE (in order)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Every email contains these sections in this order:

1. UTILITY BAR
   - Background: #f5f7fa, padding 7px 20px, centered, border-bottom 1px #e4e8ed
   - Text: "Trouble viewing this email?" + Klaviyo web view link
   - Link: {% web_view %} — color #3A9AD9, underline

2. HEADER (Logo + Subtitle)
   - Background: #FFFFFF, padding 20px 36px 14px, centered
   - Border-bottom: 3px solid #3A9AD9 (brand accent stripe)
   - Logo: <img height="36"> linked to sectorcare.com.au
   - Logo URL: https://d3k81ch9hvuctc.cloudfront.net/company/W2Ua5v/images/47898cac-310d-44a3-8d9a-29791b93b07d.png
   - Subtitle: 9px, #3A9AD9, letter-spacing 3px, uppercase (e.g. "WELCOME TO THE FAMILY")

3. HERO IMAGE
   - Full-width (600px), no padding, line-height 0 (prevent gap)
   - Linked to relevant product or site URL
   - Two available hero images:
     HI1: https://d3k81ch9hvuctc.cloudfront.net/company/W2Ua5v/images/08ffb312-e5cc-4485-8091-31a785854699.jpeg
     HI2: https://d3k81ch9hvuctc.cloudfront.net/company/W2Ua5v/images/3559e029-ad75-4195-9ba1-51d6de31f7ab.jpeg

4. HERO TEXT + CTA
   - Background: #FFFFFF, padding 30px 40px 26px, border-bottom 1px #e4e8ed
   - H1: 34px, weight 700, line-height 1.2, margin-bottom 10px
     - First line: color #111e2d
     - Second line (span): color #3A9AD9
   - Body copy: 13px, #475666, line-height 1.72, margin-bottom 20px
   - CTA button: background #3A9AD9, border-radius 4px, padding 11px 28px
     - Text: 11px, weight 700, uppercase, letter-spacing 1.5px, color #FFFFFF

5. BODY TEXT (optional warm message / intro paragraph)
   - Background: #FFFFFF, padding 22px 40px 26px, border-bottom 1px #e4e8ed
   - 13px, #475666, line-height 1.75
   - Mention NDIS registered provider as plain text here if relevant

6. OPTIONAL CONTENT SECTIONS (include as needed for email type):

   A. FEATURE GRID (2×3 tiles, product features)
      - Background: #FFFFFF, no outer padding, border-bottom 1px #e4e8ed
      - 2-column table, 3 rows (6 tiles total)
      - Each tile: padding 16px 18px, border-right + border-bottom 1px #e4e8ed
      - Icon: HTML entity, 22px, color #3A9AD9, margin-bottom 6px
      - Title: 10px, weight 700, #111e2d, letter-spacing 0.3px
      - Body: 9px, #475666, line-height 1.6
      - Standard icons: &#9671; &#9675; &#8776; &#8853; &#9633; &#9651;

   B. STATIC PRODUCT CARDS (1–3 columns)
      - Class .pc for mobile stack
      - Product image: linked, border-radius 4px, border 1px #e4e8ed
      - Product name: 16px, weight 700, #111e2d, fixed height 44px cell
      - Description: 13px, #475666, line-height 1.55, fixed height 44px cell
      - CTA button: background #3A9AD9, border-radius 4px, 11px text
      - Available products:
        Airflex 1: https://d3k81ch9hvuctc.cloudfront.net/company/W2Ua5v/images/e3a5b767-e091-4a33-b719-5ccc5a6c608b.jpeg → https://sectorcare.com.au/sectorcare-airflex-1-portable-wheelchair/
        Infinity Comfort: https://d3k81ch9hvuctc.cloudfront.net/company/W2Ua5v/images/325a1313-9e3a-463c-a703-69bcdbfcf416.jpeg → https://sectorcare.com.au/infinity-electric-wheelchair-grey-series/
        Infinity Feather: https://d3k81ch9hvuctc.cloudfront.net/company/W2Ua5v/images/8f7cae70-2e20-43e3-a038-b2fd9de3c915.jpeg → https://sectorcare.com.au/infinity-feather-electric-wheelchair-carbon-fibre/

   C. CATEGORY CARDS (3 columns: Manual / Scooter / Electric)
      - Icon circle: background #233543, border-radius 50%, 40×40px
      - Icon: 18px, color #96a3ac, line-height 40px
      - Icons: &#9855; (wheelchair) / &#128663; (scooter) / &#9889; (electric)
      - Title: 10px, weight 700, #111e2d, uppercase, letter-spacing 0.5px, height 30px cell
      - Body: 9px, #475666, line-height 1.6, height 50px cell
      - Button: background #3A9AD9, border-radius 3px, padding 7px 14px
      - URLs: /manual-wheelchair/ · /mobility-scooter/ · /electric-wheelchair/

   D. KLAVIYO CART PRODUCT CARD (abandoned cart emails)
      - Image: {{ event.item_image_url }}, 160px wide, border-radius 4px, border 1px #e4e8ed
      - Name: {{ event.item_name }}, 16px, weight 700, #111e2d
      - Price: {{ event.item_price }}, 20px, weight 700, #3A9AD9
      - Link: {{ event.item_url }}
      - CTA: "RETURN TO CART →"

   E. KLAVIYO BROWSE PRODUCT CARD (browse abandonment emails)
      - Image: {{ event.ProductImageURL }}, 200px wide
      - Name: {{ event.ProductName }}
      - Price: {{ event.ProductPrice }}
      - Link: {{ event.ProductURL }}
      - CTA: "VIEW PRODUCT DETAILS"

   F. KLAVIYO RELATED PRODUCTS (3 col, conditional)
      - Wrap in: {% if event.related_product_1_name %}...{% endif %}
      - Variables: event.related_product_N_name / _image / _url / _price (N=1,2,3)

   G. PROMO CODE BOX (optional, for emails with discount codes)
      - Background: #06141b, padding 28px 36px, centered
      - Eyebrow: 10px, #96a3ac, letter-spacing 2.5px, uppercase
      - Code box: border 2px dashed #475666, border-radius 4px, bg #111e2d, padding 12px 32px
      - Code text: 22px, weight 700, #FFFFFF, letter-spacing 6px, monospace font
      - Terms: 9px, #475666, letter-spacing 1px, uppercase

7. CONTACT SECTION
   - NDIS line: background #f5f7fa, padding 8px 40px, centered
     Text: "SectorCare is a Registered NDIS Provider" — 9px, weight 700, #3A9AD9, letter-spacing 1.5px, uppercase
   - Contact columns: background #f5f7fa, padding 18px 40px 24px, border-bottom 1px #e4e8ed
     2 columns (class .cc for mobile stack), border-right 1px #e4e8ed between
     Left: Phone icon &#9742;&#xFE0E; (text-presentation selector, prevents emoji), 20px, #3A9AD9
           Label "Phone", number 02 9172 5607, href tel:0291725607
           Hours: Mon – Fri, 9am – 5pm AEST
     Right: Email icon &#9993;, 20px, #3A9AD9
            Label "Email", address sales@sectorcare.com.au
            Hours: Mon – Fri, 9am – 5pm AEST

8. FOOTER
   - Background: #06141b, padding 18px 36px, centered
   - Legal text: 9px, #475666, line-height 1.7, letter-spacing 0.5px
     Use {{ organization.name }} and {{ organization.full_address }} (Klaviyo vars)
   - Links row: Unsubscribe · Privacy Policy
     Unsubscribe: {% unsubscribe %} — color #96a3ac, underline
     Privacy: https://www.sectorcare.com.au/privacy — color #96a3ac, underline

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
KLAVIYO VARIABLES REFERENCE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
In raw HTML files, use exactly:
  {{ person.first_name|default:"there" }}
  {{ event.item_name }}
  {{ event.item_image_url }}
  {{ event.item_price }}
  {{ event.item_url }}
  {{ event.ProductName }}
  {{ event.ProductImageURL }}
  {{ event.ProductPrice }}
  {{ event.ProductURL }}
  {{ event.related_product_1_name }}  (and _2_, _3_)
  {{ event.related_product_1_image }} (and _2_, _3_)
  {{ event.related_product_1_url }}   (and _2_, _3_)
  {{ event.related_product_1_price }} (and _2_, _3_)
  {{ organization.name }}
  {{ organization.full_address }}
  {% web_view %}
  {% unsubscribe %}
  {% if event.related_product_1_name %}...{% endif %}

IMPORTANT — Python f-string escaping (only needed if writing a Python generator):
  {{ }}  →  {{ }}  (double the braces: {{{{ }}}})
  {% %}  →  {{% %}} (double the percent braces)
  CSS {} →  {{}} in f-strings

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TECHNICAL REQUIREMENTS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
- DOCTYPE: <!DOCTYPE html>
- xmlns: <html xmlns="http://www.w3.org/1999/xhtml">
- charset meta + viewport meta required in <head>
- Reset styles in <style>:
    #outlook a{padding:0}
    body{margin:0;padding:0;background:#f5f7fa;-webkit-text-size-adjust:100%}
    table,td{border-collapse:collapse;mso-table-lspace:0;mso-table-rspace:0}
    img{border:0;outline:none;text-decoration:none;max-width:100%}
    p,h1,h2,h3{margin:0;padding:0}
- All images: display:block to remove bottom gap
- Hero image: width="600" attribute + style="display:block;width:100%;height:auto;"
- Buttons: table-based (not <a> directly), so background color renders in Outlook
- All links: target="_blank"
- Phone link: href="tel:0291725607" (no spaces or dashes)
- Email link: href="mailto:sales@sectorcare.com.au"
- Phone icon: &#9742;&#xFE0E; (&#xFE0E; forces text rendering, not emoji)
```

---

## PART 2 — SPECIFICATIONS VERIFICATION TABLE

Use this table to check that the prompt above covers every design element.

| # | Category | Element | Value / Rule | In Prompt? |
|---|----------|---------|--------------|-----------|
| 1 | Brand | Brand name spelling | SectorCare (one word) | ✓ |
| 2 | Brand | NDIS treatment | Text only, no badge | ✓ |
| 3 | Brand | Phone number | 02 9172 5607 | ✓ |
| 4 | Brand | Email address | sales@sectorcare.com.au | ✓ |
| 5 | Brand | Business hours | Mon – Fri, 9am – 5pm AEST | ✓ |
| 6 | Brand | Website URL | https://sectorcare.com.au/ | ✓ |
| 7 | Brand | Privacy URL | https://www.sectorcare.com.au/privacy | ✓ |
| 8 | Color | Brand blue | #3A9AD9 | ✓ |
| 9 | Color | Dark navy (headings) | #111e2d | ✓ |
| 10 | Color | Deep black (footer) | #06141b | ✓ |
| 11 | Color | Navy 2 (icon circles) | #233543 | ✓ |
| 12 | Color | Gray text | #475666 | ✓ |
| 13 | Color | Muted / light text | #96a3ac | ✓ |
| 14 | Color | Light background | #f5f7fa | ✓ |
| 15 | Color | Border | #e4e8ed | ✓ |
| 16 | Color | White (card bg) | #FFFFFF | ✓ |
| 17 | Typography | Primary font | Opposans → SF Pro Display → system | ✓ |
| 18 | Typography | Monospace font | Courier New (promo codes only) | ✓ |
| 19 | Typography | H1 desktop size | 34px, weight 700 | ✓ |
| 20 | Typography | H1 mobile size | 26px via .hh @media | ✓ |
| 21 | Typography | H1 two-color rule | Line 1 = #111e2d, Line 2 = #3A9AD9 span | ✓ |
| 22 | Typography | Body copy | 13px, #475666, line-height 1.72 | ✓ |
| 23 | Typography | CTA button text | 11px, 700, uppercase, letter-spacing 1.5px | ✓ |
| 24 | Typography | Section eyebrow | 9px, #3A9AD9, letter-spacing 2.5px, uppercase | ✓ |
| 25 | Typography | Feature tile title | 10px, weight 700, #111e2d | ✓ |
| 26 | Typography | Feature tile body | 9px, #475666, line-height 1.6 | ✓ |
| 27 | Typography | Product name | 16px, weight 700, #111e2d | ✓ |
| 28 | Typography | Product price | 20px, weight 700, #3A9AD9 | ✓ |
| 29 | Typography | Promo code | 22px, weight 700, #FFFFFF, letter-spacing 6px | ✓ |
| 30 | Typography | Footer legal | 9px, #475666, line-height 1.7 | ✓ |
| 31 | Typography | Footer links | 9px, #96a3ac, underline | ✓ |
| 32 | Typography | NDIS contact line | 9px, weight 700, #3A9AD9, uppercase | ✓ |
| 33 | Layout | Email max-width | 600px | ✓ |
| 34 | Layout | Outer bg + padding | #f5f7fa, 20px top / 28px bottom | ✓ |
| 35 | Layout | Card shadow | box-shadow 0 2px 16px rgba(0,0,0,0.10) | ✓ |
| 36 | Layout | Content padding | 40px horizontal desktop | ✓ |
| 37 | Layout | Section dividers | 1px solid #e4e8ed between sections | ✓ |
| 38 | Layout | Header accent stripe | 3px solid #3A9AD9 border-bottom | ✓ |
| 39 | Responsive | Mobile breakpoint | max-width 600px | ✓ |
| 40 | Responsive | .ew class | width 100% | ✓ |
| 41 | Responsive | .mp class | padding left/right 20px | ✓ |
| 42 | Responsive | .pc class | Product card stack on mobile | ✓ |
| 43 | Responsive | .cc class | Contact column stack on mobile | ✓ |
| 44 | Responsive | .hh class | H1 → 26px on mobile | ✓ |
| 45 | Section | 1. Utility bar | {% web_view %} link, #f5f7fa bg | ✓ |
| 46 | Section | 2. Header | Logo 36px height, subtitle 9px blue | ✓ |
| 47 | Section | 3. Hero image | Full-width, two image URLs, linked | ✓ |
| 48 | Section | 4. Hero text + CTA | H1 two-color, body 13px, blue button | ✓ |
| 49 | Section | 5. Body text | Optional warm intro, NDIS mention | ✓ |
| 50 | Section | 6A. Feature grid | 2×3 tiles, icons, 16/18px icon size | ✓ |
| 51 | Section | 6B. Static products | Image/name/desc/CTA per product | ✓ |
| 52 | Section | 6C. Category cards | 3-col, circle icons, SHOP NOW buttons | ✓ |
| 53 | Section | 6D. Klaviyo cart card | event.item_* variables | ✓ |
| 54 | Section | 6E. Klaviyo browse card | event.Product* variables | ✓ |
| 55 | Section | 6F. Klaviyo related | Conditional, 3 products, {% if %} wrap | ✓ |
| 56 | Section | 6G. Promo code box | #06141b bg, dashed border, monospace | ✓ |
| 57 | Section | 7. Contact | NDIS line + phone/email 2-col | ✓ |
| 58 | Section | 8. Footer | Dark bg, org vars, unsubscribe, privacy | ✓ |
| 59 | Assets | Logo URL | cloudfront.net/…/47898cac-…png | ✓ |
| 60 | Assets | Hero image 1 (HI1) | cloudfront.net/…/08ffb312-…jpeg | ✓ |
| 61 | Assets | Hero image 2 (HI2) | cloudfront.net/…/3559e029-…jpeg | ✓ |
| 62 | Assets | Airflex 1 image + URL | cloudfront + sectorcare.com.au/… | ✓ |
| 63 | Assets | Infinity Comfort image + URL | cloudfront + sectorcare.com.au/… | ✓ |
| 64 | Assets | Infinity Feather image + URL | cloudfront + sectorcare.com.au/… | ✓ |
| 65 | Klaviyo | person.first_name | With \|default:"there" fallback | ✓ |
| 66 | Klaviyo | event.item_* | 4 cart variables (name/image/price/url) | ✓ |
| 67 | Klaviyo | event.Product* | 4 browse variables | ✓ |
| 68 | Klaviyo | event.related_product_N_* | Conditional 3-product block | ✓ |
| 69 | Klaviyo | organization.* | name + full_address | ✓ |
| 70 | Klaviyo | {% web_view %} | Utility bar link | ✓ |
| 71 | Klaviyo | {% unsubscribe %} | Footer link | ✓ |
| 72 | Klaviyo | Python f-string escaping | {{ }} → {{{{ }}}}, {% %} → {{% %}} | ✓ |
| 73 | Technical | DOCTYPE + xmlns | Required for Outlook | ✓ |
| 74 | Technical | Outlook reset styles | #outlook a, mso-table-lspace/rspace | ✓ |
| 75 | Technical | Image display:block | Prevents bottom gap | ✓ |
| 76 | Technical | Hero image width attr | width="600" for Outlook | ✓ |
| 77 | Technical | Button as table | Background renders in Outlook | ✓ |
| 78 | Technical | Phone href format | tel:0291725607 (no dashes/spaces) | ✓ |
| 79 | Technical | Phone icon encoding | &#9742;&#xFE0E; (text-presentation) | ✓ |
| 80 | Technical | All links target | target="_blank" | ✓ |

---

*All 80 elements verified present in the prompt above.*
