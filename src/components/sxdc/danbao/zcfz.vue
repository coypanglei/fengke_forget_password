<template>
  <div>
    <a-spin :spinning="spinning">
      <div class="jia_top">
        <a-button type="primary" icon="save" @click="PreservationZcFz" v-show="seediaocha">保存</a-button>
      </div>

      <div style="width:100%;overflow-x: auto;">
        <div class="shouxin" style="padding-bottom:40px">
          <p class="shouxina">
            <span style="text-align:left;color:#49a0ed;font-size:16px;">资产</span>
            <span class="black">价值(万元)</span>
            <span class="black" style="width:45%">备注</span>
          </p>
          <p class="shouxinba">
            <span class="black">货币性资金</span>
            <input type="number" :value="huoBiJiaZhi" @change="(e)=>{ huoBiJiaZhi=e.target.value }" />
            <input
              :value="huoBiBeiZhu"
              style="width:45%"
              @change="(e)=>{ huoBiBeiZhu=e.target.value }"
            />
          </p>
          <p class="shouxinca">
            <span class="black">房地产</span>
            <input
              type="number"
              :value="fangDiChanJiaZhi"
              @change="(e)=>{ fangDiChanJiaZhi=e.target.value }"
            />
            <input
              :value="fangdichanbeizhu"
              style="width:45%"
              @change="(e)=>{ fangdichanbeizhu=e.target.value }"
            />
          </p>
          <p class="shouxinba">
            <span class="black">车辆</span>
            <input
              type="number"
              :value="cheliangjiazhi"
              @change="(e)=>{ cheliangjiazhi=e.target.value }"
            />
            <input
              :value="cheliangbeizhu"
              style="width:45%"
              @change="(e)=>{ cheliangbeizhu=e.target.value }"
            />
          </p>
          <p class="shouxinca">
            <span class="black">存款</span>
            <input
              type="number"
              :value="cunkuanjiazhi"
              @change="(e)=>{ cunkuanjiazhi=e.target.value }"
            />
            <input
              :value="cunkuanbeizhu"
              style="width:45%"
              @change="(e)=>{ cunkuanbeizhu=e.target.value }"
            />
          </p>
          <p class="shouxinba">
            <span class="black">应收账款</span>
            <input
              type="number"
              :value="yingshoujiazhi"
              @change="(e)=>{ yingshoujiazhi=e.target.value }"
            />
            <input
              :value="yingshoubeizhu"
              style="width:45%"
              @change="(e)=>{ yingshoubeizhu=e.target.value }"
            />
          </p>
          <p class="shouxinca">
            <span class="black">其他资产</span>
            <input type="number" :value="qitazichan" @change="(e)=>{ qitazichan=e.target.value }" />
            <input
              :value="qitabeizhu"
              style="width:45%"
              @change="(e)=>{ qitabeizhu=e.target.value }"
            />
          </p>
        </div>
      </div>

      <div style="width:100%;overflow-x: auto;">
        <div class="shouxin" style="padding-bottom:40px">
          <p class="shouxina">
            <span style="text-align:left;color:#49a0ed;font-size:16px;">负债</span>
            <span class="black">价值(万元)</span>
            <span class="black" style="width:45%">备注</span>
          </p>
          <p class="shouxinba">
            <span class="black">房贷</span>
            <input
              type="number"
              :value="fangdaijiazhi"
              @change="(e)=>{ fangdaijiazhi=e.target.value }"
            />
            <input
              :value="fandaibeizhu"
              style="width:45%"
              @change="(e)=>{ fandaibeizhu=e.target.value }"
            />
          </p>
          <p class="shouxinca">
            <span class="black">车贷</span>
            <input
              type="number"
              :value="chedaijiazhi"
              @change="(e)=>{ chedaijiazhi=e.target.value }"
            />
            <input
              :value="chedaibeizhu"
              style="width:45%"
              @change="(e)=>{ chedaibeizhu=e.target.value }"
            />
          </p>
          <p class="shouxinba">
            <span class="black">消费贷</span>
            <input
              type="number"
              :value="xiaofeijiazhi"
              @change="(e)=>{ xiaofeijiazhi=e.target.value }"
            />
            <input
              :value="xiaofeibeizhu"
              style="width:45%"
              @change="(e)=>{ xiaofeibeizhu=e.target.value }"
            />
          </p>
          <p class="shouxinca">
            <span class="black">经营性贷款</span>
            <input
              type="number"
              :value="jingyingjiazhi"
              @change="(e)=>{ jingyingjiazhi=e.target.value }"
            />
            <input
              :value="jingyingbeizhu"
              style="width:45%"
              @change="(e)=>{ jingyingbeizhu=e.target.value }"
            />
          </p>
          <p class="shouxinba">
            <span class="black">信用卡</span>
            <input
              type="number"
              :value="xinyongkajiazhi"
              @change="(e)=>{ xinyongkajiazhi=e.target.value }"
            />
            <input
              :value="xinyongkabeizhu"
              style="width:45%"
              @change="(e)=>{ xinyongkabeizhu=e.target.value }"
            />
          </p>
          <p class="shouxinca">
            <span class="black">其他负债</span>
            <input
              type="number"
              :value="qitafuzhaijiazhi"
              @change="(e)=>{ qitafuzhaijiazhi=e.target.value }"
            />
            <input
              :value="qitafuzhaibeizhu"
              style="width:45%"
              @change="(e)=>{ qitafuzhaibeizhu=e.target.value }"
            />
          </p>
        </div>
      </div>
      <div style="width:100%;overflow-x: auto;">
        <div class="shouxin" style="padding-bottom:40px">
          <p class="shouxina">
            <span style="text-align:left;color:#49a0ed;font-size:16px;">
              担保
              <a style="color:#1c1a1d;font-size:12px;">/借款人姓名</a>
            </span>
            <span class="black">价值(万元)</span>
            <span class="black">五级分类</span>
            <span class="beizhu black">备注</span>
          </p>
          <p class="shouxinba">
            <input :value="fuZhaiDanBaoName1" @change="(e)=>{ fuZhaiDanBaoName1=e.target.value }" />
            <input
              type="number"
              :value="fuZhaiDaoBaoJiaZhi1"
              @change="(e)=>{ fuZhaiDaoBaoJiaZhi1=e.target.value }"
            />
            <input :value="fuZhaiDanBaoWuJI1" @change="(e)=>{ fuZhaiDanBaoWuJI1=e.target.value }" />
            <input
              :value="fuZhaiDanBaoBeiZhu1"
              class="beizhu"
              @change="(e)=>{ fuZhaiDanBaoBeiZhu1=e.target.value }"
            />
          </p>
          <p class="shouxinca">
            <input :value="fuZhaiDanBaoName2" @change="(e)=>{ fuZhaiDanBaoName2=e.target.value }" />
            <input
              type="number"
              :value="fuZhaiDaoBaoJiaZhi2"
              @change="(e)=>{ fuZhaiDaoBaoJiaZhi2=e.target.value }"
            />
            <input :value="fuZhaiDanBaoWuJI2" @change="(e)=>{ fuZhaiDanBaoWuJI2=e.target.value }" />
            <input
              :value="fuZhaiDanBaoBeiZhu2"
              class="beizhu"
              @change="(e)=>{ fuZhaiDanBaoBeiZhu2=e.target.value }"
            />
          </p>
          <p class="shouxinba">
            <input :value="fuZhaiDanBaoName3" @change="(e)=>{ fuZhaiDanBaoName3=e.target.value }" />
            <input
              type="number"
              v-model="fuZhaiDaoBaoJiaZhi3"
              @change="(e)=>{ fuZhaiDaoBaoJiaZhi3=e.target.value }"
            />
            <input :value="fuZhaiDanBaoWuJI3" @change="(e)=>{ fuZhaiDanBaoWuJI3=e.target.value }" />
            <input
              :value="fuZhaiDanBaoBeiZhu3"
              class="beizhu"
              @change="(e)=>{ fuZhaiDanBaoBeiZhu3=e.target.value }"
            />
          </p>
          <p class="shouxinba">
            <input :value="fuZhaiDanBaoName4" @change="(e)=>{ fuZhaiDanBaoName4=e.target.value }" />
            <input
              type="number"
              v-model="fuZhaiDaoBaoJiaZhi4"
              @change="(e)=>{ fuZhaiDaoBaoJiaZhi4=e.target.value }"
            />
            <input :value="fuZhaiDanBaoWuJI4" @change="(e)=>{ fuZhaiDanBaoWuJI4=e.target.value }" />
            <input
              :value="fuZhaiDanBaoBeiZhu4"
              class="beizhu"
              @change="(e)=>{ fuZhaiDanBaoBeiZhu4=e.target.value }"
            />
          </p>
          <p class="shouxinba">
            <input :value="fuZhaiDanBaoName5" @change="(e)=>{ fuZhaiDanBaoName5=e.target.value }" />
            <input
              type="number"
              v-model="fuZhaiDaoBaoJiaZhi5"
              @change="(e)=>{ fuZhaiDaoBaoJiaZhi5=e.target.value }"
            />
            <input :value="fuZhaiDanBaoWuJI5" @change="(e)=>{ fuZhaiDanBaoWuJI5=e.target.value }" />
            <input
              :value="fuZhaiDanBaoBeiZhu5"
              class="beizhu"
              @change="(e)=>{ fuZhaiDanBaoBeiZhu5=e.target.value }"
            />
          </p>
        </div>
      </div>

      <div class="zheng_all">
        <div class="dailuanliebiao" style="background-color:#f3f2f2;border:none">
          <div
            class="dailuanliebiao_a zongzichan"
            style="width:326px;height:120px;margin-left:0px;margin-right:56px;"
          >
            <p class="dailuanliebiao_a_a">总资产(万元)</p>
            <div class="dailuanliebiao_b zongzichand">
              <p
                class="dailuanliebiao_b_s blue"
                style="font-size: 20px;font-weight: 600;"
              >{{zongZiChan}}</p>
            </div>
          </div>
          <div
            class="dailuanliebiao_a zongzichanb"
            style="width:326px;height:120px;margin-left:0px;margin-right:56px;"
          >
            <p class="dailuanliebiao_a_a">总负债(万元)</p>
            <div class="dailuanliebiao_b zongzichand">
              <p
                class="dailuanliebiao_b_s blue"
                style="font-size: 20px;font-weight: 600;"
              >{{zongFuZhai}}</p>
            </div>
          </div>
          <div
            class="dailuanliebiao_a zongzichanc"
            style="width:326px;height:120px;margin-left:0px;margin-right:56px;"
          >
            <p class="dailuanliebiao_a_a">对外担保总额(万元)</p>
            <div class="dailuanliebiao_b zongzichand">
              <p
                class="dailuanliebiao_b_s blue"
                style="font-size: 20px;font-weight: 600;"
              >{{duiWaiDanBaoZongE}}</p>
            </div>
          </div>
          <div
            class="dailuanliebiao_a"
            style="width:326px;height:120px;margin-left:0px;margin-right:56px;"
          >
            <p class="dailuanliebiao_a_a">净资产(万元)</p>
            <div class="dailuanliebiao_b zongzichand">
              <p
                class="dailuanliebiao_b_s blue"
                style="font-size: 20px;font-weight: 600;"
              >{{jingZiChan}}</p>
            </div>
          </div>
          <div
            class="dailuanliebiao_a"
            style="width:326px;height:120px;margin-left:0px;margin-right:56px;"
          >
            <p class="dailuanliebiao_a_a">资产负债率%</p>
            <div class="dailuanliebiao_b zongzichand">
              <p style="font-size: 20px;font-weight: 600;" class="zaichanfuzhai">{{ziChanFuZhaiLv}}</p>
            </div>
          </div>
        </div>
      </div>
    </a-spin>
  </div>
</template>
<script>
import { httpAction } from '@/api/manage'
import pick from 'lodash.pick'
import { getAction } from '@/api/manage'
import { putAction } from '@/api/manage'
import { postAction } from '@/api/manage'
import upshouxin from './upshouxin'
import moment from 'moment'

export default {
  name: 'xtsj',
  components: { upshouxin },
  props: ['seediaocha', 'leibie', 'instid', 'id', 'sxid', 'taskid', 'sfzh'],

  data() {
    return {
      moment,
      spinning: false,
      dateFormat: 'YYYY-MM-DD',
      allowClear: false,
      ZcFzId: '', //年收入id
      huoBiJiaZhi: '', //货币性资金价值
      huoBiBeiZhu: '', //货币性资金价值
      fangDiChanJiaZhi: '', //房地产价值
      fangdichanbeizhu: '', //房地产备注
      cheliangjiazhi: '', //车辆价值
      cheliangbeizhu: '', //车辆备注
      cunkuanjiazhi: '', //存款价值
      cunkuanbeizhu: '', //存款备注
      yingshoujiazhi: '', //应收账款价值
      yingshoubeizhu: '', //应收账款备注
      qitazichan: '', //其他资产价值
      qitabeizhu: '', //其他资产备注
      fangdaijiazhi: '', //房贷价值
      fandaibeizhu: '', //房贷备注
      chedaijiazhi: '', //车贷价值
      chedaibeizhu: '', //车贷备注
      xiaofeijiazhi: '', //消费贷价值
      xiaofeibeizhu: '', //消费贷备注
      jingyingjiazhi: '', //经营性贷款价值
      jingyingbeizhu: '', //经营性贷款备注
      xinyongkajiazhi: '', //信用卡价值
      xinyongkabeizhu: '', //信用卡备注
      qitafuzhaijiazhi: '', //其他负债价值
      qitafuzhaibeizhu: '', //其他负债备注
      fuZhaiDanBaoName1: '', //担保人姓名
      fuZhaiDaoBaoJiaZhi1: '', //担保人价值
      fuZhaiDanBaoWuJI1: '', //担保人五级分类
      fuZhaiDanBaoBeiZhu1: '', //担保人备注
      fuZhaiDanBaoName2: '', //担保人姓名
      fuZhaiDaoBaoJiaZhi2: '', //担保人价值
      fuZhaiDanBaoWuJI2: '', //担保人五级分类
      fuZhaiDanBaoBeiZhu2: '', //担保人备注
      fuZhaiDanBaoName3: '', //担保人姓名
      fuZhaiDaoBaoJiaZhi3: '', //担保人价值
      fuZhaiDanBaoWuJI3: '', //担保人五级分类
      fuZhaiDanBaoBeiZhu3: '', //担保人备注
      // fuZhaiDanBaoBeiZhu5:"",
      fuZhaiDanBaoName1: '', //资产负债担保人名字1
      fuZhaiDanBaoName2: '', //资产负债担保人名字2
      fuZhaiDanBaoName3: '', //资产负债担保人名字3
      fuZhaiDanBaoName4: '', //资产负债担保人名字4
      fuZhaiDanBaoName5: '', //资产负债担保人名字5
      fuZhaiDaoBaoJiaZhi1: '', //负债担保价值1
      fuZhaiDaoBaoJiaZhi2: '', //负债担保价值2
      fuZhaiDaoBaoJiaZhi3: '', //负债担保价值3
      fuZhaiDaoBaoJiaZhi4: '', //负债担保价值4
      fuZhaiDaoBaoJiaZhi5: '', //负债担保价值5
      fuZhaiDanBaoWuJI1: '', //负债担保五级分类1
      fuZhaiDanBaoWuJI2: '', //负债担保五级分类2
      fuZhaiDanBaoWuJI3: '', //负债担保五级分类3
      fuZhaiDanBaoWuJI4: '', //负债担保五级分类4
      fuZhaiDanBaoWuJI5: '', //负债担保五级分类5
      fuZhaiDanBaoBeiZhu1: '', //负债担保备注1
      fuZhaiDanBaoBeiZhu2: '', //负债担保备注2
      fuZhaiDanBaoBeiZhu3: '', //负债担保备注3
      fuZhaiDanBaoBeiZhu4: '', //负债担保备注4
      fuZhaiDanBaoBeiZhu5: '', //负债担保备注5

      zongZiChan: '', //总资产
      zongFuZhai: '', //总负债
      duiWaiDanBaoZongE: '', //对外担保总额
      jingZiChan: '', //净资产
      ziChanFuZhaiLv: '' //资产负债率
    }
  },
  created() {},
  watch: {
    //工薪类-授信调查-资产负债
    //总资产
    huoBiJiaZhi: function() {
      this.zongZiChan = (
        Number(this.huoBiJiaZhi) +
        Number(this.fangDiChanJiaZhi) +
        Number(this.cheliangjiazhi) +
        Number(this.cunkuanjiazhi) +
        Number(this.yingshoujiazhi) +
        Number(this.qitazichan)
      ).toFixed(1)
    },
    fangDiChanJiaZhi: function() {
      this.zongZiChan = (
        Number(this.huoBiJiaZhi) +
        Number(this.fangDiChanJiaZhi) +
        Number(this.cheliangjiazhi) +
        Number(this.cunkuanjiazhi) +
        Number(this.yingshoujiazhi) +
        Number(this.qitazichan)
      ).toFixed(1)
    },
    cheliangjiazhi: function() {
      this.zongZiChan = (
        Number(this.huoBiJiaZhi) +
        Number(this.fangDiChanJiaZhi) +
        Number(this.cheliangjiazhi) +
        Number(this.cunkuanjiazhi) +
        Number(this.yingshoujiazhi) +
        Number(this.qitazichan)
      ).toFixed(1)
    },
    cunkuanjiazhi: function() {
      this.zongZiChan = (
        Number(this.huoBiJiaZhi) +
        Number(this.fangDiChanJiaZhi) +
        Number(this.cheliangjiazhi) +
        Number(this.cunkuanjiazhi) +
        Number(this.yingshoujiazhi) +
        Number(this.qitazichan)
      ).toFixed(1)
    },
    yingshoujiazhi: function() {
      this.zongZiChan = (
        Number(this.huoBiJiaZhi) +
        Number(this.fangDiChanJiaZhi) +
        Number(this.cheliangjiazhi) +
        Number(this.cunkuanjiazhi) +
        Number(this.yingshoujiazhi) +
        Number(this.qitazichan)
      ).toFixed(1)
    },
    qitazichan: function() {
      this.zongZiChan = (
        Number(this.huoBiJiaZhi) +
        Number(this.fangDiChanJiaZhi) +
        Number(this.cheliangjiazhi) +
        Number(this.cunkuanjiazhi) +
        Number(this.yingshoujiazhi) +
        Number(this.qitazichan)
      ).toFixed(1)
    },
    //总负债
    fangdaijiazhi: function() {
      this.zongFuZhai = (
        Number(this.fangdaijiazhi) +
        Number(this.chedaijiazhi) +
        Number(this.xiaofeijiazhi) +
        Number(this.jingyingjiazhi) +
        Number(this.xinyongkajiazhi) +
        Number(this.qitafuzhaijiazhi)
      ).toFixed(1)
    },
    chedaijiazhi: function() {
      this.zongFuZhai = (
        Number(this.fangdaijiazhi) +
        Number(this.chedaijiazhi) +
        Number(this.xiaofeijiazhi) +
        Number(this.jingyingjiazhi) +
        Number(this.xinyongkajiazhi) +
        Number(this.qitafuzhaijiazhi)
      ).toFixed(1)
    },
    xiaofeijiazhi: function() {
      this.zongFuZhai = (
        Number(this.fangdaijiazhi) +
        Number(this.chedaijiazhi) +
        Number(this.xiaofeijiazhi) +
        Number(this.jingyingjiazhi) +
        Number(this.xinyongkajiazhi) +
        Number(this.qitafuzhaijiazhi)
      ).toFixed(1)
    },
    jingyingjiazhi: function() {
      this.zongFuZhai = (
        Number(this.fangdaijiazhi) +
        Number(this.chedaijiazhi) +
        Number(this.xiaofeijiazhi) +
        Number(this.jingyingjiazhi) +
        Number(this.xinyongkajiazhi) +
        Number(this.qitafuzhaijiazhi)
      ).toFixed(1)
    },
    xinyongkajiazhi: function() {
      this.zongFuZhai = (
        Number(this.fangdaijiazhi) +
        Number(this.chedaijiazhi) +
        Number(this.xiaofeijiazhi) +
        Number(this.jingyingjiazhi) +
        Number(this.xinyongkajiazhi) +
        Number(this.qitafuzhaijiazhi)
      ).toFixed(1)
    },
    qitafuzhaijiazhi: function() {
      this.zongFuZhai = (
        Number(this.fangdaijiazhi) +
        Number(this.chedaijiazhi) +
        Number(this.xiaofeijiazhi) +
        Number(this.jingyingjiazhi) +
        Number(this.xinyongkajiazhi) +
        Number(this.qitafuzhaijiazhi)
      ).toFixed(1)
    },
    //对外担保总额
    fuZhaiDaoBaoJiaZhi1: function() {
      this.duiWaiDanBaoZongE = (
        Number(this.fuZhaiDaoBaoJiaZhi1) +
        Number(this.fuZhaiDaoBaoJiaZhi2) +
        Number(this.fuZhaiDaoBaoJiaZhi3) +
        Number(this.fuZhaiDaoBaoJiaZhi4) +
        Number(this.fuZhaiDaoBaoJiaZhi5)
      ).toFixed(1)
    },
    fuZhaiDaoBaoJiaZhi2: function() {
      this.duiWaiDanBaoZongE = (
        Number(this.fuZhaiDaoBaoJiaZhi1) +
        Number(this.fuZhaiDaoBaoJiaZhi2) +
        Number(this.fuZhaiDaoBaoJiaZhi3) +
        Number(this.fuZhaiDaoBaoJiaZhi4) +
        Number(this.fuZhaiDaoBaoJiaZhi5)
      ).toFixed(1)
    },
    fuZhaiDaoBaoJiaZhi3: function() {
      this.duiWaiDanBaoZongE = (
        Number(this.fuZhaiDaoBaoJiaZhi1) +
        Number(this.fuZhaiDaoBaoJiaZhi2) +
        Number(this.fuZhaiDaoBaoJiaZhi3) +
        Number(this.fuZhaiDaoBaoJiaZhi4) +
        Number(this.fuZhaiDaoBaoJiaZhi5)
      ).toFixed(1)
    },
    fuZhaiDaoBaoJiaZhi4: function() {
      this.duiWaiDanBaoZongE = (
        Number(this.fuZhaiDaoBaoJiaZhi1) +
        Number(this.fuZhaiDaoBaoJiaZhi2) +
        Number(this.fuZhaiDaoBaoJiaZhi3) +
        Number(this.fuZhaiDaoBaoJiaZhi4) +
        Number(this.fuZhaiDaoBaoJiaZhi5)
      ).toFixed(1)
    },
    fuZhaiDaoBaoJiaZhi5: function() {
      this.duiWaiDanBaoZongE = (
        Number(this.fuZhaiDaoBaoJiaZhi1) +
        Number(this.fuZhaiDaoBaoJiaZhi2) +
        Number(this.fuZhaiDaoBaoJiaZhi3) +
        Number(this.fuZhaiDaoBaoJiaZhi4) +
        Number(this.fuZhaiDaoBaoJiaZhi5)
      ).toFixed(1)
    },
    //净资产   资产负债率
    zongZiChan: function() {
      this.jingZiChan = this.zongZiChan - this.cheliangjiazhi - this.zongFuZhai
      if (this.zongFuZhai != 0 && this.zongZiChan != 0) {
        this.ziChanFuZhaiLv = ((this.zongFuZhai / this.zongZiChan) * 100).toFixed(1)
      } else {
        this.ziChanFuZhaiLv = 0
      }
    },
    zongFuZhai: function() {
      this.jingZiChan = this.zongZiChan - this.cheliangjiazhi - this.zongFuZhai
      if (this.zongFuZhai != 0 && this.zongZiChan != 0) {
        this.ziChanFuZhaiLv = ((this.zongFuZhai / this.zongZiChan) * 100).toFixed(1)
      } else {
        this.ziChanFuZhaiLv = 0
      }
    }
  },
  methods: {
    Assetsliabilities() {
      //console.log('资产负债接口')
      let obj = {
        id: this.sxid
      }
      this.spinning = true
      getAction('/business/sxdcZcfz/queryById', obj)
        .then(res => {
          //console.log(res)
          if (res.success == true) {
            if (res.result.id == '' || res.result.id == null) {
              this.ZcFzId = ''
            } else {
              this.ZcFzId = res.result.id
            }
            this.huoBiJiaZhi = res.result.hbxzj //货币性资金价值
            this.huoBiBeiZhu = res.result.hbxzjbz //货币性资金价值
            this.fangDiChanJiaZhi = res.result.fdc //房地产价值
            this.fangdichanbeizhu = res.result.fdcbz //房地产备注
            this.cheliangjiazhi = res.result.cl //车辆价值
            this.cheliangbeizhu = res.result.clbz //车辆备注
            this.cunkuanjiazhi = res.result.ch //存款价值
            this.cunkuanbeizhu = res.result.chbz //存款备注
            this.yingshoujiazhi = res.result.yszk //应收账款价值
            this.yingshoubeizhu = res.result.yszkbz //应收账款备注
            this.qitazichan = res.result.qtzc //其他资产价值
            this.qitabeizhu = res.result.qtzcbz //其他资产备注
            this.fangdaijiazhi = res.result.fd //房贷价值
            this.fandaibeizhu = res.result.fdbz //房贷备注
            this.chedaijiazhi = res.result.cd //车贷价值
            this.chedaibeizhu = res.result.cdbz //车贷备注
            this.xiaofeijiazhi = res.result.xfd //消费贷价值
            this.xiaofeibeizhu = res.result.xfdbz //消费贷备注
            this.jingyingjiazhi = res.result.jyxdk //经营性贷款价值
            this.jingyingbeizhu = res.result.jyxdkbz //经营性贷款备注
            this.xinyongkajiazhi = res.result.xyk //信用卡价值
            this.xinyongkabeizhu = res.result.xykbz //信用卡备注
            this.qitafuzhaijiazhi = res.result.qtfz //其他负债价值
            this.qitafuzhaibeizhu = res.result.qtfzbz //其他负债备注
            this.fuZhaiDanBaoName1 = res.result.jkr1 //担保人姓名
            this.fuZhaiDaoBaoJiaZhi1 = res.result.jkje1 //担保人价值
            this.fuZhaiDanBaoWuJI1 = res.result.wjfl1 //担保人五级分类
            this.fuZhaiDanBaoBeiZhu1 = res.result.jkbz1 //担保人备注
            this.fuZhaiDanBaoName2 = res.result.jkr2 //担保人姓名
            this.fuZhaiDaoBaoJiaZhi2 = res.result.jkje2 //担保人价值
            this.fuZhaiDanBaoWuJI2 = res.result.wjfl2 //担保人五级分类
            this.fuZhaiDanBaoBeiZhu2 = res.result.jkbz2 //担保人备注
            this.fuZhaiDanBaoName3 = res.result.jkr3 //担保人姓名
            this.fuZhaiDaoBaoJiaZhi3 = res.result.jkje3 //担保人价值
            this.fuZhaiDanBaoWuJI3 = res.result.wjfl3 //担保人五级分类
            this.fuZhaiDanBaoBeiZhu3 = res.result.jkbz3 //担保人备注
            this.fuZhaiDanBaoName4 = res.result.jkr4 //担保人姓名
            this.fuZhaiDaoBaoJiaZhi4 = res.result.jkje4 //担保人价值
            this.fuZhaiDanBaoWuJI4 = res.result.wjfl4 //担保人五级分类
            this.fuZhaiDanBaoBeiZhu4 = res.result.jkbz4 //担保人备注
            this.fuZhaiDanBaoName5 = res.result.jkr5 //担保人姓名
            this.fuZhaiDaoBaoJiaZhi5 = res.result.jkje5 //担保人价值
            this.fuZhaiDanBaoWuJI5 = res.result.wjfl5 //担保人五级分类
            this.fuZhaiDanBaoBeiZhu5 = res.result.jkbz5 //担保人备注
            if (res.result.zzc == null || res.result.zzc == '') {
              this.zongZiChan = '0'
            } else {
              this.zongZiChan = res.result.zzc //总资产
            }
            if (res.result.zfz == null || res.result.zfz == '') {
              this.zongFuZhai = '0'
            } else {
              this.zongFuZhai = res.result.zfz //总负债
            }
            if (res.result.dwdbhzje == null || res.result.dwdbhzje == '') {
              this.duiWaiDanBaoZongE = '0'
            } else {
              this.duiWaiDanBaoZongE = res.result.dwdbhzje //对外担保总额
            }
            if (res.result.jzc == null || res.result.jzc == '') {
              this.jingZiChan = '0'
            } else {
              this.jingZiChan = res.result.jzc //净资产
            }
            if (res.result.zcfzl == null || res.result.zcfzl == '') {
              this.ziChanFuZhaiLv = '0'
            } else {
              this.ziChanFuZhaiLv = res.result.zcfzl //资产负债率
            }
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
    //保存资产负债
    PreservationZcFz() {
      if (this.ZcFzId == '') {
        this.addZcFz() //添加资产负债
      } else {
        this.modifyZcFz() //添加资产负债
      }
    },
    //添加资产负债
    addZcFz() {
      var obj = {
        sxid: this.sxid, //id

        hbxzj: this.huoBiJiaZhi, //货币性资金价值
        hbxzjbz: this.huoBiBeiZhu, //货币性资金价值
        fdc: this.fangDiChanJiaZhi, //房地产价值
        fdcbz: this.fangdichanbeizhu, //房地产备注
        cl: this.cheliangjiazhi, //车辆价值
        clbz: this.cheliangbeizhu, //车辆备注
        ch: this.cunkuanjiazhi, //存款价值
        chbz: this.cunkuanbeizhu, //存款备注
        yszk: this.yingshoujiazhi, //应收账款价值
        yszkbz: this.yingshoubeizhu, //应收账款备注
        qtzc: this.qitazichan, //其他资产价值
        qtzcbz: this.qitabeizhu, //其他资产备注
        fd: this.fangdaijiazhi, //房贷价值
        fdbz: this.fandaibeizhu, //房贷备注
        cd: this.chedaijiazhi, //车贷价值
        cdbz: this.chedaibeizhu, //车贷备注
        xfd: this.xiaofeijiazhi, //消费贷价值
        xfdbz: this.xiaofeibeizhu, //消费贷备注
        jyxdk: this.jingyingjiazhi, //经营性贷款价值
        jyxdkbz: this.jingyingbeizhu, //经营性贷款备注
        xyk: this.xinyongkajiazhi, //信用卡价值
        xykbz: this.xinyongkabeizhu, //信用卡备注
        qtfz: this.qitafuzhaijiazhi, //其他负债价值
        qtfzbz: this.qitafuzhaibeizhu, //其他负债备注
        jkr1: this.fuZhaiDanBaoName1, //担保人姓名
        jkje1: this.fuZhaiDaoBaoJiaZhi1, //担保人价值
        wjfl1: this.fuZhaiDanBaoWuJI1, //担保人五级分类
        jkbz1: this.fuZhaiDanBaoBeiZhu1, //担保人备注
        jkr2: this.fuZhaiDanBaoName2, //担保人姓名
        jkje2: this.fuZhaiDaoBaoJiaZhi2, //担保人价值
        wjfl2: this.fuZhaiDanBaoWuJI2, //担保人五级分类
        jkbz2: this.fuZhaiDanBaoBeiZhu2, //担保人备注
        jkr3: this.fuZhaiDanBaoName3, //担保人姓名
        jkje3: this.fuZhaiDaoBaoJiaZhi3, //担保人价值
        wjfl3: this.fuZhaiDanBaoWuJI3, //担保人五级分类
        jkbz3: this.fuZhaiDanBaoBeiZhu3, //担保人备注
        jkr4: this.fuZhaiDanBaoName4, //担保人姓名
        jkje4: this.fuZhaiDaoBaoJiaZhi4, //担保人价值
        wjfl4: this.fuZhaiDanBaoWuJI4, //担保人五级分类
        jkbz4: this.fuZhaiDanBaoBeiZhu4, //担保人备注
        jkr5: this.fuZhaiDanBaoName5, //担保人姓名
        jkje5: this.fuZhaiDaoBaoJiaZhi5, //担保人价值
        wjfl5: this.fuZhaiDanBaoWuJI5, //担保人五级分类
        jkbz5: this.fuZhaiDanBaoBeiZhu5, //担保人备注
        zzc: this.zongZiChan, //总资产
        zfz: this.zongFuZhai, //总负债
        dwdbhzje: this.duiWaiDanBaoZongE, //对外担保总额
        jzc: this.jingZiChan, //净资产
        zcfzl: this.ziChanFuZhaiLv //资产负债率
      }
      this.spinning = true
      postAction('/business/sxdcZcfz/add', obj)
        .then(res => {
          //console.log(res)
          if (res.success == true) {
            //console.log('接口成功')
            this.ZcFzId = res.result.id
            this.$notification.success({
              message: '提示',
              description: `保存成功`,
              duration: 3
            })
          } else {
            //接口失败
            //console.log('接口失败')
            this.$notification.error({
              message: '提示',
              description: `保存失败`,
              duration: 3
            })
          }
        })
        .finally(() => {
          this.spinning = false
        })
    },
    //修改资产负债
    modifyZcFz() {
      var obj = {
        id: this.ZcFzId, //资产负债ID

        hbxzj: this.huoBiJiaZhi, //货币性资金价值
        hbxzjbz: this.huoBiBeiZhu, //货币性资金价值
        fdc: this.fangDiChanJiaZhi, //房地产价值
        fdcbz: this.fangdichanbeizhu, //房地产备注
        cl: this.cheliangjiazhi, //车辆价值
        clbz: this.cheliangbeizhu, //车辆备注
        ch: this.cunkuanjiazhi, //存款价值
        chbz: this.cunkuanbeizhu, //存款备注
        yszk: this.yingshoujiazhi, //应收账款价值
        yszkbz: this.yingshoubeizhu, //应收账款备注
        qtzc: this.qitazichan, //其他资产价值
        qtzcbz: this.qitabeizhu, //其他资产备注
        fd: this.fangdaijiazhi, //房贷价值
        fdbz: this.fandaibeizhu, //房贷备注
        cd: this.chedaijiazhi, //车贷价值
        cdbz: this.chedaibeizhu, //车贷备注
        xfd: this.xiaofeijiazhi, //消费贷价值
        xfdbz: this.xiaofeibeizhu, //消费贷备注
        jyxdk: this.jingyingjiazhi, //经营性贷款价值
        jyxdkbz: this.jingyingbeizhu, //经营性贷款备注
        xyk: this.xinyongkajiazhi, //信用卡价值
        xykbz: this.xinyongkabeizhu, //信用卡备注
        qtfz: this.qitafuzhaijiazhi, //其他负债价值
        qtfzbz: this.qitafuzhaibeizhu, //其他负债备注
        jkr1: this.fuZhaiDanBaoName1, //担保人姓名
        jkje1: this.fuZhaiDaoBaoJiaZhi1, //担保人价值
        wjfl1: this.fuZhaiDanBaoWuJI1, //担保人五级分类
        jkbz1: this.fuZhaiDanBaoBeiZhu1, //担保人备注
        jkr2: this.fuZhaiDanBaoName2, //担保人姓名
        jkje2: this.fuZhaiDaoBaoJiaZhi2, //担保人价值
        wjfl2: this.fuZhaiDanBaoWuJI2, //担保人五级分类
        jkbz2: this.fuZhaiDanBaoBeiZhu2, //担保人备注
        jkr3: this.fuZhaiDanBaoName3, //担保人姓名
        jkje3: this.fuZhaiDaoBaoJiaZhi3, //担保人价值
        wjfl3: this.fuZhaiDanBaoWuJI3, //担保人五级分类
        jkbz3: this.fuZhaiDanBaoBeiZhu3, //担保人备注
        jkr4: this.fuZhaiDanBaoName4, //担保人姓名
        jkje4: this.fuZhaiDaoBaoJiaZhi4, //担保人价值
        wjfl4: this.fuZhaiDanBaoWuJI4, //担保人五级分类
        jkbz4: this.fuZhaiDanBaoBeiZhu4, //担保人备注
        jkr5: this.fuZhaiDanBaoName5, //担保人姓名
        jkje5: this.fuZhaiDaoBaoJiaZhi5, //担保人价值
        wjfl5: this.fuZhaiDanBaoWuJI5, //担保人五级分类
        jkbz5: this.fuZhaiDanBaoBeiZhu5, //担保人备注
        zzc: this.zongZiChan, //总资产
        zfz: this.zongFuZhai, //总负债
        dwdbhzje: this.duiWaiDanBaoZongE, //对外担保总额
        jzc: this.jingZiChan, //净资产
        zcfzl: this.ziChanFuZhaiLv //资产负债率
      }
      this.spinning = true
      putAction('/business/sxdcZcfz/edit', obj)
        .then(res => {
          //console.log(res)
          if (res.success == true) {
            //console.log('接口成功')
            this.$notification.success({
              message: '提示',
              description: `保存成功`,
              duration: 3
            })
          } else {
            //接口失败
            //console.log('接口失败')
            this.$notification.error({
              message: '提示',
              description: `保存失败`,
              duration: 3
            })
          }
        })
        .finally(() => {
          this.spinning = false
        })
    }
  }
}
</script>
<style scoped>
.jia_top {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  border-bottom: 1px solid #f1f1f3;
}
.shouxin {
  position: relative;
  width: 100%;
  min-width: 1103px;
  border: 1px solid rgba(73, 160, 237, 0.4);
  border-radius: 10px;
  min-height: 100px;
  margin-top: 24px;
  font-size: 12px;
  color: #1e1c1f;
  padding-bottom: 66px;
}
.shouxina {
  height: 68px;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: justify;
  -ms-flex-pack: justify;
  justify-content: space-between;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  padding: 0 42px;
}
.shouxina span {
  width: 204px;
  text-align: center;
}
.shouxinba {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: justify;
  -ms-flex-pack: justify;
  justify-content: space-between;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  padding: 0 42px;
  height: 45px;
  background-color: #ebecee;
}
.shouxinba span {
  width: 204px;
}
.shouxinba input {
  width: 202px;
  border: 1px solid #d9d9d9;
  height: 30px;
  text-indent: 10px;
}
.shouxinca {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: justify;
  -ms-flex-pack: justify;
  justify-content: space-between;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  padding: 0 42px;
  height: 45px;
}
.shouxinca span {
  width: 204px;
}
.shouxinca input {
  width: 202px;
  border: 1px solid #d9d9d9;
  height: 30px;
  text-indent: 10px;
}
.zheng_all {
  margin-top: 20px;
}
.dailuanliebiao {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  padding: 0 0;
  -ms-flex-wrap: wrap;
  flex-wrap: wrap;
  border: 1px solid rgba(73, 160, 237, 0.6);
  padding-bottom: 40px;
  padding-right: 15px;
  background-color: rgba(73, 160, 237, 0.08);
  border-radius: 6px;
  margin-top: 20px;
}
.dailuanliebiao_a {
  cursor: pointer;
  width: 198px;
  height: 95px;
  padding: 10px 15px;
  -webkit-box-shadow: 0 0 7px rgba(124, 123, 123, 0.34);
  box-shadow: 0 0 7px rgba(124, 123, 123, 0.34);
  border-radius: 10px;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
  -ms-flex-flow: column;
  flex-flow: column;
  -webkit-box-pack: justify;
  -ms-flex-pack: justify;
  justify-content: space-between;
  margin-left: 56px;
  margin-top: 40px;
  background-color: #fff;
}
.dailuanliebiao_a_a {
  font-size: 12px;
  color: #464646;
  font-weight: 600;
  padding-bottom: 2px;
  border-bottom: 1px solid #d6d6d6;
}
.dailuanliebiao_b {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
}
.dailuanliebiao_b div {
  width: 50%;
  text-align: center;
}
.dailuanliebiao_a_b {
  font-size: 12px;
  color: #777676;
}
.dailuanliebiao_b_a {
  font-size: 14px;
  font-weight: 600;
  color: #49a0ed;
  line-height: 30px;
}
.dailuanliebiao_a:hover {
  background: #49a0ed;
  color: #fff !important;
}

.zongzichand {
  height: 57px;
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  justify-content: center;
}
.blue {
  color: #49a0ed;
}
.zaichanfuzhai {
  color: red;
}
.dailuanliebiao_a:hover .dailuanliebiao_a_a {
  color: #fff;
}
.dailuanliebiao_a:hover .dailuanliebiao_b_a {
  color: #fff;
}
.dailuanliebiao_a:hover .dailuanliebiao_a_b {
  color: #fff;
}

.dailuanliebiao_a:hover .dailuanliebiao_a_c {
  color: #fff;
}
.dailuanliebiao_a:hover .dailuanliebiao_b_s {
  color: #fff;
}
.dailuanliebiao_a:hover .zaichanfuzhai {
  color: #fff;
}
</style>