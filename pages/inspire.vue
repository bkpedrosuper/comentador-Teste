<template>
  <div id="app">
    <form action="">
      <label>Comentário</label>
      <div id="fields">
        <textarea v-model="comment"></textarea>
      </div>
      <label>Autor</label>
      <div id="fields">
        <input v-model="autor" type="text">
      </div>

      <br>
      <v-btn outline color="primary" dark v-on:click="addComment">text</v-btn>

      <div id="show-comments" v-bind:key="message.index" v-for="(message,index) in comments">
        <div id="mostra">
          
          <v-icon>{{message.icon}}</v-icon>
          <label>{{message.message}}</label>
          <label>{{message.cara}}</label>

          <v-btn outline color="deep-purple" dark v-on:click="removeComment(index)"> Remover comentário</v-btn>
        </div>

        <br>
        
      </div>
    </form> 
  </div>
</template>

<script>
import '@fortawesome/fontawesome-free/css/all.css'

export default {
  data(){
    return{
      comment: '',
      autor: '',
      comments : [],
    }
  },
  methods: {
    addComment(){
      if(!this.comment || this.comment=='' || !this.autor || this.autor==''){
        let obj = {
          icon: 'fas fa-ad',
          message: 'Você deve colocar os negóço ali'
        }
        this.comments.push(obj);
        this.autor='';
        this.comment='';
      }
      else{
        let obj = {
          message: "''" + this.comment + "''" + ", ",
          cara: this.autor,
          icon: 'fas fa-code',
        }
        this.comments.push(obj);
        this.autor='';
        this.comment='';
      }
    },
    removeComment(i){
      this.comments.splice(i,1);
    }
  },
}
</script>

<style scoped>
  #fields{
    border: 2px;
    background: #ffffff;
    color: blue;
    display: flex;
    width: 200px;
  }
  #show-comments{
    display: grid;
    margin-top: 10px;
  }

</style>