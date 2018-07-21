
[ckeditor5 官网](https://docs.ckeditor.com/ckeditor5/latest/index.html)
# 安装
npm 安装ckeditor5   使用的 10.1.0版本
~~~
npm install --save @ckeditor/ckeditor5-build-classic
~~~

# vue 页面使用
## html
~~~
<textarea id="editor" name="editor" v-model="ruleForm.content"></textarea>
~~~
## 导入

~~~
import ClassicEditor from '@ckeditor/ckeditor5-build-classic';
~~~

## 初始化使用
~~~

mounted() {
    let that = this;
    if (this.editorStatus == null && document.querySelector('#editor')) {
      this.editorStatus = "success";
      ClassicEditor
        .create(document.querySelector('#editor'), {
          ckfinder: {
          // url 是上传图片的路径
          // 后台至少返回两个参数
          // uploaded     1    表示上传成功
          // url               表示编辑器中存放的img标签的src路径
            uploadUrl: 'url?command=QuickUpload&type=Files&responseType=json'
          },
          toolbar: [
            'heading',
            'bold',
            'italic',
            'link',
            'bulletedList',
            'numberedList',
            'blockQuote',
            'undo',
            'redo',
            'imageUpload'
          ],
          image: {
            toolbar: [ 'imageTextAlternative', '|', 'imageStyle:alignLeft', 'imageStyle:full', 'imageStyle:alignRight' ],

            styles: [
              'full',
              'alignLeft',
              'alignRight'
            ]
          }
        })
        .then(editor => {
          that.editor = editor;
        })
        .catch(error => {
          console.error(error);
        });
    }

  },
~~~
## 提交表单
this.editor.getData(); 用于获取编辑器内容
~~~
// 提交表单
    submitForm(formName) {
        this.ruleForm.content = this.editor.getData();
        let that = this;
        this.$refs[formName].validate((valid) => {
          if (valid) {
            this.$axios.post('url', {
              title: this.ruleForm.title,
              content: this.ruleForm.content
            })
              .then(function(response) {
                
              })
              
          } 
        });
      }
~~~	