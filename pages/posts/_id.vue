<template>
  <div class="my-5">
    <h1 class="display-1 my-5">
     {{post.title}}
    </h1>
    <img :src="post.imageUrl" :alt="post.title" class="rounded w-100 mb-3">
    <div>
      {{post.description}}
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  validate({params}){
    return /^\d+$/.test(params.id)
  },

  async asyncData({params,error}){
    try {
    let {data} = await axios.get(`http://localhost:3333/posts/${params.id}`)
    return {post:data}

    }catch(e){
      error({statusCode:404,message:'Post not found.'})
    }
  },

  head(){
    return {
      title:this.post.title
    }
  }


}
</script>

