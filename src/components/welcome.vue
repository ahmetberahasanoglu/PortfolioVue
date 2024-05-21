<template>
  <div class="portfolio">
    <div class="welcome">
      <div class="content">
        <h2>{{ skills[0] }} | {{ skills[1] }}</h2>
        <h1>{{profession}}</h1>
        <p>Hey I am {{ name }} please contact me for your web design jobs adssaduygsadasyjdvasdıasvdaısdsa</p>
      </div>
    </div>
    <div class="image">
      <img src="@/assets/OIP.jpeg" />
    </div>
  </div>
  <div class="skills-container">
    <ul class="skills">
      <li><img src="@/assets/html-logo.png" alt="HTML Icon" /></li>
      <li><img src="@/assets/jslogo.png" alt="JS" /></li>
      <li><img src="@/assets/css.png" alt="CSS" /></li>
      <li><img src="@/assets/logo.png" alt="Vue" /></li>
      <li><img src="@/assets/react.png" alt="React" /></li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "Ahmet",
      skills: ["Branding", "Design"],
      profession:"Web Developer",
      veri:123
    };
  },
};
</script>

<style scoped>
body {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
  background-color: #fff; 
  font-family: "Poppins", sans-serif;
}

.portfolio {
  display: flex;
  flex-direction: row; 
  align-items: center;
  justify-content: center;
  text-align: left;
  padding: 20px;
  margin-top: 60px;
  color: #2c3e50; 
}

.welcome .content {
  margin-right: 20px; 
}

.content h2 {
  font-size: 24px;
  color: #ff7f50; 
}

.welcome h1 {
  color: #2c3e50;
  font-size: 36px;
  margin: 10px 0;
}

.welcome p {
  color: #2c3e50;
  font-size: 20px;
  font-weight: bold;
}

.image {
  flex-shrink: 0; 
}

.image img {
  width: 250px; 
  height: auto;
  border-radius: 20%; 
}

.skills-container {
  display: flex;
  justify-content: center;
  margin-top: 20px;
}

.skills {
  display: flex;
  gap: 20px;
  padding: 0;
  margin: 0;
  list-style: none;
}

.skills li {
  display: flex;
  align-items: center;
  justify-content: center;
}

.skills li img {
  width: 50px;
  height: auto;
  transition: transform 0.3s;
}

.skills li img:hover {
  transform: scale(0.8);

  filter: drop-shadow(2px 4px 6px #ff7f50);
}
</style>
