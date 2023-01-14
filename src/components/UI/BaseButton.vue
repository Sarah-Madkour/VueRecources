<template>
    <button class="badge" :type="type" :class="mode">
        <slot></slot>
    </button>
</template>

<script>
    export default {
        name :'BaseButton',
        props:['type' , 'mode']
    }
</script>

<style scoped>
.badge{
    background-color: #3a0061;
    color: #fff;
    width: 100px;
    height: 40px;
    border: none;
    outline: none;
    color: #fff;
    text-transform: capitalize;
    font-size: 17px;
    font-weight: 600;
    margin: 0.5rem 0;
    cursor: pointer;
    margin: 1rem 0;
    padding: .5rem;
}
button:hover,
button:active{
    background-color: #edd2ff;
}

.flat{
    background-color: transparent;
    color: #3a0061;
    border: none;
}
.flat:active{
    background-color: #3a0061;
}
</style>