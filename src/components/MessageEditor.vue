

<script>
import axios from "axios";
export default {
  name: "MessageEditor.vue",
  data() {
    return {
      message: {author: this.User, message: ""},
      User: "Anonymous"
    }
  },
  methods: {
    updateMessage() {
      if (this.message.message !== "")
        axios.post("https/chat-with-mat-server.herokuapp.com/message",
            {
              author: this.User,
              message: this.message.message
            }
        ).then(response => {})
      this.message = {author: this.User, message: ""};
    }
  }
}
</script>

<template>
  <div class="message-editor">
    <input class="text-field" type="text" v-model="message.message" @keyup.enter="updateMessage()">
    <input class="button-field" type="button" value="SEND" @click="updateMessage()">
    <input class="nickname" v-model="this.User" type="text">
  </div>
</template>

<style scoped>
  .message-editor {
    margin-top: 2%;
    height: 50%;
    background-color: #1e2a2f;
    border: 2px solid #2c3e50;
    border-radius: 10px;
    font-size: large;
    font-style: italic;
    max-height: 122px;
    place-self: center;
    padding-bottom: 8%;
  }

  .message-editor .text-field {
    width: 80%;
    height: 25%;
    border: none;
    border-radius: 10px;
    background-color: #2c3e50;
    color: #ffffff;
    font-size: large;
    font-style: italic;
    margin-left: 9%;
    margin-top: 1%;
    padding: 1%;
  }

  .message-editor .button-field:hover {
    background-color: #2c3e50;
    border: 2px solid #2c3e50;
  }

  .message-editor .button-field {
    width: 25%;
    height: 25%;
    border: #1e2a2f;
    border-radius: 10px;
    background-color: #1e2a2f;
    color: #ffffff;
    font-size: large;
    font-style: italic;
    margin-left: 37%;
    margin-top: 1%;
  }

  .nickname {
    width: 10%;
    height: 2%;
    border: none;
    border-radius: 10px;
    background-color: #2c3e50;
    color: #ffffff;
    font-size: large;
    font-style: italic;
    margin-left: 9%;
    margin-top: 0.5%;
    padding: 0.5%;
  }
</style>
