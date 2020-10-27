<template>
  <div class="container">
      <!-- user: {{name}}
      <nuxt-link to="/about">to about</nuxt-link>
      <div>
        fromServerData :{{host}}, {{acc}}
      </div> -->
      <Modal :show="toggle" title="Modal title" :onClose="closeHandler" :onComfirm="onConfirm"> 
           <div class="inner-content">{{text}}</div>
      </Modal>
    <button @click="btnHandler">Toggle Modal</button>
    <textarea cols="30" rows="10" v-model="text" ></textarea>

  </div>
</template>

<script>
import Modal from './../components/Modal';
import showToast from './../tools/toast'
export default {
  async asyncData({ req, res }) {
    if (process.server) {
      return { host: req.headers.host , acc : req.headers['accept-language'] }
    }
    return {}
  },
  data(){
    return {
      toggle : false,
      text : '',
    }
  },
  methods :{
    btnHandler(){
      this.toggle = true;
    },
    onConfirm(){
      showToast({msg : '您确定了了', type: 'success'})
    },
    closeHandler(){
      this.toggle = false;
      showToast({msg : '您取消了', type:'fail'})
    }
  }

}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
.inner-content{
  font-size: 22px;
}
</style>
