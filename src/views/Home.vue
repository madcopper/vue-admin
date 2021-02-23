<template>
  <div>
    <h1>Welcome to {{ title }}</h1>
    <h2>{{ title2 }}</h2>
    <input type="text" v-model="input1"/>
    <button type="button" @click="getData">클릭</button>
    <button type="button" @click="setData">변경</button>
    <button type="button" @click="toggleTable">테이블 보여주기</button>

    <select class="form-control" v-model="region" @change="changeRegion">
      <option :key="index" v-for="(data, index) in options" :value="data.v">{{data.t}}</option>
    </select>

    <table class="table table-bordered" v-if="tableShow">
      <tr :key="index" v-for="(data, index) in options">
        <td>{{data.v}}</td>
        <td>{{data.t}}</td>
        <td>이건 엘리먼트 자체를 그리지 않는다.</td>
      </tr>
    </table>

    <table class="table table-bordered" v-show="tableShow">
      <tr :key="index" v-for="(data, index) in options">
        <td>{{data.v}}</td>
        <td>{{data.t}}</td>
        <td>이건 엘리먼트를 그리지만 display:none가 된다</td>
      </tr>
    </table>

  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "엠코코아",
      title2: "당신을 환영합니다.",
      input1: "default",
      options: [
        {v : "S", t:"Seoul"},
        {v : "G", t:"Gyunggi"},
        {v : "J", t:"Jeju"},
      ],
      region : "J",
      tableShow : false,
    }
  },
  watch: {
    input1() {
      //데이터 이름과 동일하게 만들면 스테이트가 변경되면 실행됨
      console.log(this.input1);
    }
  },
  methods: {
    getData() {
      alert(this.input1)
    },
    setData() {
      this.input1 = "change data";
    },
    changeRegion() {
      alert(this.region)
    },
    toggleTable(){
      this.tableShow = !this.tableShow
    },
  },
  beforeCreate() {
    console.log("beforeCreate : 만들어지기 전")
  },
  created() {
    console.log("created : 만들고 난 후")
  },
  beforeMount() {
    console.log("beforeMount : 보여지기 전")
  },
  mounted() {
    console.log("mounted : 보여진 상태")
  },
  beforeUpdate() {
    console.log("beforeUpdate : 스테이트 변경 전")
  },
  updated() {
    console.log("updated : 스테이트 변경")
  },
  beforeDestroy() {
    console.log("beforeDestroy : 창 사라지기 전")
  },
  destroyed() {
    console.log("destroyed : 창 사라짐")
  }
};
</script>
