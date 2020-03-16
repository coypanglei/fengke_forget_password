<template>
  <a-card :bordered="false">

    <!-- 查询区域 -->
    <div class="table-page-search-wrapper">
      <a-form layout="inline">
        <a-row :gutter="24">

          
          <a-col :md="6" :sm="8">
            <a-form-item label="制度名称">
              <a-input placeholder="请输入制度名称" v-model="queryParam.zdmc"></a-input>
            </a-form-item>
          </a-col>
        
        <a-col :md="6" :sm="8">
            <a-form-item label="报审日期">
              <j-date
					  placeholder="报审日期起"
					  v-model="queryParam.createTime_begin"
					  :showTime="true"
					  dateFormat="YYYY-MM-DD"
					/>
            </a-form-item>
          </a-col>
          <a-col :md="6" :sm="8">
            <a-form-item label="~">
              <j-date
					  placeholder="报审日期止"
					  v-model="queryParam.createTime_end"
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
      <a-button @click="handleAdd" type="primary" icon="plus">新增</a-button>
      <a-button type="primary" icon="download" @click="handleExportXls('规章制度报审')">导出</a-button>
      <!-- <a-upload name="file" :showUploadList="false" :multiple="false" :headers="tokenHeader" :action="importExcelUrl" @change="handleImportExcel">
        <a-button type="primary" icon="import">导入</a-button>
      </a-upload>
      <a-dropdown v-if="selectedRowKeys.length > 0">
        <a-menu slot="overlay">
          <a-menu-item key="1" @click="batchDel"><a-icon type="delete"/>删除</a-menu-item>
        </a-menu>
        <a-button style="margin-left: 8px"> 批量操作 <a-icon type="down" /></a-button>
      </a-dropdown> -->
    </div>

    <!-- table区域-begin -->
    <div>
      <!-- <div class="ant-alert ant-alert-info" style="margin-bottom: 16px;">
        <i class="anticon anticon-info-circle ant-alert-icon"></i> 已选择 <a style="font-weight: 600">{{ selectedRowKeys.length }}</a>项
        <a style="margin-left: 24px" @click="onClearSelected">清空</a>
      </div> -->

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

          <!-- <a-divider type="vertical" />
          <a-dropdown>
            <a class="ant-dropdown-link">更多 <a-icon type="down" /></a>
            <a-menu slot="overlay">
              <a-menu-item>
                <a-popconfirm title="确定删除吗?" @confirm="() => handleDelete(record.id)">
                  <a>删除</a>
                </a-popconfirm>
              </a-menu-item>
            </a-menu>
          </a-dropdown> -->
        </span>

      </a-table>
    </div>
    <!-- table区域-end -->

    <!-- 表单区域 -->
    <gzzdbs-modal ref="modalForm" @ok="modalFormOk"></gzzdbs-modal>
  </a-card>
</template>

<script>
import JDate from '@/components/jeecg/JDate'
  import GzzdbsModal from './modules/GzzdbsModal'
  import { JeecgListMixin } from '@/mixins/JeecgListMixin'

  export default {
    name: "GzzdbsList",
    mixins:[JeecgListMixin],
    components: {
      GzzdbsModal,JDate
    },
    data () {
      return {
        description: '规章制度报审管理页面',
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
            title: '制度类别',
            align:"center",
            dataIndex: 'zdlb'
           },
		   {
            title: '制度名称',
            align:"center",
            dataIndex: 'zdmc'
           },
		   {
            title: '报审人',
            align:"center",
            dataIndex: 'createByName'
           },
		   
          {
            title: '操作',
            dataIndex: 'action',
            align:"center",
            scopedSlots: { customRender: 'action' },
          }
        ],
		url: {
          list: "/hg2/gzzdbs/list",
          delete: "/hg2/gzzdbs/delete",
          deleteBatch: "/hg2/gzzdbs/deleteBatch",
          exportXlsUrl: "hg2/gzzdbs/exportXls",
          importExcelUrl: "hg2/gzzdbs/importExcel",
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