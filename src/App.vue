<template>
  <div class="wrapper">
    <h3>English to luganda Translator.</h3>
    <div class="bar"></div>
    <div class="inner">
      <div class="boxes">
        <textarea name="" id="from" cols="27" rows="20" placeholder="type english here..." v-model="beforeText" ></textarea>
        <textarea name="" id="" cols="27" rows="20" placeholder="luganda shows up here..." readonly disabled></textarea>
      </div>
      <button @click.prevent="translate()" >Translate</button>
      <!-- <div> {{beforeText}} </div> -->
    </div>
  </div>
</template>

<script>
  import { ref } from "vue";


export default {
  name: 'App',
  components: {
    
  },
  setup() {
    const beforeText = ref('')
    const afterText = ref('')
    const english = 'en'
    const luganda = 'lg'

    const translate = () => {
      fetch(`https://www.translated.net/hts/?f=quote&cid=htsdemo&p=htsdemo5&s=english&t=japanese,italian&text=https://www.translated.net/hts/HTS_Tech_Spec.pdf&df=pdf&jt=P&pn=SimpleTest&w=300078&of=json`)
      .then(res => res.json())
      .then(data => {
        console.log(data)
      })
      document.getElementById('from').innerText = ''
    }
    return {
      beforeText,
      afterText,
      translate
    }
  }

}
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@100;200;300;400;500;600;700;800;900&display=swap');

  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'poppins', sans-serif;
  }
  body {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100%;
  }
  .wrapper {
    padding: 1rem;
  }
  .wrapper h3 {
    text-align: center;
  }
  .bar {
    margin: 1rem auto;
    background-color: black;
    width: 100px;
    height: 3px;
  }
  .inner {
    display: flex;
    flex-direction: column;
  }
  .boxes textarea {
    margin: .5rem;
    border: none;
    background-color: #eeeeee;
    border-radius: 1rem;
    padding: 1rem;
    transition: 0.4s;
  }
  textarea:focus {
    outline: none;
    box-shadow: 1px 1px 55px -5px rgba(0,0,0,0.27);
    -webkit-box-shadow: 1px 1px 55px -5px rgba(0,0,0,0.27);
    -moz-box-shadow: 1px 1px 55px -5px rgba(0,0,0,0.27);
  }
  button {
    margin: auto;
    border: none;
    background-color: rgb(0, 0, 78);
    color: #fff;
    border-radius: 1rem;
    padding: 0.5rem 1rem;
    cursor: pointer;
    font-size: 18px;
  }
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
