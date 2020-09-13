<template>
  <button class="eidtor-btn" @click="btnClick($event)" :title="title">
    <slot>
      <SvgIcon :icon-class="icon"></SvgIcon>
    </slot>
  </button>
</template>

<script>
import SvgIcon from '@/package/SvgIcon.vue'

import '@/assets/icon/b.svg'
import '@/assets/icon/strick.svg'
import '@/assets/icon/button.svg'
import '@/assets/icon/copy.svg'
import '@/assets/icon/backColor.svg'
import '@/assets/icon/formatColor.svg'
import '@/assets/icon/fontName.svg'
import '@/assets/icon/leftIndent.svg'
import '@/assets/icon/rightIndent.svg'
import '@/assets/icon/h1.svg'
import '@/assets/icon/h2.svg'
import '@/assets/icon/h3.svg'
import '@/assets/icon/h4.svg'
import '@/assets/icon/h5.svg'
import '@/assets/icon/h6.svg'
import '@/assets/icon/i.svg'
import '@/assets/icon/img.svg'
import '@/assets/icon/justify.svg'
import '@/assets/icon/l.svg'
import '@/assets/icon/left.svg'
import '@/assets/icon/link.svg'
import '@/assets/icon/m.svg'
import '@/assets/icon/os.svg'
import '@/assets/icon/p.svg'
import '@/assets/icon/redo.svg'
import '@/assets/icon/right.svg'
import '@/assets/icon/s.svg'
import '@/assets/icon/textClear.svg'
import '@/assets/icon/u.svg'
import '@/assets/icon/ul.svg'
import '@/assets/icon/undo.svg'
import '@/assets/icon/upload.svg'
import '@/assets/icon/code.svg'


export default {
  name: "Btn",
  components: {
    SvgIcon
  },
  props:{
      icon:{
          type:[String],
          required:true,
          default:'button'
      }
  },
  data() {
    return {
      title: ""
    };
  },

  methods: {
    btnClick(e) {
      this.$emit("click",e);
    }
  }
};
</script>
<style scoped>
.eidtor-btn {
  margin:0 1px;
  padding:0;
  cursor: pointer;
  box-sizing: border-box;
  width: 24px;
  height: 24px;
  font-size: 14px;
  border: transparent;
  border-radius: 4px;
  background-color: transparent;
  line-height: 24px;
  vertical-align: middle;
  text-align: center;
  outline: none;
}
.eidtor-btn:hover{
  background-color: #dddddd;
  /* fill:#0000FF; */
}
</style>