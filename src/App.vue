<template>
  <div id="app">
    <ind-nav :pathname="pathname" :logo="logo"></ind-nav>

    <router-view/>

    <ind-footer :data="footer"></ind-footer>
  </div>
</template>

<script>
  import indNav from '@/base/Head/ind_nav'
  import indFooter from '@/base/Head/footer'
  import {getLogo, getFootInfo, test} from '@/public/js/fetch'

  export default {
    name: 'App',
    components: {
      indNav,
      indFooter
    },
    data() {
      return {
        pathname: '',
        logo: '',
        footer: ''
      }
    },
    created() {
      this._getLogo()
      this._getFootInfo()
    },
    methods: {
      _getLogo() {
        const result = getLogo()
        result.then(res => {
          if (res.status === 0) {
            this.logo = res.msg
          }
        }).catch(err => {
          console.log(err.response)
        })
      },
      _getFootInfo() {
        const result = getFootInfo()
        result.then(res => {
          if (res.status === 0) {
            this.footer = res.msg
          }
        }).catch(err => {
          console.log(err.response)
        })
      }
    },
    watch: {
      "$route"(to, from) {
        this.pathname = to.meta[0]
        document.title = to.name + ' - 四川省自然科学博物馆协会'
      }
    }
  }

</script>

<style>
  @import "./public/css/base.css";

  #app {
    display: flex;
    flex-direction: column;
    height: 100%;
  }

  .header {
    flex: 0 0 auto;
  }

  .container {
    flex: 1 0 auto;
  }

  .footer {
    flex: 0 0 auto;
  }
</style>
