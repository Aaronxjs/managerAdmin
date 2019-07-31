<template>
  <div id="infor">
      <el-col :span=24>
          <el-form>
            <el-row type="flex" justify="center">
                <el-col :span=12 class="title">
                    公司简介
                </el-col>
            </el-row>
            <el-row type="flex" justify="center">
                <el-col :span=16 class="content">
                    <quill-editor v-model="infoContent" ref="infoQuillEditor" @ready="onEditorReady($event)">
                    </quill-editor>
                </el-col>
            </el-row>
            <el-row type="flex" justify="center">
                <el-button type="primary" @click="submitForm()">修改</el-button>
            </el-row>
          </el-form>
      </el-col>
  </div>
</template>

<script>
  import 'quill/dist/quill.core.css'
  import 'quill/dist/quill.snow.css'
  import 'quill/dist/quill.bubble.css'
  import { quillEditor } from 'vue-quill-editor' //调用编辑器
  export default {
    components: {
        quillEditor
    },
    data() {
      return {
          infoContent: ''
      }
    },
    computed: {
      editor() {
        return this.$refs.myQuillEditor.quill
      }
    },
    mounted() {
      //初始化
    },
    methods: {
        onEditorReady(editor) {
        
        },
        submitForm(){

        }
    }
  }
</script>
<style lang="scss" scoped>
#infor{
    .title{
        text-align: center;
        padding: 10px;
    }
    .content{
        line-height: normal;
        /deep/ .ql-container .ql-editor{
        height: 200px;
        }
    }
}
.el-row{
    padding: 20px;
}
</style>
