- Goto: https://codepen.io/avcoder/pen/RemBWg

## Infrastructure

1. in JS:
   ```js
   new Vue({
     el: "#app",
     data: {
       newComment: ""
     }
   });
   ```
1. In HTML:

   ```html
   <input type="text" id="stuff" v-model="newComment">
   <p>{{ newComment }}</p>
   ```

1. Try typing in input box now

## Show comments

1. In JS:
   ```js
   data: {
     comments: comments;
   }
   ```
1. In HTML:
   ```html
   <ul>
       <li v-for="comment in comments" :key="comment">{{ comment.text }}</li>
   </ul>
   ```

## Add a new comment

1. In HTML add a new attribute:
   ```html
   <input @keyup.enter="submitComment">
   ```
1. In JS - what do you think we should insert inside the push method?:
   ```js
   methods: {
       submitComment() {
           // does this add what we think it adds?
           this.comments.push(this.newComment)
       }
   }
   ```

- Try typing something to add. What's wrong? We're feeding it a string, but it expects an object

1. Fix it; In JS:
   ```js
   submitComment() {
       this.comments.push({
           text: this.newComment,
           author: "avcoder"
           authorImg: newCommentUrl
       })
       this.newComment ="";
   }
   ```

## Clear input box after adding

1. In JS:
   ```js
   submitComment() {
       this.comments.push(this.newComment);
       this.newComment = "";
   }
   ```

## Use Components

1. In HTML, remove our {{}} inside the list tag:

   ```html
   <ul>
    <li v-for="comment in comments" :key="comment"></li>
   </ul>
   ```

1. In HTML, (for now) create following template:

   ```html
   <script type="text/x-template" id="commentTemplate">
    <li>
        <img :src="comment.authorImg" class="post-img">
        <small>{{ comment.author }}</small>
        <p class="post-comment">{{ comment.text }}</p>
    </li>
   </script>
   ```

1. In JS, let Vue know we have a component

   ```js
   /* place above Vue instantiation */
   Vue.component("AppComment", {
     template: "#commentTemplate"
   });

   let app = new Vue({});
   ```

1. But child doesn't know of comment

1. In JS, inside component, add props:

   ```js
   template: "#commentTemplate",
   props: ['comment']
   ```

1. In HTML, create new list tag: (kabab-case)

   ```html
   <ul>
       <li is="app-comment" :comment="comment" v-for="comment in comments" :key="comment"></li>
   </ul>
   ```

## watch

1. In JS, after methods, create watch
   ```js
   watch: {
       comments() {
           console.log('changed');
       }
   }
   ```

- Now input a comment and see console. Thus, any time that thing changes, it gives you a hook.

## v-if and template

1. In JS:

   ```js
   data: {
     show: true;
   }
   ```

1. In HTML, surround everything with a template tag then use v-if:

   ```html
   <template v-if="show">

   </template>
   ```

- Try changing the boolean value of show. See docs and compare to v-show.

## create a button to toggle it.

1. In HTML, use :

   ```html
   <ul v-if="show">
       ...
   <button @click="toggleShow">{{ btnComment }}</button>
   ```

1. In JS:

   ```js
   toggleShow() {
     this.show = !this.show;
     this.btnComment = (this.show ? "Hide comments" : "Show comments")
   }
   ```

## v-html

1. In HTML:
   ```html
   <p class="post-comment" v-html="comment.text"></p>
   ```

- try entering hi&quot; &#039; &#39;
