<template>
  <div class="footer">
    <p>
      This portfolio made by Ahmet for whatever reasons
    </p>
    <p>
      © Created for something <a href="#">asdasd</a>
    </p>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.footer {
  display: flex;
  flex-direction: column; /* Mobil uyum için dikey hizalama */
  justify-content: center; /* Merkezde hizalama */
  align-items: center; /* Ortada hizalama */
  padding: 1rem; /* İçerik boşluğu */
  color: white;
  background: #2c3e50; 
  border-top: 4px solid red;
  position: relative;
  bottom: 0;
  width: 100%;
  text-align: center; /* Metin ortalama */
  font-weight: 300;
}

.footer p {
  margin: 5px 0; /* Üst ve alt boşluk */
}

a {
  color: rgb(196, 196, 196);
  text-decoration: none;
  transition: color 0.3s;
}

a:hover {
  color: #ff7f50; /* Hover'da renk değişimi */
}

@media (min-width: 600px) {
  .footer {
    flex-direction: row; /* Geniş ekranlarda yatay hizalama */
    height: 60px; /* Yüksekliği artırma */
    padding: 0 2rem; /* Yatay boşluk */
  }

  .footer p {
    margin: 0 10px; /* Yatay boşluk */
  }
}
</style>
