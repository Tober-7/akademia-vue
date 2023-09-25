<template>
  <div class="div-container">
    <div class="div-container-item-row div-container-item-bb">
      <input class="input" type="text" v-model="input" @keyup.enter="addItem">
      <button class="add" :disabled="isAddDisabled" @click="addItem()">Add</button>
    </div>
    <div class="div-container-item-column div-container-item-bb">
      <span class="text-title">Položky</span>
      <ul v-for="item in validItems" :key="`item-${item.id}`">
        <li class="list-item">
          <span class="delete" @click="deleteItem(item)">X</span>
          {{ item.text.trim() }}
        </li>
      </ul>    
    </div>
    <div class="div-container-item-column">
      <span class="text-title">Zmazané Položky</span>
      <ul v-for="item in deletedItems" :key="`item-${item.id}`">
        <li class="list-item">
          {{ item.text.trim() }}
        </li>
      </ul>    
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        input: "",
        list: [],
      }
    },

    computed: {
      validItems() {
        return this.list.filter(item => !item.is_deleted)
      },

      deletedItems() {
        return this.list.filter(item => item.is_deleted)
      },

      isAddDisabled() {
        return this.input.trim() == "" ? true : false;
      }
    },

    methods: {
      addItem() {
        if (this.input.trim() == "") return;

        this.list.push({
          id: this.list.length + 1,
          text: this.input,
          is_deleted: false
        })
        this.input = ""
      },
      deleteItem(item) {
        item.is_deleted = true
      }
    },
  }
</script>

<style>
  /*#region Fonts*/

  @font-face {
      font-family: "SF-Pro-Display";
      src: url(./assets/SF-Pro-Display-Regular.woff) format(woff);
  }

  /*#endregion*/

  /*#region Other*/

  html, body {
    max-width: 100%;
    overflow-x: hidden;
  }

  header, body{
    margin: 0;
  }

  ::-webkit-scrollbar {
    display: none;
  }

  *{
    font-family: "SF-Pro-Display", sans-serif;
  }

  /*#endregion*/

  /*#region General*/

  .div-container{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: stretch;

    margin: 24px;
    padding: 24px;

    border-radius: 10px;
    box-shadow: 0 0 15px 1px rgba(0, 0, 0, 0.15);
  }

  .div-container-item-row{
    display: flex;
    justify-content: center;

    margin: 24px;
  }

  .div-container-item-column{
    display: flex;
    flex-direction: column;
    align-items: center;

    margin: 24px;
  }

  /* bb = border bottom*/
  .div-container-item-bb{
      padding-bottom: 24px;
      margin-bottom: 0;
      border-bottom: solid 0.1rem #202020;
  }

  /*#endregion*/

  /*#region Input Section*/

  .input{
    min-width: 100px;
    max-width: 300px;
    width: 100%;
    height: 24px;

    padding: 0 8px;

    border-radius: 5px;

    background-color: transparent;
    border: solid 0.1rem #202020;

    color: #202020;
    letter-spacing: 1px;

    transition: 0.2s;
  }

  .input:hover{
    border: solid 0.1rem #49D191;

    transition: 0.2s;
  }

  .add{
    cursor: pointer;

    margin: 0 0 0 12px;

    border-radius: 5px;

    background-color: transparent;
    border: solid 0.1rem #202020;

    transition: 0.2s;
  }

  .add:disabled{
    pointer-events: none;
    cursor: default;

    opacity: 0.5;

    transition: 0.2s;
  }

  .add:hover{
    border: solid 0.1rem #49D191;
    color: #49D191;

    transition: 0.2s;
  }

  /*#endregion*/

  /*#region Item Section*/

  .text-title{
    cursor: default;

    margin: 0 0 24px 0;

    font-size: 40px;
    color: #202020;
    letter-spacing: 1px;
  }

  ul{
    display: flex;
    justify-content: center;

    width: 100%;

    padding: 0;
    margin: 0;

    list-style-type: none;
  }

  .list-item{
    cursor: default;

    display: flex;

    max-width: 100%;

    padding: 8px;
    margin: 12px 0;

    overflow: hidden;
    color: #202020;
    letter-spacing: 1px;

    border-radius: 5px;

    border: solid 0.1rem #202020;
  }

  .delete{
    cursor: pointer;

    margin: 0 12px 0 0;

    transition: 0.2s;
  }

  .delete:hover{
    color: #FF0000;

    transition: 0.2s;
  }

  /*#endregion*/
  
</style>
