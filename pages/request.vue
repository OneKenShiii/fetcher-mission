<template >
  <div class="container">
    <div class="page">
      <div class="header">
        <div class="boxText">
          <h1>Click for Random Data</h1>
        </div>
        <div class="boxButton">
          <button
            class="buttonRand"
            @click="random1">Click</button>
        </div>
      </div>
      <div class="boxData1">
        <div class="Data1">
          <h1 class="font">ID : {{ id }}</h1>
          <h1 class="font">Title : {{ user }}</h1>
          <h1 class="font">Body : {{ body }} </h1>
        </div>
      </div>
      <div class="boxCommend">
        <div
          class="Data2"
          v-for="item in commend"
          :key="item.commend">
          <h1 class="font">Name : {{ item.name }} </h1>
          <h1 class="font">E-mail : {{ item.email }}</h1>
          <h1 class="font">Body : {{ item.body }}</h1>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      posts: [],
      commend: [],
      user: '',
      x: 0,
      id: '',
      e: '',
      errors: [],
      body: '',
    };
  },
  methods: {
    // random() {
    //   this.x = Math.floor((Math.random() * 100) + 1);
    //   axios.get(`https://jsonplaceholder.typicode.com/posts/${this.x}`)
    //     .then((response) => {
    //       this.posts = response.data;
    //       this.user = this.posts.title;
    //       this.id = this.posts.id;
    //       this.body = this.posts.body;
    //       return axios.get(`https://jsonplaceholder.typicode.com/posts/${this.x}/comments`);
    //     })
    //     .then((resp) => {
    //       this.commend = resp.data;
    //     })
    //     .catch((e) => {
    //       this.errors.push(e);
    //       alert(e);
    //     });
    // },
    async random1() {
      try {
        this.x = Math.floor((Math.random() * 100) + 1);
        let a = await axios.get(`https://jsonplaceholder.typicode.com/posts/${this.x}` )
        this.posts = a.data;
        this.user = this.posts.title;
        this.id = this.posts.id;
        this.body = this.posts.body;
        console.log(this.posts);
        a = await axios.get(`https://jsonplaceholder.typicode.com/posts/${this.x}/comments` )
        this.commend = a.data;
      } catch(e){
        this.errors.push(e);
        console.log(this.errors);
      };
    },
  },
};
</script>

<style scoped>

  h1{
    margin: 0;
  }
  .container {
    width           : 100%;
    height          : 100%;
    min-height      :100vh;
    display         : flex;
    align-items     : center;
    flex-direction  : column;
    background-color: #363636;
  }
  .page {
    height          : 100%;
    width           : 50%;
    /* background-color: pink; */
  }
  .header {
    display         : flex;
    width           : 100%;
    height          : 188px;
    background-color: black;
  }
  .boxText {
    display         : flex;
    justify-content : center;
    align-items     :  center;
    width           : 80%;
    height          : 168px;
    background-color: rgba(255,140, 0, 1);
    border          : 10px solid rgb(255,69,0,1);
  }
  .boxButton {
    display         : flex;
    justify-content : center;
    align-items     : center;
    width           : 20%;
    height          : 188px;
    background-color: gold;
  }
  .boxData1 {
    display         : flex;
    width           : 100%;
    /* margin-top: 10px; */
    height          : 160px;
    background-color: #A1A1A1;
    justify-content : center;
    align-items     : center;
  }
  .Data1 {
    width           : 90%;
    height          : 130px;
    background-color: #FFE7BA;
    padding-left    : 5px;
    border          : 5px solid black;
  }
  .boxCommend {
    display         : flex;
    height          : 589px;
    width           : 100%;
    background-color: #C9C9C9;
    display         : flex;
    flex-direction  : column;
    align-items     : center;
    /* justify-content: center; */
  }
  .font {
    font-size: 1.1rem;
  }
  .buttonRand {
    width           : 60px;
    height          : 60px;
    font-size       : 16px;
    border-radius   : 1px;
  }
  .Data2 {
    height          : 107px;
    margin-top      : 8px;
    width           : 95%;
    background-color: #EED8AE;
    padding-left    : 10px;
  }
  /* @media only screen and (max-height:950px){
    .container {
      height: 950px;
    }
    .page {
      height: 950px;
    }
  } */
  @media only screen and (max-width:1080px){
    .Data2 {
      width: 515px;
      height: 120px;
    }
    .boxCommend {
      height: 670px;
    }
    .page {
      width: 532px;
      /* background-color: grey; */
    }
    .container {
      height: 1020px;
    }
  }
  @media only screen and (max-width:1080px){
    .Data2 {
      width: 515px;
      height: 120px;
    }
    .boxCommend {
      height: 670px;
    }
    /* .page {
      width: 532px;
    } */
    /* .container{
      height: 100vh;
    } */
  }
  @media only screen and (max-width:550px){
    .container {
      display: flex;
      align-items: flex-start;
      width: 550px;
    }
  }
</style>
