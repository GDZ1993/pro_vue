<template>
  <a-modal
    v-model="showMode"
    centered
    :bodyStyle="{padding: '0'}"
    title="项目履历"
    @ok="okClick"
    @cancel="cancel"
    class="modal-item"
    :width="$store.getters.modalWidth > 100 ? $store.getters.modalWidth+'px':$store.getters.modalWidth +'%'">
    <div class="modal-div">
      <a-card title="基本信息变更履历" :headStyle="headStyle" class="card-item">
        <a-table :columns="tableColumns_one" :data-source="tableData_one" rowKey="id" :pagination="false" :scroll="{y: tableData_one.length >= 5 ? 150 : false}">
          <div slot="fields">
            <span>变更字段</span>
            <a-icon type="search" style="color: #1890ff;margin-left: 5px"/>
          </div>
          <div slot="content">
            <span>变更内容</span>
            <a-icon type="search" style="color: #1890ff;margin-left: 5px"/>
          </div>
          <div slot="changePerson">
            <span>变更人</span>
            <a-icon type="search" style="color: #1890ff;margin-left: 5px"/>
          </div>
          <div slot="date">
            <span>变更日</span>
            <a-icon type="search" style="color: #1890ff;margin-left: 5px"/>
          </div>
        </a-table>
      </a-card>
      <a-card title="投标信息变更履历" :headStyle="headStyle" class="card-item">
        <a-table :columns="tableColumns_one" :data-source="tableData_one" rowKey="id" :pagination="false" :scroll="{y: tableData_one.length >= 5 ? 150 : false}">
          <div slot="fields">
            <span>变更字段</span>
            <a-icon type="search" style="color: #1890ff;margin-left: 5px"/>
          </div>
          <div slot="content">
            <span>变更内容</span>
            <a-icon type="search" style="color: #1890ff;margin-left: 5px"/>
          </div>
          <div slot="changePerson">
            <span>变更人</span>
            <a-icon type="search" style="color: #1890ff;margin-left: 5px"/>
          </div>
          <div slot="date">
            <span>变更日</span>
            <a-icon type="search" style="color: #1890ff;margin-left: 5px"/>
          </div>
        </a-table>
      </a-card>
      <a-card title="合同信息变更履历" :headStyle="headStyle" class="card-item">
        <a-table :columns="tableColumns_one" :data-source="tableData_one" rowKey="id" :pagination="false" :scroll="{y: tableData_one.length >= 5 ? 150 : false}">
          <div slot="fields">
            <span>变更字段</span>
            <a-icon type="search" style="color: #1890ff;margin-left: 5px"/>
          </div>
          <div slot="content">
            <span>变更内容</span>
            <a-icon type="search" style="color: #1890ff;margin-left: 5px"/>
          </div>
          <div slot="changePerson">
            <span>变更人</span>
            <a-icon type="search" style="color: #1890ff;margin-left: 5px"/>
          </div>
          <div slot="date">
            <span>变更日</span>
            <a-icon type="search" style="color: #1890ff;margin-left: 5px"/>
          </div>
        </a-table>
      </a-card>
    </div>
  </a-modal>
</template>

<script>
  export default {
    name: 'Record',
    props: {
      show: {
        type: Boolean,
        default: false
      }
    },
    data() {
      return {
        showMode: false,
        headStyle: { fontSize: '14px', fontWeight: 'bold', color: 'rgba(0,0,0,0.65)' },
        tableData_one: [
          {
            id: 0,
            fields: '实际开工日期',
            content: '第二项目部相单位',
            changePerson: '测试用户1',
            date: '2020-12-21'
          },
          {
            id: 1,
            fields: '实际开工日期',
            content: '第二项目部相关位',
            changePerson: '测试用户1',
            date: '2020-12-21'
          },
          {
            id: 2,
            fields: '实际开工日期',
            content: '第二项目部相位',
            changePerson: '测试用户1',
            date: '2020-12-21'
          },
          {
            id: 3,
            fields: '实际开工日期',
            content: '第二项目关单位',
            changePerson: '测试用户1',
            date: '2020-12-21'
          },
          {
            id: 4,
            fields: '实际开工日期',
            content: '第二项目部单位',
            changePerson: '测试用户1',
            date: '2020-12-21'
          },
          {
            id: 5,
            fields: '实际开工日期',
            content: '第二项目关单位',
            changePerson: '测试用户1',
            date: '2020-12-21'
          }
        ],
        tableColumns_one: [
          {
            dataIndex: 'fields',
            slots: { title: 'fields' },
          },
          {
            dataIndex: 'content',
            slots: { title: 'content' },
          },
          {
            dataIndex: 'changePerson',
            slots: { title: 'changePerson' },
          },
          {
            dataIndex: 'date',
            slots: { title: 'date' },
          }
        ]
      }
    },
    watch: {
      show(value) {
        this.showMode = value
      }
    },
    methods: {
      okClick() {
        this.$emit('handleOk')
        this.cancel()
      },
      cancel() {
        this.$emit('cancel')
      }
    }
  }
</script>
<style>
  .modal-div .ant-table-body::-webkit-scrollbar {
    width: 5px;
    background: white;
    border-radius: 10px;
  }

  .modal-div .ant-table-body::-webkit-scrollbar-track {
    -webkit-box-shadow: inset 0 0 5px rgba(0, 0, 0, 0.3);
    border-radius: 10px;
  }

  .modal-div .ant-table-body::-webkit-scrollbar-thumb {
    border-radius: 10px;
    background: rgba(0, 0, 0, 0.45);
  }
</style>
<style scoped>

  .card-item {
    margin: 12px auto;
  }
</style>