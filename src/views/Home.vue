<template>
  <div>
    <h1>Welcome to {{title}}!</h1>
    <input type="text" v-model="input1">
    <button type="button" @click="getData">Get</button>
    <button type="button" @click="setData">Set</button>

    <select class="form-control" v-model="region" @change="changeRegion">
      <option :key="i" :value="d.v" v-for="(d,i) in options">{{d.t}}</option>
    </select>

    <table class="table table-bordered" v-if="tableShow"> <!-- v-if 는 랜더링 조차 안함, v-show는 랜더링은 하지만 화면에 안보이게 함 -->
      <tr :key="i" v-for="(d,i) in options">
        <td>{{d.v}}</td>
        <td>{{d.t}}</td>
      </tr>
    </table>
  </div>
</template>
<script>
export default {
  data() {
    return {
      title: "개발자의 품격",
      input1: "abc",
      options: [
        {v:"S", t:"Seoul"},
        {v:"J", t:"Jeju"},
        {v:"B", t:"Busan"}
      ],
      region: "B",
      tableShow: true
    }
  },
  watch: {  // 변수명과 동일한 이름으로 함수 만들어서 특정 데이터 모니터링함(변경을 캐치함)
    input1() {
      console.log(this.input1);
    }
  },
  methods : {
    getData() {
      alert(this.input1);
    },
    setData() {
      this.input1 = "12345";
    },
    changeRegion() {
      alert(this.region)
    }
  },
  beforeCreate() {
    console.log("beforeCreate")
  },
  created() {
    console.log("created")  // DB에서 데이터 가져올때 beforeCreate나 created에서 가져와야 Mount될 때 한번에 랜더링되면서 데이터가 같이 적용됨
  },
  beforeMount() {
    console.log("beforeMount")
  },
  mounted() {
    console.log("mounted")
  },
  beforeUpdate() {
    console.log("beforeUpdate")
  },
  updated() {
    console.log("updated")
  },
  beforeDestroy() {
    console.log("beforeDestroy")
  },
  destroyed() {
    console.log("destroyed")
  }
};
</script>