<template>
  <div class="tab-bar-item" v-on:click='itemClick'>
      <div v-if="!this.isActive"><slot name="item-icon"></slot></div>
      <div v-else><slot name="item-icon-active"></slot></div>
      <div v-bind:style="this.activeStyle"><slot name="item-text"></slot></div>  
  </div>
</template>

<script>
export default {
    props:{
        path:String,
        activeColor:{
            type:String,
            default:'red'
        }
    },
    data() {
        return {
            // isActive:true
        }
    },
    computed: {
        isActive(){
            return this.$route.path.indexOf(this.path)!== -1
        },
        activeStyle(){
            return this.isActive? {color:this.activeColor} : {}
        }
    },
    methods: {
        itemClick(){
            this.$router.replace(this.path)
        }
    },
}
</script>

<style>
    .tab-bar-item {
        flex: 1;
        text-align: center;
        height: 49px;
        font-size: 14px;
    }

    .tab-bar-item img{
        height: 24px;
        width: 24px;
        margin-top: 3px;
        margin-bottom: 2px;
        vertical-align: middle;
    }

</style>