<template>
  <div :class="['component', 'g-divider', `g-divider--${direction}`]">
    <div
      v-if="content && direction !== 'vertical'"
      :class="['g-divider__text', `is-${contentPosition}`]">
      <span>{{content}}</span>
    </div>
  </div>
</template>

<script>
  import {VueExtend} from 'godspen-lib'

  export default {
    mixins: [VueExtend.mixin],
    name: 'GDivider',
    label: process.env.LABEL,
    style: process.env.STYLE,
    stack: false, // 是否是堆叠模式 ，true：孩子元素会按楼层一个个向下排布， false: 孩子元素绝对定位，随意放置位置
    childLimit: 9999,  // 孩子元素最大限制数
    leaf: false, // 是否是叶子节点，为true的时候该节点下面不能添加节点
    data () {
      return {}
    },
    props: {
      direction: {
        type: String,
        default: 'horizontal',
        editor: {
          type: 'enum',
          label: '分割线方向',
          defaultList: {
            horizontal: '水平',
            vertical: '垂直'
          }
        }
      },
      contentPosition: {
        type: String,
        default: 'center',
        editor: {
          type: 'enum',
          label: '文案位置',
          defaultList: {
            left: '左',
            center: '中',
            right: '右'
          }
        }
      },
      content: {
        type: String,
        default: '分割线文案',
        editor: {
          label: '分割线文案'
        }
      }
    },
    computed: {
    },
    editorMethods: {
    },
    methods: {
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus" type="text/stylus" scoped>
  .component {
    width: 100%;
    height: 100%;
  }
  .g-divider{
    background-color:#DCDFE6;
    position:relative;
  }
  .g-divider--horizontal{
    display:block;
    height:1px;
    width:100%;
    margin:24px 0;
  }
  .g-divider--vertical{
    display:inline-block;
    width:1px;
    height:1em;
    margin:0 8px;
    vertical-align:middle;
    position:relative;
  }
  .g-divider__text{
    position:absolute;
    background-color:#FFF;
    padding:0 20px;
    font-weight:500;
    color:#303133;
    font-size:14px;
  }
  .g-divider__text.is-left{
    left:20px;
    transform:translateY(-50%);
  }
  .g-divider__text.is-center{
    left:50%;
    transform:translateX(-50%) translateY(-50%);
  }
  .g-divider__text.is-right {
    right:20px;
    transform:translateY(-50%);
  }
</style>
