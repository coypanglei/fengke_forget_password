<template>
  <a-card :bordered="false">

    <!-- 查询区域 -->
    <div class="table-page-search-wrapper">
      <a-form layout="inline">
        <a-row :gutter="24">

          <a-col :md="6" :sm="8">
            <a-form-item label="施行日期">
              <j-date
					  placeholder="请选择"
					  v-model="queryParam.sxrq_begin"
					  :showTime="true"
					  dateFormat="YYYY-MM-DD"
					/>
            </a-form-item>
          </a-col>
          
          <a-col :md="6" :sm="8">
            <a-form-item label="~">
              <j-date
					  placeholder="请选择"
					  v-model="queryParam.sxrq_end"
					  :showTime="true"
					  dateFormat="YYYY-MM-DD"
					/>
            </a-form-item>
          </a-col>
        
          <a-col :md="6" :sm="8" >
            <span style="float: left;overflow: hidden;" class="table-page-search-submitButtons">
              <a-button type="primary" @click="searchQuery" icon="search">查询</a-button>
              <a-button type="primary" @click="searchReset" icon="reload" style="margin-left: 8px">重置</a-button>
              
            </span>
          </a-col>

        </a-row>
      </a-form>
    </div>

    <!-- 操作按钮区域 -->
    <div class="table-operator">
      
      <a-button type="primary" icon="download" @click="handleExportXls('内规管理日志')">导出</a-button>
      
    </div>

    <!-- table区域-begin -->
    <div>
      <div class="ant-alert ant-alert-info" style="margin-bottom: 16px;">
        <i class="anticon anticon-info-circle ant-alert-icon"></i> 已选择 <a style="font-weight: 600">{{ selectedRowKeys.length }}</a>项
        <a style="margin-left: 24px" @click="onClearSelected">清空</a>
      </div>

      <a-table
        ref="table"
        size="middle"
        bordered
        rowKey="id"
        :columns="columns"
        :dataSource="dataSource"
        :pagination="ipagination"
        :loading="loading"
        :rowSelection="{selectedRowKeys: selectedRowKeys, onChange: onSelectChange}"
        @change="handleTableChange">

        <span slot="action" slot-scope="text, record">
          <a @click="handleEdit(record)">查看</a>

          
        </span>

      </a-table>
    </div>
    <!-- table区域-end -->

    <!-- 表单区域 -->
    <!-- <ngglHis-modal ref="modalForm" @ok="modalFormOk"></ngglHis-modal> -->
    <nggl-modal ref="modalForm" @ok="modalFormOk"></nggl-modal>
  </a-card>
</template>

<script>
  import NgglModal from './modules/NgglHisModal'
  import { JeecgListMixin } from '@/mixins/JeecgListMixin'
import JDate from '@/components/jeecg/JDate'

  export default {
    name: "NgglHisList",
    mixins:[JeecgListMixin],
    components: {
      NgglModal,JDate
    },
    data () {
      return {
        description: '内规管理日志管理页面',
        // 表头
        columns: [
          {
            title: '序号',
            dataIndex: '',
            key:'rowIndex',
            width:60,
            align:"center",
            customRender:function (t,r,index) {
              return parseInt(index)+1;
            }
           },
		   {
            title: '制度名称',
            align:"center",
            dataIndex: 'zdmc'
           },
		   {
            title: '制度类别',
            align:"center",
            dataIndex: 'zdlb'
           },
		   {
            title: '制度文号',
            align:"center",
            dataIndex: 'zdwh'
           },
		   {
            title: '启用状态',
            align:"center",
            dataIndex: 'qyzt'
           },
		   {
            title: '施行日期',
            align:"center",
            dataIndex: 'sxrq'
           },
		   {
            title: '发布时间',
            align:"center",
            dataIndex: 'fbsj'
           },
          {
            title: '操作',
            dataIndex: 'action',
            align:"center",
            scopedSlots: { customRender: 'action' },
          }
        ],
		url: {
          list: "/hg2/ngglHis/list",
          delete: "/hg2/ngglHis/delete",
          deleteBatch: "/hg2/ngglHis/deleteBatch",
          exportXlsUrl: "hg2/ngglHis/exportXls",
          importExcelUrl: "hg2/ngglHis/importExcel",
       },
    }
  },
  computed: {
    importExcelUrl: function(){
      return `${window._CONFIG['domianURL']}/${this.url.importExcelUrl}`;
    }
  },
    methods: {
     
    }
  }
</script>
<style scoped>
  @import '~@assets/less/common.less'
</style>