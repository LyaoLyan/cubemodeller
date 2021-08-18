<template>
  <div class="container">
    <div class="container-header">
      <div class="header-row">
        <div class="right">
          <div class="right-title">Selecting a widget</div>
          <div class="right-info">
            <button class="btn">
              <img
                class="header-row-btn-img"
                src="../assets/alert-circle.svg"
                alt=""
               
              />
            </button>
          </div>
        </div>
        <div class="left">
          <button class="btn">
            <img class="btn-img" src="../assets/dots.svg" alt="" />
          </button>
        </div>
      </div>
    </div>
    <div class="container-body widget">
      <v-image v-for="image in images" :key="image" :image="image"  @chooseChart="chooseChart"></v-image>
    </div>
    <div class="container-footer"></div>
  </div>
</template>

<script>
import vImage from "./vImage.vue"
export default {
  name: "vWidget",
  components: {
    vImage
  },
  data() {
    return {
      images: ["line", "bar", "radar", "scatter", "bubble", "Barnew"],
      choosenChart: ""
    }
  },
  methods: {
    chooseChart(data) {
      this.choosenChart = data.choosenChart
      this.$emit("chooseChart", {
        choosenChart: this.choosenChart
      })
    }
  }
};
</script>

<style lang="scss" scoped>
.container {
  height: 100%;
}
.widget {
  display: flex;
  flex-wrap:wrap;
  flex-grow: 0;
  height: 15vh;
  overflow-y: scroll; /* прокрутка по вертикали */
  scrollbar-color: #D8D8D8 #D8D8D8 0.2;
  scrollbar-width: thin;
}
.right {
  display: flex;
  align-items: center;
  &-info {
    padding-left: 5px;
    .btn {
      border: none;
      background: none;
    }
  }
}

</style>