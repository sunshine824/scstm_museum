<template>
  <div class="notice-con">
    <div class="title">
      <router-link :to="url">
        {{title}}+
      </router-link>
    </div>
    <ul class="list clearfix">
      <li v-for="(item,index) in data" :key="index">
        <span class="splt"></span>
        <router-link target="_blank" :to="url+'/'+item.id">
          {{item.title}}
        </router-link>
      </li>
    </ul>
  </div>
</template>
<script type="text/ecmascript-6">
  export default {
    props: {
      data: {
        type: Array,
        default: ''
      },
      url: {
        type: String,
        default: ''
      },
      title: {
        type: String,
        default: ''
      }
    },
    data() {
      return {}
    }
  }
</script>
<style lang="less">
  .notice-con {
    .title {
      font-size: 22px;
      margin-top: 40px;
      a {
        color: #004179;
      }
    }
    ul.list {
      margin-top: 30px;
      padding-bottom: 20px;
      border-bottom: 2px solid #004179;
      li {
        margin-top: 15px;
        &:hover {
          a {
            color: #004179;
          }
        }
        &:first-child {
          margin-top: 0;
        }
        a {
          font-size: 14px;
          color: #191919;
          padding-left: 6px;
          overflow: hidden;
          text-overflow: ellipsis;
          white-space: nowrap;
          width: 93%;
          display: inline-block;
          vertical-align: middle;
        }
        .splt {
          width: 0;
          height: 0;
          border-top: 6px solid transparent;
          border-left: 6px solid #004179;
          border-bottom: 6px solid transparent;
          display: inline-block;
          vertical-align: middle;
        }
      }
    }
  }
</style>
