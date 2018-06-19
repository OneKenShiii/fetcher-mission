<template>
  <div class="container" >
    <div >
      <p v-show="show">Loading...</p>
      <button
        @click="clicktry">Clicktry</button>
      <button
        @click="click">Click</button>
      <alertError
        :status="eStatus"
        :text1="eTextStatus"
        :message="eMessage"
        :shows="showExit"
        v-show="showAlert"/>
      <complete
        :numb="numCom"
        :show2="showExit2"
        v-show="showCom"/>
      <div
        class="box"
        v-for="item in posts"
        :key="item.posts"
        v-show="showData">
        <h2>Name : {{ item.name }}</h2>
        <h2>Username : {{ item.username }}</h2>
        <h2>Email : {{ item.email }}</h2>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import alertError from '~/components/alertError.vue';
import complete from '~/components/complete.vue';

export default {
  components: {
    alertError,
    complete,
  },
  data() {
    return {
      posts: [],
      errors: [],
      show: false,
      e: '',
      eStatus: 0,
      eTextStatus: '',
      eMessage: '',
      showAlert: false,
      numCom: 0,
      showCom: false,
      showData: false,
      showExit: false,
      showExit2: false,
    };
  },
  methods: {
    clicktry() {
      this.showExit2 = false;
      this.showCom = false;
      axios.get('https://reqres.in/api/unknown/23')
        .then((response) => {
          // JSON responses are automatically parsed.
          setTimeout(() => {
            this.posts = response.data;
          }, 2000);
          console.log(this.posts);
        })
        .catch((e) => {
          this.showCom = false;
          this.show = true;
          this.showData = false;
          setTimeout(() => {
            this.errors = e;
            this.eStatus = e.response.status;
            this.eTextStatus = e.response.statusText;
            this.eMessage = e.message;
            this.show = false;
            this.showAlert = true;
            this.showExit = true;
          }, 2000);
          // this.errors.push(e);
          console.log(e);
          // alert(`${e.response.statusText} ${e.response.status}`);
        });
    },

    click() {
      this.posts = [];
      this.showAlert = false;
      this.showExit = false;
      axios.get('https://jsonplaceholder.typicode.com/users')
        .then((response) => {
          // this.showAlert = false;
          this.show = true;
          // JSON responses are automatically parsed.
          setTimeout(() => {
            this.showData = true;
            this.posts = response.data;
            this.show = false;
            this.numCom = this.posts.length;
            this.showCom = true;
            this.showExit2 = true;
          }, 2000);
          // alert(response);
          console.log(this.posts);
        })
        .catch((e) => {
          this.errors.push(e);
        });
    },
  },
};
</script>

<style>
  .container {
    height: 100%;
    height: 100vh;
    width: 100%;
  }
</style>
