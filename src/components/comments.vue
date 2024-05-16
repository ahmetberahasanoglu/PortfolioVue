<template>
  <div class="comment-container">
    <div v-if="comments.length > 0" class="comments-container">
      <div
        v-for="(comment, index) in comments"
        :key="index"
        class="comment-wrapper"
      >
        <div class="comment">
          <div class="comment-details">
            <div class="comment-text">
              {{ truncateText(comment.commentText, 36) }}
            </div>
            <div class="commenter-info">{{ comment.commenterName }}</div>
            <div class="comment-stars">
              <i
                v-for="star in comment.rating"
                :key="star"
                class="fas fa-star"
              ></i>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div v-else>
      <p>Henüz bir yorum yapılmamış.</p>
    </div>
    <div class="work-and-input">
      <div class="work-and-input-wrapper">
        
        <div class="lets-work-together">
          <h2>Let's Work Together</h2>
          <div class="contact-links">
            <a href="https://twitter.com/yourusername" target="_blank">
              <i class="fab fa-twitter"></i>
            </a>
            <a href="https://github.com/yourusername" target="_blank">
              <i class="fab fa-github"></i>
            </a>
            <a href="mailto:example@gmail.com">
              <i class="far fa-envelope"></i>
            </a>
          </div>
        </div>
        
        <div class="input-group">
          <textarea
            v-model="commentText"
            placeholder="Yorumunuz"
            maxlength="36"
          ></textarea>
         
          <div class="character-count">{{ commentText.length }}/36</div>
          <div class="rating-stars">
            <i
              v-for="star in 5"
              :key="star"
              :class="{
                'fas fa-star': star <= tempRating,
                'far fa-star': star > tempRating,
              }"
              @mouseover="highlightStars(star)"
              @mouseleave="resetStarsIfNeeded"
              @click="setRating(star)"
            ></i>
          </div>
          <button @click="addComment" class="yorum">Yorumu Gönder</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      commenterName: "Ahmet Hasanoglu",
      commentText: "",
      rating: 0,
      tempRating: null,
      comments: [],
    };
  },
  methods: {
    addComment() {
      if (this.commentText) {
        if (!this.rating) {
          alert("Lütfen bir puan verin!");
          return;
        }
        this.comments.unshift({
          commenterName: this.commenterName,
          commentText: this.commentText,
          rating: this.rating,
        });
        this.commentText = "";
        this.rating = 0;
        this.resetStars();
      } else {
        alert("Lütfen yorumunuzu girin!");
      }
    },
    setRating(rating) {
      this.rating = rating;
      this.tempRating = rating;
    },
    highlightStars(star) {
      if (!this.rating) {
        this.tempRating = star;
      }
    },
    resetStarsIfNeeded() {
      if (this.rating == 0) {
        this.tempRating = null;
      }
    },
    resetStars() {
      this.tempRating = null;
    },
    truncateText(text, limit) {
      if (text.length > limit) {
        return text.substring(0, limit) + "...";
      } else {
        return text;
      }
    },
  },
};
</script>

<style scoped>
.comment-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  max-width: 1260px;
  margin: 0 auto;
  padding: 20px;
  text-align: center;
}

.comments-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 20px;
  width: 100%;
}

.comment-wrapper {
  flex: 0 0 calc(50% - 10px);
  display: flex;
  justify-content: center;
}

.comment {
  display: flex;
  flex-direction: column;
  align-items: center;
  border: 1px solid #ccc;
  border-radius: 10px; /* Yuvarlatılmış köşeler */
  padding: 20px; /* Daha geniş padding */
  background-color: #f9f9f9; /* Daha açık arka plan */
  width: 100%;
}

.comment-details {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
}

.comment-text {
  font-size: 16px; /* Daha büyük yazı tipi */
  margin-bottom: 10px;
}

.commenter-info {
  font-style: italic;
  color: #555; /* Daha açık renk */
  
}

.comment-stars img {
  width: 20px;
  height: 20px;
  
}

.work-and-input {
  display: flex;
  justify-content: center;
 
  width: 100%;
}

.work-and-input-wrapper {
  display: flex;
  justify-content: space-between; /* Elemanları aralarda hizala */
  align-items: flex-start; /* Dikeyde üste hizala */
  width: 100%;
  max-width: 600px; /* İstenilen maksimum genişlik */
}

.lets-work-together {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 20px;
}

.contact-links {
  display: flex;
  justify-content: center;
  gap: 20px;
  margin-top: 10px;
}

.contact-links a {
  text-decoration: none;
  color: #333;
  font-size: 1.5rem;
  transition: color 0.3s;
}

.contact-links a:hover {
  color: #007bff;
}

.input-group {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
  margin-top: 20px; /* Yeni eklenen stil */
}

textarea {
  width: 100%; /* Genişlik arttırıldı */
  max-width: 300px; /* Maksimum genişlik sınırı */
  height: 60px;
  padding: 10px; /* Daha geniş padding */
  border-radius: 5px;
  border: 1px solid #ccc;
  resize: none;
}

.character-count {
  font-size: 12px;
  color: #666;
}

.rating-stars {
  display: flex;
  align-items: center;
}

.yorum {
  padding: 10px;
  border: none;
  font-size: 15px;
  border-radius: 5px;
  cursor: pointer;
  background-color: #20303f;
  color: white;
}

.yorum:hover {
  background-color: #2b3c4b;
  transform: scale(1.03);
  filter: drop-shadow(2px 4px 6px #20303f);
}

</style>

