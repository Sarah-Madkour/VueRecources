<template>
    <base-card>
        <header>
            <h2>{{title}}</h2>
            <base-button @click="removeResource(id)" mode="flat">delete</base-button>
        </header>
        <p>{{desc}}</p>
        <a :href="link">Vue resource</a>
    </base-card>
</template>

<script>
import BaseButton from '../UI/BaseButton.vue'
import BaseCard from '../UI/BaseCard.vue'
    export default {
        components: { 
            BaseCard,
            BaseButton  
        },
        name : 'ResourcesItem',
        props:['id' , 'title' , 'desc' , 'link'],
        inject:['removeResource']
    }
</script>

<style scoped>
header{
    display: flex;
    justify-content: space-between;
    align-content: center;
}
a{
    text-decoration: none;
    color: #cc8213;
    font-weight: 600;
    text-transform: capitalize;
}
p{
    margin-bottom: 1rem;
}
</style>