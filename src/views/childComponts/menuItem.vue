<template>
  <div class="mait">
    <div v-for="(item, index) in maitItem" :key="index" class="mait-item">
      <img :src="item.image" alt @click="itemClick(item)" />
      <div class="item-title">
        <span>{{item.title}}</span>
      </div>
    </div>
    <toast :theItem="theItem" @toastBtn="toastBtn" v-show="theShow"></toast>
  </div>
</template>

<script>
import Toast from '@/components/toast/Toast'
export default {
  name: "menuItem",
  components: {
    Toast
  },
  props: {
    maitItem: {
      type: Object,
      default() {
        return {};
      },
    },
  },
  data() {
    return {
      theItem: {},
      theShow: false,
    }
  },
  methods: {
    itemClick(item) {
      this.theItem = item;
      this.theShow = true;
      console.log(this.theItem);
    },
    toastBtn(s) {
      this.theShow = s;
    }
  }
};
</script>

<style scoped>
.mait {
  vertical-align: middle;
  overflow: hidden;
}
.mait-item {
  float: left;
  margin-top: 15px;
  margin-left: 8px;
}
.mait-item img {
  width: 270px;
  height: 270px;
  margin-bottom: 10px;
}
.item-title {
  font-size: 11px;
  text-align: center;
}
</style>
