<template>
  <div class="container">
    <global-header :user="currentUser"></global-header>
    <column-list :list="list"></column-list>
    <validate-form @form-submit="onFormSubmit">
      <div class="mb-3">
        <label class="form-label">mail address</label>
        <validate-input
          type="text"
          :rules = "emailRules"
          v-model = "emailVal"
          placeholder="请输入邮箱地址"
          ref = "inputRef"
        />
        <div class="form-text" v-if="emailRef.error">
          {{emailRef.message}}
        </div>
      </div>
      <div class="mb-3">
        <label class="form-label">password</label>
        <validate-input
            type="password"
            placeholder="请输入暗証番号"
            :rules="passwordRules"
            v-model="passwordVal"
        />
      </div>
      <template #submit>
        <span class="btn btn-danger">submit</span>
      </template>
    </validate-form>

  </div>
</template>

<script lang="ts">
  import {defineComponent, reactive, ref} from 'vue'
  import ColumnList, {ColumnProps} from "./components/columnlist/ColumnList.vue"
  import ValidateInput, {RulesProp} from "@/components/validateinput/ValidateInput.vue";
  import 'bootstrap/dist/css/bootstrap.min.css'
  import GlobalHeader, {UserProps} from "@/components/globalheader/GlobalHeader.vue";
  import ValidateForm from "@/components/validateform/ValidateForm1.vue"
  const currentUser: UserProps = {
    isLogin: true,
    name: 'Evan'
  }
  const testData: ColumnProps[] = [
    {
      id: 1,
      title: '合格証書1',
      description: 'this is a test1',
      avatar: 'https://cdn.favware.tech/img/tslogo.png'
    },
    {
      id: 2,
      title: '合格証書2',
      description: 'this is a test2'
    },
  ]
  const emailReg = /^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$/
  export default defineComponent({
    name: 'App',
    components: {
      ColumnList,
      GlobalHeader,
      ValidateInput,
      ValidateForm
    },
    setup() {
      const inputRef = ref<any>()
      const emailVal = ref('')
      const emailRules: RulesProp = [
      {type: 'required', message: '电子邮箱地址不能为空'},
      {type: 'email', message: '请输入正确的电子邮箱格式' }
      ]
      const passwordVal = ref('')
      const passwordRules: RulesProp = [
        {type: 'required', message: '暗証番号不能为空'}
      ]
      const emailRef = reactive({
        val: '',
        error: false,
        message: ''
      })
      const onFormSubmit = (result: boolean) => {
        console.log('result',inputRef.value.validateInput())
      }
      return {
        list: testData,
        currentUser,
        emailRef,
        emailRules,
        emailVal,
        passwordVal,
        passwordRules,
        onFormSubmit,
        inputRef
      }
    }
  })
</script>

<style>
</style>
