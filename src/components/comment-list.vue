<template>
    <div class="col-md-8">
    <h3 class="reply">评论回复：</h3>
    <h2 v-show="!comments.length">暂无评论，点击左侧添加评论！！！</h2>
    <ul class="list-group">
        <item v-for="(comment, index) in comments"
              :comment="comment"
              :delete-comment="deleteComment"
              key="index"></item>
    </ul>
  </div>
</template>

<script>

  import item from './comment-item.vue'

  export default {
      props: {
        deleteComment: {
            type: Function
        },
        comments: {
            type: Array
        }
      },
      components: {
          item
      }
  }
</script>

<style type="text/css">

</style>
