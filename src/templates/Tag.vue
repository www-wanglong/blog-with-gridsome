<template>
  <div>
    <h1>{{ $page.tag.title }}</h1>
    <ul>
      <li v-for="post in $page.tag.posts" :key="post.id">
        {{  }}
      </li>
    </ul>
  </div>
</template>

<page-query>
query ($id: ID!) {
  tag:  strapiTags(id: $id) {
    id,
    title,
    posts {
      title,
      content
    }
  }
}
</page-query>
<script>
export default {
  name: 'TagPage'
}
</script>

<style>

</style>