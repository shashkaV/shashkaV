<template>
  <div>
    <divider text="Формат работы"/>

    <section class="work-item" v-for="(item, i) in workWith" :id="item.id">
      <h2 class="work-item__title">{{item.title}}</h2>
      <h2 v-if="item.subtitle" class="work-item__subtitle">( {{item.subtitle}} )</h2>

      <div class="wrapper flex-between">
        <div class="work-item__image-wrapper">
          <img class="work-item__image" :src="item.image">
        </div>
        <div v-if="item.tags">
          <work-format-type-section class="work-item__tags" :work-format-items="item.tags"/>
        </div>

        <div v-if="item.pack" style="padding-top: 20px;">
          <div  v-for="subItem in item.pack" :key="subItem.id">
            <ul class="subItem-list">
              <li class="subItem-list__item" v-for="point in subItem.description" :key="point">
                <span class="subItem-list__text">{{ point }}</span>
              </li>
            </ul>
            <div class="work-item__price">Стоимость: {{subItem.price}}₽</div>
          </div>
        </div>

      </div>
      <div v-if="item.tags" class="work-item__price">Стоимость: {{item.price}}₽</div>
      <div class="work-item__price-button flex-end-line">
        <app-button type="link" to="/Contacts">Записаться на консультацию</app-button>
      </div>
      <divider v-if="i !== 3" />
    </section>
  </div>
</template>

<script>
  import Divider from "../UI/elements/Divider";
  import {workWithValues} from "../helpers/textValues";
  import WorkFormatTypeSection from "../components/workFormat/WorkFormatTypeSection";
  import AppButton from "../UI/forms/AppButton";

  export default {
    name: "Workwith",
    layout: 'BasePageLayout',
    components: { Divider, WorkFormatTypeSection, AppButton },
    data() {
      return {
        workWith: workWithValues
      }
    },
  }
</script>

<style scoped lang="scss">
  @import "assets/scss/variables";

  .work-item {
    padding: 0 20px;
    &__title {
      font-weight: bold;
      font-size: 35px;
      color: #A2C1AF;
      margin-bottom: 20px;
    }
    &__subtitle {
      color: #A2C1AF;
      font-size: 25px;
    }
    &__image {
      width: 600px;
      margin-top: 20px;
      -webkit-border-radius: 20px;
      -moz-border-radius: 20px;
      border-radius: 20px;
      box-shadow: rgba(0, 0, 0, 0.16) 0px 10px 36px 0px, rgba(0, 0, 0, 0.06) 0px 0px 0px 1px;
    }
    &__price {
      text-align: right;
      font-size: 25px;
      font-weight: bold;
      color: #92721F;
    }
    &__price-button {
      margin-top: 50px;
    }
    &__tags {
      padding-top: 20px;
    }
  }
  .subItem-list {
    margin-left: 70px;
    &__item {
      margin: 20px 0;
      color: $base-olive-green;
      font-size: 20px;
    }
    &__text {
      font-size: 20px;
      color: $accent-middle-grey;
    }
  }

  @media screen and (max-width: 1023px){
    .wrapper {
      flex-direction: column;
    }
    .work-item {
      &__title {
        font-size: 20px;
        text-align: center;
      }
      &__subtitle {
        font-size: 16px;
        text-align: center;
      }

      &__image {
        width: 60%;
        display: block;
        margin: auto;
      }
      &__price {
        text-align: center;
        margin-top: 20px;
      }
      &__price-button {
        margin-top: 50px;
        justify-content: center;
      }
    }
    .subItem-list {
      width: 70%;
      margin: 20px auto;
      &__item {
        margin: 10px 0;
        font-size: 16px;
      }
      &__text {
        font-size: 16px;
      }
      &__price {
        font-size: 18px;
      }
    }
  }

  @media screen and (max-width: 767px) {
    .work-item {
      &__image {
        width: 80%;
      }
    }
    .subItem-list {
      width: 80%;
    }
  }

  @media screen and (max-width: 450px) {
    .work-item {
      &__image {
        width: 95%;
      }
    }
    .subItem-list {
      width: 90%;
    }
  }
</style>
