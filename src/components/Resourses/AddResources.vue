<template>
    <base-dialog v-if="dataIsInvalid" title="Invalid Input" @close="confirmError">
        <template #default>
            <p>Unfortunately, at least one input value is invalid!</p>
            <p>Please check your inputs and make sure you enter few characters.</p>
        </template>
        <template v-slot:actions>
            <base-button @click="confirmError">okay</base-button>
        </template>
    </base-dialog>
    <base-card>
        <form @submit.prevent="submitForm">
            <div>
                <label for="title">title</label>
                <input id="title" type="text" v-model.trim="title"/>
            </div>
            <div>
                <label for="desc">description</label>
                <textarea id="desc"  rows="5" v-model.trim="desc"></textarea>
            </div>
            <div>
                <label for="link">link</label>
                <input type="url" id="link" v-model.trim="link">
            </div>
            <div>
                <base-button class="btn">add resource</base-button>
            </div>
        </form>
    </base-card>
</template>

<script>
import BaseButton from '../UI/BaseButton.vue'
import BaseCard from '../UI/BaseCard.vue'
import BaseDialog from '../UI/BaseDialog.vue'

    export default {
    components: { BaseCard, BaseButton, BaseDialog },
            name : 'AddResources',
            inject:['addNewResource'],
            data(){
                return{
                    title:'',
                    desc:'',
                    link:'',
                    dataIsInvalid : false
                }
            },
            methods:{
                submitForm(){
                  const enteredTitle = this.title;
                  const enteredDesc = this.desc;
                  const enteredUrl = this.link;

                    if(enteredTitle==='' ||
                        enteredDesc==='' ||
                        enteredUrl===''){
                            this.dataIsInvalid = true;
                            return;
                        }

                  this.addNewResource(enteredTitle , enteredDesc , enteredUrl)
                },
                confirmError(){
                    this.dataIsInvalid = false
                }
            }
        }
</script>

<style scoped>
label{
    text-transform: capitalize;
    font-weight: 600;
    display: block;
    margin-bottom: 0.5rem;
}
input{
    height: 25px;
    padding: 0.25rem;
}
textarea{
    padding: 0.5rem
}
input,textarea{
    width: 100%;
}
input:hover,
textarea:hover{
    background-color: #fdf0fd;
}
div{
    margin-block: 1rem;
}
.btn{
    width:170px
}
</style>