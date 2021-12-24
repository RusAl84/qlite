<template>
  <q-page class="flex flex-center">
    <div>
    <div>
    <div><q-input v-model="text" label="Standard" /></div>
    <div>{{text}}</div>
    <div><q-btn color="white" text-color="black" label="Standard" @click="btn_click()"/></div>
    </div>
    <div>
    <form>
      <h4>оздание поста</h4>
      <q-input class="input" v-model="title" label="Название:" />
      <q-input class="input" v-model="body" label="Описание:" />
      <q-btn class="btn" color="white" text-color="black" label="Standard" @click="create_post()"/>
    </form>
    <div class="post" v-for="post in posts" :key="post.id">
      <div><strong>Название:</strong>{{post.title}}</div>
      <div><strong>Описание:</strong>{{post.body}}</div>
    </div>
    </div>
</div>


  </q-page>
</template>

<script>
import { defineComponent } from 'vue';
import { ref } from 'vue'
export default defineComponent({
  name: 'PageIndex',
    setup () {
    return {
      text: ref('')
    }
  },
  data() {
    return{
      title:"",
      body:"",
      posts:[
        {id: 1, title: 'Test Vue', body: 'Описание поста'},
        {id: 1, title: 'Test Vue', body: 'Описание поста'},
        {id: 1, title: 'Test Vue', body: 'Описание поста'},
      ]
    }

  },
 methods: {
    btn_click () { 
      alert(this.text) 
    }, 
    create_post(){
      const newPost= {
        id: Date.now(),
        title: this.title,
        body: this.body,
      }
      this.posts.push(newPost)
    }
  },

})

</script>
<style scoped>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;

}
div{
  
display: flex;
flex-direction: column;
}
.post{
  padding: 15px;
  border: 2px solid teal;
  margin-top: 15px;
}
.input{
  width: 100%;
  border: 1px solid teal;
  padding: 10px 15px ;
  margin-top: 15px;
}
.btn{
  align-self: flex-end;}
</style>