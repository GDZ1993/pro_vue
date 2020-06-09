<template>
  <a-modal
    v-model="show"
    centered
    :bodyStyle="{padding: '0'}"
    title="项目详情"
    @ok="okClick"
    @cancel="cancel"
    class="modal-item"
    :width="$store.getters.modalWidth > 100 ? $store.getters.modalWidth+'px':$store.getters.modalWidth +'%'">
    <div class="modal-div">
      <a-card title="基本信息" :headStyle="headStyle" class="card-item">
        <div class="row-start form-item">
          <div class="form-label fl70">项目名称：</div>
          <div class="form-text ft70">大连港30万吨级原油码头工程大连港30万吨级原油码头工程大连港30万吨</div>
        </div>
        <div class="row-start">
          <div class="form-label fl70">实施单位：</div>
          <div class="form-text ft70">中交一航局三公司第一项目部</div>
        </div>
        <a-divider/>
        <div class="row-between three-points">
          <div class="row-start">
            <div class="form-label fl70">项目状态：</div>
            <div class="form-text ft70">已交付</div>
          </div>
          <div class="row-start">
            <div class="form-label fl70">项目性质：</div>
            <div class="form-text ft70">现汇</div>
          </div>
          <div class="row-start">
            <div class="form-label fl70">项目阶段：</div>
            <div class="form-text ft70">重点跟踪</div>
          </div>
        </div>
        <div class="row-between three-points">
          <div class="row-start">
            <div class="form-label fl70">项目类型</div>
            <div class="form-text ft70">水工</div>
          </div>
          <div class="row-start">
            <div class="form-label fl70">工程分类：</div>
            <div class="form-text ft70">xxxx</div>
          </div>
          <div class="row-start">
            <div class="form-label fl70">境内/境外：</div>
            <div class="form-text ft70">境内</div>
          </div>
        </div>
        <div class="row-start three-points">
          <div class="row-start">
            <div class="form-label fl70">所属区域：</div>
            <div class="form-text ft70">东北</div>
          </div>
          <div class="row-start">
            <div class="form-label fl70">项目地点：</div>
            <div class="form-text ft70">辽宁省大连市</div>
          </div>
        </div>
        <a-divider/>
        <div class="row-start" style="align-items: flex-start">
          <div class="form-label fl70">工程简介：</div>
          <div class="form-text ft70">
            <span>{{ form.intro }}</span>
            <span v-if="introStr.length > 143" @click="introClick" class="textBut">{{ form.intro.length > 143 ? '收起' : '展开' }}</span>
          </div>
        </div>
      </a-card>
      <a-card title="投标信息" :headStyle="headStyle" class="card-item">
        <div class="row-between three-points">
          <div class="row-start" style="align-items: center">
            <div class="form-label">投资额（万元）：</div>
            <div class="form-text">3650</div>
          </div>
          <div class="row-start" style="align-items: center">
            <div class="form-label">合同额（万元）：</div>
            <div class="form-text">2860</div>
          </div>
          <div class="row-start" style="align-items: center">
            <div class="form-label">名义投标单位：</div>
            <div class="form-text">三公司</div>
          </div>
        </div>
        <div class="row-start three-points">
          <div class="row-start" style="align-items: center">
            <div class="form-label">业主单位：</div>
            <div class="form-text">大连港股份公司</div>
          </div>
          <div class="row-start" style="align-items: center">
            <div class="form-label">设计单位：</div>
            <div class="form-text">三公司</div>
          </div>
        </div>
      </a-card>
      <a-card title="合同信息" :headStyle="headStyle" class="card-item">
        <div class="row-between three-points">
          <div class="row-start" style="align-items: center">
            <div class="form-label">合同开工日期：</div>
            <div class="form-text">2013-05-13</div>
          </div>
          <div class="row-start" style="align-items: center">
            <div class="form-label">合同竣工日期：</div>
            <div class="form-text">2017-03-31</div>
          </div>
          <div class="row-start" style="align-items: center">
            <div class="form-label">合同工期：</div>
            <div class="form-text">4年</div>
          </div>
        </div>
        <div class="row-between three-points">
          <div class="row-start" style="align-items: center">
            <div class="form-label">项目管理模式：</div>
            <div class="form-text">已交付</div>
          </div>
          <div class="row-start" style="align-items: center">
            <div class="form-label">重点工程划分：</div>
            <div class="form-text">xxxx</div>
          </div>
          <div class="row-start" style="align-items: center">
            <div class="form-label">获奖情况：</div>
            <div class="form-text">xxxx</div>
          </div>
        </div>
        <div class="row-between three-points">
          <div class="row-start" style="align-items: center">
            <div class="form-label">跟踪状态：</div>
            <div class="form-text">重点跟踪</div>
          </div>
          <div class="row-start" style="align-items: center">
            <div class="form-label">中标日期：</div>
            <div class="form-text">2013-05-01</div>
          </div>
          <div class="row-start" style="align-items: center">
            <div class="form-label">实际开工日期：</div>
            <div class="form-text">2013-05-05</div>
          </div>
        </div>
        <div class="row-between three-points">
          <div class="row-start" style="align-items: center">
            <div class="form-label">实际完工日期：</div>
            <div class="form-text">2017-08-31</div>
          </div>
        </div>
      </a-card>
    </div>
  </a-modal>
</template>

<script>
  export default {
    name: 'DetailsModal',
    props: {
      entity: {
        type: Object,
        default: null
      }
    },
    data() {
      return {
        visible: false,
        show: false,
        steps: ['跟踪', '新中标', '在建', '停工', '完工未验收', '验收未结算', '竣工已结算'],
        stepsCurrent: 1,
        form: {
          intro: ''
        },
        intro: null,
        introStr: '老山隧道是江苏省最长和跨度最大的高速公路隧道之一，是宁淮（南京—淮安）高速公路南京江北段全线的咽喉工程，它的建成将给美丽复的老山风景区增加一道亮丽的风景线。在建设过程中，隧道淮安方向出口处，遭遇山体滑坡和地下溶洞，阻碍施工进程，制严重影响工程施工和工程进度。为了进一步查明该段内边坡滑坡体及棚洞',
        headStyle: { fontSize: '14px', fontWeight: 'bold', color: '#000000' }

      }
    },
    watch: {
      entity(value) {
        value ? this.show = true : this.show = false
      }
    },
    methods: {
      introClick () {
        this.form.intro.length > 143 ? this.introChange() : this.form.intro = this.form.intro.substring(0, 140) + this.introStr.substring(140, this.introStr.length)
      },
      handleSubmit() {
      },
      okClick() {
        this.$emit('handleOk')
        this.handleCancel()
      },
      cancel() {
        this.show = false
        this.$emit('cancel')
      },
      introChange() {
        this.introStr.length > 143 ? this.form.intro = this.introStr.substring(0, 140) + '...' : ''
      }
    },
    beforeMount() {
      this.introChange()
    }
  }
</script>

<style scoped>
  .modal-item .ant-modal-footer {
    border: none;
  }

  .modal-div {
    width: 100%;
    height: calc(100vh - 200px);
    overflow-y: auto;
    padding: 12px 24px;
  }

  .modal-div .ant-divider-horizontal {
    margin: 16px 0;
  }

  .modal-div::-webkit-scrollbar {
    width: 5px;
    background: white;
    border-radius: 10px;
  }

  .modal-div::-webkit-scrollbar-track {
    -webkit-box-shadow: inset 0 0 5px rgba(0, 0, 0, 0.3);
    border-radius: 10px;
  }

  .modal-div::-webkit-scrollbar-thumb {
    border-radius: 10px;
    background: rgba(0, 0, 0, 0.45);
  }

  .form-item {
    margin-bottom: 16px;
  }

  .form-label {
    font-size: 12px;
    font-family: Microsoft YaHei;
    font-weight: 400;
    line-height: 22px;
    color: rgba(0, 0, 0, 0.40);
  }

  .form-text {
    font-size: 12px;
    font-family: Microsoft YaHei;
    font-weight: 400;
    color: rgba(0, 0, 0, 0.65);
  }

  .fl70 {
    width: 70px;
  }

  .ft70 {
    width: calc(100% - 70px)
  }

  .fl120 {
    width: 120px;
  }

  .ft120 {
    width: calc(100% - 120px)
  }

  .three-points {
    width: 100%;
    align-items: baseline;
    flex-wrap: wrap;
  }

  .three-points > div {
    width: calc(100% / 3);
    align-items: flex-start;
  }

  .card-item {
    margin: 12px auto;
  }

  .textBut {
    color: #00A0E9;
    font-size: 12px;
  }
  .textBut:hover{
    cursor:pointer
  }
</style>