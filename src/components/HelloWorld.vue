<template>
  <div class="hello">
   <button @click="pickerSex">选择器</button>
   <div>{{sex.sex}}</div>
  </div>
</template>

<script>
import Picker from "../plugins/picker/picker.js";
import  "../plugins/picker/picker.css"
export default {
  name: 'HelloWorld',
  data () {
    return {
      sexChose:[{sexId:1,sex:"男"},{sexId:2,sex:"女"}],
      sex:{sexId:1,sex:"男"}
    }
  },
  methods:{
    pickerSex(){
var that=this;
     new Picker({
    "title": '请选择', //标题(可选)
    
    //默认值： 多个用空格隔开；（可选）
    "defaultValue": '女', 

    //需要联动级数[1、2、3]（可选）
    //不传时默认获取数据的深度,最多3级
    "type": 1,

    //数据(必选)
    //在使用时，把cityData替换为后台返回的数据即可，但格式要和cityData一致
    "data": that.sexChose, 

    //数据内的键名称[Code、Name、level](必选)
    "keys": {
        "id": "sexId",
        "value": "sex",
        "childData": "level"
    },

   //回调函数（val为当前选中的值）(必选)
   "callBack": function (val,id) {
     
        // 可在此处显示选中的值
       that.sex.sexId=id;
        that.sex.sex=val;
    }
});
    }
  },
 
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
