<template>
  <div class="lite-editor-box">
    <div class="lite-editor-toolbar">
      <btn
        v-for="(item,index) in buttons"
        :key="index"
        :title="item.title"
        :icon="item.icon"
        @click="btnClick(item,$event)"
      ></btn>
    </div>
    <div
      ref="liteEditorContent"
      contenteditable
      @input="contentChange"
      @blur="editorBlur"
      @focus="editorFocus"
      class="lite-editor-main"
      placeholder="please input"
    ></div>
    <textarea v-model="editorContent" style="display:none;"></textarea>
  </div>
</template>

<script>
import btn from "@/package/btn";

export default {
  name: "Editor",
  components: {
    btn
  },

  data() {
    return {
      buttons: [
        {
          icon: "b",
          title: "blod",
          cmd: {
            aCommandName: "bold",
            aShowDefaultUI: false,
            aValueArgument: null
          }
        },
        {
          icon: "strick",
          title: "strick",
          cmd: {
            aCommandName: "strikeThrough",
            aShowDefaultUI: false,
            aValueArgument: null
          }
        },
        {
          icon: "i",
          title: "i",
          cmd: {
            aCommandName: "italic",
            aShowDefaultUI: false,
            aValueArgument: null
          }
        },
        {
          icon: "u",
          title: "underline",
          cmd: {
            aCommandName: "underline",
            aShowDefaultUI: false,
            aValueArgument: null
          }
        },
        {
          icon: "backColor",
          title: "backColor",
          cmd: {
            aCommandName: "backColor",
            aShowDefaultUI: false,
            aValueArgument: '#ff0000'
          }
        },
        {
          icon: "formatColor",
          title: "Fore Color",
          cmd: {
            aCommandName: "foreColor",
            aShowDefaultUI: false,
            aValueArgument: "#0000FF"
          }
        },
        {
          icon: "fontName",
          title: "Font Name",
          cmd: {
            aCommandName: "fontName",
            aShowDefaultUI: false,
            aValueArgument: "Arial"
          }
        },
        {
          icon: "p",
          title: "program",
          cmd: {
            aCommandName: "formatBlock",
            aShowDefaultUI: false,
            aValueArgument: "p"
          }
        },
        {
          icon: "h1",
          title: "h1",
          cmd: {
            aCommandName: "formatBlock",
            aShowDefaultUI: false,
            aValueArgument: "h1"
          }
        },
        {
          icon: "h2",
          title: "h2",
          cmd: {
            aCommandName: "formatBlock",
            aShowDefaultUI: false,
            aValueArgument: "h2"
          }
        },
        {
          icon: "h3",
          title: "h3",
          cmd: {
            aCommandName: "formatBlock",
            aShowDefaultUI: false,
            aValueArgument: "h3"
          }
        },
        {
          icon: "h4",
          title: "h4",
          cmd: {
            aCommandName: "formatBlock",
            aShowDefaultUI: false,
            aValueArgument: "h4"
          }
        },
        {
          icon: "h5",
          title: "h5",
          cmd: {
            aCommandName: "formatBlock",
            aShowDefaultUI: false,
            aValueArgument: "h5"
          }
        },
        {
          icon: "h6",
          title: "h6",
          cmd: {
            aCommandName: "formatBlock",
            aShowDefaultUI: false,
            aValueArgument: "h6"
          }
        },
        {
          icon: "left",
          title: "left",
          cmd: {
            aCommandName: "justifyLeft",
            aShowDefaultUI: false,
            aValueArgument: null
          }
        },
        {
          icon: "justify",
          title: "justify",
          cmd: {
            aCommandName: "justifyCenter",
            aShowDefaultUI: false,
            aValueArgument: null
          }
        },
        {
          icon: "right",
          title: "right",
          cmd: {
            aCommandName: "justifyRight",
            aShowDefaultUI: false,
            aValueArgument: null
          }
        },
        {
          icon: "leftIndent",
          title: "Left Indent",
          cmd: {
            aCommandName: "indent",
            aShowDefaultUI: false,
            aValueArgument: "1"
          }
        },
        {
          icon: "rightIndent",
          title: "Right Indent",
          cmd: {
            aCommandName: "outdent",
            aShowDefaultUI: false,
            aValueArgument: "-1"
          }
        },
        // {
        //   icon: "link",
        //   title: "link",
        //   cmd: {
        //     aCommandName: "createLink",
        //     aShowDefaultUI: false,
        //     aValueArgument: "http://www.baidu.com"
        //   }
        // },
        {
          icon: "s",
          title: "small",
          cmd: {
            aCommandName: "fontSize",
            aShowDefaultUI: false,
            aValueArgument: 1
          }
        },
        {
          icon: "m",
          title: "middle",
          cmd: {
            aCommandName: "fontSize",
            aShowDefaultUI: false,
            aValueArgument: 3
          }
        },
        {
          icon: "l",
          title: "large",
          cmd: {
            aCommandName: "fontSize",
            aShowDefaultUI: false,
            aValueArgument: 5
          }
        },
        // {
        //   icon: "img",
        //   title: "Image",
        //   cmd: {
        //     aCommandName: "insertImage",
        //     aShowDefaultUI: false,
        //     aValueArgument: null
        //   }
        // },
        {
          icon: "ul",
          title: "UnList",
          cmd: {
            aCommandName: "insertUnorderedList",
            aShowDefaultUI: false,
            aValueArgument: null
          }
        },
        {
          icon: "os",
          title: "Order List",
          cmd: {
            aCommandName: "insertOrderedList",
            aShowDefaultUI: false,
            aValueArgument: null
          }
        },
        // {icon:"upload",title:'upload',cmd:{aCommandName:'bold',aShowDefaultUI:false,aValueArgument:null}},
        {
          icon: "undo",
          title: "undo",
          cmd: {
            aCommandName: "undo",
            aShowDefaultUI: false,
            aValueArgument: null
          }
        },
        {
          icon: "redo",
          title: "redo",
          cmd: {
            aCommandName: "redo",
            aShowDefaultUI: false,
            aValueArgument: null
          }
        },
        {
          icon: "copy",
          title: "copy",
          cmd: {
            aCommandName: "copy",
            aShowDefaultUI: false,
            aValueArgument: null
          }
        },
        {
          icon: "textClear",
          title: "textClear",
          cmd: {
            aCommandName: "removeFormat",
            aShowDefaultUI: false,
            aValueArgument: null
          }
        },
        // {icon:"button",title:'button',cmd:{aCommandName:'bold',aShowDefaultUI:false,aValueArgument:null}}
        // {icon:"code",title:'Source code',cmd:{aCommandName:'formatBlock',aShowDefaultUI:false,aValueArgument:'div'}}
      ],
      editorContent: ""
    };
  },

  methods: {
    execCmd(name = null, ui = false, arg = null) {
      document.execCommand(name, ui, arg);
    },

    contentChange(e) {
      const vm=this;
      let contents=e.target.innerHTML;
      vm.editorContent=contents||''
      vm.$emit('change',contents)
      vm.$emit('input',contents)
    },
    
    editorBlur(){
      this.$emit('blur')
    },

    editorFocus(){
      this.$emit('focus')
    },

    btnClick(item, e) {
      const vm = this;
      e.preventDefault();
      const cmdObj = item.cmd;
      if (cmdObj.aCommandName == "copy") {
        // 复制选中的文本
        vm.execCmd(cmdObj.aCommandName);
      }else if(cmdObj.icon==='code'){
        //todo
        return
      } else {
        vm.execCmd(
          cmdObj.aCommandName,
          cmdObj.aShowDefaultUI,
          cmdObj.aValueArgument
        );
      }
    }
  }
};
</script>

<style scoped>
.lite-editor-box {
  margin: 0;
  padding: 0;
  border: 1px solid #d1d1d1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.lite-editor-box .lite-editor-toolbar {
  min-height: 26px;
  line-height: 24px;
  background-color: #f8f8f8;
  border-bottom: 1px solid #d1d1d1;
}
.lite-editor-box .lite-editor-main {
  padding: 5px;
  margin: 0;
  box-sizing: border-box;
  width: 100%;
  height: 100%;
  outline: none;
  background-color: #ffffff;
}
</style>