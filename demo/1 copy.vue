<template>
  <div
    class="demo"
  >{{ getTime("2019-07-16^2019-07-17^2019-07-18^2019-07-19^2019-07-20^2019-07-21^2019-07-22") }}</div>
</template>
<script>
export default {
  data() {
    return {};
  },
  methods: {
    getTime(date) {
      if(date){
        var arr = date.split("^");
      var arrObj = {};
      for (var i = 0; i < arr.length; i++) {
        arrObj["arr" + i] = arr[i].split("-");//将拆分得到的数组存进对象，通过arrObj["arr" + i]可以获得这个数组
        //存在的情况
        //1,年份月份相同，只有具体日不同
        if(arrObj['arr'+0][0]==arrObj['arr'+i][0]&&arrObj['arr'+0][1]==arrObj['arr'+i][1]){
          date = arrObj['arr'+0][0] +"年" +arrObj['arr'+0][1] +"月" +arrObj['arr'+0][2] +"日."
          date = date + arrObj['arr'+i][2] +"日."
        }
        //2,年份相同，月份有两个，日期也不同
        //3,年份不同，月份不同

      }
      }
      
    }
  }
};
</script>