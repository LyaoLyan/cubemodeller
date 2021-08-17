<template>
  <div class="content">
    <div class="content-body"></div>
  </div>
</template>

<style scoped lang="scss">
.content {
  display: flex;
  flex-direction: column;
  width: 97%;
  height: 100%;
  background: #ffffff;
  /* stroke */

  box-sizing: border-box;
  border-radius: 13px ;
  &-body {
    border: 1px solid #ebebeb;
    height: 56%;
    background-color: #eef1fa;
    border-radius: 13px 13px 0 0;
  }
}
</style>