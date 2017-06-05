<template>
  <div class="test">
      <input type="text" v-model="title"><br/>
    {{title}}
    <p v-if="showName">{{user.firstName}}</p>
    <p v-else="showName">Guest</p>
    <ul>
        <li v-for="item in items">{{item.title}}</li>
    </ul>
    <button v-on:click="greet('Hello World')">Say Greeting</button>
    <br/>
    <input type="text" v-on:keyup="presskey" v-on:keyup.enter="enterHit">
    <hr/>
    <label>First Name</label>
    <input type="text" v-model="user.firstName">
    <br/>
    <label>Last Name</label>
    <input type="text" v-model="user.lastName">
    <h3>{{fullname}}</h3>
    <h2>{{msg}}</h2>
  </div>
</template>

<script>
export default {
  name: 'test',
  props:{
      msg:{
          type:String,
          default:'Foobar'
      }
  },
  data(){
      return{
          title:'Hello World',
          user:{
              firstName:'John',
              lastName:'Doe'
          },
          showName:true,
          items:[
              {title:'Item One'},
              {title:'Item two'},
              {title:'Item three'}
          ]
      }
  },
  methods:{
      greet:function(greeting){
          alert(greeting);
      },
      presskey:function(e){
          console.log(e.target.value);
      },
      enterHit:function(){
          console.log('You hit enter');
      }
  },
  computed:{
      fullname:function(){
            return this.user.firstName+' '+this.user.lastName;
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

</style>
