<template>
  <div class="col-md-4">
    <form class="form-horizontal">
      <div class="form-group">
        <label>用户名{{comment.username}}</label>
        <input type="text" class="form-control" placeholder="用户名" v-model="comment.username">
      </div>
      <div class="form-group" v-model="comment.content">
        <label>评论内容{{comment.content}}</label>
        <textarea class="form-control" rows="6" placeholder="评论内容" v-model="comment.content" ></textarea>
      </div>
      <div class="form-group">
        <div class="col-sm-offset-2 col-sm-10">
          <button type="button" class="btn btn-default pull-right" v-on:click="submit">提交</button>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data(){
      return {
        comment: {
          username: null,
          content: null
        }
      }
  },
  props: {
    addComment: {
          type: Function
      }
  },
  methods: {
    submit(){
        let comment = this.comment;
        comment.id = Date.now();
        this.addComment(comment);
        //这里注意必须是this.comment 如果用 comment= {} 不生效，因为变量是按值传递的
        this.comment = {
          username: null,
          content: null
        }
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

</style>
