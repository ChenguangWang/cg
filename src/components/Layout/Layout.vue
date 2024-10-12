<template>
  <a-layout>
    <a-layout-header :style="{ position: 'fixed', zIndex: 1, width: '100%' }">
      <div class="logo">王晨光</div>
      <a-menu
        v-model:selectedKeys="selectedKeys"
        theme="dark"
        mode="horizontal"
        :style="{ lineHeight: '64px', marginLeft: '50px' }"
      >
        <a-menu-item key="about">关于我</a-menu-item>
        <a-menu-item key="skills">技能</a-menu-item>
        <a-menu-item key="experience">工作经历</a-menu-item>
        <a-menu-item key="projects">项目展示</a-menu-item>
        <a-menu-item key="contact">联系方式</a-menu-item>
      </a-menu>
    </a-layout-header>

    <a-layout-content :style="{ padding: '0 50px', marginTop: '64px' }">
      <!-- <div :style="{ background: '#fff', padding: '24px', minHeight: '380px' }">Content</div> -->
      <div id="about" class="about-me">
        <a-card class="about-me-card">
          <a-avatar src="your-avatar-url" size="large" />
          <h2>hi，我是王晨光</h2>
          <p>具有Vue、Angular、Java 等工作经验的前端工程师。</p>
        </a-card>
      </div>

      <div id="skills" class="skills">
        <div class="skill-tags">
          <a-tag color="blue">Vue</a-tag>
          <a-tag color="geekblue">TypeScript</a-tag>
          <a-tag color="green">Java</a-tag>
        </div>
      </div>

      <div id="experience" class="timeline">
        <a-timeline>
          <a-timeline-item>Create a front-end for Company A (2020-2022)</a-timeline-item>
          <a-timeline-item>Work as a software engineer at Company B (2018-2020)</a-timeline-item>
        </a-timeline>
      </div>

      <div id="projects">
        <a-card>
          <a-card-grid class="project-grid">
            <h3>Project A</h3>
            <p>Technologies: Vue, Ant Design, Node.js</p>
          </a-card-grid>
          <a-card-grid class="project-grid">
            <h3>Project B</h3>
            <p>Technologies: TypeScript, Webpack</p>
          </a-card-grid>
        </a-card>
      </div>

      <div id="contact" class="contact-form">
        <a-form>
          <a-form-item>
            <a-input placeholder="Your Name" />
          </a-form-item>
          <a-form-item>
            <a-input placeholder="Your Email" />
          </a-form-item>
          <a-form-item>
            <a-textarea rows="{4}" placeholder="Your Message" />
          </a-form-item>
          <a-button type="primary">Send</a-button>
        </a-form>

        <div class="contact-icons">
          <a-icon type="github" />
          <a-icon type="linkedin" />
        </div>
      </div>
    </a-layout-content>
    <a-layout-footer style="text-align: center"> ©2024 Created by WangChenguang </a-layout-footer>
  </a-layout>
</template>

<script lang="ts">
import { defineComponent, ref, onMounted } from 'vue';
export default defineComponent({
  setup() {
    const targetOffset = ref<number | undefined>(undefined);

    onMounted(() => {
      targetOffset.value = window.innerHeight / 2;
    });
    return {
      selectedKeys: ref<string[]>(['about']),
    };
  },
});
</script>

<style lang="less" scoped>
.ant-layout-header {
  display: flex;
}
.ant-layout-content {
  min-height: calc(100vh - 64px);
}
.logo {
  width: 120px;
  font-size: 16px;
  color: #fff;
}
.about-me {
  text-align: center;
  padding: 40px 0;
}
.about-me-card {
  max-width: 600px;
  margin: 0 auto;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.skills {
  padding: 20px 0;
  text-align: center;
}
.skill-tags {
  margin-bottom: 20px;
}

.timeline {
  padding: 40px 0;
}
.timeline-item {
  font-size: 16px;
}

.project-grid {
  width: 25%;
  text-align: center;
  padding: 20px;
  transition: transform 0.2s, box-shadow 0.2s;
}
.project-grid:hover {
  transform: scale(1.05);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
}

.contact-form {
  max-width: 600px;
  margin: 0 auto;
  padding: 40px 0;
}
.contact-icons a-icon {
  font-size: 24px;
  margin: 0 10px;
  cursor: pointer;
  transition: color 0.2s;
}
.contact-icons a-icon:hover {
  color: #1890ff;
}
</style>
