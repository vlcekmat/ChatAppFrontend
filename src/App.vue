<script>
  import MessageEditor from "./components/MessageEditor.vue";
  import Messages from "./components/Messages.vue";
  export default {
    name: "App",
    components: {
      Messages,
      MessageEditor
    },
    data() {
      return {
      }
    }
  }
</script>

<style>
  .editor {
    position: inherit;
    bottom: -16px;
  }

  #main-interface {
    margin-top: 2%;
  }
</style>

<template>
  <main>
    <div id="main-interface">
      <Messages />
      <MessageEditor />
    </div>

  </main>
</template>

