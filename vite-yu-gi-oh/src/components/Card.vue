<template>
  <div class="card-grid">
    <div  :key="card.id" class="card">
      <img :src="card.card_images[0].image_url" :alt="card.name" class="card-image" />
      <h3 class="card-title">{{ card.name }}</h3>
      <p class="card-text">{{ card.archetype }}</p>
    </div>
  </div>
</template>
  
<script>
export default {
  props: {
card: {
type: Object,
required: false,
default: () => ({})
},
},
};
</script>
  
<style scoped>
.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 5px;
  margin: 20px;
}

.card {
  background-color: #B66233;
  box-shadow: 0px 7px 7px rgba(0, 0, 0, 0.3);
  text-align: center;
  padding: 5px;
  width: 250px;
}

.card-image {
  width: 300px;
  height: 350px;
  margin-bottom: 10px;
}

.card-title {
  font-size: 1.2rem;
  margin-bottom: 10px;
  color: white;
}

.card-text {
  font-size: 1.3rem;
  line-height: 1.5;
  margin-bottom: 20px;
}
</style>