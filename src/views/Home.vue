<template>
  <div class="home">
    <global-header></global-header>
    <div v-html="msg[0]"></div>
    <div v-html="msg[1]"></div>
    <div v-html="msg[2]"></div>
    <div v-html="msg[3]"></div>
  </div>
</template>

<script>
// @ is an alias to /src

import GlobalHeader from '../components/GlobalHeader.vue'
import axios from 'axios'

let account = []
const Auth = axios.create({
  baseURL: "https://aaeonbackend.azurewebsites.net/auth/"
  })

  Auth.post("/login",{password: "1",email: "111@test.com.tw"}).then((res) => {
  console.log(res.data.data.tokenData.token)
  axios.get('https://aaeonbackend.azurewebsites.net/permissions',{
    headers:{
      'Authorization' : `Bearer ${res.data.data.tokenData.token}`
    }
    }).then(resp => { 
    console.log(resp.data)
    console.log(resp.data.length)
    for(let i = 0;i<resp.data.length;i++){
      account[i] = `description :${resp.data[i].description}  name:  ${resp.data[i].name} id: ${resp.data[i]._id}`
    }
    
    
  })
});

export default {
  name: 'Home',
  components: {
    GlobalHeader
  },

  data () {
    return {
      msg: account
    }
  }
  
}
</script>
