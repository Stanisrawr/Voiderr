<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h1>{{ msg }}</h1>
    <ul v-cloak v-for="moment in moments" :key="moment.moments">
      <li>
    {{moment.title}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'app',
   moments_API_URI:'https://newsapi.org/v2/top-headlines?country=us&category=business&apiKey=API_KEY',
  data () {
    moments:[]
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  methods:{
           
            getMoments: function ()
        {
         
            let self = this;

            axios.get(moments_API_URI)
                .then((resp) => {
                this.moments = resp.data;
                })
                .catch((err) => {
                console.error(err);
                console.log('Test Icicles');
                console.log(this.moments);
                });
        }
  },
         created:function()
       {
           console.log("ran");
          this.getMoments();
       }
  
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
