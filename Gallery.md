---
layout: single
title: "Gallery"
permalink: /Gallery/
author_profile: true
---

<div class="gallery-slideshow" style="max-width:700px;margin:2rem auto;">
  <div style="position:relative;border-radius:8px;overflow:hidden;background:#f4f4f4;">
    <img id="slide-img" src="" alt="" style="width:100%;display:block;">
    <button id="prev-btn" aria-label="Previous photo"
      style="position:absolute;left:10px;top:50%;transform:translateY(-50%);
             width:38px;height:38px;border-radius:50%;border:none;
             background:rgba(0,0,0,0.55);color:#fff;font-size:20px;cursor:pointer;">‹</button>
    <button id="next-btn" aria-label="Next photo"
      style="position:absolute;right:10px;top:50%;transform:translateY(-50%);
             width:38px;height:38px;border-radius:50%;border:none;
             background:rgba(0,0,0,0.55);color:#fff;font-size:20px;cursor:pointer;">›</button>
  </div>
  <p id="slide-caption" style="text-align:center;font-size:0.95rem;color:#555;margin:0.75rem 0 0.5rem;"></p>
  <div id="slide-dots" style="display:flex;gap:6px;justify-content:center;"></div>
</div>

<script>
(function() {
  const slides = [
    { src: "/assets/images/gallery/Getting ready for first ever flight campaign.JPG", caption: "Getting ready for my first every flight campaign with NASA SARP! (June, 2025)" },
    { src: "/assets/images/gallery/Working with WAS cans pt2.JPG", caption: "Collecting Whole Air Samples (WAS) above the Great Dismal Swamp (June, 2025)" },
    { src: "/assets/images/gallery/Flight Campaign and Me.JPG", caption: "Me in front of the Dynamic Aviation B-200 Aircraft! (June, 2025)" },
    { src: "/assets/images/gallery/COMETLab.JPG", caption: "Working on building air quality sensors for 3D-PAWS at the NCAR COMET lab (featuring Emily Nigro and William Nicewonger) (June, 2026)" }
  ];

  let i = 0;
  const img = document.getElementById('slide-img');
  const caption = document.getElementById('slide-caption');
  const dots = document.getElementById('slide-dots');

  slides.forEach((s, idx) => {
    const dot = document.createElement('button');
    dot.setAttribute('aria-label', 'Go to photo ' + (idx + 1));
    dot.style.cssText = 'width:8px;height:8px;border-radius:50%;border:none;padding:0;cursor:pointer;background:#ccc;';
    dot.onclick = () => { i = idx; render(); };
    dots.appendChild(dot);
  });

  function render() {
    img.src = slides[i].src;
    img.alt = slides[i].caption;
    caption.textContent = slides[i].caption;
    [...dots.children].forEach((d, idx) => {
      d.style.background = idx === i ? '#333' : '#ccc';
    });
  }

  document.getElementById('prev-btn').onclick = () => { i = (i - 1 + slides.length) % slides.length; render(); };
  document.getElementById('next-btn').onclick = () => { i = (i + 1) % slides.length; render(); };

  render();
})();
</script>
