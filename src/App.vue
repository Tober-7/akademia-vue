<template>
  <div class="div-container">
    <div class="div-container-item div-container-item-bb">
      <input class="input" type="text" v-model="input">
      <button class="add" @click="addItem()">Add</button>
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
    methods: {
      addItem() {
        this.list.push({
          id: this.list.length + 1,
          text: this.input,
          is_deleted: false
        })
        this.input = ""
      }
    },
  }
</script>

<style scoped>
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

  .div-container-item{
    display: flex;
    justify-content: center;

    margin: 24px;
  }

  /* bb = border bottom*/
  .div-container-item-bb{
      padding-bottom: 24px;
      border-bottom: solid 1px #202020;
  }

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

  .add:hover{
    border: solid 0.1rem #49D191;
    color: #49D191;

    transition: 0.2s;
  }
</style>
