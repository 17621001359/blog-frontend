<template>
  <div class="articles">
    <div class="article" v-for="item in articles" :key="item.id">
      <g-link :to="`/article/${item.id}`" class="article-link">
        <g-image
          :src="item.thumbnail"
          :alt="item.title"
          class="thumbnail"
        />
        <h3 class="article-title">{{ item.title }}</h3>
        <div class="categories">
          <span
            class="category"
            v-for="(item, index) in item.categories"
            :key="index"
            >{{ item }}</span
          >
        </div>
      </g-link>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    articles: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped>
.articles {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 4rem;
}
.article {
  grid-column: auto / span 2;
  text-align: center;
}
.article-link {
  text-decoration: none;
}
.thumbnail {
  height: 560px;
  object-fit: cover;
  transition: all 0.15s ease;
  box-shadow: 0 0 40px -20px rgba(0, 0, 0, 0.25);
}
.article-title {
  font-size: 1rem;
  color: var(--color-contrast);
  margin: 2rem 0 1rem 0;
}
.categories {
  font-size: 0.8rem;
  color: var(--color-contrast-1);
}
.category {
  margin-right: 0.8rem;
}
.category:last-of-type {
  margin: 0;
}
.article:hover .thumbnail {
  transform: scale(1.02);
  box-shadow: 0 20px 40px -20px rgba(0, 0, 0, 0.25);
}

@media (min-width: 920px) {
  .article {
    grid-column: auto / span 1;
  }
  .article:nth-child(3n + 1) {
    grid-column: auto / span 2;
  }
}
</style>
