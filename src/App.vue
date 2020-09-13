<template>
  <div id="app">
    <editor 
    @change="editorContentChange"
    @focus="editorFocus"
    @blur='editorBlur'
    ></editor>
  </div>
</template>

<script>
import editor from "@/components/editor.vue";

export default {
  name: "App",
  components: {
    editor
  },
  data() {
    return {};
  },
  methods: {
    editorContentChange(contents) {
      console.log(contents);
    },
    
    editorFocus(){
      console.log('focus')
    },

    editorBlur(){
      console.log('blur')
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center;
  color: #2c3e50;
  margin-top: 60px; */
  font-size: 14px;
  color: #000000;
}
</style>
