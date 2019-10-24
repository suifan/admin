<template>
  <div>
    <a-button type="primary" @click="showDrawer"> Open </a-button>
    <a-drawer
      title="Create"
      width="300"
      placement="right"
      :closable="false"
      @close="onClose"
      :visible="visible"
      style="height: calc(100% - 55px);overflow: 'auto';paddingBottom: 53px"
    >
      <a-form :form="form">
        <a-form-item
          label="用户名"
          :labelCol="{ span: 5 }"
          :wrapperCol="{ span: 12 }"
        >
          <a-input
            v-decorator="[
              'username',
              {
                rules: [{ required: true, message: '用户名不能为空!' }]
              }
            ]"
          />
        </a-form-item>
      </a-form>
      <div
        :style="{
          position: 'absolute',
          bottom: 0,
          width: '100%',
          borderTop: '1px solid #e8e8e8',
          padding: '10px 16px',
          textAlign: 'right',
          left: 0,
          background: '#fff',
          borderRadius: '0 0 4px 4px'
        }"
      >
        <a-button
          :style="{
            marginRight: 8
          }"
          @click="onClose"
        >
          Cancel
        </a-button>
        <a-button @click="editUser" type="primary">edit</a-button>
        <a-button @click="handleSubmit" type="primary">Submit</a-button>
      </div>
    </a-drawer>
  </div>
</template>
<script>
export default {
  data() {
    return {
      visible: false,
      formLayout: "horizontal",
      form: this.$form.createForm(this),
      user: {
        username: ""
      }
    };
  },
  methods: {
    showDrawer() {
      this.visible = true;
      this.form.getFieldDecorator("username");
      this.form.setFieldsValue({
        username: "hello"
      });
    },
    onClose() {
      this.form.resetFields();
      this.visible = false;
    },
    editUser() {
      this.user.username = "yuuki";
    },
    handleSubmit(e) {
      e.preventDefault;
      let that = this;
      this.form.validateFields((err, values) => {
        if (!err) {
          alert(that.user.username);
        }
      });
    }
  }
};
</script>
