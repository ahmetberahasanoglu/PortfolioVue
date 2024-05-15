<template>
  <div class="comment-container">
    <div class="comments-container">
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
              <img
                v-for="star in comment.rating"
                :key="star"
                src="@/assets/yıldız-dolu1.png"
                alt="filled star"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="work-and-input">
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
        <button @click="addComment" class="yorum">Yorumu Gönder</button>
        <div class="rating-stars">
          <img
            v-for="star in 5"
            :key="star"
            :src="
              star <= tempRating
                ? require('@/assets/yıldız-dolu1.png')
                : require('@/assets/yıldız-bos.png')
            "
            @mouseover="highlightStars(star)"
            @mouseleave="resetStars"
            @click="setRating(star)"
          />
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
      rating: 1,
      tempRating: null,
      comments: [],
    };
  },
  methods: {
    addComment() {
      if (this.commentText) {
        this.comments.unshift({
          commenterName: this.commenterName,
          commentText: this.commentText,
          rating: this.rating,
        });
        this.commentText = "";
        this.rating = 1;
      } else {
        alert("Lütfen yorumunuzu girin!");
      }
    },
    setRating(rating) {
      this.rating = rating;
      this.tempRating = null;
    },
    highlightStars(star) {
      this.tempRating = star;
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
.comment-stars img:hover{
  transform: scale(1.1);
}
.work-and-input {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 20px;
  width: 100%;
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

.rating-stars img {
  width: 30px;
  height: 30px;
  cursor: pointer;
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
.yorum:hover{
  background-color: #445566;
  transform: scale(1.5);
}
</style>
