<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <button
      id="iOS-redirect-btn"
    >
      iOS redirect Btn
    </button>

    <button
      id="android-redirect-btn"
    >
      Android redirect Btn
    </button>
  </div>
</template>

<script>
export default {
  name: 'App',
  mounted () {
    // eslint-disable-next-line no-undef
    console.log('ulink', ULink)
    if (/(iPhone|iPad|iPod|iOS)/i.test(navigator.userAgent)) { // 判断iPhone|iPad|iPod|iOS
      console.log('is iOS')
      // eslint-disable-next-line no-undef
      ULink({
        id: 'usr19iucc2jnvjvj',
        data: {},
        selector: '#iOS-redirect-btn',
        timeout: 1000,
        useOpenInBrowerTips: 'default',
        lazy: false,
        auto: true,
        useClipboard: false,
        proxyOpenDownload: async (defaultAction, ctx) => {
          if (ctx.solution.type === 'scheme') {
            // qq或者微信环境特殊处理下
            // eslint-disable-next-line no-undef
            if (ULink.isWechat || ULink.isQQ) {
              // 在qq或者微信环境执行内置逻辑，具体内置逻辑为:当设置了useOpenInBrowerTips字段时，qq&&微信&&scheme时，启用蒙层提示去浏览器打开
              defaultAction()
            } else {
              window.location.href = ctx.solution.downloadUrl
            }
          } else if (ctx.solution.type === 'universalLink') {
            console.log('trigger universalLink')
          }

          return true
        }
      })
    } else if (/(Android)/i.test(navigator.userAgent)) { // 判断Android
      console.log('is Android')
      // eslint-disable-next-line no-undef
      ULink({
        id: 'usr19iucc2jnvjvj',
        data: {},
        selector: '#android-redirect-btn',
        timeout: 1000,
        useOpenInBrowerTips: 'default',
        lazy: false,
        auto: true,
        useClipboard: false,
        proxyOpenDownload: async (defaultAction, ctx) => {
          if (ctx.solution.type === 'scheme') {
            // qq或者微信环境特殊处理下
            // eslint-disable-next-line no-undef
            if (ULink.isWechat || ULink.isQQ) {
              // 在qq或者微信环境执行内置逻辑，具体内置逻辑为:当设置了useOpenInBrowerTips字段时，qq&&微信&&scheme时，启用蒙层提示去浏览器打开
              defaultAction()
            } else {
              window.location.href = ctx.solution.downloadUrl
            }
          } else if (ctx.solution.type === 'universalLink') {
            console.log('trigger universalLink')
          }

          return true
        }
      })
    } else {
      console.log('in desktop')
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
