<template>
  <a-card :bordered="false">

    <!-- 查询区域 -->
    <div class="table-page-search-wrapper">
      <a-form layout="inline">
        <a-row :gutter="24">

          <a-col :md="6" :sm="8">
            <a-form-item label="申请人姓名">
              <a-input placeholder="请输入申请人姓名" v-model="queryParam.sqrxm"></a-input>
            </a-form-item>
          </a-col>
          <a-col :md="6" :sm="8">
            <a-form-item label="身份证号">
              <a-input placeholder="请输入身份证号" v-model="queryParam.sfzh"></a-input>
            </a-form-item>
          </a-col>
        <template v-if="toggleSearchStatus">
        <a-col :md="6" :sm="8">
            <a-form-item label="性别">
              <a-input placeholder="请输入性别" v-model="queryParam.xb"></a-input>
            </a-form-item>
          </a-col>
          <a-col :md="6" :sm="8">
            <a-form-item label="联系方式">
              <a-input placeholder="请输入联系方式" v-model="queryParam.lxfs"></a-input>
            </a-form-item>
          </a-col>
          <a-col :md="6" :sm="8">
            <a-form-item label="居住地址">
              <a-input placeholder="请输入居住地址" v-model="queryParam.jzdz"></a-input>
            </a-form-item>
          </a-col>
        </template>
          <a-col :md="6" :sm="8" >
            <span style="float: left;overflow: hidden;" class="table-page-search-submitButtons">
              <a-button type="primary" @click="searchQuery" icon="search">查询</a-button>
              <a-button type="primary" ghost @click="searchReset" icon="reload" style="margin-left: 8px">重置</a-button>
              <a @click="handleToggleSearch" style="margin-left: 8px">
                {{ toggleSearchStatus ? '收起' : '展开' }}
                <a-icon :type="toggleSearchStatus ? 'up' : 'down'"/>
              </a>
            </span>
          </a-col>

        </a-row>
      </a-form>
    </div>

    <!-- 操作按钮区域 -->
    <div class="table-operator">
      <a-button @click="handleAdd" type="primary" icon="plus">新增</a-button>
      <a-button type="primary" style="margin-left: 10px" icon="audit" @click="diacha">查看打印</a-button>
    </div>

    <!-- table区域-begin -->
    <div>
      <a-table
        ref="table"
        size="small"
        bordered
        rowKey="id"
        :columns="columns"
        :dataSource="dataSource"
        :pagination="ipagination"
        :loading="loading"
        :rowSelection="{selectedRowKeys: selectedRowKeys,type:'radio', onChange: onSelectChange}"
        @change="handleTableChange">

        <span slot="action" slot-scope="text, record">
          <a @click="handleEdit(record)">编辑</a>

          <a-divider type="vertical" />
          <a-dropdown>
            <a class="ant-dropdown-link">更多 <a-icon type="down" /></a>
            <a-menu slot="overlay">
              <a-menu-item>
                <a-popconfirm title="确定删除吗?" @confirm="() => handleDelete(record.id)">
                  <a>删除</a>
                </a-popconfirm>
              </a-menu-item>
            </a-menu>
          </a-dropdown>
        </span>

      </a-table>
    </div>
    <!-- 经营简化类 -->
    <grdkdcjbjhjyl ref="grdkdcjbjhjylas" ></grdkdcjbjhjyl>
    <!-- 经营类 -->
    <grdkdcjbjyl ref="grdkdcjbjylas"></grdkdcjbjyl>
    <!-- 农户类 -->
    <grdkdcjbnhl ref="grdkdcjbnhlas"></grdkdcjbnhl>
    <!-- 表单区域 -->
    <sxspdyGrdk-modal ref="modalForm" @ok="modalFormOk"></sxspdyGrdk-modal>
  </a-card>
</template>

<script>
  import SxspdyGrdkModal from './modules/SxspdyGrdkModal'
  import { JeecgListMixin } from '@/mixins/JeecgListMixin'
  import grdkdcjbjhjyl from './modules/grdkdcjbjhjyl'
  import grdkdcjbjyl from './modules/grdkdcjbjyl'
  import grdkdcjbnhl from './modules/grdkdcjbnhl'
  export default {
    name: "SxspdyGrdkList",
    mixins:[JeecgListMixin],
    components: {
      SxspdyGrdkModal,
      grdkdcjbjhjyl,
      grdkdcjbjyl,
      grdkdcjbnhl
    },
    data () {
      return {
        description: '个人贷款调查简表管理页面',
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
            title: '申请人姓名',
            align:"center",
            dataIndex: 'sqrxm'
           },
		   {
            title: '身份证号',
            align:"center",
            dataIndex: 'sfzh'
           },
		   {
            title: '性别',
            align:"center",
            dataIndex: 'xb'
           },
		   {
            title: '联系方式',
            align:"center",
            dataIndex: 'lxfs'
           },
		   {
            title: '居住地址',
            align:"center",
            dataIndex: 'jzdz'
           },
		   {
            title: '调查类型',
            align:"center",
            dataIndex: 'dclx'
           },
		   {
            title: '受理支行',
            align:"center",
            dataIndex: 'slzh'
           },
          {
            title: '操作',
            dataIndex: 'action',
            align:"center",
            scopedSlots: { customRender: 'action' },
          }
        ],
		url: {
          list: "/business/sxspdyGrdk/list",
          delete: "/business/sxspdyGrdk/delete",
          deleteBatch: "/business/sxspdyGrdk/deleteBatch",
          exportXlsUrl: "business/sxspdyGrdk/exportXls",
          importExcelUrl: "business/sxspdyGrdk/importExcel",
       },
    }
  },
  computed: {
    importExcelUrl: function(){
      return `${window._CONFIG['domianURL']}/${this.url.importExcelUrl}`;
    }
  },
    methods: {
     diacha() {
       let a = "农户类"
      let that = this
      if (that.selectedRowKeys.length == 0) {
        that.$notification.warn({
          message: '提示',
          description: `请选择要打印得数据`,
          duration: 3
        })
      } else {
        if( a == '经营类' ){
          that.$refs.grdkdcjbjylas.dakai(that.selectedRowKeys[0])
        }else if( a == '经营简化类' ){
          that.$refs.grdkdcjbjhjylas.dakai(that.selectedRowKeys[0])
        }else if( a=="农户类" ){
          console.log( "农户类" )
          that.$refs.grdkdcjbnhlas.dakai( that.selectedRowKeys[0] )
        }
        
      }
    }
    }
  }
</script>
<style scoped>
  @import '~@assets/less/common.less'
</style>