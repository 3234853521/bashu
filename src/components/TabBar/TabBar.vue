<template>
  <div id="tab-bar" style="margin-bottom: 1em">
    <el-card shadow="hover" style="margin: 0 auto;border-radius: 2em 2em 0 0">
      <el-row type="flex" style="width: 100%">
        <el-col :span="2" :xs="0"></el-col>
        <el-col v-for="(item,index) in btnContent" :key="item" :span="3">
          <button :class="{BtnActive:index===currentIndex}" class="Btn" @click="btnClick(index)">{{ item }}</button>
        </el-col>
      </el-row>
      <el-row style="padding: 15px 0">
        <el-col :sm="{span:20,offset: 2}" :span="22">
          <el-input v-model="input" class="input-with-select" style="outline: none;border-radius: 0"
                    placeholder="搜索输入相关资料">
            <el-button slot="append" class="to-search" style="background-color: crimson;border-radius: 0 "
                       @click="handleSearch">
              <span style="border-right: 1px solid ;padding-right: 25px;">搜索</span>
            </el-button>
            <el-button slot="append" class="to-search"
                       style="margin-left: 0;background-color: crimson;border-radius:0 2em 2em 0">
              高级搜索
            </el-button>
          </el-input>
        </el-col>
      </el-row>
    </el-card>
  </div>
</template>

<script>
export default {
  name: "TabBAr",
  data() {
    return {
      input: "",
      btnContent: [
        "全网检索",
        "电子图书",
        "电子期刊",
        "影音资料",
        "数据文献"
      ],
      currentIndex: 0
    }
  },
  methods: {
    btnClick(index) {
      this.currentIndex = index;
    },
    async handleSearch() {
      const res = await this.$http.search(this.input);
      console.log(res)
      this.$router.push('show')
    }
  }
}
</script>

<style scoped>

.to-search {
  color: white !important;
  font-weight: bold;
}

.input-with-select >>> .el-input__inner {
  background-color: gainsboro;
  overflow: hidden;
  padding-left: 10%;
  outline: none;
}

.input-with-select >>> .el-input-group__append {
  outline: none;
  border: 0;
  background: transparent;
}

.Btn {
  cursor: pointer;
  border: 0;
  text-align: center;
  outline: none;
  background-color: transparent;
  font-size: 1em;
}


.BtnActive::after {
  content: "";
  display: inline-block;
  width: 80%;
  height: 3px;
  background-color: #f52443;
  border-radius: 2em;
}

.el-input-group__append {
  border: none;
}

>>> input::-webkit-input-placeholder { /* WebKit, Blink, Edge */
  color: #000;
}

>>> input:-moz-placeholder { /* Mozilla Firefox 4 to 18 */
  color: #000;
}

>>> input::-moz-placeholder { /* Mozilla Firefox 19+ */
  color: #000;
}

>>> input:-ms-input-placeholder { /* Internet Explorer 10-11 */
  color: #000;
}
</style>
