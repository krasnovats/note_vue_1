<script>
import IconCheck from '@/assets/icons/IconCheck.vue';
import IconRemove from '@/assets/icons/IconRemove.vue';
import IconSearch from '@/assets/icons/IconSearch.vue';

    export default {
        components: {
           IconCheck, 
           IconRemove,
           IconSearch,
        },
        props: {
            id: {
                type: Number,
                required: true
            },
            text: {
                type: String,
                required: true
            },

     
        },
        data () {
            return {
                editText: this.text,
                isReady: false,
            }
        },
        methods: {
            ready () {
                this.isReady = !this.isReady;
            }
        }
    }
</script>

<template>

<div class="list">


        <p class="list-id">{{ id }}</p>
        <div><textarea v-model="editText" :style="{textDecoration:  isReady ?'line-through' : 'none'}"  @keyup.enter="$emit('change', id, editText)">{{ text }}</textarea></div>
        <button class="button-ready" @click="ready">
           <IconCheck/> 
         </button>
        <button @click="$emit('remove', id)" class="button-remove">
            <IconRemove/>
        </button> 
    </div>
</template>

<style>

.list {
    padding-bottom: 20px;
    margin: 20px 0;
    border-bottom: 1px solid gray;
  
}

.button-ready {
    color: green;
}

.button-remove {
    color: brown;
}

.list-id {
     font-weight: bold;
}



</style>