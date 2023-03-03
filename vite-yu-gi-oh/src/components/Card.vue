<template>
  <div class="card-grid">
    <div v-for="card in cards" :key="card.id" class="card">
      <img :src="card.imageUrl" :alt="card.name" class="card-image" />
      <h3 class="card-title">{{ card.name }}</h3>
      <p class="card-text">{{ card.description }}</p>
    </div>
  </div>
</template>
  
<script>
export default {
  props: {
    cards: {
      type: Array,
      required: true,
    },
  },
};
</script>
  
<style scoped>
.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 20px;
}

.card {
  background-color: #ffffff;
  box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.3);
  padding: 20px;
  border-radius: 5px;
  text-align: center;
}

.card-image {
  width: 100%;
  max-height: 200px;
  object-fit: cover;
  border-radius: 5px;
  margin-bottom: 10px;
}

.card-title {
  font-size: 1.2rem;
  margin-bottom: 10px;
}

.card-text {
  font-size: 1rem;
  line-height: 1.5;
  margin-bottom: 10px;
}
</style>