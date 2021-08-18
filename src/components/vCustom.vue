<template>
<div class="footer">
    <div class="footer__add">
        <button class="add-btn"><img src="../assets/add.svg" alt="" /></button>
      </div>
      <div class="footer__metrica">
        <input
          class="footer__metrica-input"
          type="text"
          placeholder="Metrica"
          v-model="metricaName"
        />
      </div>
      <div class="footer__formula">
        <input
          class="footer__formula-input"
          type="text"
          placeholder="Formula"
        />
      </div>
      </div>
</template>

<script>

export default ({
    data() {
        return {
            metricaName: ""
        }
    }
})
</script>

<style lang="scss" scoped>
.footer {
    margin-top: 10px;
    border-radius: 0px 0px 13px 13px;
    flex-basis: 6%;
    background: #eef1fa;
    display: flex;
    border-top: 1.5px solid #dfe0eb;
  &__add {
    flex-basis: 4%;
    display: flex;
    justify-content: center;
  }
  &__metrica {
    flex-basis: 50%;
    border-right: 1.5px solid #dfe0eb;
    border-left: 1.5px solid #dfe0eb;
    &-input {
      width: 100%;
      height: 100%;
      background: none;
      border: none;
      padding: 0px;
      margin: 0px;
      padding-left: 10px;
      font-family: "Inter", sans-serif;
      letter-spacing: 2px;

      &:focus {
        outline: none;
        // border: #33A3FA05 1px solid;
      }
      &::placeholder {
        color: #11263c;
        opacity: 0.2;
        // font-family: 'Inter', sans-serif;
      }
    }
  }
  &__formula {
    flex-basis: 45%;
    &-input {
      width: 100%;
      height: 100%;
      background: none;
      border: none;
      padding: 0px;
      margin: 0px;
      padding-left: 10px;
      font-family: "Inter", sans-serif;
      letter-spacing: 2px;

      &::placeholder {
        color: #11263c;
        opacity: 0.2;
        // font-family: 'Inter', sans-serif;
      }
      &:focus {
        outline: none;

        border-radius: 0px 0px 13px 0px;
      }
    }
  }
}
</style>
