# vue_comment

> A Vue.js project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```
## tutorial

### 四个组件

#### App主组件

  * 负责接收add组件传递过来的数据
  * 向list组件分发数据
  * 操作数据: 调用deleteComment函数
  
    ```
    deleteComment(comment){
    
        let index = this.comments.indexOf(comment);

        this.comments.splice(index, 1);

        //delete this.comments[index];
        
      }
    ```
   > 注意：不能使用 `delete`操作符 操作数组，value返回undefined 

#### addComment组件

* 获取用户界面输入的数据
* 为 `button` 按钮绑定事件 `v-on:click="submit"`
* 在组件方法中调用 `addComment(comment)` 
* 向App主组件传递数据

```
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
```
  
#### comment-list组件

* 容纳 `comment-item` 组件
* 负责中间传递数据，遍历 `comment-item`组件

 ```
 <ul class="list-group">
     <item v-for="(comment, index) in comments"
           :comment="comment"
           :delete-comment="deleteComment"
           key="index"></item>
 </ul>
 ```
 
 
#### comment-item组件

* 显示遍历过的数据
* 向主组件传入deleteComment函数
* 绑定删除事件 `v-on:click="removeItem"`
* 在组件方法中调用父组件传过来的 `deleteComment(comment)` 方法

```
export default {
      props: {
        comment: Object,
        deleteComment: Function
      },
      methods: {
        removeItem(){
          let comment = this.comment;
          this.deleteComment(comment);
        }
      }
    }
```
> 完成时间：2017年8月1日23:27:40
  
  
  
  
  
  
  
