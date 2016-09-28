<template>
  <ul class="bus-tabs sort-bar js_sort_item">
    <li class="tabs-item " v-on:click="setTime" data-sort="Time" style="-webkit-flex: 1.5; flex: 1.5;">出发时间<i class="icon-sort {{sort.time }}"></i></li>
    <li class="tabs-item " v-on:click="setSumTime" data-sort="SumTime" >耗时<i class="icon-sort {{sort.sumTime }}"></i></li>
    <li class="tabs-item " v-on:click="setPrice" data-sort="Price" >价格<i class="icon-sort {{sort.price }}"></i></li>
  </ul>
</template>

<script>
export default {
  props: ['sort'],
  methods: {
    _resetData: function () {
      this.sort.time = '';
      this.sort.sumTime = '';
      this.sort.price = '';
    },

    setTime: function () {
      this._setData('time');
    },

    setSumTime: function () {
      this._setData('sumTime');
    },

    setPrice: function () {
      this._setData('price');
    },

    _setData: function (key) {
      //如果设置当前key存在，则反置，否则清空筛选，设置默认值
      if (this.sort[key] != '') {
        if (this.sort[key] == 'up') this.sort[key] = 'down';
        else this.sort[key] = 'up';
      } else {
        this._resetData();
        this.sort[key] = 'down';
      }
    }
  },
  data: function(){
      return {

      }
  }
}
</script>

