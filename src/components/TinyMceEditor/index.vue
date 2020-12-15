<template>
  <editor
    :api-key="apiKey"
    :init="editorInit"
    v-model="contentHtml"></editor>
</template>

<script>
    import Editor from '@tinymce/tinymce-vue'

    const apiKey = 'pd8sa6ak0ehzqc50oklrhhdpu5rpc3r68owl74xtplnaayck'
    //
    export default {
        name: 'TinyMceEditor',
        components: { Editor },
        props: {
            content: {
                type: String,
                default: ''
            }
        },
        data () {
            return {
                apiKey,
                // 编辑器配置
                editorInit: {
                    language_url: '/tinymce/langs/zh_CN.js',
                    language: 'zh_CN',
                    height: 500,
                    menubar: true,
                    plugins: [
                        'advlist autolink lists link image charmap print preview anchor',
                        'searchreplace visualblocks code fullscreen',
                        'insertdatetime media table paste code help wordcount',
                        'image'
                    ],
                    toolbar:
                        'undo redo | formatselect | bold italic backcolor | alignleft aligncenter alignright alignjustify | bullist numlist outdent indent | removeformat | image table',
                    branding: false,
                     // 自定义图片上传
                    images_upload_handler: () => {}
                },
                contentHtml: '',
                updateTimer: null
            }
        },
        model: {
            prop: 'content',
            event: 'change'
        },
        watch: {
            content (val) {
                this.contentHtml = val
            },
            contentHtml (val) {
                this.$emit('change', val)
            }
        }
    }
</script>
