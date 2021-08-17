<template>
  <div class="container">
    <div class="container-header">
      <div class="header-row">
        <div class="header-row-title">Metrics</div>
        <div class="header-row-alert">
          <button class="alert-btn">
            <img src="../assets/alert-circle.svg" alt="" />
          </button>
        </div>
        <div class="header-row-search">
          <input class="search-input" type="search" />
        </div>
        <div class="header-row-add">
          <button class="add-btn">
            <img src="../assets/add.svg" alt="" />
          </button>
        </div>
      </div>
    </div>
    <div class="container-body">
      <ul class="options">
        <li class="options__item">
          <details class="options__item-details">
            <summary class="options__item-details-summary">Templates</summary>
            <ul class="options__item-details-list">
              <li class="options__item-details-list-item"><input type="checkbox">Metrica 1</li>
              <li class="options__item-details-list-item"><input type="checkbox">Metrica 2</li>
              <li class="options__item-details-list-item"><input type="checkbox">Metrica 3</li>
            </ul>
          </details>
        </li>
        <li class="options__item">
          <details class="options__item-details">
            <summary class="options__item-details-summary">Data pool</summary>
            <li></li>
            <li></li>
            <li></li>
          </details>
        </li>
        <li class="options__item">
          <details class="options__item-details">
            <summary class="options__item-details-summary">Custom</summary>
            <li></li>
            <li></li>
            <li></li>
          </details>
        </li>
      </ul>
    </div>
    <div class="container-footer"></div>
  </div>
</template>

<style lang="scss" scoped>
.search-input {
  background: #ffffff;
  border: 1.23597px solid #ece9f1;
  box-sizing: border-box;
  border-radius: 9px;
}
.container-body {
  .options {
    margin: 0px;
    padding-top: 13px;
    &__item {
      color: rgba(116, 89, 217, 1);
      font-size: 14px;
      padding-bottom: 5px;
      list-style-type: none;
      &-details {
        &-summary {
          list-style-type: none;
          &::-webkit-details-marker {
            display: none;
          }
          &::marker {
            display: none;
          }
          &::before {
            padding-right: 5px;
            content: url("../assets/open.svg");
          }
        }
        &[open] > summary::before {
          padding-right: 0px;
          content: url("../assets/opened.svg");
        }

        &-list {
          &-item {
            color: #4f4f4f;
            list-style-type: none;
            &:before {

            }
          }
        }
      }
    }
  }
}
summary {
  list-style-type: none;
  content: url("../assets/open.svg");
}
</style>