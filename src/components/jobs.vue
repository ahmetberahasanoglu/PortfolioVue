<template>
  <div class="latest-work-container">
    <h1>Yaptıklarım</h1><br>
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
        { title: "Proje 4", image: require("@/assets/job1.png"), category: "Grafik Tasarım" },
        { title: "Proje 5", image: require("@/assets/job2.png"), category: "Grafik Tasarım" },
        { title: "Proje 6", image: require("@/assets/job3.png"), category: "Grafik Tasarım" },
        { title: "Proje 6", image: require("@/assets/job3.png"), category: "Grafik Tasarım" },
        { title: "Proje 6", image: require("@/assets/job3.png"), category: "Grafik Tasarım" },
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
