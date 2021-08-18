<template>
  <div class="chart">
    <input type="radio" name="chart" :id="image" class="chart__radio" />
    <label class="chart__label" :for="image" @click="chooseChart"
      ><img
        class="chart__label__image"
        :src="require(`../assets/charts/${image}.svg`)"
        alt=""
    /></label>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  props: {
    image: String,
  },
  methods: {
    chooseChart() {
      // console.log(isActive);
      this.$emit("chooseChart", {
          choosenChart: this.image
      })
      this.isActive = !this.isActive;
    },
  },
};
</script>

<style lang="scss" scoped>
// .chart {
//   width: 100px;
//   height: 100px;
//   margin: 10px;

//   &__button {
//     &-image {
//       width: 100%;
//       height: 100%;
//     }
//     &__active {
//       border: 1.5px solid #7087ff;
//       box-shadow: 0px 2px 4px rgba(68, 68, 79, 0.15),
//         0px 4px 15px rgba(68, 68, 79, 0.1);
//       border-radius: 9px;
//     }
//   }
// }
.chart {
  width: 27%;
  margin: 10px;
  &__label {
    &__image {
      width: 100%;
      height: 100%;
    }
  }
  &__radio {
    display: none;
    &:checked {
      & + label img {
        border: 1.5px solid #7087ff;
        box-shadow: 0px 2px 4px rgba(68, 68, 79, 0.15),
          0px 4px 15px rgba(68, 68, 79, 0.1);
        border-radius: 9px;
      }
    }
  }
}
// .chart__radio:checked + label img{
// border: 1.5px solid #7087ff;
//         box-shadow: 0px 2px 4px rgba(68, 68, 79, 0.15),
//           0px 4px 15px rgba(68, 68, 79, 0.1);
//         border-radius: 9px;
// }
</style>