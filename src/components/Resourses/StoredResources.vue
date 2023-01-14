<template>
    <ul>
      <resources-item 
        v-for="res in resources" 
        :key="res.id"
        :id="res.id"
        :title="res.title"
        :desc="res.description"
        :link="res.link">
      </resources-item>
    </ul>
</template>

<script>
import ResourcesItem from './ResourcesItem.vue';

    export default {
        name : 'StoredResources',
        components:{
            ResourcesItem,
        },
        inject:['resources']
    }
</script>

<style scoped>

</style>