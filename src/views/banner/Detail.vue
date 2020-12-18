<!--
 * @Description: 高盈动态详情页
 * @Author: Harry
 * @Date: 2020-12-15 15:52:53
 * @LastEditTime: 2020-12-16 18:39:41
 * @LastEditors: Harry
-->
<template>
  <!-- hidden PageHeaderWrapper title demo -->
  <page-header-wrapper :title="false">
    <a-card :body-style="{padding: '24px 32px'}" :bordered="false">
      <a-form @submit="handleSubmit" :form="form">
        <a-form-item
          label="标题"
          :labelCol="{lg: {span: 7}, sm: {span: 7}}"
          :wrapperCol="{lg: {span: 10}, sm: {span: 17} }">
          <a-input
            v-decorator="['date']"
            name="name"
            style="width: 100%"
          />
        </a-form-item>
        <a-form-item
          label="发布状态"
          :labelCol="{lg: {span: 7}, sm: {span: 7}}"
          :wrapperCol="{lg: {span: 10}, sm: {span: 17} }"
          :required="false"
        >
          <a-radio-group v-decorator="['target', { initialValue: 1 }]">
            <a-radio :value="1">发布</a-radio>
            <a-radio :value="2">下架</a-radio>
          </a-radio-group>
        </a-form-item>
        <!-- <a-form-item
          label="文章内容"
          :labelCol="{lg: {span: 7}, sm: {span: 7}}"
          :wrapperCol="{lg: {span: 10}, sm: {span: 17} }">
          <TinyMceEditor v-model="content"></TinyMceEditor>
        </a-form-item> -->
        <!-- <a-form-item
          :wrapperCol="{ span: 24 }"
          style="text-align: center"
        >
          <a-button htmlType="submit" type="primary">确定</a-button>
          <a-button style="margin-left: 8px">取消</a-button>
        </a-form-item> -->
      </a-form>
      <div class="uploader-box">
        <div class="uploader-box__hd">
          中文简体
        </div>
        <div class="uploader-box__content">
          <a-form :form="form">
            <a-form-item
              label="banner图"
              :labelCol="{lg: {span: 7}, sm: {span: 7}}"
              :wrapperCol="{lg: {span: 10}, sm: {span: 17} }"
              help="注意：尺寸1920*798px">
              <a-upload
                name="avatar"
                list-type="picture-card"
                class="avatar-uploader"
                :show-upload-list="false"
                action="https://www.mocky.io/v2/5cc8019d300000980a055e76"
                :before-upload="beforeUpload"
                @change="handleChange"
              >
                <img v-if="imageUrl" :src="imageUrl" alt="avatar" />
                <div v-else>
                  <a-icon :type="loading ? 'loading' : 'plus'" />
                  <div class="ant-upload-text">
                    Upload
                  </div>
                </div>
              </a-upload>
            </a-form-item>
            <a-form-item
              label="标题"
              :labelCol="{lg: {span: 7}, sm: {span: 7}}"
              :wrapperCol="{lg: {span: 10}, sm: {span: 17} }">
              <a-input
                v-decorator="['date']"
                name="name"
                style="width: 100%"
              />
            </a-form-item>
          </a-form>
        </div>
      </div>
    </a-card>
  </page-header-wrapper>
</template>

<script>
import { TinyMceEditor } from '@/components'

export default {
  name: 'DynamicDetail',
  components: { TinyMceEditor },
  data () {
    return {
      form: this.$form.createForm(this),
      content: ''
    }
  },
  methods: {
    // handler
    handleSubmit (e) {
      e.preventDefault()
      this.form.validateFields((err, values) => {
        if (!err) {
          console.log('Received values of form: ', values)
        }
      })
    }
  }
}
</script>
