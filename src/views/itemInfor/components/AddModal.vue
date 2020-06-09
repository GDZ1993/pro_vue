<template>
  <a-modal
    v-model="showMode"
    centered
    :bodyStyle="{padding: '0'}"
    title="添加项目"
    @ok="okClick"
    @cancel="cancel"
    class="modal-item"
    :width="$store.getters.modalWidth > 100 ? $store.getters.modalWidth+'px':$store.getters.modalWidth +'%'">
    <div class="modal-div">
      <a-form layout="horizontal">
        <a-card title="基本信息" :headStyle="headStyle" class="card-item">
          <a-form-item label="项目名称:" >
            <a-input placeholder="请输入项目名称" />
          </a-form-item>
          <a-row type="flex" justify="space-between">
            <a-form-item label="项目阶段:" class="form-item-2">
              <a-input placeholder="请输入项目阶段" />
            </a-form-item>
            <a-form-item label="工程分类:" class="form-item-2">
              <a-input placeholder="请输入工程分类" />
            </a-form-item>
          </a-row>
          <a-row type="flex" justify="space-between">
            <a-form-item label="所属区域:" class="form-item-2">
              <a-input placeholder="请输入所属区域" />
            </a-form-item>
            <a-form-item label="境内/境外:" class="form-item-2">
              <a-radio-group v-model="formData.radio">
                <a-radio :value="1">境内</a-radio>
                <a-radio :value="2">境外</a-radio>
              </a-radio-group>
            </a-form-item>
          </a-row>
          <a-form-item>
            <a-popover :visible="popover" @visibleChange="visibleChange" trigger="click" style="width: 100%" :get-popup-container="getPopupContainer">
              <div slot="title" class="row-between">
                <span>选择地址</span>
                <div @click="popover = false">
                  <a-icon type="close" />
                </div>
              </div>
              <div slot="content" :style="{width: $store.getters.innerWidth+'px'}">
                <div class="row-start" style="margin-bottom:20px">
                  <div class="address-label">地址查询:</div>
                  <a-input placeholder="请输入" style="width: 200px;margin-right: 10px"/>
                  <a-button type="primary">查询</a-button>
                </div>
                <div id="allmap" style="width: 100%;height: 215px;margin-bottom:20px"></div>
                <div class="row-between">
                  <span>所选地址：广东省广州市越秀区解放北路542号之6 距离市中心约6148米</span>
                  <div>
                    <a-button style="margin-right:10px" @click="popover = false" size="small">取消</a-button>
                    <a-button type="primary" size="small" @click="popover = false">确认</a-button>
                  </div>
                </div>
              </div>
              <div class="row-start address-div" >
                <div class="address-label">项目所在地点:</div>
                <a href="#" @click="mapBaidu()">选择地址</a>
              </div>
            </a-popover>
          </a-form-item>
          <a-form-item label="工程简介:">
            <a-textarea placeholder="请输入工程简介" :auto-size="{ minRows: 6, maxRows: 6 }" />
          </a-form-item>
        </a-card>
        <a-card title="投标信息" :headStyle="headStyle" class="card-item">
          <a-row type="flex" justify="space-between">
            <a-form-item label="预设投标时间:" class="form-item-3">
              <a-date-picker style="width: 100%"/>
            </a-form-item>
            <a-form-item label="投标日期:" class="form-item-3">
              <a-date-picker style="width: 100%"/>
            </a-form-item>
            <a-form-item label="中标日期:" class="form-item-3">
              <a-date-picker style="width: 100%"/>
            </a-form-item>
          </a-row>
          <a-row type="flex" justify="space-between">
            <a-form-item label="投资额（万元）:" class="form-item-3">
              <a-input placeholder="请输入投资额（万元）" />
            </a-form-item>
            <a-form-item label="合同额（万元）:" class="form-item-3">
              <a-input placeholder="请输入合同额（万元）" />
            </a-form-item>
            <a-form-item label="名义投标单位:" class="form-item-3">
              <a-input placeholder="请输入名义投标单位" />
            </a-form-item>
          </a-row>
          <a-row type="flex" justify="space-between">
            <a-form-item label="业主单位:" class="form-item-3">
              <a-input placeholder="请输入业主单位:" />
            </a-form-item>
            <a-form-item label="设计单位:" class="form-item-3">
              <a-input placeholder="请输入设计单位" />
            </a-form-item>
            <a-form-item class="form-item-3">
            </a-form-item>
          </a-row>
        </a-card>
      </a-form>
    </div>
  </a-modal>
</template>

<script>
  import moment from 'moment'
  export default {
    name: 'AddModal',
    props: {
      show: {
        type: Boolean,
        default: false
      },
    },
    data () {
      return {
        showMode: false,
        popover: false,
        headStyle: { fontSize: '14px', fontWeight: 'bold', color: 'rgba(0,0,0,0.65)' },
        formData: {
          radio: 1
        }
      }
    },
    watch: {
      show (value) {
        this.showMode = value
      }
    },
    methods: {
      moment,
      okClick() {
        this.$emit('handleOk')
        this.cancel()
      },
      cancel() {
        this.$emit('cancel')
      },
      getPopupContainer(trigger) {
        return trigger.parentElement
      },
      visibleChange (val) {
        this.popover = val
        console.log(val)
      },
      mapBaidu () {
        setTimeout(() => {
          var map = new BMap.Map('allmap')
          map.centerAndZoom(new BMap.Point(116.404, 39.915), 11)
          map.setCurrentCity('北京')
          map.enableScrollWheelZoom(true)
        }, 300)
      }
    }
  }
</script>
<style>
  .modal-div .ant-form-item{
    margin-bottom: 0;
  }
</style>
<style scoped>
  .card-item {
    margin: 12px auto;
  }
  .form-item-2 {
    width: calc(100% / 2 - 10px);
  }
  .form-item-3 {
    width: calc(100% / 3 - 10px);
  }
  .address-div{
    margin-top: 10px;
  }
  .address-label{
    font-size:14px;
    font-family:Microsoft YaHei;
    font-weight:400;
    color:rgba(0,0,0,0.65);
    margin-right: 10px;
  }
</style>