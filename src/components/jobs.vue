<template>
  <div class="latest-work-container">
    <br>
    <div class="specialities">
      <div class="speciality">UX Design</div>
      <div class="speciality">Interactive Design</div>
      <div class="speciality">Product Design</div>
    </div>
    <h1>Yaptıklarım</h1>
    <div class="gallery">
      <a v-for="(project, index) in projects" :key="index" class="gallery-item">
        <img class="gallery-item-image" :src="project.image" :alt="project.title" />
        <div class="gallery-item-description">
          <div class="gallery-item-title">{{ project.title }}</div>
          <div class="gallery-item-category">{{ project.category }}</div>
        </div>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      projects: [
        { title: "Proje 1", image: require("@/assets/job1.png"), category: "UI, Sanat yönetmeliği" },
        { title: "Proje 2", image: require("@/assets/job2.png"), category: "Web Tasarımı" },
        { title: "Proje 3", image: require("@/assets/job3.png"), category: "Grafik Tasarım" },
        { title: "Proje 4", image: require("@/assets/job1.png"), category: "UX, User Experience" },
        { title: "Proje 5", image: require("@/assets/job2.png"), category: "Backend Developer" },
        { title: "Proje 6", image: require("@/assets/job3.png"), category: "UI, Sanat yönetmeliği" },
        { title: "Proje 7", image: require("@/assets/job1.png"), category: "Grafik Tasarım" },
        { title: "Proje 8", image: require("@/assets/job2.png"), category: "Web Tasarımı" },
      ]
    };
  }
};
</script>

<style scoped>
.latest-work-container {
  display: flex;
  flex-direction: column;
  align-items: center; 
}
.specialities {
  display: flex;
  justify-content: center;
  gap: 20px;
  margin-bottom: 20px;
}

.speciality {
  padding: 10px 20px;
  background-color: #f0f0f0;
  border-radius: 20px;
  font-weight: bold;
}
.speciality:hover{
  transform: scale(1.01);
  box-shadow: 0 7px 10px rgba(0, 0, 0, 0.15);
}
.gallery {
  display: flex;
  flex-wrap: wrap;
  max-width: 1260px;
  justify-content: center; 
  gap: 20px;
  width: 100%;
}

.gallery-item {
  text-decoration: none;
  width: 300px; 
  margin: 0 auto; 
  text-align: left;
  font-family: "epilogue";
  color: black;
  transition: transform 0.3s, box-shadow 0.3s;
}

.gallery-item:hover {
  transform: scale(1.05);
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.15);
}

.gallery-item-image {
  width: 100%;
  height: auto;
  object-fit: cover;
  border-radius: 10px;
}

.gallery-item-description {
  padding: 10px;
}

.gallery-item-title {
  font-weight: 600;
}

.gallery-item-category {
  font-size: 16px;
  color: #777;
}
</style>
