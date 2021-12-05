<template>
  <div class="home">
    <van-button type="primary" v-copy='`湿哒哒沙雕`'>拷贝按钮</van-button>
    <van-button type="success" v-copy='`湿哒哒沙雕2`'>拷贝按钮2</van-button>
    <!-- 可以使用 CellGroup 作为容器 -->
<van-cell-group inset>
  <van-field v-model="value1" label="文本" placeholder="请输入用户名" />
</van-cell-group>

<!-- 弹出层 -->
<van-cell is-link @click="showPopup">展示弹出层</van-cell>
<van-popup v-model:show="show" position="bottom">
  <van-area title="标题"  :area-list="areaList" @confirm="selectAddress"/>
</van-popup>
<!-- 省市区编辑 -->

  
  
  
  </div>
</template>

<script lang='ts'>
import { areaList } from '@vant/area-data';
import { defineComponent, onMounted, ref } from 'vue'
export default defineComponent({
  components:{  },
  setup:()=>{
    onMounted(() => {
      console.log('第一次加载')
      console.log('第二次加载哈哈哈哈哈哈哈');
    })
    // 填写省市区编辑功能
    const show = ref(false)
    const selectAddress = (result: any[]) => {
       console.log(result);
       value1.value = result.map(i=> {
         return i.name
       })
       .join(',')
       show.value = false
    }
    const showPopup= () => {
      show.value = true
    }


    //填写用户名功能  
    const value1 = ref('')
    return {
      areaList,
      selectAddress,
      value1,
      show,
      showPopup,
      }
      
  },
  computed:{
  }
  
  
})
</script>

<style lang="scss" scoped>
.home{
  background-color: #eee;
}
</style>