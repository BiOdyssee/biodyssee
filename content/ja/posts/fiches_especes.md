---
title: "種のプロフィール"
date: 2025-08-14T14:00:00+01:00
draft: false
cover: "/images/galerie.png"
hideCoverInPost: true 
categories: ["galerie"]
author: lucie
lang: "ja"
---

<!--more-->

<div class="gallery">
  {{< gallery folder="/images/galerie" >}}
</div>

<style>
.gallery-lightbox {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 5px;
  margin-top: 20px;
}


.gallery-thumb {
  margin: 1px;
  width: 100%;
  height: 320px;
  object-fit: cover;
  border-radius: 6px;
}

.gallery-thumb:hover {
  transform: scale(1.05);
}

/* Lightbox simple */
.gallery-link {
  display: inline-block;
}

/* Lightbox modal */
body.modal-open {
  overflow: hidden;
}

#lightbox-modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.8);
  display: none;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

#lightbox-modal img {
  max-width: 90%;
  max-height: 90%;
  border-radius: 8px;
}
</style>

<script>
document.querySelectorAll('.gallery-link').forEach(link => {
  link.addEventListener('click', function(e) {
    e.preventDefault(); // empêche la navigation
    
    let modal = document.getElementById('lightbox-modal');
    if(!modal) {
      modal = document.createElement('div');
      modal.id = 'lightbox-modal';
      modal.style.cssText = `
        position: fixed; top:0; left:0; width:100%; height:100%;
        background: rgba(0,0,0,0.8); display:flex;
        justify-content:center; align-items:center; z-index:1000;
      `;
      document.body.appendChild(modal);
      modal.addEventListener('click', () => {
        modal.style.display = 'none';
        document.body.classList.remove('modal-open');
      });
    }

    let img = document.createElement('img');
    img.src = this.href;
    img.style.cssText = 'max-width:90%; max-height:90%; border-radius:8px;';
    
    modal.innerHTML = '';
    modal.appendChild(img);
    modal.style.display = 'flex';
    document.body.classList.add('modal-open');
  });
});
</script>
