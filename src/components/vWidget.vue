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
    <div class="container-body"></div>
    <div class="container-footer"></div>
  </div>
</template>

<script>
export default {
  name: "vWidget",
};
</script>

<style lang="scss" scoped>
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