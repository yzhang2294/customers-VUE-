<template>
  <div class="details container">
    <h1 class="page-header">
      {{customer.name}}
      <span class="pull-right">
        <router-link class="btn btn-primary" v-bind:to="'/update/'+ customer.id">编辑</router-link>
        <button class="btn btn-danger" @click="deleteCustomer(customer.id)">删除</button>
      </span>
      </h1>
    <ul class="list-group">
        <li class="list-group-item"><span class="glyphicon glyphicon-user"></span>  {{customer.name}}</li>
        <li class="list-group-item"><span class="glyphicon glyphicon-align-center"></span>  {{customer.phone}}</li>
        <li class="list-group-item"><span class="glyphicon glyphicon-user"></span>  {{customer.email}}</li>
        <li class="list-group-item"><span class="glyphicon glyphicon-align-center"></span>  {{customer.education}}</li>
        <li class="list-group-item"><span class="glyphicon glyphicon-user"></span>  {{customer.school}}</li>
        <li class="list-group-item"><span class="glyphicon glyphicon-align-center"></span>  {{customer.profession}}</li>
        <li class="list-group-item"><span class="glyphicon glyphicon-user"></span>  {{customer.profile}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'customerDetails',
  data () {
    return {
        customer:""
    }
  },
  methods: {
    getCustomers:function(id){
        this.$http.get("http://localhost:3000/users/"+id)
          .then((data) =>{
              this.customer = data.data;
          },function(){
            console.log('请求失败');
          })        
    },
    deleteCustomer:function(id){
        this.$http.delete("http://localhost:3000/users/"+id)
          .then((data)=>{
            this.$router.push({path:'/',query:{alert:'[' + this.customer.name+ ']'+"信息已删除"}});
          })  
    }
  },
  created() {
      this.getCustomers(this.$route.params.id);   
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
