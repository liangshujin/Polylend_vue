<template>
  <div id="app">
    <router-view />
  </div>
</template>

<script>
export default {
  name: 'App',
  created() {
    this.web3Init()
  },
  methods: {
    /* 实例化Web3*/
    web3Init() {
      const _this = this
      console.log(this.GLOBAL)
      this.GLOBAL.web3 = window.web3 = new this.Web3(window.ethereum)

      window.ethereum.autoRefreshOnNetworkChange = false
      window.ethereum.on('accountsChanged', () => {
        switch (_this.$router.path) {
          case '/':
            this.connectMetaMask()
            break
          default:
        }
      })
      window.ethereum.on('networkChange', () => {
        switch (_this.$router.path) {
          case '/':
            this.connectMetaMask()
            break
          default:
        }
      })
    }
  }
}
</script>
