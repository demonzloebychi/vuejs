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
  <div>
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
        <div>Описнание: {{post.body}}</div>
      </div>

    </div>
  </div>
</template>

<style>
.content{
  
}
.form{
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin-bottom: 50px;
}
.input{
  width: 100%;
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
  background-color: #9c69ac;
}
.post{
  border: 1px solid #9637b3;
  margin-bottom: 20px;
  padding: 10px;
}



</style>
