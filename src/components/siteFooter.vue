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
  flex-direction: column; 
  justify-content: center; 
  align-items: center; 
  padding: 10px; 
  color: white;
  background-color: rgba(44, 62, 80, 0.9);
  border-top: 4px solid #ff7f50;
  position: static; 
  bottom: 0; 
  width: 100%;
  text-align: center;
  font-weight: 300;
}

.footer p {
  margin: 5px 0; 
}

a {
  color: rgb(196, 196, 196);
  text-decoration: none;
  transition: color 0.3s;
}

a:hover {
  color: #ff7f50; 
}

@media (min-width: 600px) {
  .footer {
    flex-direction: row; /* Geniş ekranlarda yatay hizalama */
    height: 60px; /* Yüksekliği artırma */
    padding: 0 2rem; /* Yatay boşluk */
  }

  .footer p {
    margin: 0 10px; 
  }
}
</style>
