<template>
  <Layout>
    <div class="journal">
      <div class="container journal-container">

        <div class="journal-header">
          <h1 v-html="journal.title" class="journal-title" />
          <div class="journal-meta">
            <div class="journal-author">
              <span class="label">Author</span>
              <span class="author-name" v-text="journal.author" />
            </div>
            <div class="journal-date">
              <span class="label">Date</span>
              <div v-text="journal.date"/>
            </div>
            <div class="journal-time">
              <span class="label">Time</span>
              <span>{{ journal.timeToRead }} min read</span>
            </div>
          </div>          
        </div>
        <div class="journal-content" v-html="journal.content" />

      </div>
    </div>
  </Layout>
</template>

<page-query>
query ($id: ID!) {
  journal (id: $id) {
    title
    author
    date (format: "D. MMMM YYYY")
    timeToRead
    content
  }
}
</page-query>

<script>

export default {
  name: "Journal",
  metaInfo () {
    return {
      title: this.journal.title
    }
  },
  computed: {
    journal () {
      return this.$page.journal
    }
  }
  
}
</script>

<style scoped>
.journal-container {
  max-width: 840px;
}
.journal-header {
  padding: 2rem 0 4rem 0;
}
.journal-title {
  font-size: 4rem;
  margin: 0 0 4rem 0;
  padding: 0;
}
.journal-meta {
  display: flex;
  flex-wrap: wrap;
  font-size: 0.8rem;
}
.journal-meta > div {
  margin-right: 4rem;
}
.journal-meta > div:last-of-type {
  margin: 0;
}
</style>
