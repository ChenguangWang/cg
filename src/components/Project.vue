<template>
  <a-card hoverable class="common-card" title="项目展示">
    <div class="product-gallery">
      <a-card v-for="(product, index) in products" :key="index" hoverable class="product-card">
        <!-- 图片轮播 -->
        <a-carousel autoplay>
          <div v-for="(image, idx) in product.images" :key="idx" class="product-image-wrapper">
            <img :src="image" :alt="`Product ${index + 1} Image ${idx + 1}`" class="product-image" />
          </div>
        </a-carousel>

        <!-- 产品名称和描述 -->
        <a-card-meta :title="product.name" style="margin-top: 12px">
          <template #description>
            <a-descriptions :column="1" layout="vertical">
              <a-descriptions-item label="项目描述">
                <div v-html="product.description"></div>
              </a-descriptions-item>
              <a-descriptions-item label="主要工作内容及成果">
                <div v-html="product.work"></div>
              </a-descriptions-item>
            </a-descriptions>
          </template>
        </a-card-meta>
      </a-card>
    </div>
    <!-- <a-carousel autoplay>
      <div style="background: red">
        <img
          src="http://e.hiphotos.baidu.com/image/pic/item/a1ec08fa513d2697e542494057fbb2fb4316d81e.jpg"
          alt="project 1 image 1"
          class="project-card-img"
        />
      </div>
      <div>
        <img
          src="http://c.hiphotos.baidu.com/image/pic/item/30adcbef76094b36de8a2fe5a1cc7cd98d109d99.jpg"
          alt="project 1 image 2"
          class="project-card-img"
        />
      </div>
    </a-carousel>
    <a-card-meta style="margin-top: 12px" title="App Analytics （应用统计分析平台）">
      <template #description>
        <a href="https://www.talkingdata.com/products.jsp?languagetype=zh_cn"> 应用分析 </a>
        能够帮助移动应用开发者收集、处理、分析一方数据，可视化运营指标，监测用户行为，帮助产品设计。
      </template>
    </a-card-meta> -->
  </a-card>
</template>

<script setup lang="ts" name="Project">
import { ref } from 'vue';
import aa1 from '@/assets/aa/1.jpg';
import aa2 from '@/assets/aa/2.jpg';
import aa3 from '@/assets/aa/3.jpg';
import aa4 from '@/assets/aa/4.jpg';

const products = ref([
  {
    name: 'App Analytics （应用统计分析平台）',
    description: `<a href="https://www.talkingdata.com/products.jsp?languagetype=zh_cn" target="_blank"> 应用分析 </a>
        能够帮助移动应用开发者收集、处理、分析一方数据，可视化运营指标，监测用户行为，帮助产品设计。`,
    work: `<ul><li>负责SaaS版及私有版功能开发及部署，承担主要的设计与研发工作；</li>
<li>制定前端编码规范和开发流程，集成Prettier、ESLint实现代码格式化与代码质量检查；</li>
<li>主导事件体系重构，封装事件类业务组件，提升前端交付速度；</li>
<li>剔除源码引入子项目的嵌入方式，减少多项目配置的维护精力；</li>
<li>封装并推广图表样式node包，统一公司SaaS侧图表样式；</li>
<li>优化部分列表查询体验，表格按列查询渲染，拆分用户等待时间，提升用户体验；</li>
<li>统计分析项目是公司的初创项目，历经多年主题交互却长期未变，于是基于老旧代码的逻辑改造与梳理后，主导了版面交互样式大更新，结束将近8年未变的交互体验。</li> </ul>`,
    images: [aa1, aa2, aa3, aa4],
  },
  {
    name: 'TalkingAds 素材观象台',
    description: `TalkingAds素材观象台平台是一款针对国内移动端广告投放市场的、帮助从业者进行营销决策的信息服务平台。旨在为广告主提供素材实时分析、处理海量数据，结合投放业务规则和大数据手段，预测展示效果。其中的创意工坊可以帮助广告主快速的生成批量广告素材，帮助广告主快速进行广告投放的工具平台。用户通过使用批量制图、视频混剪技术，简单操作即可帮助用户制作出批量的广告素材，从而达到帮助用户缩减视频剪辑和图片制作的时间及人力成本。`,
    work: `<ul>
    <li>前端工程架构设计及日常前端工作安排，定期review代码，保证产品质量；</li>
<li>基于组件化开发思想，设计并规划公共组件，超产品预期完成项目开发工作；</li>
<li>浏览素材信息适合瀑布流方式，但是下拉加载生成的DOM数量过多时，对浏览器内存消耗巨大。为解决这一问题，基于对virtual-grid的源码改造，封装成符合项目的组件，大大减少素材页面对浏览器的压力，提升用户浏览体验；</li>
<li>使用原生Canvas绘制技术完成视频在线播放与在线编辑技术方案的落地；</li>
<li>基于cropperjs封装制图组件，处理后的图片用于广告制图和视频图片使用；</li>
<li>合理规划任务，制定代码规范，利用gitHooks统一代码风格；</li>
<li>配置jenkins自动化部署脚本，配合eslint在构建部署前找到代码中的问题，保证产品质量；</li>
<li>混剪技术专利文档编写。</li>
</ul>`,
    images: [],
  },
  {
    name: 'Analytics Enterprise Plus （运营分析平台-企业版）',
    description: `通过对全移动行业超过30亿受众数据的汇聚、清洗、智能运算，构建了庞大的第三方精准人群数据中心，以开放接口形式为全行业从业者提供标准的精准人群标签，辅助优化投放和提升营销效果。基于SDK采集的数据和上传的一方数据，构建出以人为中心的用户分群和用户洞察，为运营、营销等活动提供精准人群支撑。`,
    work: `<ul>
<li>项目内公共组件及工具类函数封装，例如全局搜索、空数据展示等业务组件，提升开发效率，统一数据展示方式；
</li>
<li>封装初始化的ECharts配置，并开发成工具函数，通过上传至公司npm私有库，实现了公司数据图表展示的统一化；
</li>
<li>主导项目从ng6升级到ng8，实现页面加载速度提升30%，大幅改善用户体验；
</li>
<li>团队内部定期CodeReview，及时找出代码痛点，提升代码质量；
</li>
<li>优化AE子工程灵动分析项目，优化后初始页面加载速度由5秒多提升到3秒内展示。
</li>
</ul>`,
    images: [],
  },
  {
    name: '海尔优家云平台',
    description: `海尔优家云平台主要提供一些基础服务（例如：天气、消息推送、资源系统、缓存系统等等）和设备服务（例如：设备远程操控、设备属性上报等等）`,
    work: `<ul>
<li>基于springboot封装用于智能电子秤的api接口；
</li>
<li>负责开放原有云平台自有软件服务；
</li>
<li>负责维护原有的能力dubbo服务和开发新服务。
</li></ul>`,
    images: [],
  },
  {
    name: '阳光保险',
    description: `项目包含 pc官网、移动官网、微信的几大类，涉及产品中心、会员中心、积分商城、保全操作、超级会员等模块，页面使用freemarker模板技术，整体框架是基于SpringMVC注解形式完成的，后台数据库使用Oracle。
整体分为两个部分，一部分是前端电商网站，面向客户，客户可以在此购买保险、查看客户保单、参加节日活动抽奖等操作；另一部分是后端电商管理系统，主要包括对网站信息的维护、用户管理、各险种销售报表、留言管理等。`,
    work: `<ul>
<li>负责设计并撰写开发设计文档；
</li>
<li>根据业务提供的需求进行PC官网、移动官网、以及微信端的功能开发；
</li>
<li>期间参与公司研发奖励计划，设计开发了一个预警系统，以工具类的方式嵌入各个系统，提供了邮件和微信的告警通知，填补了保险业务预警的空缺。
</li></ul>`,
    images: [],
  },
]);
</script>

<style lang="less" scoped>
@import '@/styles/main.less';

.common-card {
  margin-bottom: 40px;
}
.product-card {
  margin-bottom: 24px;
}

.product-image {
  max-height: 200px;
  object-fit: cover;
  margin: 0 auto;
}
:deep(.slick-slide) {
  background: #f0f2f5;
}
</style>
