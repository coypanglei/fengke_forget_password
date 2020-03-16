<template>
  <!-- 基本信息 -->
  <div style="padding: 30px 20px 30px;">
    <a-spin :spinning="spinning">
      <div class="jia_top">
        <a-button type="primary" icon="save" :loading="loading" @click="baocun">保存</a-button>
      </div>
      <div class="jiben">
        <span class="jibena">汇法网信息</span>
        <div class="jibenb">
          <div class="shouxinaa">
            <div class="shouxinb">
              <span class="right">客户风险预警系统信息:</span>
              <a-textarea
                class="textarea"
                autosize
                placeholder
                :value="yujing"
                @change="(e) => { yujing = e.target.value }"
              />
            </div>
            <div class="shouxinb">
              <span class="right">汇法网信息:</span>
              <a-textarea
                class="textarea"
                autosize
                placeholder
                :value="huifawang"
                @change="(e) => { huifawang = e.target.value }"
              />
            </div>
          </div>
        </div>
      </div>
    </a-spin>
  </div>
</template>

<script>
import Vue from 'vue'
import moment from 'moment'
import { getAction } from '@/api/manage'
import { postAction } from '@/api/manage'
import { putAction } from '@/api/manage'
import { USER_INFO } from '@/store/mutation-types'

export default {
  name: 'jbxx',
  components: {},
  data() {
    return {
      yearList: [], //年份列表
      spinning: false,
      loading: false,
      yujing: '',//预警信息
      huifawang: '',//汇法网信息
      huifawangid: '',//汇法网id
    }
  },
  watch: {},
  props: ['id'],
  created() {},
  computed: {},

  methods: {
    getchuju() {
      let obj = {
        pid: this.id
      }
      this.loading = true
      getAction('/dhjcmb/dhjcmbGrjyHfw/queryByPid', obj)
        .then(res => {
          console.log(res)
          if (res.success == true) {
            this.huifawangid = res.result.id
            this.yujing = res.result.khfxyjxtxx
            this.huifawang = res.result.hfwxx
          } else {
            // 接口失败
            this.$notification.error({
              message: '提示',
              description: res.message,
              duration: 3
            })
          }
        })
        .finally(() => {
          this.loading = false
        })
    },
    //点击保存
    baocun() {
        this.add() //添加
    },
    //添加
    add() {
      let obj = {
        pid: this.id,
        id: this.huifawangid,
        khfxyjxtxx: this.yujing,
        hfwxx:this.huifawang,
      }
      this.loading = true
      putAction('/dhjcmb/dhjcmbGrjyHfw/saveOrUpdate', obj)
        .then(res => {
          console.log(res)
          if (res.success == true) {
            this.jibenid = res.result.id
            this.$emit('getjibenid',res.result.id)
            this.$notification.success({
              message: '成功',
              description: res.message,
              duration: 3
            })
          } else {
            // 接口失败
            this.$notification.error({
              message: '提示',
              description: res.message,
              duration: 3
            })
          }
        })
        .finally(() => {
          this.loading = false
        })
    }
  }
}
</script>

<style lang="less" scoped>
.jiben {
  position: relative;
  border: 1px solid rgba(73, 160, 237, 0.4);
  border-radius: 10px;
  min-height: 100px;
  margin-top: 24px;
  .jibena {
    position: absolute;
    left: 40px;
    top: -20px;
    background-color: #f3f2f2;
    height: 40px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #49a0ed;
    font-size: 16px;
    font-weight: 500;
    padding: 0 20px;
  }
  .jibenb {
    padding: 30px 10px 1px 10px;
    display: flex;
    flex-wrap: wrap;
    padding-bottom: 30px;
  }
}
.shouxinaa {
  position: relative;
  width: 100%;
  min-width: 1056px;
  min-height: 100px;
  font-size: 12px;
  color: #1e1c1f;
  .xuanzeqi {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 0px 42px;
    margin: 0;
    margin-bottom: 12px;
    span {
      width: 120px;
      text-align: right;
    }
    .data {
      width: 756px;
      height: 30px;
      color: black;
    }
    .right {
      margin-right: 30px;
      color: black;
    }
  }
  .shouxinb {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 0px 42px;
    margin: 0;
    margin-bottom: 12px;
    height: 123px;
    span {
      width: 120px;
      text-align: right;
    }
    input {
      width: 756px;
      height: 30px;
      color: black;
    }
    .data {
      width: 756px;
      height: 30px;
      color: black;
    }
    .right {
      margin-right: 30px;
      color: black;
    }
    .textarea {
      width: 756px !important;
      height: 123px !important;
      color: black;
    }
  }
}
</style>
