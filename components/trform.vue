<template>
    <div>
        <form @submit="fanyifangfa" class="form form-inline col-md-4">
          <input typeof="text" placeholder="请输入需要翻译的内容" v-model="shuru" class="form-control">
          <select v-model="lang" class="form-control">
            <option value="en">English</option>
            <option value="it">意大利语</option>
            <option value="fr">法语</option>
            <option value="ja">日语</option>
          </select>
          <input type="submit" value="翻译" class="btn btn-info">
        </form>
    </div>
</template>

<script>
    export default {
        name: "trform",
      data:function(){
        return{
          shuru:"",
          lang:"en",
        }
      },
      methods:{
        fanyifangfa:function (e) {
            this.$emit("fanyitoapp",this.shuru,this.lang);
            e.preventDefault();
          }
      }
    }
</script>

<style scoped>
  form {
    display: block;
    margin-left: auto;
    margin-right: auto;
  }
</style>
