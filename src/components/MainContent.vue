<template>
    <h2 class="content-title">{{ content.label }}</h2>
    <component :is="targetComponent"></component>
</template>

<script>
import { defineAsyncComponent } from 'vue'

export default {
    name:"MainContent",
    props:{
        content:{
            type:Object,
            default(){
                return{
                    label:"test",
                    path:"test",
                    index:"test"
                }
            }
        }
    },
    data(){
        return {
            targetComponent:null,
        }
    },
    watch:{
        content:{
            deep : true,
            handler: function(newValue){
                this.targetComponent = defineAsyncComponent(()=>
                import(`@/components/${newValue.path}/${newValue.index}.vue`))
                // console.log(this.targetComponent.name)
            }
        }
    }
}
</script>

<style>

</style>