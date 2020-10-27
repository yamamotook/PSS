<template>
  <transition name="fade" :duration="300">
    <div class="modal-container flex-center" v-if="show"  @click="onClose">
          <div class="modal-content" @click.stop="()=>{}">
          <h5 class="modal-title" v-if="title ? true : false">{{title}}</h5>
          <slot></slot>
          <div class="modal-btns">
              <button class="modal-cancel modal-btn" @click="onClose">关闭</button>
              <button class="modal-sure modal-btn" @click="onComfirm">确定</button>
          </div>
      </div>
      
  </div>
  </transition>
</template>

<script>
export default {
    props : {
        show : {
            type : Boolean,
            default : false
        },
        title : {
            type : String,
            default : ''
        },
        onClose : {
            type : Function,
            default : ()=>{}
        },
        onComfirm:{
            type : Function,
            default : ()=>{}
        }
    }
   
}
</script>

<style scoped>
.modal-container{
    position: fixed;
    left: 0;
    right: 0;
    top : 0;
    bottom: 0;
    background: rgba(0, 0, 0, .5);
}
.flex-center{
    display: flex;
    justify-content: center;
    align-items: center;
}
.modal-content{
    background-color : #f1f1f1;
    padding: 15px;
    box-sizing: border-box;
    border-radius: 5px;
    max-height: 500px;
    max-width: 600px;
    transform: scale(1);
}
.modal-title{
    height: 30px;
    line-height: 30px;
    font-size: 18px;
    text-align: left;
    margin-bottom: 10px;
}
.modal-btns{
    display: flex;
    justify-content: flex-end;
}
.modal-btn{
   padding: 8px 15px;
    margin-top: 15px;    
    cursor: pointer;
    transition: box-shadow .3s ease;
    border: none;
    border-radius: 3px;
}
.modal-cancel{
    order: 1;
    background-color: rgb(224, 223, 223);
}
.modal-sure{
    margin-right: 10px;
    order: 0;
    background: #74b9ff;
    color: #fff;
}
.modal-btn:hover{
    box-shadow: 1px 1px 3px 0px rgba(0, 0, 0, .2);
}
.fade-enter-active, .fade-leave-active {
  transition: opacity .3s ease;
}
.fade-enter, .fade-leave-to  {
  opacity: 0;
}
.fade-enter .modal-content,
.fade-leave-to .modal-content
{
    transform: scale(.2);
}
.fade-enter-active .modal-content,
.fade-leave-active .modal-content{
    transition : all .3s ease;
}



</style>>
