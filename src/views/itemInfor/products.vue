<template>
  <page-header-wrapper>
    <a-card :hoverable="false">
      <G-headline title="项目总览"/>
      <a-form layout="inline" :form="formData" @submit="handleSubmit" style="margin-bottom: 24px">
        <a-form-item label="项目名称:">
          <a-input placeholder="请输入项目名称" class="input-item"/>
        </a-form-item>
        <a-form-item label="实施单位:">
          <a-input placeholder="请输入实施单位" class="input-item"/>
        </a-form-item>
        <a-form-item label="所属区域:">
          <a-input placeholder="请输入所属区域" class="input-item"/>
        </a-form-item>
        <div v-if="form_show">
          <a-form-item label="项目状态:">
            <a-select placeholder="请选择项目状态" class="input-item">
              <a-select-option value="jack"> Jack</a-select-option>
            </a-select>
          </a-form-item>
          <a-form-item label="项目性质:">
            <a-select placeholder="请选择项目性质" class="input-item">
              <a-select-option value="jack"> Jack</a-select-option>
            </a-select>
          </a-form-item>
          <a-form-item label="项目类型:">
            <a-select placeholder="请选择项目类型" class="input-item">
              <a-select-option value="jack"> Jack</a-select-option>
            </a-select>
          </a-form-item>
          <a-form-item>
            <a-button type="primary">查询</a-button>
            <a-button>重置</a-button>
            <a-button type="link" @click="form_show = !form_show">{{ form_show ? '收起' : '展开' }}</a-button>
          </a-form-item>
        </div>
        <a-form-item v-if="!form_show">
          <a-button type="primary">查询</a-button>
          <a-button>重置</a-button>
          <a-button type="link" @click="form_show = !form_show">{{ form_show ? '收起' : '展开' }}</a-button>
        </a-form-item>
      </a-form>
      <a-button type="primary" style="margin-bottom: 20px" @click="add_project">添加项目</a-button>
      <a-button type="primary" style="margin-left: 20px" @click="recordModal = true">项目履历</a-button>
      <a-table :columns="columns" :data-source="tableData" rowKey="id" :pagination="pageConfig" :scroll="{ x: $store.getters.scroll_x }">
        <a-button type="link" slot="operation" slot-scope="row" @click="detailsEvent(row)">详情</a-button>
      </a-table>
    </a-card>
    <DetailsModal :entity="detailsModal" @handleOk="handleOk" @cancel="detailsModal = null"/>
    <AddModal :show="addModal" @cancel="addModal=false"/>
    <Record :show="recordModal" @cancel="recordModal=false"/>
  </page-header-wrapper>
</template>

<script>
  export default {
    name: 'ItemInfor',
    components: {
      DetailsModal: () => import('./components/DetailsModal.vue'),
      AddModal: () => import('./components/AddModal.vue'),
      Record: () => import('./components/Record.vue')
    },
    data() {
      return {
        form_show: false,
        formData: {},
        columns: [
          {
            title: '操作',
            align: 'center',
            fixed: 'left',
            key: 'operation',
            width: 100,
            scopedSlots: { customRender: 'operation' }
          },
          { title: '项目名称', dataIndex: 'name', key: 'name', align: 'center' },
          { title: '实施单位', dataIndex: 'unit', key: 'unit', align: 'center' },
          { title: '项目状态', dataIndex: 'status', key: 'status', align: 'center', width: 150 },
          { title: '项目性质', dataIndex: 'nature', key: 'nature', align: 'center', width: 150 },
          { title: '工程分类', dataIndex: 'classify', key: 'classify', align: 'center', width: 100 },
          { title: '境内/境外', dataIndex: 'inside', key: 'inside', align: 'center', width: 100 },
          { title: '所属区域', dataIndex: 'area', key: 'area', align: 'center', width: 100 },
          { title: '合同额（万元）', dataIndex: 'amount', key: 'amount', align: 'center', width: 150 },
          { title: '项目管理模式', dataIndex: 'project_anage', key: 'project_anage', align: 'center', width: 150 }
        ],
        tableData: [
          {
            id: 0,
            name: '大连港30万吨级原油码头工程',
            unit: '大连港30万吨级原油码头工程',
            status: '已交付',
            nature: '现汇',
            classify: '水利工程',
            inside: '境内',
            area: '大连',
            amount: '100',
            project_anage: '根据合同'
          },
          {
            id: 1,
            name: '大连港30万吨级原油码头工程',
            unit: '大连港30万吨级原油码头工程',
            status: '已交付',
            nature: '现汇',
            classify: '水利工程',
            inside: '境内',
            area: '大连',
            amount: '100',
            project_anage: '根据合同'
          },
          {
            id: 2,
            name: '大连港30万吨级原油码头工程',
            unit: '大连港30万吨级原油码头工程',
            status: '已交付',
            nature: '现汇',
            classify: '水利工程',
            inside: '境内',
            area: '大连',
            amount: '100',
            project_anage: '根据合同'
          },
          {
            id: 3,
            name: '大连港30万吨级原油码头工程',
            unit: '大连港30万吨级原油码头工程',
            status: '已交付',
            nature: '现汇',
            classify: '水利工程',
            inside: '境内',
            area: '大连',
            amount: '100',
            project_anage: '根据合同'
          },
          {
            id: 4,
            name: '大连港30万吨级原油码头工程',
            unit: '大连港30万吨级原油码头工程',
            status: '已交付',
            nature: '现汇',
            classify: '水利工程',
            inside: '境内',
            area: '大连',
            amount: '100',
            project_anage: '根据合同'
          },
          {
            id: 5,
            name: '大连港30万吨级原油码头工程',
            unit: '大连港30万吨级原油码头工程',
            status: '已交付',
            nature: '现汇',
            classify: '水利工程',
            inside: '境内',
            area: '大连',
            amount: '100',
            project_anage: '根据合同'
          },
          {
            id: 6,
            name: '大连港30万吨级原油码头工程',
            unit: '大连港30万吨级原油码头工程',
            status: '已交付',
            nature: '现汇',
            classify: '水利工程',
            inside: '境内',
            area: '大连',
            amount: '100',
            project_anage: '根据合同'
          },
          {
            id: 7,
            name: '大连港30万吨级原油码头工程',
            unit: '大连港30万吨级原油码头工程',
            status: '已交付',
            nature: '现汇',
            classify: '水利工程',
            inside: '境内',
            area: '大连',
            amount: '100',
            project_anage: '根据合同'
          },
        ],
        pageConfig: {
          showSizeChanger: true,
          showQuickJumper: true,
          defaultCurrent: 1,
          total: 500,
          pageSize: 10,
          onChange: (a, b) => {
            this.pageConfig.pageSize = b
            this.pageConfig.defaultCurrent = a
          }
        },
        detailsModal: null,
        addModal: false,
        recordModal: false
      }
    },
    methods: {
      add_project () {
        this.addModal = true
      },
      handleOk () {
      },
      handleSubmit() {
        console.log(this.formData)
      },
      detailsEvent(row) {
        this.detailsModal = row
      },
      onShowSizeChange(current, pageSize) {
        this.pageConfig.pageSize = pageSize
      }
    }
  }
</script>

<style scoped>
  .input-item {
    width: 280px;
  }

  .ant-btn + .ant-btn {
    margin-left: 16px;
  }

  .row-div {
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
  }
</style>