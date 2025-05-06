---
title: "🗺️ 日本の旅を一緒に辿ってみましょう！"
date: 2025-04-14
layout: "map"
draft: false 
cover: "/images/carte_drapeau.png"
hideCoverInPost: true 
lang : "ja"
categories : ["expedition 2026"]
---

こちらは、インタラクティブな地図です。
私たちの旅のルートをたどりながら、各地での出来事を写真やエピソード、そして訪れた場所へのリンクとともにご覧いただけます。

<!--more-->
この地図では、旅の中で立ち寄る予定のすべての場所を追うことができます。
それぞれの地点には、写真やちょっとしたエピソード、そしてより詳しく知るためのリンクを掲載しています。
私たちが出会った人々や自然とのふれあいを、みなさんと少しでも共有できれば嬉しいです。
ポイントをクリックして、ぜひ一緒に旅を体験してください！

<!-- Importation de Leaflet -->
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<!-- Création du conteneur de la carte -->
<div id="map" style="width: 100%; height: 500px;"></div>

<script>
  // Vérification que Leaflet est bien chargé
  console.log("Leaflet chargé ?", typeof L !== "undefined");

  // Création de la carte centrée sur le Japon
  var map = L.map('map').setView([36, 137], 5);

  // Ajout d'une couche de tuiles (OpenStreetMap)
  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; OpenStreetMap contributors'
  }).addTo(map);
  
<!-- Ajout des points des villes avec images-->
 var locations = [
    { coords: [35.682839, 139.759455], 
      text: "<b>Tokyo</b><br>Capitale du Japon<br><img src='/images/tokyo.jpg'width='150px'>" },
    { coords: [35.011564, 135.768149], 
      text: "<b>Kyoto</b><br>Ancienne capitale<br><img src='/images/kyoto.jpg' width='150px'>" },
    { coords: [34.693738, 135.502165], 
      text: "<b>Osaka</b><br> Forêt primitive de Kasugayama<br>"},
    { coords: [43.0667, 141.3500],
      text: "<b>Sapporo</b>" },
    { coords: [43.5333, 142.9500],
      text: "<b>Daisetsuzan</b><br>Parc national de Daisetsuzan<br>"},
    { coords: [43.0156, 144.3817],
      text: "<b>Kushiro</b><br>Parc national de Kushiro Shitsugen, écomusée du lac Toro-ko, sanctuaire de Tsurui-Itō Tanchō<br>"},
    { coords: [35.5011, 134.2351],
      text: "<b>Tottori</b><br>Zones humides de Hachigoro Toshima, parc Hyogo de la cigogne blanche orientale<br>"},
    { coords: [30.3580, 130.5280],
      text: "<b>Yakushima</b><br>Parc national de Yakushima<br> " },
    { coords: [26.2124, 127.6809],
      text: "<b>Okinawa</b><br>Manko Waterbird and Wetland Center<br> "},
    { coords: [24.3900, 123.8400],
      text: "<b>Iriomote-Ishigaki</b><br>Hirugi Mangrove Community<br>"},
    { coords: [40.5167, 140.2167],
      text: "<b>Shirakami-Sanchi</b><br>Forêt milléniare inscrite au World National Heritage<br> " }




];

<!-- Ajoute des pop-ip--> 
locations.forEach(loc => {L.marker(loc.coords).addTo(map).bindPopup(loc.text);});

</script>


<!-- pour ajouter un lien vers un post : <a href='/fr/posts/premier-article/'>Voir le post sur Tokyo</a --> 
