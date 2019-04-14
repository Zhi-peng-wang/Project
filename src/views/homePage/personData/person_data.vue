<template>
    <div>
      <div class="panel panel-info">
        <div class="panel-heading">
          个人信息
        </div>
        <div class="panel-body">
          <h1>个人资料界面</h1>
          <div :span="24">
            <el-form label-width="100px">
              <el-form-item label="昵称">
                <el-input v-model="nickname"></el-input>
              </el-form-item>
              <el-form-item label="签名">
                <el-input v-model="sign"></el-input>
              </el-form-item>
              <el-form-item label="年龄">
                <el-input v-model="age"></el-input>
              </el-form-item>
              <el-form-item label="Tel">
                <el-input v-model="tel"></el-input>
              </el-form-item>
              <el-form-item label="邮箱">
                <el-input v-model="email"></el-input>
              </el-form-item>
              <el-form-item label="生日">
                <el-input v-model="brith"></el-input>
              </el-form-item>
              <el-form-item label="地址">
                <el-input v-model="address"></el-input>
              </el-form-item>

              <el-form-item>
                <el-button type="primary" @click="submit_person_data">提交</el-button>
              </el-form-item>
            </el-form>

          </div>
        </div>
      </div>
    </div>
</template>

<script>
    import {getUser} from "../../../api";

    export default {
      data(){
        return{
          nickname: '',
          sign: '',
          age: '',
          tel:'',
          email:'',
          brith:'',
          address:''
        }
      },
      mounted(){
        let id = this.$route.params.id;
        getUser({userid:id})
          .then(res=>{
            console.log("请求个人信息");
            console.log(res.object);
            const result=res.object;
            this.nickname=result.nickname;
            this.sign=result.sign;
            this.age=result.age;
            this.tel=result.phone;
            this.email=result.email;
            this.brith=result.brithday;
            this.address=result.address
          })
          .catch(error=>{
            console.log("请求个人信息失败");
          })
      },
      methods:{
        submit_person_data(){
          console.log("点击事件被触发");
        }
      }
    }
</script>

<style scoped>

</style>
