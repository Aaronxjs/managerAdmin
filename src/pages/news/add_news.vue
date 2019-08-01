<template>
  <div>
    <el-row class="warp">
      <!--
      Form 组件提供了表单验证的功能，只需要通过 rule 属性传入约定的验证规则，并 Form-Item 的 prop 属性设置为需校验的字段名即可。具体可以参考官网：http://element.eleme.io/#/zh-CN/component/form
      -->
      <el-col :span="24" class="warp-main">
        <el-form ref="infoForm" :model="infoForm" :rules="rules" label-width="120px">
          <el-form-item>
            <el-col align="center">编辑新闻</el-col>
          </el-form-item>
          <el-form-item label="标题" prop="a_title">
            <el-input v-model="infoForm.a_title"></el-input>
          </el-form-item>

          <el-form-item label="分类" prop="a_source">
              <el-cascader
                v-model="value"
                :options="options"
                @change="handleChange"></el-cascader>
          </el-form-item>
          <!--使用编辑器
          -->
          <el-form-item label="详细">
            <div class="edit_container">
              <quill-editor v-model="infoForm.a_content"
                            ref="myQuillEditor"
                            class="editer"
                             @ready="onEditorReady($event)">
              </quill-editor>
            </div>
          </el-form-item>

          <el-form-item align="center">
            <el-button type="primary" @click="onSubmit">确认提交</el-button>
          </el-form-item>
        </el-form>
      </el-col>

    </el-row>
  </div>
</template>

<script>
  import 'quill/dist/quill.core.css'
  import 'quill/dist/quill.snow.css'
  import 'quill/dist/quill.bubble.css'
  import { quillEditor } from 'vue-quill-editor' //调用编辑器
  export default {
    components: {
      //使用编辑器
      quillEditor
    },
    data() {
      return {
        infoForm: {
          a_title: '',
          a_source: '',
          a_content:'',
          editorOption: {}
        },
        //表单验证
        rules: {
          a_title: [
            {required: true, message: '请输入标题', trigger: 'blur'}
          ],
          a_content: [
            {required: true, message: '请输入详细内容', trigger: 'blur'}
          ]
        },
        options: [
          {
            value: '1',
            label: '公司动态',
            children: [
             {
              value: '2',
              label: '公司动态'
             },
             {
              value: '3',
              label: '公司动态'
             }
            ]
          },
          {
            value: '4',
            label: '行业动态',
            children: [
             {
              value: '5',
              label: '行业动态'
             },
             {
              value: '6',
              label: '行业动态'
             }
            ]
          }
        ]
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
      onSubmit() {

      }
    },

  }
</script>
<style lang="scss" scoped>
  .edit_container{
    line-height: normal;
    /deep/ .ql-container .ql-editor{
      height: 200px;
    }
  }
</style>
