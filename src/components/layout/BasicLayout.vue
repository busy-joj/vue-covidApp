<template>
    <el-container class="main">
        <el-header><BasicHeader/></el-header>
        <el-container>
            <el-aside :width="menuWidth"><SideMenu :isCollapse="isCollapse"/></el-aside>
            <el-main>Main</el-main>
        </el-container>
    </el-container>
</template>

<script>
import BasicHeader from './BasicHeader'
import SideMenu from './SideMenu'
import useBreakpoint from '@/composables/useBreakpoint'
import { computed } from 'vue'

export default {
    name:"basicLayout",
    components:{
        BasicHeader,
        SideMenu
    },
    setup(){
        const { type } = useBreakpoint()
        const isCollapse = computed(()=>type.value === "sm")
        const menuWidth = computed(()=>isCollapse.value ? "65px" : "200px")
        return{
            isCollapse,menuWidth
        }
    }
}
</script>

<style>
.el-header{
    background:#4bb480bb;color:#fff;display:flex;justify-content:center;align-items:center;
}
.main{height:100%;}
</style>