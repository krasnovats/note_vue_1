<script>
import IconCheck from '@/assets/icons/IconCheck.vue';
import IconRemove from '@/assets/icons/IconRemove.vue';

    export default {
        components: {
           IconCheck, 
           IconRemove,
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

        }
    }
</script>

<template>
    <div class="list">
        <p>{{ id }}</p>
        <div><textarea name="" id="">{{ text }}</textarea></div>
        <button class="button-ready">
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
</style>