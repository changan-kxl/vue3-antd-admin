<template>
  <div class="exception-page">
    <div class="img">
      <img :src="config[type].img" />
    </div>
    <div class="content">
      <h1>{{ config[type].title }}</h1>
      <div class="desc">{{ config[type].desc }}</div>
      <div class="action">
        <a-button type="primary" @click="backHome">返回首页</a-button>
      </div>
    </div>
  </div>
</template>

<script>
import Config from './typeConfig';
import { ref } from 'vue';
import { useRouter } from 'vue-router';

export default {
  name: 'ExceptionPage',
  props: ['type', 'homeRoute'],
  emits: ['backHome'],
  setup(props, ctx) {
    const router = useRouter();
    const config = Config;
    function backHome() {
      if (props.homeRoute) {
        router.push(props.homeRoute);
      }
      ctx.$emit('backHome', props.type);
    }
    return {
      config,
      backHome
    };
  }
};
</script>

<style lang="less" scoped>
@base-bg-color: #ffff;
.exception-page {
  border-radius: 4px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: @base-bg-color;
  padding: 20px 0;
  .img {
    padding-right: 52px;
    zoom: 1;
    img {
      max-width: 430px;
    }
  }
  .content {
    h1 {
      color: #434e59;
      font-size: 72px;
      font-weight: 600;
      line-height: 72px;
      margin-bottom: 24px;
    }
    .desc {
      color: #000000;
      font-size: 20px;
      line-height: 28px;
      margin-bottom: 16px;
    }
  }
}
</style>
