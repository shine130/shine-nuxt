<template>
  <div>
    <h1 class="display-1 my-5">List</h1>
    <div class="row justify-content-center">
    <div class="col-md-6" v-for="post in posts" :key="post.id">
        <div class="card my-3">
          <nuxt-link :to="{name:'posts-id',params:{id:post.id}}">
          <img :src="post.imageUrl" :alt="post.title" class="card-img-top">
          <div class="cart-body">
            <h5 class="card-title">{{post.title}}</h5>
            <h6 class="card-subtitle mb-2 text-black-50">{{post.author}}</h6>
          </div>
            </nuxt-link>
            <div class="cart-footer">
              <button @click="destroyAction(post.id)" class="btn btn-link">Delete</button>
            </div>
        </div>
    </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  // async asyncData(){
  //   let {data} = await axios.get('http://localhost:3333/posts')
  //   return {posts:data}
  // },
  async fetch({store}){
    const response = await axios.get('http://localhost:3333/posts')
    store.commit('post/setList',response.data)
  },
  computed:{
    posts(){
      return this.$store.state.post.list
    }
  },
  methods:{
    destroyAction(id){
      this.$store.dispatch('post/destroyAction',id)
    }
  },
  head(){
    return {
      title:'Posts'
    }
  }

}
</script>
