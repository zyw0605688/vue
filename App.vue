<template>
  <div id="app">
    <h1 class="text-muted ">在线翻译</h1>
    <h5 class="text-muted">简单 / 易用 / 便捷</h5>
    <!--<trform @fanyitoapp="fanyijieguo"></trform>
    <out v-text="jieguo"></out>-->

    <input type="text" v-model="inputText">
    <select v-model="selectLang">
      <option value="en">English</option>
    </select>
    <input type="button" value="翻译" @click="fanyijieguo" />

    <p v-model="dayinjieguo">{{dayinjieguo}}</p>
  </div>
</template>

<script>
import trform from '@/components/trform'
import out from '@/components/out'

export default {
  name: 'App',
  data:function(){
    return{
      jieguo:"",
      dayinjieguo:"",
      inputText:"",
      selectLang:"en",

    }
  },
  components: {
    trform,out
  },
  methods:{
    fanyijieguo:function (shurutext,xuanzelang) {
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20181126T030807Z.84872243bdf00f14.ef830d0690007daadf1eaec59d63dda46101c751\n&lang='+this.selectLang+'&text='+this.inputText)
        .then((response)=>{
          console.log(response.body.text[0]);
          this.dayinjieguo = response.body.text[0];
        })
      console.log(shurutext);
    },
  },
}
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
}
h1,h5,div,footer{
    display: block;
    text-align: center;
    margin:15px;
  }
h1{
  margin-top: 100px;
}
</style>
