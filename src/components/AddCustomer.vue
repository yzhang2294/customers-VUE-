<template>
  <div class="addCustomer container">
    <h1 class="page-header">添加用户</h1>
    <form role="form" @submit.prevent="addUser()">
        <div class="well">
            <label>用户信息</label>
            <div class="form-group">
                <label for="name">姓名</label>
                <input type="text" class="form-control" id="name" placeholder="请输入姓名" v-model="customer.name">
            </div>
            <div class="form-group">
                <label for="phone">电话</label>
                <input type="number" class="form-control" id="phone" placeholder="请输入电话" v-model="customer.phone">
            </div>
            <div class="form-group">
                <label for="email">邮箱</label>
                <input type="text" class="form-control" id="name" placeholder="请输入邮箱" v-model="customer.email">
            </div>
            <div class="form-group">
                <label for="education">学历</label>
                <input type="text" class="form-control" id="education" placeholder="请输入学历" v-model="customer.education">
            </div>
            <div class="form-group">
                <label for="school">毕业学校</label>
                <input type="text" class="form-control" id="school" placeholder="请输入毕业学校" v-model="customer.school">
            </div>
            <div class="form-group">
                <label for="profession">职业</label>
                <input type="text" class="form-control" id="profession" placeholder="请输入职业" v-model="customer.profession">
            </div>
            <div class="form-group">
                <label for="profile">个人简介</label>
                <textarea class="form-control" rows="6" id="profile" v-model="customer.profile"></textarea>
            </div>              
        </div>
        <button type="submit" class="btn btn-default">添加</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'addCustomer',
  data () {
    return {
        customer:{}
    }
  },
  methods: {
      addUser:function(){
          if(!this.customer.name || !this.customer.phone|| !this.customer.email){
              console.log('请正确输入');
          }else{
              var newCustomer = {
                  name:this.customer.name,
                  phone:this.customer.phone,
                  email:this.customer.email,
                  education:this.customer.education,
                  school:this.customer.school,
                  profession:this.customer.profession,
                  profile:this.customer.profile
              }

              this.$http.post("http://localhost:3000/users",newCustomer)
                .then((data)=>{
                    this.$router.push({path:"/",query:{alert:'[' + newCustomer.name+ ']'+"信息添加成功"}});
                })             
          }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
