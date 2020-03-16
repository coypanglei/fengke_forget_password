<template>
  <a-modal
    :title="title"
    :width="690"
    :destroyOnClose="xiaohui"
    :footer="null"
    style="height:470px;padding: 0px;"
    :visible="visible"
    @cancel="handleCancel"
    @ok="handleOk"
  >
    <a-spin :spinning="confirmLoading">
      <a-button v-print="'#grsxdcdya'" ghost type="primary" icon="printer">打印</a-button>
      <div id="grsxdcdya">
        <h3 align="center">东海农村商业银行个人授信调查、审批表</h3>
        <span style="margin-left: 50px">东海石梁河支行</span>
        <span style="margin-left: 380px">金额单位：万元</span>
        <table class="mainInfo">
          <tbody>
            <tr>
              <td align="center" style="width:20%;border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;">申请人姓名</td>
              <td colspan="3" align="left" style="width: 35%;border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;">&nbsp;&nbsp;张广利</td>
              <td align="center" style="width: 18%;border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;">婚姻状况</td>
              <td colspan="3" align="left" style="width: 25%;border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;">&nbsp;&nbsp;已婚</td>
            </tr>
            <tr>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" align="center">身份证件号码</td>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" colspan="3" align="left">&nbsp;&nbsp;32072219641127331X</td>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" align="center">联系方式</td>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" colspan="3" align="left">&nbsp;&nbsp;18761323686</td>
            </tr>
            <tr>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" align="center">身份证件住址</td>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" colspan="7" align="left">&nbsp;&nbsp;江苏省连云港市东海县石梁河镇贾庄村委会</td>
            </tr>
            <tr>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" align="center">常住地址</td>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" colspan="7" align="left">&nbsp;&nbsp;江苏省东海县石梁河镇贾庄村16-11号</td>
            </tr>
            <tr>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" align="center">经营事项</td>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" colspan="7" align="left">&nbsp;&nbsp;</td>
            </tr>
            <tr>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" align="center">存量授信</td>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" align="center">综合授信额度</td>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" align="left" colspan="2">&nbsp;&nbsp;0.0</td>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" align="center" colspan="2">贷款余额</td>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" align="left" colspan="2">&nbsp;&nbsp;1</td>
            </tr>
            <tr>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" align="center" rowspan="2">本次申请</td>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" align="center">授信方式</td>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" align="center">综合授信</td>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" align="center">授信额度</td>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" align="left">&nbsp;&nbsp;1</td>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" align="center">营销人</td>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" align="left" colspan="2">&nbsp;&nbsp;李荣光</td>
            </tr>
            <tr>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" align="center">用途</td>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" align="left" colspan="2">&nbsp;&nbsp;</td>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" align="center" colspan="2">期限</td>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" align="left">&nbsp;&nbsp;36</td>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" align="center">月</td>
            </tr>
            <tr>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" align="center" rowspan="7">
                调
                <br />查
                <br />岗
                <br />意
                <br />见
              </td>
              <td colspan="7" align="left" style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;border-bottom: none;border-top: none">
                <!-- 							 &nbsp;&nbsp;&nbsp;&nbsp; 根据借款人申请资料，经与申请人当面核验、面谈，本人认为借款人借款行为真实，借款人资料齐备、真实、有效，现提出如下意见： -->
              </td>
            </tr>
            <tr>
              <td  colspan="7" align="left" style="border-right:1px solid #999999; height: 30px; font-size: 14px;vertical-align: middle;border-bottom: none;border-top: none">
                建议：综合授信金额：1万元;期限36月;授信到期日期：2021&nbsp;年&nbsp;01&nbsp;月&nbsp;07&nbsp;日;其中
                保证担保1万元、
                利率按总行相关规定执行。
              </td>
            </tr>
            <tr>
              <td colspan="7" align="left" style="border-right:1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;border-bottom: none;border-top: none">还款方式：</td>
            </tr>
            <tr>
              <td colspan="7" align="left" style="border-right:1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;border-bottom: none;border-top: none"></td>
            </tr>
            <tr>
              <td colspan="7" align="left" style="border-right:1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;border-bottom: none;border-top: none">
                <!-- 							 &nbsp;&nbsp;&nbsp;&nbsp;本人对上述调查真实性负责。<br> -->
                调查人签字:
              </td>
            </tr>
            <tr>
              <td colspan="7" align="left" style=" border-right:1px solid #999999;font-size: 14px;vertical-align: middle;border-bottom: none;border-top: none"></td>
            </tr>
            <tr>
              <td
                colspan="7"
                align="right"
                style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;border-top: none"
              >2018&nbsp;年&nbsp;01&nbsp;月&nbsp;09&nbsp;日</td>
            </tr>

            <tr>
              <td style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;" align="center">
                用
                <br />信
                <br />审
                <br />批
                <br />人
                <br />意
                <br />见
              </td>
              <td
                colspan="7"
                align="right"
                style="border: 1px solid #999999;height: 30px; font-size: 14px;vertical-align: middle;border-top: none;padding-top: 120px"
              >&nbsp;&nbsp;年&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;月&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;日</td>
            </tr>
          </tbody>
        </table>
      </div>
    </a-spin>
  </a-modal>
</template>

<script>
import { postAction } from '@/api/manage'
import { getAction } from '@/api/manage'
export default {
  name: 'grsxdcdy',
  data() {
    return {
      title: '个人征信、调查审批表',
      xiaohui: true,
      confirmLoading: false,
      visible: false
    }
  },
  created() {},
  methods: {
    dakai(zjhm, id) {
      this.visible = true
    },
    close() {
      this.visible = false
    },
    handleOk() {
      this.visible = false
    },
    handleCancel() {
      this.visible = false
    }
  }
}
</script>

<style  scoped>
</style>