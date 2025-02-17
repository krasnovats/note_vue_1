<script>
  import List from './components/List.vue'
  import Header from './components/Header.vue'
  import Search  from './components/Search.vue';

  export default {
    components: {   
      List,
      Header,
      Search,
    },
    data () {
      return {
        lists: [
          {
            id: 1,
            text: 'первая задача'
          },
          {
            id: 2,
            text: 'вторая задача'
          },
        ],
        newText: '',
        backgroundColor: '',
        isNewStyle: false, 
      }
    },
    methods: {
      add () {
        let id = this.lists.length + 1;
        if (this.newText.length < 1) {
          alert ('Заполните поле') 
        } else {
          this.lists.push({
            id: id,
            text: this.newText
          })
        }
      },
      remove (id) {
        this.lists = this.lists.filter(list => list.id !== id);
        this.updateId();
      },

      updateId () {
        this.lists = this.lists.map((list, index)=> {
          return {...list, id: index + 1};
        })
      },

      change (id, text) {
        this.lists = this.lists.map(list => 
        list.id === id ? {...list, text} : list
        )
      },
      toggleStyle () {
        this.isNewStyle = !this.isNewStyle;
      } 
      },
      computed: {
      styleClass() {
        return this.isNewStyle ? 'new-style' : 'default-style'; // Определяем класс стиля в зависимости от состояния
      }
    },
  }
</script>

<template>
  <Header
  @toggle-style="toggleStyle"
  />
  <div class="main_block container">

  <div :class="styleClass" class="items-box">
    <Search />

    <List
        v-for="list in lists"
        :key="list.id"
        :id="list.id"
        :text="list.text"
        :currentStyle="styleClass"
        @change="change"
        @remove="remove"
        />
  </div>

    <div class="new_item">
      <h2>Введите новую задачу</h2>
      <div class="new_item-item">
        <div>
          <textarea v-model="newText" class="new_item-item-text" @keyup.enter="add"></textarea>
        </div>
        <button @click="add" class="button-save">Добавить</button>
      </div>
    </div>
  </div>
</template>

<style>

body {
  background: #f7f7f7;
}

h2 {
  margin-bottom: 20px;
}
  .main_block {
   position: relative;
   padding-top: 80px;
  }

  .new_item-item {
    margin-top: 20px 0;
  }

  .new_item-item-text{
    width: 600px;
    height: 200px;
    margin-bottom: 20px;
  }

  button {
    background: none; /* Убираем фон */
    border: none; /* Убираем рамку */
    cursor: pointer; /* Указываем, что это кнопка */
    transition: color 0.3s; /* Плавный переход цвета */
  }

  .button-save {
    background: rgb(1, 44, 184);
    color: white;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    padding: 7px 18px;
    border-radius: 4px;
    font-size: 14px;
  }

  button:hover {
    opacity: 0.8;
  }

  button:active {
    opacity: 1;
  } 

  textarea, input {
    border: none; /* Убирает рамку */
    background: rgb(255, 255, 255); /* Убирает фон */
    padding: 5px 10px; /* Убирает внутренние отступы */
    border-radius: 8px;
    margin: 0; /* Убирает внешние отступы */
    font: inherit; /* Устанавливает шрифт как у родителя */
    color: inherit; /* Устанавливает цвет текста как у родителя */
    resize: none; /* Убирает возможность изменения размера текстового поля */
    outline: rgb(1, 36, 153);
    box-shadow: none; /* Убирает тень (если есть) */
}

textarea:focus {
    border: 2px solid rgb(225, 234, 253); /* Пример стиля при фокусе */ 
}
  

.items-box {
  position: absolute;
  width: 600px;
  padding: 20px;
  background-color: white;
  border-radius: 8px;
  
}


.new-style {
  transition: all 0.8s;
  transform: translateX(0%);
}

.default-style {
  transition: all 0.8s;
  transform: translateX(-200%);
  
}
</style>