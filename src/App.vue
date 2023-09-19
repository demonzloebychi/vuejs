<script>
export default {
  data(){
    return {
      posts: [
        {id: 1, title: "This a first post", body: "This post is never mind"},
        {id: 2, title: "This a second post", body: "This post is something mind"},
        {id: 3, title: "This a third post", body: "This post is maybe something mind"},
      ],
      title: '',
      body: '',
    }
  },
  methods: {
    createPost(){
      const newPost ={
        id: Date.now(),
        title: this.title,
        body: this.body,
      }
      this.posts.push(newPost);
    },
  }
}
</script>

<template>
  <div class="wrapper">
    <div class="content">

      <form class="form" @submit.prevent>
        <h3>Новое объявление</h3>
        <input v-bind:value="title" @input="title = $event.target.value" class="input" type="text" placeholder="Название">

        <input v-bind:value="body" @input="body = $event.target.value" class="input" type="text" placeholder="Описание">

        <button class="btn" @click="createPost">
          Создать
        </button>
      </form>
    
      <div class="post" v-for="post in posts">
        <div>Название: {{post.title}}</div>
        <div>Описание: {{post.body}}</div>
      </div>

    </div>
  </div>
</template>

<style>
.wrapper{
  max-width: 1140px;
  margin: 0 auto;
  padding: 15px;
  min-height: 100%;
  overflow: hidden;
  box-sizing: content-box;
}
.content{
  
}
*{
  font-family: sans-serif;
  font-size: 16px;
  font-weight: 500;
}
.form{
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin-bottom: 50px;

}
.input{
  height: 40px;
  border: 2px solid #9637b3;
}
.btn{
  border: 2px solid #9637b3;
  color: #213547;
  font-size: 16px;
  height: 40px;
}
.btn:hover{
  background-color: #c7c7c7;
}
.post{
  border: 1px solid #9637b3;
  margin-bottom: 20px;
  padding: 10px;
}



</style>
