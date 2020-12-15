<template>
    <div>
        
    </div>
</template>

<script>
    import Editor from "@tinymce/tinymce-vue"
    //
    export default {
        name: "TinyMceEditor",
        components: {Editor},
        data() {
            return {
                //编辑器配置
                editorInit：{
                    language_url: "/zh_CN.js",
                    language: "zh_CN",
                    height: 500,
                    menubar: true,
                    plugins: [
                        "advlist autolink lists link image charmap print preview anchor",
                        "searchreplace visualblocks code fullscreen",
                        "insertdatetime media table paste code help wordcount",
                        "image",
                    ],
                    toolbar:
                        "undo redo | formatselect | bold italic backcolor | \
                        alignleft aligncenter alignright alignjustify | \
                        bullist numlist outdent indent | removeformat | image table",
                    branding: false,
                     // 自定义图片上传
                    images_upload_handler: ()=>{}
                }
            }
        },
        model: {
            prop: "content",
            event: "change"
        },
        props: {
            content: {
                type: String,
                default: ""
            }
        }
    },

    
</script>