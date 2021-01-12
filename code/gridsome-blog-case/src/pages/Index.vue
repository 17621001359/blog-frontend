<template>
  <Layout>
    <TitlePage />
    
    <div class="container">
      <HomeArticle :articles="articles" />
    </div>
    <LatestJournals :journals="journals" />
  </Layout>
</template>

<page-query>
query {
	articles: allHomeArticle {
    edges {
      node {
        id
        date (format: "YYYY")
        title
        categories
        thumbnail (quality: 90)
        path
      }
    }
  }
  journals: allJournal (perPage: 4) {
    edges {
      node {
        id
        path
        title
      }
    }
  }
}
</page-query>

<script>
import TitlePage from "@/components/TitlePage"
import HomeArticle from "@/components/HomeArticle"
import LatestJournals from "@/components/LatestJournals"

export default {
  metaInfo: {
    title: 'Home'
  },
  name: "Home",
  components: { TitlePage, HomeArticle, LatestJournals },
  computed: {
    articles () {
      return this.$page.articles.edges.map(item => item.node)
    },
    journals () {
      return this.$page.journals.edges.map(item => item.node)
    }
  }
}
</script>

<style>
.home-links a {
  margin-right: 1rem;
}
</style>
