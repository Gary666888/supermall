<template>
  <div>
    <nav-bar>
      <div slot="left" class="back" @click="backClick">
        <img src="~assets/img/common/back.svg">
      </div>
      <div slot="center" class="title">
        <div
          v-for="(item, index) in titles"
          class="title-item"
          :key="item"
          @click="itemClick(index)"
          :class="{ active : currentIndex===index }"
        >
          {{ item }}
        </div>
      </div>
    </nav-bar>
  </div>
</template>

<script scoped>
import NavBar from "components/common/navbar/NavBar";
export default {
  name: "DetailNavBar",
  data() {
    return {
      titles: ["商品", "参数", "评论", "推荐"],
      currentIndex: 0,
    };
  },
  components: {
    NavBar,
  },
  methods: {
    itemClick(index) {
      this.currentIndex = index;
      this.$emit('toCurrent',index)
    },
    backClick(){
      this.$router.back();
    }
  },
};
</script>
<style scoped>
.title {
  display: flex;
  font-size: 13px;
}
.title-item {
  flex: 1;
}
.back img{
  margin-top: 10px;
}
.active{
  color: var(--color-high-text);
}
</style>
