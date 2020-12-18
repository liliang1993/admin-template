<!--
 * @Description: 高盈动态详情页
 * @Author: Harry
 * @Date: 2020-12-15 15:52:53
 * @LastEditTime: 2020-12-18 19:40:12
 * @LastEditors: Harry
-->
<template>
  <!-- hidden PageHeaderWrapper title demo -->
  <page-header-wrapper :title="false">
    <a-card :body-style="{padding: '24px 32px'}" :bordered="false">
      <a-form @submit="handleSubmit" :form="form">
        <a-form-item
          label="选择年度"
          :labelCol="{lg: {span: 7}, sm: {span: 7}}"
          :wrapperCol="{lg: {span: 10}, sm: {span: 17} }">
          <a-input
            v-decorator="['date']"
            name="name"
            style="width: 100%"
          />
        </a-form-item>
        <a-form-item
          label="选择日期"
          :labelCol="{lg: {span: 7}, sm: {span: 7}}"
          :wrapperCol="{lg: {span: 10}, sm: {span: 17} }">
          <a-input
            v-decorator="['date']"
            name="name"
            style="width: 100%"
          />
        </a-form-item>
        <a-form-item
          label="更新内容"
          :labelCol="{lg: {span: 7}, sm: {span: 7}}"
          :wrapperCol="{lg: {span: 10}, sm: {span: 17} }">
          <a-tabs default-active-key="1" @change="callback">
            <a-tab-pane key="1" tab="中文简体">
               <a-textarea placeholder="Basic usage" :rows="4" :maxLength="10" />
            </a-tab-pane>
            <a-tab-pane key="2" tab="中文简体" force-render>
              <a-textarea placeholder="Basic usage" :rows="4" />
            </a-tab-pane>
            <a-tab-pane key="3" tab="英文">
               <a-textarea placeholder="Basic usage" :rows="4" />
            </a-tab-pane>
          </a-tabs>
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

      <a-row>
        <a-col :span="24" style="text-align: center;">
          <a-button htmlType="submit" type="primary">确定</a-button>
          <a-button style="margin-left: 8px">取消</a-button>
        </a-col>
      </a-row>
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
