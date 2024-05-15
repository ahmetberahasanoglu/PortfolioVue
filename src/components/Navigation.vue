<template>
  <div class="navigation">
    <div class="logo"><a href="#">Logo</a></div>
    <div class="login">
      <span v-if="!loggedIn">
        <a href="#">Login</a> | <a href="#">Sign In</a>
      </span>
      <span v-else>
        <span>
          <img src="@/assets/job1.png" alt="User Icon" class="user-icon" />
        </span>
        <span>{{ username }}</span>
      </span>
    </div>
    <nav>
      <div class="links">
        <a href="#">Home</a>
        <a href="#">About</a>
        <a href="#">Work</a>
        <a href="#" class="marginR">Contact</a>
      </div>
    </nav>
  </div>
</template>

<script>
export default {
  data() {
    return {
      loggedIn: true,
      username: "Ahmet",
    };
  },
};
</script> 

<style scoped>
.marginR{
  margin-right: 20px;
}
.navigation {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 1000;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: rgba(44, 62, 80, 0.9); /* Hafif yarı şeffaf arka plan */
  padding: 10px 20px;
  font-family: "Poppins", sans-serif;
}

.logo a {
  font-weight: bold;
  font-size: 25px;
  color: #ff7f50;
  text-decoration: none;
  transition: transform 0.3s ease; /* Büyüme efekti için geçiş eklendi */
}

.logo a:hover {
  transform: scale(1.3); 
  color: #fff;
}

.login {
  display: flex;
  align-items: center;
}

.login a {
  font-weight: bold;
  font-size: 20px;
  padding: 3px;
  color: #fff;
  text-decoration: none;
}

.login a:hover {
  color: #ff7f50;
}

.user-icon {
  width: 20px; /* Daha büyük ikon */
  height: 20px;
  margin-right: 5px;
}

nav {
  display: flex;
}

.links {
  display: flex;
  gap: 17px;
}

.links a {
  font-weight: bold;
  font-size: 15px;
  color: #fff;
  text-decoration: none;
  padding: 10px;
  border-radius: 4px;
}
.links a:hover {
  color: #ff7f50;
}
</style>

