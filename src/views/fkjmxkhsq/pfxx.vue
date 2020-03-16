<template>
  <div style="padding: 30px 20px 30px;">
    <a-spin :spinning="spinning">
      <div class="jia_top">
        <a-button type="primary" icon="save" v-show="xianshi" @click="baocun">保存</a-button>
        <a-button
          v-show="dangqian && xianshi"
          type="primary"
          icon="save"
          @click="pifua"
          style="margin-left: 15px;"
        >批复</a-button>
      </div>
      <div class="jiben">
        <span class="jibena1">申请人信息</span>
        <div class="jibenb">
          <div class="jibenb_a1" v-for="(item,index) in piFuList" :key="index">
            <span class="jibenb_a_name1">{{item.name}}:</span>
            <a-date-picker
              class="data smallRight"
              style="width:198px;font-size:12px"
              v-if="item.value == null || item.value == ''"
              v-show="item.status == '2'"
              :allowClear="allowClear"
              :format="dateFormat"
              :disabled="jinyong"
              @change="(date, dateString)=>{ item.value =  dateString }"
            />
            <a-date-picker
              class="data smallRight"
              style="width:198px;font-size:12px"
              v-else
              v-show="item.status == '2'"
              :value="moment( item.value, dateFormat) "
              :allowClear="allowClear"
              :format="dateFormat"
              :disabled="jinyong"
              @change="(date, dateString)=>{ item.value =  dateString }"
            />
            <a-select
              placeholder
              :dropdownMatchSelectWidth="false"
              v-model="item.value"
              v-show="item.status == 3 "
              :disabled="jinyong"
              style="width:198px;font-size:12px"
            >
              <a-select-option
                v-for="(itea,ind) in item.second"
                :key="ind"
                :value="itea.name"
              >{{itea.name}}</a-select-option>
            </a-select>
            <a-textarea
              v-show="item.status == '4' "
              placeholder
              :value="item.value"
              :disabled="jinyong"
              @change="(value) => { item.value = value.target.value }"
              style="width:648px;height:60px;font-size:12px;color: black;"
            />
            <!-- <textarea
              v-show="item.status == '4' "
              :value="item.value"
              @change="(value) => { item.value = value }"
              style="width:648px;height:60px;padding:8px;font-size:12px;color: black;border-radius: 4px;border: 1px solid #d9d9d9;"
              placeholder
            ></textarea>-->
          </div>
        </div>
      </div>
      <shenpi ref="shenpi" :sfzh="zjhm"></shenpi>
    </a-spin>
  </div>
</template>

<script>
import Vue from 'vue'
import moment from 'moment'
import shenpi from '../../components/sxsq/danbao/jmxShenPi'
import { getAction } from '@/api/manage'
import { postAction } from '@/api/manage'
import { putAction } from '@/api/manage'
import { USER_INFO } from '@/store/mutation-types'

export default {
  name: 'jbxx',
  components: {
    shenpi
  },
  data() {
    return {
      moment,
      spinning: false,
      allowClear: false,
      dateFormat: 'YYYY-MM-DD',
      pifuid: '', //基本信息id
      jinyong: false,
      xianshi: true,
      piFuList: [
        {
          paraName: 'ncqcs',
          name: '是否获批',
          require: true,
          placehold: '',
          value: '',
          status: '3',
          second: [{ name: '是' }, { name: '否' }]
        },
        {
          paraName: 'pfrq',
          name: '批复日期',
          require: false,
          placehold: '',
          value: '',
          status: '2'
        },
        {
          paraName: 'pfnr',
          name: '批复内容',
          require: false,
          placehold: '',
          value: '',
          status: '4'
        }
      ]
    }
  },
  props: ['zjhm', 'id', 'dangqian', 'instid', 'taskid', 'look', 'notName'],
  watch: {},
  created() {
    
    if (this.look == false) {
      //当look为false时按钮隐藏，不可编辑
      this.jinyong = true //不可编辑
      this.xianshi = false //按钮隐藏
    } else {
      this.jinyong = false
      this.xianshi = true
    }
    if (this.notName == true) {
      //notName为true时按钮显示，可以编辑
      this.jinyong = false
      this.xianshi = true
    } else {
      this.jinyong = true
      this.xianshi = false
    }
  },
  computed: {},

  methods: {
    getchuju() {
      console.log(this.id)
      let obj = {
        pid: this.id
      }
      this.spinning = true
      getAction('/fkjmxkhsq/fkjmxkhsqPfxx/queryByPid', obj)
        .then(res => {
          console.log(res)
          if (res.success == true) {
            if(res.result == null){
              return
            }
            if (res.result.id == null || res.result.id == '') {
              this.pifuid = ''
            } else {
              this.pifuid = res.result.id
            }
            this.piFuList[0].value = res.result.sfhp //是否批复
            this.piFuList[1].value = res.result.pfrq //批复日期
            this.piFuList[2].value = res.result.pfnr //批复内容
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
          this.spinning = false
        })
    },
    // 保存按钮
    baocun() {
      if (this.pifuid == '') {
        this.addPiFu() //添加批复信息
      } else {
        this.editPiFu()
      }
    },
    //添加批复信息
    addPiFu() {
      let obj = {
        pid: this.id,
        sfhp: this.piFuList[0].value, //是否批复
        pfrq: this.piFuList[1].value, //批复日期
        pfnr: this.piFuList[2].value //批复内容
      }
      this.spinning = true
      postAction('/fkjmxkhsq/fkjmxkhsqPfxx/add', obj)
        .then(res => {
          console.log(res)
          if (res.success == true) {
            this.getchuju();
            this.$notification.success({
              message: '提示',
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
          this.spinning = false
        })
    },
    //更改批复信息
    editPiFu() {
      let obj = {
        id: this.pifuid,
        sfhp: this.piFuList[0].value, //是否批复
        pfrq: this.piFuList[1].value, //批复日期
        pfnr: this.piFuList[2].value //批复内容
      }
      this.spinning = true
      putAction('/fkjmxkhsq/fkjmxkhsqPfxx/edit', obj)
        .then(res => {
          console.log(res)
          if (res.success == true) {
            this.$notification.success({
              message: '提示',
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
          this.spinning = false
        })
    },
    //批复
    pifua() {
      console.log(this.pifuid)
      if (this.pifuid == '' || this.pifuid == null) {
        this.$notification.warn({
          message: '提示',
          description: '请先保存信息!',
          duration: 3
        })
        return
      }

      this.$refs.shenpi.dakai(this.instid, this.taskid)
    }
  }
}
</script>

<style scoped>
.jiben {
  position: relative;
  border: 1px solid rgba(73, 160, 237, 0.4);
  border-radius: 10px;
  min-height: 100px;
  margin-top: 24px;
}

.jibena1 {
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
  padding: 10px 10px;
  display: flex;
  flex-wrap: wrap;
  padding-bottom: 30px;
}

.jibenb_a1 {
  display: flex;
  /* // width: 346px; */
  margin-top: 20px;
  align-items: center;
  margin-right: 10px;
}

.jibenb_a_name1 {
  color: black;
  width: 240px;
  font-size: 12px;
  padding-right: 10px;
  text-align: right;
  display: flex;
  justify-content: flex-end;

  align-items: center;
}
</style>
