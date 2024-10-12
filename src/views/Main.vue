<template>
  <div class="main-container">
    <a-anchor
      class="anchor"
      :direction="anchorDirection"
      :offsetTop="anchorDirection == 'horizontal' ? 0 : 40"
      :items="ANCHOR_DATA"
    ></a-anchor>

    <div class="content">
      <!-- <div :style="{ background: '#fff', padding: '24px', minHeight: '380px' }">Content</div> -->
      <div id="about" class="about-me">
        <a-card class="about-me-card">
          <a-avatar :src="avatarUrl" size="large" />
          <h2>hi，我是王晨光</h2>
          <!-- <p>具有Vue、Angular、Java 等工作经验的前端工程师。</p> -->
          <p>一只不太专业但却热爱前端的攻城狮。</p>
        </a-card>
      </div>

      <div id="skills" class="skills">
        <a-card class="skills-card" title="专业技能">
          <a-list bordered :data-source="skillsData">
            <template #renderItem="{ item }">
              <a-list-item>{{ item }}</a-list-item>
            </template>
            <template #header>
              <a-tag color="blue" class="skill-tags">Vue</a-tag>
              <a-tag color="geekblue" class="skill-tags">TypeScript</a-tag>
              <a-tag color="green" class="skill-tags">Angular</a-tag>
              <a-tag color="blue" class="skill-tags">Java</a-tag>
            </template>
          </a-list>
        </a-card>
      </div>

      <div id="experience" class="timeline">
        <a-card class="experience-card" title="工作经历">
          <a-timeline>
            <a-timeline-item>
              <div class="company-wrap">
                <p class="company-title">北京腾云天下科技有限公司</p>
                <p class="company-job">前端工程师</p>
              </div>
              <p class="company-time">2020.12 - 至今</p>
            </a-timeline-item>
            <a-timeline-item color="gray">
              <div class="company-wrap">
                <p class="company-title">北京艾迪信科技有限公司</p>
                <p class="company-job">前端工程师</p>
              </div>
              <p class="company-time">2016.11 - 2020.12</p>
            </a-timeline-item>
            <a-timeline-item color="gray">
              <div class="company-wrap">
                <p class="company-title">北京人和创建信息技术有限公司</p>
                <p class="company-job">Java工程师</p>
              </div>
              <p class="company-time">2016.3 - 2016.11</p>
            </a-timeline-item>
            <a-timeline-item color="gray">
              <div class="company-wrap">
                <p class="company-title">北京瑞友科技股份有限公司</p>
                <p class="company-job">Java工程师</p>
              </div>
              <p class="company-time">2014.11 - 2015.11</p>
            </a-timeline-item>
            <a-timeline-item>
              <template #dot>
                <ClockCircleOutlined style="font-size: 16px" />
              </template>
            </a-timeline-item>
          </a-timeline>
        </a-card>
      </div>

      <div id="projects">
        <Project></Project>
      </div>

      <div id="contact">
        <Contact></Contact>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, onMounted, onUnmounted } from 'vue';
// import LionImage from '@/assets/lion.png';
import LionImage from '@/assets/cg.jpeg';
import { ClockCircleOutlined } from '@ant-design/icons-vue';
import { ANCHOR_DATA } from './../settings/commonSettings';
import Contact from '@/components/Contact.vue';
import Project from '@/components/Project.vue';

export default defineComponent({
  components: { ClockCircleOutlined, Project, Contact },
  data() {
    return {
      avatarUrl: LionImage,
    };
  },
  setup() {
    // 锚点方向
    const anchorDirection = ref('vertical');

    const skillsData: String[] = [
      '熟悉掌握W3C规范，具有编写良好风格规范代码的习惯',
      '具备扎实的面向对象编程基础和模块化开发经验',
      '熟练掌握JavaScript、Typescript，熟悉ES6语法',
      '熟练掌握小程序及H5研发',
      '熟练掌握 Vue 2 和 Vue 3，同时具备 Angular 的项目开发经验，具有丰富的实战开发经验，能够灵活运用不同框架独立进行前端开发',
      '熟练配置 Webpack、Vite，优化前端打包流程，减少打包体积并提升构建效率',
      '熟练使用 ECharts 和 AntV 中的 G2 进行数据可视化，能够设计和实现各种复杂的数据图表',
      '熟悉Java开发语言，数据库查询语言，能够熟练编写查询语言以获取所需数据',
      '了解Linux操作系统，熟练使用Linux操作命令部署前端工程',
      '具备使用 Jenkins 集成 Git、Maven、Node.js 等工具的能力，确保项目构建、测试、部署流程自动化',
      '熟练使用Git及其工作流，合理管理分支提高敏捷开发',
    ];
    const resizeFunc = () => {
      anchorDirection.value = window.innerWidth <= 768 ? 'horizontal' : 'vertical';
    };

    onMounted(() => {
      resizeFunc();
      window.addEventListener('resize', resizeFunc);
    });
    onUnmounted(() => {
      window.removeEventListener('resize', resizeFunc);
    });
    return {
      anchorDirection,
      selectedKeys: ref<string[]>(['about']),
      skillsData,
      ANCHOR_DATA,
    };
  },
});
</script>

<style lang="less" scoped>
.main-container {
  background-color: #f0f2f5;
  display: flex;
  flex-direction: row-reverse;
  justify-content: space-evenly;
  .anchor {
    padding-top: 50px;
    width: 200px;
  }
  .content {
    width: calc(100% - 240px);
    padding: 0 50px;
  }
}

.about-me {
  text-align: center;
  padding: 40px 0;
}
.about-me-card,
.skills-card,
.experience-card {
  max-width: 600px;
  margin: 0 auto;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  h2 {
    margin: 24px 0;
  }
}

.skills-card {
  text-align: left;
}

.skill-tags {
  margin-bottom: 8px;
}

.timeline {
  padding: 40px 0;
  :deep(.ant-timeline-item-content) {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  p {
    margin-bottom: 0px;
  }
  .company-title {
    font-weight: 500;
    margin-bottom: 8px;
  }
  .company-time {
    color: #aaa;
    min-width: 100px;
    text-align: right;
    white-space: nowrap;
  }
  :deep(.ant-timeline-item-last .ant-timeline-item-content) {
    min-height: 0;
  }
}

@media screen and (max-width: 768px) {
  .main-container {
    flex-direction: column;
    align-items: center;
    .content {
      width: 100%;
      padding: 20px 24px 24px;
    }
    .anchor {
      padding-top: 0;
      padding: 10px;
      background: #fff;
      width: 100vw;
      height: 40px;
      position: fixed;
      top: 0;
      z-index: 1;
    }
  }
}
</style>
