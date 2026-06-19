<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Joshua Arch</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Mono:wght@400;500&family=Syne:wght@600;700;800&display=swap" rel="stylesheet">
<style>
:root {
  --bg:#0f0f13; --surface:#1a1a22; --surface2:#22222e; --border:#2e2e3e;
  --accent:#00e5a0; --accent2:#f0c040;
  --text:#e8e8f0; --muted:#6b6b80; --radius:12px;
}
*{box-sizing:border-box;margin:0;padding:0;}
html{scroll-behavior:smooth;}
body{background:var(--bg);color:var(--text);font-family:'DM Mono',monospace;min-height:100vh;}
a{color:inherit;text-decoration:none;}

/* NAV */
nav{
  position:sticky;top:0;z-index:100;
  background:rgba(15,15,19,.93);backdrop-filter:blur(12px);
  border-bottom:1px solid var(--border);
  display:flex;align-items:center;justify-content:space-between;
  padding:14px 28px;
}
.nav-logo{font-family:'Syne',sans-serif;font-size:15px;font-weight:800;color:var(--accent);}
.nav-links{display:flex;gap:4px;}
.nav-link{
  padding:6px 14px;border-radius:20px;font-size:11px;letter-spacing:.5px;
  color:var(--muted);transition:all .15s;border:1px solid transparent;
}
.nav-link:hover{color:var(--text);border-color:var(--border);background:var(--surface);}
.nav-link.cta{background:var(--accent);color:#000;border-color:var(--accent);}
.nav-link.cta:hover{opacity:.85;}

/* HERO */
#hero{
  padding:80px 28px 64px;
  border-bottom:1px solid var(--border);
}
.hero-name{
  font-family:'Syne',sans-serif;
  font-size:clamp(40px,8vw,80px);
  font-weight:800;line-height:.95;letter-spacing:-2px;
  color:var(--text);margin-bottom:20px;
}
.hero-meta{
  display:flex;flex-wrap:wrap;gap:10px;align-items:center;
  font-size:12px;color:var(--muted);
}
.hero-meta span{display:flex;align-items:center;gap:6px;}
.hero-meta span::before{content:'';display:inline-block;width:4px;height:4px;border-radius:50%;background:var(--accent);}
.hero-meta span:first-child::before{display:none;}

/* SECTION */
.section{padding:60px 28px;border-bottom:1px solid var(--border);}
.section-label{
  font-size:10px;letter-spacing:2px;text-transform:uppercase;color:var(--accent);
  margin-bottom:32px;display:flex;align-items:center;gap:10px;
}
.section-label::before{content:'';display:inline-block;width:24px;height:1px;background:var(--accent);}

/* GALLERY */
.gallery-toolbar{display:flex;align-items:center;gap:8px;flex-wrap:wrap;margin-bottom:16px;}
.gallery-controls{
  display:flex;align-items:center;gap:8px;flex-wrap:wrap;
}
.gallery-toggle-group{
  display:flex;align-items:center;gap:8px;flex-wrap:wrap;
}
.filter-btn{
  padding:8px 16px;border-radius:999px;border:1px solid var(--border);
  background:var(--surface);color:var(--muted);font-family:'DM Mono',monospace;
  font-size:11px;cursor:pointer;transition:all .15s;white-space:nowrap;
}
.filter-btn.active{
  background:var(--accent);color:#000;border-color:var(--accent);
  box-shadow:0 0 0 1px rgba(0,229,160,.18);
}
.gallery-status{
  margin-left:auto;font-size:11px;color:var(--muted);
  background:var(--surface);border:1px solid var(--border);
  padding:4px 12px;border-radius:20px;
}
.gallery-status.ok{color:var(--accent);border-color:rgba(0,229,160,.3);}
.gallery-status.err{color:#ff5f6d;}
.gallery-grid{
  display:grid;
  grid-template-columns:repeat(auto-fill,minmax(220px,1fr));
  gap:12px;
}
.gallery-placeholder,.gallery-spinner{
  grid-column:1/-1;padding:48px;text-align:center;
  color:var(--muted);font-size:12px;line-height:1.8;
  background:var(--surface);border:1px solid var(--border);border-radius:var(--radius);
}
.gallery-spinner{display:flex;flex-direction:column;align-items:center;gap:12px;}
.spinner{width:26px;height:26px;border:2px solid var(--border);border-top-color:var(--accent);border-radius:50%;animation:spin .7s linear infinite;}
@keyframes spin{to{transform:rotate(360deg);}}
.photo-card{
  aspect-ratio:1;border-radius:10px;overflow:hidden;
  background:var(--surface2);border:1px solid var(--border);
  cursor:pointer;transition:border-color .15s,transform .15s;position:relative;
}
.photo-card:hover{transform:translateY(-1px);border-color:var(--accent);}
.photo-card.active{border-color:var(--accent);box-shadow:inset 0 0 0 1px rgba(0,229,160,.15);}
.photo-card img{width:100%;height:100%;object-fit:cover;display:block;}
.photo-card .ph-label{
  position:absolute;top:8px;left:8px;font-size:9px;letter-spacing:.5px;
  padding:3px 8px;border-radius:10px;background:rgba(0,0,0,.65);color:#fff;
}
.photo-card .ph-placeholder{
  position:absolute;left:0;right:0;bottom:0;
  padding:10px 10px 12px;
  background:linear-gradient(to top, rgba(0,0,0,.78), rgba(0,0,0,.18));
  color:#fff;font-size:10px;letter-spacing:.6px;text-transform:uppercase;
}

/* RESUME */
.resume-grid{display:grid;grid-template-columns:1fr 1fr;gap:16px;}
.res-card{
  background:var(--surface);border:1px solid var(--border);
  border-radius:var(--radius);padding:24px;
}
.res-heading{
  font-size:9px;letter-spacing:2px;text-transform:uppercase;
  color:var(--accent2);border-bottom:1px solid var(--border);
  padding-bottom:10px;margin-bottom:20px;
}
.res-entry{margin-bottom:24px;}
.res-entry:last-child{margin-bottom:0;}
.res-row{display:flex;justify-content:space-between;align-items:baseline;gap:8px;margin-bottom:2px;}
.res-title{font-family:'Syne',sans-serif;font-size:13px;font-weight:700;}
.res-date{font-size:10px;color:var(--muted);white-space:nowrap;}
.res-role{font-size:11px;color:var(--accent);margin-bottom:2px;}
.res-loc{font-size:10px;color:var(--muted);margin-bottom:10px;}
.res-bullets{list-style:none;display:flex;flex-direction:column;gap:5px;}
.res-bullets li{font-size:11px;color:var(--muted);line-height:1.6;padding-left:14px;position:relative;}
.res-bullets li::before{content:'›';position:absolute;left:0;color:var(--accent);}
.res-bullets li.sub{padding-left:28px;font-size:10px;}
.res-bullets li.sub::before{content:'○';font-size:8px;top:2px;}
.skill-group{margin-bottom:16px;}
.skill-group:last-child{margin-bottom:0;}
.skill-group-label{font-size:9px;letter-spacing:1.5px;text-transform:uppercase;color:var(--muted);margin-bottom:8px;}
.skill-chips{display:flex;flex-wrap:wrap;gap:6px;}
.skill-chip{
  font-size:11px;padding:4px 10px;border-radius:6px;
  background:var(--surface2);border:1px solid var(--border);color:var(--text);
}
.res-download{
  margin-top:20px;display:flex;align-items:center;justify-content:space-between;
  padding:14px 16px;background:var(--surface2);border:1px solid var(--border);
  border-radius:var(--radius);gap:12px;
}
.res-download-label{font-size:11px;color:var(--muted);}
.dl-btn{
  padding:8px 16px;border-radius:8px;background:var(--surface);
  border:1px solid var(--border);font-family:'Syne',sans-serif;
  font-size:11px;font-weight:700;color:var(--text);cursor:pointer;
  transition:border-color .15s;white-space:nowrap;
}
.dl-btn:hover{border-color:var(--accent);color:var(--accent);}

/* CONTACT */
#contact{padding:60px 28px 80px;border-bottom:none;}
.contact-links{display:flex;flex-wrap:wrap;gap:10px;margin-top:24px;}
.contact-pill{
  display:inline-flex;align-items:center;gap:8px;
  padding:10px 18px;border-radius:var(--radius);
  background:var(--surface);border:1px solid var(--border);
  font-size:12px;color:var(--muted);transition:border-color .15s,color .15s;
}
.contact-pill:hover{border-color:var(--accent);color:var(--text);}

/* LIGHTBOX */
.lightbox{
  display:none;position:fixed;inset:0;background:rgba(8,8,12,.95);
  z-index:300;align-items:center;justify-content:center;padding:48px 20px;
}
.lightbox.open{display:flex;}
.lightbox img{max-width:100%;max-height:100%;object-fit:contain;border-radius:8px;}
.lb-close{
  position:absolute;top:14px;right:16px;width:40px;height:40px;border-radius:50%;
  background:var(--surface);border:1px solid var(--border);color:var(--text);
  font-size:20px;cursor:pointer;display:flex;align-items:center;justify-content:center;
}
.lb-nav{
  position:absolute;top:50%;transform:translateY(-50%);
  width:44px;height:44px;border-radius:50%;background:var(--surface);
  border:1px solid var(--border);color:var(--accent);font-size:22px;
  cursor:pointer;display:flex;align-items:center;justify-content:center;
}
.lb-nav.prev{left:10px;}
.lb-nav.next{right:10px;}
.lb-cap{
  position:absolute;bottom:14px;left:50%;transform:translateX(-50%);
  font-size:11px;color:var(--muted);background:var(--surface);
  border:1px solid var(--border);padding:6px 16px;border-radius:20px;white-space:nowrap;
}

@media(max-width:640px){
  nav{padding:12px 16px;}
  .nav-link{padding:6px 10px;font-size:10px;}
  #hero,.section,#contact{padding-left:16px;padding-right:16px;}
  .resume-grid{grid-template-columns:1fr;}
  .gallery-grid{grid-template-columns:repeat(auto-fill,minmax(140px,1fr));}
}
</style>
</head>
<body>

<nav>
  <div class="nav-logo">Joshua Arch</div>
  <div class="nav-links">
    <a class="nav-link" href="#gallery">Work</a>
    <a class="nav-link" href="#resume">Resume</a>
    <a class="nav-link cta" href="#contact">Contact</a>
  </div>
</nav>

<!-- HERO -->
<section id="hero">
  <h1 class="hero-name">Joshua<br>Arch</h1>
  <div class="hero-meta">
    <span>Sous Chef</span>
    <span>Mrs. Fred's — Fredonia, NY</span>
    <span>Nov. 2024 – Present</span>
  </div>
</section>

<!-- RESUME -->
<section class="section" id="resume">
  <div class="section-label">Resume</div>
  <div class="resume-grid">

    <div class="res-card">
      <div class="res-heading">Work History</div>

      <div class="res-entry">
        <div class="res-row">
          <span class="res-title">Mrs. Fred's</span>
          <span class="res-date">Nov. 2024 – Present</span>
        </div>
        <div class="res-role">Sous Chef</div>
        <div class="res-loc">Fredonia, NY</div>
        <ul class="res-bullets">
          <li>Led a team of 8 staff members during busy shifts, overseeing all kitchen operations and ensuring high-quality dishes.</li>
          <li class="sub">Primarily worked sauté and expo on the line.</li>
          <li>Developed staple menu items and constant daily specials, creatively utilizing leftover ingredients.</li>
          <li class="sub">Conducted detailed cost analysis for dishes and ingredients, optimizing menu pricing and food purchasing.</li>
          <li class="sub">Streamlined kitchen workflows by optimizing food preparation, cleaning, and prep routines.</li>
        </ul>
      </div>

      <div class="res-entry">
        <div class="res-row">
          <span class="res-title">The White Inn</span>
          <span class="res-date">Oct. 2025 – Dec. 2025</span>
        </div>
        <div class="res-role">Pastry Chef</div>
        <div class="res-loc">Fredonia, NY</div>
        <ul class="res-bullets">
          <li>Specialized in baking dinner rolls, brioche rolls, focaccia, fresh pastas and desserts.</li>
          <li class="sub">Led cold side during dinners.</li>
          <li>Left to pursue line working experience.</li>
        </ul>
      </div>

      <div class="res-heading" style="margin-top:24px;">Education</div>

      <div class="res-entry">
        <div class="res-row">
          <span class="res-title">Monroe CC &amp; RIT</span>
          <span class="res-date">Jul. 2023</span>
        </div>
        <div class="res-role">Applied Science, Mechanical Engineering</div>
        <div class="res-loc">Rochester, NY</div>
        <ul class="res-bullets">
          <li>Graduated top 20% of class.</li>
          <li>Led a team from the RIT Multidisciplinary Robotics Club (MDRC).</li>
          <li class="sub">Created a brainwave controlled power wheels car.</li>
          <li>RIT Launch Initiative.</li>
          <li class="sub">Designed, digitally simulated and manufactured my own rocket.</li>
        </ul>
      </div>

      <div class="res-download">
        <span class="res-download-label">Full resume available to download</span>
        <!-- Update href to point to your hosted .docx -->
        <a class="dl-btn" href="Joshua_Arch_Resume.docx" download>↓ Download</a>
      </div>
    </div>

    <div class="res-card">
      <div class="res-heading">Skills</div>
      <div class="skill-group">
        <div class="skill-group-label">Skills</div>
        <div class="skill-chips">
          <span class="skill-chip">Project Management</span>
          <span class="skill-chip">Technical Problem Solving</span>
          <span class="skill-chip">Production Planning</span>
          <span class="skill-chip">Service Execution</span>
          <span class="skill-chip">Quality Control</span>
          <span class="skill-chip">Adaptability</span>
          <span class="skill-chip">Willingness to Learn</span>
        </div>
      </div>
      <div class="skill-group">
        <div class="skill-group-label">Technologies</div>
        <div class="skill-chips">
          <span class="skill-chip">AutoCAD</span>
          <span class="skill-chip">Onshape</span>
          <span class="skill-chip">Solidworks</span>
          <span class="skill-chip">Python</span>
          <span class="skill-chip">C#</span>
          <span class="skill-chip">HTML</span>
        </div>
      </div>
      <div class="skill-group">
        <div class="skill-group-label">Interests</div>
        <div class="skill-chips">
          <span class="skill-chip">Cooking &amp; Baking</span>
          <span class="skill-chip">DIY Home Projects</span>
          <span class="skill-chip">3D Printing &amp; Modeling</span>
          <span class="skill-chip">Gaming</span>
          <span class="skill-chip">Snowboarding</span>
          <span class="skill-chip">Programming</span>
        </div>
      </div>
    </div>

  </div>
</section>

<!-- GALLERY -->
<section class="section" id="gallery">
  <div class="section-label">Food Work</div>

  <script>
  const PHOTO_ITEMS = [
    { url: "https://raw.githubusercontent.com/JozNski/Resume/main/Pictures-20260618T223033Z-3-001/Pictures/FB_IMG_1781133208534.jpg", placeholder: "Desserts" },
    { url: "https://raw.githubusercontent.com/JozNski/Resume/main/Pictures-20260618T223033Z-3-001/Pictures/FB_IMG_1781133217471.jpg", placeholder: "Desserts" },
    { url: "https://raw.githubusercontent.com/JozNski/Resume/main/Pictures-20260618T223033Z-3-001/Pictures/FB_IMG_1781133237950.jpg", placeholder: "Desserts" },
    { url: "https://raw.githubusercontent.com/JozNski/Resume/main/Pictures-20260618T223033Z-3-001/Pictures/FB_IMG_1781133265382.jpg", placeholder: "Desserts" },
    { url: "https://raw.githubusercontent.com/JozNski/Resume/main/Pictures-20260618T223033Z-3-001/Pictures/FB_IMG_1781133301607.jpg", placeholder: "Fresh Baked" },
    { url: "https://raw.githubusercontent.com/JozNski/Resume/main/Pictures-20260618T223033Z-3-001/Pictures/FB_IMG_1781133338521.jpg", placeholder: "Fresh Baked" },
    { url: "https://raw.githubusercontent.com/JozNski/Resume/main/Pictures-20260618T223033Z-3-001/Pictures/FB_IMG_1781133360489.jpg", placeholder: "Fresh Baked" },
    { url: "https://raw.githubusercontent.com/JozNski/Resume/main/Pictures-20260618T223033Z-3-001/Pictures/FB_IMG_1781133401891.jpg", placeholder: "Fresh Baked" },
    { url: "https://raw.githubusercontent.com/JozNski/Resume/main/Pictures-20260618T223033Z-3-001/Pictures/FB_IMG_1781133426159.jpg", placeholder: "Dinner Specials" },
    { url: "https://raw.githubusercontent.com/JozNski/Resume/main/Pictures-20260618T223033Z-3-001/Pictures/FB_IMG_1781133674952.jpg", placeholder: "Dinner Specials" },
    { url: "https://raw.githubusercontent.com/JozNski/Resume/main/Pictures-20260618T223033Z-3-001/Pictures/FB_IMG_1781133751161.jpg", placeholder: "Dinner Specials" },
    { url: "https://raw.githubusercontent.com/JozNski/Resume/main/Pictures-20260618T223033Z-3-001/Pictures/FB_IMG_1781133836928.jpg", placeholder: "Dinner Specials" },
    { url: "https://raw.githubusercontent.com/JozNski/Resume/main/Pictures-20260618T223033Z-3-001/Pictures/FB_IMG_1781133847662.jpg", placeholder: "Desserts" },
    { url: "https://raw.githubusercontent.com/JozNski/Resume/main/Pictures-20260618T223033Z-3-001/Pictures/IMG_20260610_182155.jpg", placeholder: "Fresh Baked" },
    { url: "https://raw.githubusercontent.com/JozNski/Resume/main/Pictures-20260618T223033Z-3-001/Pictures/IMG_20260610_185704.jpg", placeholder: "Fresh Baked" },
    { url: "https://raw.githubusercontent.com/JozNski/Resume/main/Pictures-20260618T223033Z-3-001/Pictures/IMG_20260610_185808.jpg", placeholder: "Dinner Specials" },
    { url: "https://raw.githubusercontent.com/JozNski/Resume/main/Pictures-20260618T223033Z-3-001/Pictures/IMG_20260610_190212.jpg", placeholder: "Dinner Specials" },
    { url: "https://raw.githubusercontent.com/JozNski/Resume/main/Pictures-20260618T223033Z-3-001/Pictures/IMG_20260610_190302.jpg", placeholder: "Desserts" },
    { url: "https://raw.githubusercontent.com/JozNski/Resume/main/Pictures-20260618T223033Z-3-001/Pictures/IMG_20260610_190339.jpg", placeholder: "Dinner Specials" },
    { url: "https://raw.githubusercontent.com/JozNski/Resume/main/Pictures-20260618T223033Z-3-001/Pictures/IMG_20260610_190341.jpg", placeholder: "Fresh Baked" },
    { url: "https://raw.githubusercontent.com/JozNski/Resume/main/Pictures-20260618T223033Z-3-001/Pictures/IMG_20260610_190403.jpg", placeholder: "Desserts" },
    { url: "https://raw.githubusercontent.com/JozNski/Resume/main/Pictures-20260618T223033Z-3-001/Pictures/received_676585687663276.jpeg", placeholder: "Dinner Specials" },
    { url: "https://raw.githubusercontent.com/JozNski/Resume/main/Pictures-20260618T223033Z-3-001/Pictures/received_971636300609863.jpeg", placeholder: "Fresh Baked" }
  ];
  </script>

  <div class="gallery-toolbar">
    <div class="gallery-controls">
      <div class="gallery-toggle-group">
        <button class="filter-btn active" id="galleryToggleBtn">Hide Photos</button>
        <button class="filter-btn active" data-category-toggle="Desserts">Desserts</button>
        <button class="filter-btn active" data-category-toggle="Fresh Baked">Fresh Baked</button>
        <button class="filter-btn active" data-category-toggle="Dinner Specials">Dinner Specials</button>
      </div>
    </div>
    <div class="gallery-status" id="galleryStatus">⟳ Loading...</div>
  </div>
  <div class="gallery-grid" id="galleryGrid">
    <div class="gallery-spinner"><div class="spinner"></div>Loading...</div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="section-label">Contact</div>
  <div class="contact-links">
    <a class="contact-pill" href="mailto:7165234958jta@gmail.com">✉ 7165234958jta@gmail.com</a>
    <a class="contact-pill" href="tel:7165234958">☏ (716) 523-4958</a>
    <span class="contact-pill">📍 Dunkirk, NY 14048</span>
  </div>
</section>

<script>
// ── GALLERY ──
const categoryState = {
  all: true,
  "Desserts": true,
  "Fresh Baked": true,
  "Dinner Specials": true
};

function updateGalleryButton(){
  const btn = document.getElementById("galleryToggleBtn");
  const grid = document.getElementById("galleryGrid");
  if (!btn) return;
  btn.classList.toggle("active", categoryState.all && grid.style.display !== "none");
  btn.textContent = categoryState.all ? "Hide Photos" : "Show Photos";

  document.querySelectorAll('[data-category-toggle]').forEach(button => {
    const category = button.dataset.categoryToggle;
    button.classList.toggle("active", categoryState[category]);
    button.textContent = categoryState[category] ? category : `${category} (Hidden)`;
  });
}

function toggleGalleryGrid(){
  categoryState.all = !categoryState.all;
  if (!categoryState.all) {
    categoryState["Desserts"] = false;
    categoryState["Fresh Baked"] = false;
    categoryState["Dinner Specials"] = false;
  } else {
    categoryState["Desserts"] = true;
    categoryState["Fresh Baked"] = true;
    categoryState["Dinner Specials"] = true;
  }
  updateGalleryButton();
  loadGallery();
}

function toggleCategory(category){
  categoryState[category] = !categoryState[category];
  categoryState.all = ["Desserts", "Fresh Baked", "Dinner Specials"].every(c => categoryState[c]);
  updateGalleryButton();
  loadGallery();
}

function loadGallery(){
  const grid = document.getElementById("galleryGrid");
  const status = document.getElementById("galleryStatus");

  if(!PHOTO_ITEMS || !PHOTO_ITEMS.length){
    grid.innerHTML = `<div class="gallery-placeholder">No photos yet.<br>Add items to the PHOTO_ITEMS array.</div>`;
    status.textContent = "No photos";
    status.className = "gallery-status err";
    return;
  }

  if (!categoryState.all && !["Desserts", "Fresh Baked", "Dinner Specials"].some(c => categoryState[c])) {
    grid.innerHTML = "";
    status.textContent = "All photos hidden";
    status.className = "gallery-status err";
    return;
  }

  status.textContent = "⟳ Loading...";
  status.className = "gallery-status";
  grid.innerHTML = `<div class="gallery-spinner"><div class="spinner"></div>Loading photos...</div>`;

  setTimeout(() => {
    const visiblePhotos = PHOTO_ITEMS.filter(photo => categoryState.all || categoryState[photo.placeholder]);
    grid.innerHTML = "";

    if (!visiblePhotos.length) {
      grid.innerHTML = `<div class="gallery-placeholder">No photos selected.<br>Use the toggles above.</div>`;
      status.textContent = "No visible photos";
      status.className = "gallery-status err";
      return;
    }

    visiblePhotos.forEach((photo, index) => {
      const card = document.createElement("div");
      card.className = "photo-card";
      card.innerHTML = `
        <img src="${photo.url}" alt="Photo ${index + 1}" loading="lazy">
        <div class="ph-label">Photo ${index + 1}</div>
        <div class="ph-placeholder">${photo.placeholder || "Gallery"}</div>
      `;
      grid.appendChild(card);
    });

    status.textContent = `${visiblePhotos.length} photo${visiblePhotos.length === 1 ? "" : "s"}`;
    status.className = "gallery-status ok";
    updateGalleryButton();
  }, 200);
}

document.getElementById("galleryToggleBtn").addEventListener("click", toggleGalleryGrid);
document.querySelectorAll('[data-category-toggle]').forEach(button => {
  button.addEventListener('click', () => toggleCategory(button.dataset.categoryToggle));
});
updateGalleryButton();
loadGallery();
</script>
</body>
</html>
