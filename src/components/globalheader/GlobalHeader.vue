<template>
    <div>
        <nav class="navbar navbar-dark bg-primary justify-content-between mb-4">
            <a class="navbar-brand" href="#">Navbar</a>
            <ul v-if="!user.isLogin" class="list-inline mb-0">
                <li class="list-inline-item"><a href="#" class="btn btn-outline-light">登録</a></li>
                <li class="list-inline-item"><a href="#" class="btn btn-outline-light">新規</a></li>
            </ul>
            <ul v-else class="list-inline mb-0" style="margin-right: 18px">
                <drop-down :title="`こんにちは ${user.name}`"></drop-down>
            </ul>
        </nav>
    </div>
</template>


<script lang="ts">
 import {defineComponent, PropType} from  'vue'
 import DropDown from "@/components/dropdown/DropDown.vue";
 export interface UserProps {
     isLogin: boolean;
     name?: string;
     id?: number;
 }
 export  default defineComponent({
     name: 'GlobalHeader',
     components: {
       DropDown
     },
     props: {
         user: {
             type: Object as PropType<UserProps>,
             required: true
         }

     }
 })
</script>


<style>

</style>
