<template>
  <Layout>
    <div class="article">

      <div class="container">

        <div class="article-header">
          <h1 class="article-title" v-html="article.title" />
          <div class="article-info">

            <div class="categories-container">
              <div class="categories">
                <span class="label">Categories</span>
                <span 
                  class="category"
                  v-for="(category, index) in article.categories" 
                  :key="index"
                  v-text="category"
                />
              </div>
            </div>

            <div class="year-container">
              <span class="label">Year</span>
              <div v-html="article.date"/>
            </div>
          </div>
        </div>

        <div v-html="article.content" class="content" />

      </div>

    </div>
  </Layout>
</template>
<page-query>
query ($id: ID!) {
  article: homeArticle (id: $id) {
    title
    date (format: "YYYY")
    content
    categories
    article_bg_color
    article_fg_color
  }
}
</page-query>
<script>
export default {
  name: 'Article',
  metaInfo () {
    return {
      title: this.article.title,
      bodyAttrs: {
        style: `background-color: ${this.article.article_bg_color ? this.article.article_bg_color : 'var(--color-base)'}; color: ${this.article.article_fg_color ? this.article.article_fg_color : 'var(--color-contrast)'}`
      }
    }
  },
  computed: {
    article () {
      return this.$page.article
    }
  }
}
</script>

<style scoped>
.article-header {
  padding-bottom: 4rem;
}
.article-title {
  font-size: 4rem;
  margin: 0 0 4rem 0;
  padding: 0;
}
.article-info {
  display: flex;
  flex-wrap: wrap;
  font-size: 0.8rem;
}
.article-info > div {
  margin-right: 4rem;
}
.article-info > div:last-of-type {
  margin: 0;
}
.category:after {
  content: ', '
}
.category:last-of-type:after {
  content: '';
}
</style>
