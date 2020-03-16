<template>
  <a-card :bordered="false">
    <!-- 查询区域 -->
    <div class="table-page-search-wrapper">
      <a-form layout="inline">
        <a-row :gutter="24">
          <a-col :md="6" :sm="8">
            <a-form-item label="企业名称">
              <a-input placeholder="请输入企业名称" v-model="queryParam.qymc"></a-input>
            </a-form-item>
          </a-col>
          <a-col :md="6" :sm="8">
            <a-form-item label="企业证件号码">
              <a-input placeholder="请输入企业证件号码" v-model="queryParam.qyzjhm"></a-input>
            </a-form-item>
          </a-col>
          <template v-if="toggleSearchStatus">
            <a-col :md="6" :sm="8">
              <a-form-item label="贷款金额">
                <a-input placeholder="请输入贷款金额" v-model="queryParam.dkje"></a-input>
              </a-form-item>
            </a-col>
            <a-col :md="6" :sm="8">
              <a-form-item label="贷款余额">
                <a-input placeholder="请输入贷款余额" v-model="queryParam.dkye"></a-input>
              </a-form-item>
            </a-col>
            <a-col :md="6" :sm="8">
              <a-form-item label="起始日期">
                <a-input placeholder="请输入起始日期" v-model="queryParam.qsrq"></a-input>
              </a-form-item>
            </a-col>
          </template>
          <a-col :md="6" :sm="8">
            <span style="float: left;overflow: hidden;" class="table-page-search-submitButtons">
              <a-button type="primary" @click="searchQuery" icon="search">查询</a-button>
              <a-button
                type="primary"
                ghost
                @click="searchReset"
                icon="reload"
                style="margin-left: 8px"
              >重置</a-button>
              <a @click="handleToggleSearch" style="margin-left: 8px">
                {{ toggleSearchStatus ? '收起' : '展开' }}
                <a-icon :type="toggleSearchStatus ? 'up' : 'down'" />
              </a>
            </span>
          </a-col>
        </a-row>
      </a-form>
    </div>

    <!-- 操作按钮区域 -->
    <div class="table-operator">
      <a-button type="primary" icon="form" @click="tianbao">填报</a-button>
      <a-button type="primary" class="moBan" icon="download" @click="handleExportXlsas('对公贷款')">
        导出
      </a-button>
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
        :scroll="{ x: 1800}"
        @change="handleTableChange"
      ></a-table>
    </div>
    <!-- table区域-end -->
    <dgdk ref="modalForm" @diaoyong="diaoyong" @ok="modalFormOk"></dgdk>
  </a-card>
</template>

<script>
import { JeecgListMixin } from '@/mixins/JeecgListMixin'
import dgdk from './modules/dgdkModal'
import {getAction, downFile} from '@/api/manage'
export default {
  name: 'DhjcmbDgdkList',
  mixins: [JeecgListMixin],
  components: {
    dgdk
  },
  data() {
    return {
      description: '对公贷款管理页面',
      // 表头
      columns: [
        {
          title: '序号',
          dataIndex: '',
          key: 'rowIndex',
          width: 60,
          align: 'center',
          customRender: function(t, r, index) {
            return parseInt(index) + 1
          }
        },
        {
          title: '企业名称',
          align: 'center',
          dataIndex: 'qymc'
        },
        {
          title: '企业证件号码',
          align: 'center',
          dataIndex: 'qyzjhm'
        },
        {
          title: '贷款金额',
          align: 'center',
          dataIndex: 'dkje'
        },
        {
          title: '贷款余额',
          align: 'center',
          dataIndex: 'dkye'
        },
        {
          title: '起始日期',
          align: 'center',
          dataIndex: 'qsrq'
        },
        {
          title: '担保方式',
          align: 'center',
          dataIndex: 'dbfs'
        },
        {
          title: '贷款用途',
          align: 'center',
          dataIndex: 'dkyt'
        },
        {
          title: '客户地址',
          align: 'center',
          dataIndex: 'khdz'
        },
        {
          title: '法人代表',
          align: 'center',
          dataIndex: 'frdb'
        },
        {
          title: '法人证件号码',
          align: 'center',
          dataIndex: 'frzjhm'
        },
        {
          title: '联系方式',
          align: 'center',
          dataIndex: 'lxfs'
        },
        {
          title: '风险分类',
          align: 'center',
          dataIndex: 'fxfl'
        },
        {
          title: '所属行业',
          align: 'center',
          dataIndex: 'sshy'
        }
      ],
      url: {
        list: '/dhjcmb/dhjcmbDgdk/list'
      }
    }
  },
  computed: {
    importExcelUrl: function() {
      return `${window._CONFIG['domianURL']}/${this.url.importExcelUrl}`
    }
  },
  methods: {
    diaoyong() {
      this.loadData()
    },
    //填报
    tianbao() {
      if (this.selectedRowKeys.length == 0) {
        this.$notification.warn({
          message: '提示',
          description: `请选择填报的数据`,
          duration: 3
        })
      } else {
        //  this.$refs.modalForm.dakai()
        this.$refs.modalForm.dakai(this.selectionRows[0])
      }
    },//导出
    handleExportXlsas(fileName) {
      if (this.selectedRowKeys.length == 0) {
        this.$notification.warn({
          message: '提示',
          description: `请选择导出的数据`,
          duration: 3
        })
      } else {
        // this.see = true
        //  this.$refs.modalForm.dakai()
        for (let i = 0; i < this.dataSource.length; i++) {
          if (this.selectedRowKeys[0] == this.dataSource[i].id) {
            if (!fileName || typeof fileName != "string") {
              fileName = "导出文件"
            }
            let param = {...this.queryParam};
            if (this.selectedRowKeys && this.selectedRowKeys.length > 0) {
              param['selections'] = this.selectedRowKeys.join(",")
            }
            console.log("导出参数", param)
            downFile('/dhjcmb/dhjcmbDgdk/exportExcel?id=' + this.dataSource[i].id + '&sshy=' + this.dataSource[i].sshy, param).then((data) => {
              if (!data) {
                this.$message.warning("文件下载失败")
                return
              }
              if (typeof window.navigator.msSaveBlob !== 'undefined') {
                window.navigator.msSaveBlob(new Blob([data]), fileName + '.xls')
              } else {
                let url = window.URL.createObjectURL(new Blob([data]))
                let link = document.createElement('a')
                link.style.display = 'none'
                link.href = url
                link.setAttribute('download', fileName + '.xls')
                document.body.appendChild(link)
                link.click()
                document.body.removeChild(link); //下载完成移除元素
                window.URL.revokeObjectURL(url); //释放掉blob对象
              }
            })
          }
        }
      }
    }

  }
}
</script>
<style scoped>
@import '~@assets/less/common.less';
.moBan {
  background: #17c295;
  border: 1px solid #17c295;
}
.moBan:hover {
  background: #3ad0a8;
  border: 1px solid #17c295;
}
</style>