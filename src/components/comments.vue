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
  padding: 20px;
  font-family: "Poppins", sans-serif;
}

.comments-container {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.comment-wrapper {
  background-color: #f0f0f0;
  border-radius: 8px;
  padding: 10px;
}

.comment {
  display: flex;
  flex-direction: column;
}

.comment-details {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.comment-text {
  font-size: 16px;
  font-weight: 300;
}

.commenter-info {
  font-size: 14px;
  font-weight: bold;
}

.comment-stars i {
  color: #ff7f50;
}

.work-and-input {
  margin-top: 20px;
}

.work-and-input-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
}

.lets-work-together h2 {
  font-size: 24px;
  color: #2c3e50;
}

.contact-links a {
  margin: 0 5px;
  color: #2c3e50;
  font-size: 24px;
  text-decoration: none;
  transition: color 0.3s;
}

.contact-links a:hover {
  color: #ff7f50;
}

.input-group {
  display: flex;
  flex-direction: column;
  gap: 10px;
  width: 100%;
  max-width: 600px;
}

textarea {
  width: 100%;
  padding: 10px;
  border-radius: 8px;
  border: 1px solid #ccc;
  font-size: 16px;
  font-family: "Poppins", sans-serif;
}

.character-count {
  text-align: right;
  font-size: 12px;
  color: #777;
}

.rating-stars {
  display: flex;
  justify-content: center;
  gap: 5px;
}

.rating-stars i {
  font-size: 24px;
  cursor: pointer;
  color: #ff7f50;
}

.rating-stars .far.fa-star {
  color: #ccc;
}

.yorum {
  padding: 10px 20px;
  border: none;
  background-color: #ff7f50;
  color: #fff;
  font-size: 16px;
  font-family: "Poppins", sans-serif;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.yorum:hover {
  background-color: #ff5722;
}
</style>
