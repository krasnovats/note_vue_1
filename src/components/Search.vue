<script>

import IconSearch from '@/assets/icons/IconSearch.vue';

    export default {
        components: {

           IconSearch,
        },
        
    }
</script>




<template>
    <div class="search_box">
        <IconSearch class="search-icon" @click="search"/>
        <input v-model="searchQuery" class="input-search" type="text" placeholder="Найти..." @keyup.enter="search">
    </div>
</template>

<style>
.search_box {
  position: relative;
  display: flex;
  align-items: center;
  width: 100%;
  margin-bottom: 60px;
}

.search-icon {
  position: absolute;
  left: 10px;
  top: 45%;
  transform: translateY(-50%); /* Центрирование по вертикали */
  cursor: pointer;
}

.input-search {
  padding-left: 40px;
  width: 100%;
  border-bottom: 1px solid gray;
  border-radius: 0;
  padding-bottom: 10px;

}


</style>