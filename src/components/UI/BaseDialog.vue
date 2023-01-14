<template>
    <teleport to="body">
        <div @click="$emit('close')"></div>
        <dialog open>
            <header>
                <slot name="header">
                    <h2>{{title}}</h2>
                </slot>
            </header>
            <section>
                <slot></slot>
            </section>
            <menu>
                <slot name="actions">
                </slot>
            </menu>
        </dialog>
    </teleport>
</template>

<script>


    export default {

        name : 'BaseDialog',
        props:['title'],
    }
</script>

<style scoped>
div{
background-color: rgba(0,0,0,0.6);
position: fixed;
top: 0;
left: 0;
width: 100%;
height: 100vh;
z-index: 1;
}
dialog{
    width: 600px;
    min-height: 200px;
    background-color: #fff;
    color: #000;
    border-radius: 0.5rem;
    border: none;
    box-shadow: 2px 2px 4px rgba(0,0,0,0.26);
    z-index: 2;
    position: fixed;
    left: 50%;
    top: 50%;
    transform: translate(-50%,-50%);
}
header{
    width: 100%;
    height: 70px;
    color: #fff;
    background-color: #3a0061;
    padding: 1rem;
    text-align: center;
    border-radius: 0.5rem 0.5rem 0 0;
}
section{
    padding: 1rem;
}
menu{
    display: flex;
    justify-content: flex-end;
    padding: 1rem;
}
</style>