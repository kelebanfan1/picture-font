<template>
  <div id="loginPage">
    <div class="title">鱼皮云图库-用户登陆</div>
    <a-form
      :model="formState"
      name="basic"
      :label-col="{ span: 8 }"
      :wrapper-col="{ span: 16 }"
      autocomplete="off"
      @finish="onFinish"
      @finishFailed="onFinishFailed"
    >
      <a-form-item :rules="[{ required: true, message: '请输入账号!' }]">
        <a-input placeholder="请输入账号" v-model:value="formState.username" />
      </a-form-item>

      <a-form-item :rules="[{ required: true, message: '请输入密码!' }]">
        <a-input-password placeholder="请输入密码" v-model:value="formState.password" />
      </a-form-item>

      <div class="toRegister">没有账号？<span @click="toRegister">去注册</span></div>

      <a-form-item :wrapper-col="{ offset: 8, span: 16 }">
        <a-button type="primary" html-type="submit">登陆</a-button>
      </a-form-item>
    </a-form>
  </div>
</template>
<script lang="ts" setup>
import { reactive } from 'vue'
import { useRouter } from 'vue-router'
const router = useRouter()
// 前往登陆页面
const toRegister = () => {
  router.push('/user/register')
}
interface FormState {
  username: string
  password: string
}

const formState = reactive<FormState>({
  username: '',
  password: '',
})
const onFinish = (values: any) => {
  console.log('Success:', values)
}

const onFinishFailed = (errorInfo: any) => {
  console.log('Failed:', errorInfo)
}
</script>
<style scoped lang="scss">
#loginPage {
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-left: -10%;
  .title {
    font-size: 25px;
    font-weight: 500;
    margin-left: 120px;
  }
  .ant-form {
    margin-top: 20px;
    width: 500px;
    .ant-input,
    .ant-input-password {
      margin-left: 150px;
    }

    .toRegister {
      margin-left: 385px;
      span {
        color: #1677ff;
        cursor: pointer;
      }
    }
    .ant-btn {
      margin-top: 20px;
      width: 100%;
      margin-left: -17px;
    }
  }
}
</style>
