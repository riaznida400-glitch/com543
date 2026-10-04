ARBOR COMPUTERS - STATIC SITE (v3, with photography)

FILES
  index.html, dental-it.html, business-it.html, repair.html, contact.html
  robots.txt, sitemap.xml
  vercel.json              Cache headers for /assets (Vercel only; ignored elsewhere)
  assets/
    css/site-images.css    All photo, hero-image, card and video styling
    images/                Optimized photos (.webp at 3 sizes + .jpg fallback), og-image.jpg
      illustrations/       Original SVG illustrations (pc.svg is still used on the repair page)
    video/                 hero.mp4 + hero-poster.jpg (home page hero)

WHERE EACH PHOTO IS USED
  cybersecurity-laptop         Home card (Business IT) + Business IT "Cybersecurity and recovery"
  server-room-technician       Business IT page hero
  it-team-onsite               Business IT "Managed IT for teams" + Repair "PC and Mac repair"
  dental-imaging-workstations  Home card (Dental IT) + Dental IT "Software, imaging and backup" + social share image
  dental-operatory             Dental IT page hero
  dental-front-desk-support    Home "Built around your front desk and chairside" section
  repair-counter-consultation  Home card (Repair)
  repair-counter-hero          Repair page hero (same photo, mirrored and cropped wide)

DEPLOY (GitHub + Vercel)
  1. Unzip and push the folder contents to the repo root.
  2. Import the repo in Vercel (Framework preset: Other, no build command, output = root).
  3. Check every page on desktop and phone.

BEFORE GOING LIVE
  - CONTACT FORM IS A DEMO. It validates but does not send. Connect it to a form
    service (Formspree, Web3Forms, Netlify Forms) or the current Arbor form.
  - Confirm "walk in, no appointment" is current policy and add business hours.
  - These photos are generic stock-style images. Swap in real team/shop/office photos
    when available (keep the same filenames, or update the <picture> tags).
  - Add Google Analytics / Search Console verification if used.
  - Fonts load from Google Fonts. Self-host them if privacy rules require.

ADDING MORE IMAGES
  1. Export widths (e.g. 640 / 1024 / 1440 px) as .webp plus one .jpg fallback into assets/images/.
  2. Use this pattern (width/height = the .jpg size, stops layout shift):
     <picture>
       <source type="image/webp" srcset="assets/images/NAME-640.webp 640w, assets/images/NAME-1024.webp 1024w, assets/images/NAME-1440.webp 1440w" sizes="(max-width:900px) 100vw, 560px">
       <img src="assets/images/NAME.jpg" width="1440" height="810" alt="Describe the photo" loading="lazy" decoding="async">
     </picture>
  3. Inside a "split" section the photo is framed automatically.
     Page hero: add class "photo" to <header class="pagehero"> and put the <picture> first.
     Focal point: style="--pos:70% 40%" (desktop) and "--pos-m:65% 50%" (mobile) on the header.

ADDING VIDEOS
  Put files in assets/video/ (MP4/H.264, under ~5 MB for background loops, plus a poster .jpg).
  Background loop:  <video autoplay muted loop playsinline preload="metadata" poster="assets/video/NAME.jpg" aria-hidden="true"><source src="assets/video/NAME.mp4" type="video/mp4"></video>
  Content video:    <figure class="media media-video"><video controls preload="metadata" poster="assets/video/NAME.jpg"><source src="assets/video/NAME.mp4" type="video/mp4"></video></figure>
  For a full-width video hero, replace the <picture> in a "pagehero photo" header with a <video> as above.
