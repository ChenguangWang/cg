<template>
  <a-card hoverable class="common-card" title="联系方式">
    <a-descriptions :column="1">
      <a-descriptions-item>
        <template #label>
          <PhoneOutlined class="ant-icon" />
        </template>
        177 1034 1026
      </a-descriptions-item>
      <a-descriptions-item>
        <template #label>
          <MailOutlined class="ant-icon" />
        </template>
        wcg1026@163.com
      </a-descriptions-item>
      <a-descriptions-item>
        <template #label>
          <GithubOutlined class="ant-icon" />
        </template>
        <a href="https://github.com/ChenguangWang" target="_blank">https://github.com/ChenguangWang</a>
      </a-descriptions-item>
      <a-descriptions-item>
        <template #label>
          <WechatOutlined class="ant-icon" />
        </template>
        <img :src="wxImage" height="200" alt="微信二维码" />
      </a-descriptions-item>
    </a-descriptions>
  </a-card>
</template>

<script setup lang="ts" name="Contact">
import wxImage from '@/assets/wx.jpg';
import { MailOutlined, PhoneOutlined, GithubOutlined, WechatOutlined } from '@ant-design/icons-vue';
</script>

<style lang="less" scoped>
@import '@/styles/main.less';
.ant-icon {
  color: rgba(1, 1, 1, 0.6);
  font-size: 12px;
}
</style>
