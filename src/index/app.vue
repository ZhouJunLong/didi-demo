<template>
  <view>
    <text>{{message}}</text>
    <text>{{value1}}</text>
    <button v-on:click="reverseMessage">反转消息</button>
     <button v-on:click="getStorage">获取本地存储</button>
  </view>
</template>
<script>
  export default {
    data(){
      return {
      	message: 'Hello Tenon',
        value1: '111111'
      }
    },
    methods: {
      reverseMessage(){
        this.message = this.message.split('').reverse().join('')
      },
      getStorage(){
        
        let value1 = Storage.get("key1");
        this.value1 = value1
        console.log('1111',value1);
        let dialog = new Dialog();
        dialog.confirm("title", "test", "OK", "Cancel",
          () => {
              Toast.show('ok click');
          }, () => {
              Toast.show('cancel click');
          });
        }
    },
    mounted(){
      Storage.set("key1", "value1111");
      
    }
  }
</script>