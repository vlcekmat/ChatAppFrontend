<template>
  <div class="messages scrollable">
    <ul>
      <li v-for="message in messages" :key="message">
        {{ message.author }}: {{ message.message }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Messages.vue",
  mounted () {
    this.timer = setInterval(this.updateMessages, 200);
  },
  data() {
    return {
      timer: null,
      messages: []
    }
  },
  methods: {
    updateMessages: function() {
      axios
          .get("https://chat-with-mat-server.herokuapp.com/message")
          .then(response => {
            this.messages = [];
            response.data.forEach(message => {
              this.messages.push({author: message.author, message: message.message})
            });
          }

          );
    }
  },

  beforeDestroy() {
    clearInterval(this.timer);
  }

}
</script>

<style scoped>
  .messages {
    justify-content: left;
    height: 500px;
    background-color: #1e2a2f;
    border: 2px solid #2c3e50;
    border-radius: 5px;
    font-size: large;
    alignment: top;
    width: 100%;
  }

  .messages ul {
    list-style: none;
    padding: 2%;
    margin: 2%;
  }

  .scrollable {
    overflow-y: scroll;
  }
</style>
