<template>
    <div class="loginbox" >
        
        <el-form
    ref="ruleFormRef"
    :model="ruleForm"
    status-icon
    :rules="rules"
    label-width="80px"
    class="demo-ruleForm"
  >
  <h2>管理系统</h2>
    <el-form-item label="账号" prop="username">
      <el-input v-model="ruleForm.username" type="username" autocomplete="off" />
    </el-form-item>

    <el-form-item label="密码" prop="password">
      <el-input
        v-model="ruleForm.password"
        type="password"
        autocomplete="off"
      />
    </el-form-item>
    
    <el-form-item>
      <el-button type="primary" class="loginbtn" @click="submitForm(ruleFormRef)"
        >Submit</el-button
      >
      <el-button class="loginbtn" @click="resetForm(ruleFormRef)">Reset</el-button>
    </el-form-item>
  </el-form>
       
    </div>
</template>

<script lang="ts">
import { defineComponent,reactive,toRefs,ref } from "vue";
import type { FormInstance } from 'element-plus'

const ruleFormRef = ref<FormInstance>()

/*
interface LoginData{
  username:string
  password:string
}*/
import {LoginData} from '../type/login'
export default defineComponent({
    setup () {
        const data = reactive(new LoginData())
        const rules={
                username:[
                    { required: true, message: 'Please input Activity name', trigger: 'blur' },
                    { min: 3, max: 5, message: 'Length should be 3 to 5', trigger: 'blur' },
                ],
                password:[
                    { required: true, message: 'Please input Activity name', trigger: 'blur' },
                    { min: 3, max: 10, message: 'Length should be 3 to 10', trigger: 'blur' },
                ]

            }
            const submitForm = (formEl: FormInstance | undefined) => {
  if (!formEl) return
  formEl.validate((valid) => {
    if (valid) {
      console.log('submit!')
    } else {
      console.log('error submit!')
      return false
    }
  })
}

const resetForm = () => {
 data.ruleForm.username=""
 data.ruleForm.password=""
}
        return {...toRefs(data),rules,ruleFormRef,submitForm,resetForm};
    }
});
</script>

<style lang='scss' scoped>
.loginbox{
    width: 100%;
    height: 100%;
    background: url("../assets/bg.png");
    padding: 1px;
    text-align: center;
    .demo-ruleForm{
        width: 40%;
        margin: 200px auto;
        background-color: antiquewhite;
        padding: 30px;
        border-radius: 20px;
    }
    .loginbtn{
        width: 48%;
    }
}

</style>