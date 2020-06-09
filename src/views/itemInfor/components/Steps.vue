<template>
  <div class="Steps row-start">
    <div v-for="(item,inx) in arr" :key="inx" class="column-div Steps-item">
      <div class="Steps-index column-div" v-if="index <= inx">{{ inx + 1 }}</div>
      <a-icon type="check-circle" v-else style="font-size: 25px;color: #1890ff;margin-bottom: 7px"/>
      <div class="Steps-text " :style="index == inx ? {color: '#1890ff',fontWeight: 'bold'} : inx < index ? {color: 'rgba(0,0,0,0.65)'}: ''">{{ item }}</div>
    </div>
  </div>
</template>
<script>
  export default {
    name: 'Steps',
    props: {
      index: {
        type: Number,
        default: 0
      }
    },
    data() {
      return {
        arr: ['跟踪', '新中标', '在建', '停工', '完工未验收', '验收未结算', '竣工已结算']
      }
    }
  }
</script>

<style scoped>
  .Steps {
    width: 100%;
  }

  .Steps-index {
    width: 24px;
    height: 24px;
    border-radius: 50%;
    background: #00A0E9;
    font-size: 14px;
    font-family: Microsoft YaHei;
    font-weight: 400;
    color: white;
    margin-bottom: 7px;
  }

  .Steps-text {
    width: 100%;
    font-size: 12px;
    font-family: Microsoft YaHei;
    font-weight: 400;
    color:rgba(0,0,0,0.40);
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    text-align: center;
  }

  .Steps-item{
    width: calc(100% / 7);
    position: relative;
  }

  .Steps-item::after{
    position: absolute;
    left: calc(100% / 2 + (100% / 2) / 2);
    top: 11px;
    content: " ";
    width: calc(100% / 2);
    height: 2px;
    background: rgba(24,144,255,1);
  }

  .Steps > .Steps-item:last-child::after{
    content: "";
    width: 0;
    height: 0;
  }
</style>