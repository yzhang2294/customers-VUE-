<template>
  <div class="customers container">
    <Alert v-if="msg" v-bind:message="msg"></Alert>
    <h1 class="page-header">用户管理系统</h1>
    <input type="text" v-model="inputtext" class="form-control" placeholder="搜索用户姓名">
    <div class="table-responsive">
      <table class="table table-striped">
        <thead>
          <tr>
            <th>姓名</th>
            <th>电话</th>
            <th>邮箱</th>
            <th></th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="customer in filterBy(customers,inputtext)">
            <td>{{customer.name}}</td>
            <td>{{customer.phone}}</td>
            <td>{{customer.email}}</td>
            <td><router-link class="btn btn-default" v-bind:to="'/customer/' + customer.id">详情</router-link></td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import Alert from './Alert'

export default {
  name: 'customers',
  data () {
    return {
      customers:[],
      msg:"",
      inputtext:""
    }
  },
  methods: {
    getCustomers:function(){
      this.$http.get("http://localhost:3000/users")
          .then((data) => {
            //console.log(data);
            this.customers = data.data;
          },function(){
            console.log('请求失败');
          })        
    },
    filterBy:function(customers,value){
      return customers.filter(function(customer){
        return customer.name.match(value);
      })
    }
  },
  created() {
    if(this.$route.query.alert){
      this.msg = this.$route.query.alert;
    }
    this.getCustomers();
  },
  components: {
    Alert
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
