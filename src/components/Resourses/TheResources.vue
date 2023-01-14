<template>
   <base-card class="form">
    <base-button class="btn" @click="setSelectedTab('stored-resources')" :mode="storedResourcesMode">stored resources</base-button>
    <base-button class="btn" @click="setSelectedTab('add-resources')" :mode="addResourcesMode">add resources</base-button>
   </base-card>
   <keep-alive>
    <component :is="activeTab"></component>
   </keep-alive>
</template>

<script>
import BaseButton from '../UI/BaseButton.vue'
import BaseCard from '../UI/BaseCard.vue'
import AddResources from './AddResources.vue'
import StoredResources from './StoredResources.vue'
    export default {
        components: { 
            BaseCard ,
            BaseButton,
            AddResources,
            StoredResources
        },
        name :'TheForm',
        data(){
            return{
            resources:[
                {
                id:'official-guide',
                title:'Official Guide',
                description : 'The official Vue.js documentation.',
                link: 'https://vuejs.org/'
                },
                {
                id:'google',
                title:'Google',
                description : 'learn to google..',
                link: 'https://google.com/'
                }
            ],
                activeTab: 'stored-resources'
            }
        },
        computed:{
            storedResourcesMode(){
                return this.activeTab==='stored-resources' ? null : 'flat'
            },
            addResourcesMode(){
                return this.activeTab==='add-resources' ? null : 'flat'
            }
        },
        provide(){
            return{
                removeResource:this.removeResource,
                resources:this.resources,
                addNewResource :this.addNewResource
            }
        },
        methods:{
            removeResource(resId){
                const resIndex = this.resources.find((res)=> res.id === resId)
                this.resources.splice(resIndex , 1)
            },
            setSelectedTab(tab){
            this.activeTab = tab
           },
           addNewResource(enteredTitle , enteredDesc , enteredUrl){
                const newResource = {
                    id: new Date().toISOString(),
                    title : enteredTitle,
                    description : enteredDesc,
                    link : enteredUrl
                }
                this.resources.unshift(newResource)
                this.activeTab = 'stored-resources'
           }
        }
    }
</script>

<style scoped>
.form{
    display: flex;
    justify-content: space-between;
    align-content: center;
}
.btn{
    width:170px
}
</style>