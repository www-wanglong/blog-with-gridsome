<template>
  <Layout>
    <!-- Page Header -->
    <header
      class="masthead"
      :style="{
        backgroundImage: `url(${GRIDSOME_API_URL + $page.post.cover.url})`
      }"
    >
      <div class="overlay"></div>
      <div class="container">
        <div class="row">
          <div class="col-lg-8 col-md-10 mx-auto">
            <div class="post-heading">
              <h1>{{ $page.post.title }}</h1>
              <span>Posted by
              <a href="#"> {{ $page.post.created_at }}</a>
                on  {{ $page.post.created_at }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </header>

    <!-- Post Content -->
    <article>
      <div class="container">
        <div class="row">
          <div class="col-lg-8 col-md-10 mx-auto" v-html="mdToHtml($page.post.content)">

          </div>
        </div>
      </div>
    </article>
  </Layout>
</template>

<page-query>
  query($id: ID!) {
    post: strapiPosts (id: $id) {
      id,
      title,
      published_at,
      content,
      created_at,
      cover {
        url
      }
    }
  }
</page-query>

<script>
import MarkdownIt from 'markdown-it'
const md = new MarkdownIt()
//console.log(md.render('# hw'))
export default {
  name: 'PostPage',
  metaInfo () {
    return {
      title: this.$page.post.title
    }
  },
  methods: {
    mdToHtml (markdown) {
      return md.render(markdown)
    }
  }
};
</script>

<style></style>
