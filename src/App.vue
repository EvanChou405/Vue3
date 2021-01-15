<template>
  <div class="container">
    <global-header :user="currentUser"></global-header>
    <column-list :list="list"></column-list>

  </div>
</template>

<script lang="ts">
  import {defineComponent} from 'vue'
  import ColumnList, {ColumnProps} from "./components/columnlist/ColumnList.vue"
  import 'bootstrap/dist/css/bootstrap.min.css'
  import GlobalHeader, {UserProps} from "@/components/globalheader/GlobalHeader.vue";
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
  export default defineComponent({
    name: 'App',
    components: {
      ColumnList,
      GlobalHeader
    },
    setup() {
      return {
        list: testData,
        currentUser
      }
    }
  })
</script>

<style>
</style>
