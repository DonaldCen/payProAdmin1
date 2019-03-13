<template>
  <a-modal
    v-model="show"
    :centered="true"
    :keyboard="false"
    :footer="null"
    :width="750"
    @cancel="handleCancleClick"
    title="渠道信息">
    <a-layout class="user-info">
      <a-layout-content class="user-content-one">
        <p><a-icon type="user"/>id：{{userInfoData.id}}</p>
        <p :title="userInfoData.channelCode"><a-icon type="star"/>渠道编码：{{userInfoData.roleName? userInfoData.roleName: '暂无角色'}}</p>
        <p><a-icon type="skin"/>渠道名称：{{userInfoData.channelName}}</p>
        <p><a-icon type="phone"/>交易类型：{{userInfoData.tradeType}}</p>
        <p><a-icon type="mail"/>通道成本利率：{{userInfoData.chanelCostRate}}%</p>
        <p><a-icon type="mail"/>通道成本费用：{{userInfoData.channelCost}}%</p>
      </a-layout-content>
      <a-layout-content class="user-content-two">
        <p>
          结算类型：
          <template v-if="userInfoData.settlementType === '0'">
            <a-tag color="cyan">D0</a-tag>
          </template>
          <template v-else-if="userInfoData.settlementType === '1'">
            <a-tag color="cyan">T+0</a-tag>
          </template>
          <template v-else-if="userInfoData.settlementType === '2'">
            <a-tag color="cyan">T+1</a-tag>
          </template>
          <template v-else>
            {{userInfoData.status}}
          </template>
        </p>
        <p>
          <a-icon type="smile" v-if="userInfoData.status === '0'"/>
          <a-icon type="frown" v-else/>状态：
          <template v-if="userInfoData.status === '0'">
            <a-tag color="cyan">可用</a-tag>
          </template>
          <template v-else-if="userInfoData.status === '1'">
            <a-tag color="red">禁用</a-tag>
          </template>
          <template v-else>
            {{userInfoData.status}}
          </template>
        </p>
        <p><a-icon type="clock-circle"/>创建时间：{{userInfoData.createTime}}</p>
        <p><a-icon type="login" />最近登录：{{userInfoData.lastLoginTime}}</p>
        <p :title="userInfoData.description"><a-icon type="message"/>描述：{{userInfoData.description}}</p>
      </a-layout-content>
    </a-layout>
  </a-modal>
</template>
<script>
export default {
  name: 'ChannelInfo',
  props: {
    userInfoVisiable: {
      require: true,
      default: false
    },
    userInfoData: {
      require: true
    }
  },
  computed: {
    show: {
      get: function () {
        return this.userInfoVisiable
      },
      set: function () {
      }
    }
  },
  methods: {
    handleCancleClick () {
      this.$emit('close')
    }
  }
}
</script>
<style lang="less" scoped>
@import "UserInfo";
</style>
