<template>
  <div id="app">
    <header class="site-header jumbotron">
      <div class="container">
        <div class="row">
          <div class="col-xs-12">
            <h1>请发表对Dota2的评论</h1>
          </div>
        </div>
      </div>
    </header>

    <div class="container">
      <addComment :addComment="addComment"></addComment>
      <list :comments="comments" :delete-comment="deleteComment"></list>
    </div>

  </div>
</template>

<script>
  import addComment from './components/addComment.vue'
  import list from './components/comment-list.vue'

  export default {
    data(){
      return {
          comments: []
      }
    },
    created(){
        //模拟发送Ajax请求 异步获取数据
      setTimeout(()=> {
        this.comments = [
          {
            username: 'juggernaut',
            content: '剑刃风暴'
          },
          {
            username: 'phantom assassin',
            content: '我的暗杀名单上有五个名字'
          }
        ];
      }, 2000)
    },
    components: {
      addComment,
      list
    },

    methods: {
      addComment(comment){
        this.comments.unshift(comment);
      },
      deleteComment(comment){

        let index = this.comments.indexOf(comment);

        this.comments.splice(index, 1);

        //delete this.comments[index];

      }
    }

  }
</script>

<style>

</style>
