<template>
  <div>
    <button :disabled="disabled" class="button" :class="{disabled: disabled}" v-if="type === 'button'" @click="$emit('click')">
      <slot />
    </button>

    <NuxtLink class="button" v-if="type === 'link'" :to="`${to}`">
      <slot />
    </NuxtLink>
  </div>
</template>

<script>
  export default {
    name: "AppButton",
    props: {
      type: {
        type: String,
        required: true,
      },
      to: {
        type: String,
        required: false,
      },
      disabled: {
        type: Boolean,
        required: false
      }
    }
  }
</script>

<style scoped lang="scss">
  @import "assets/scss/variables";
  .button{
    text-decoration: none;
    background-color: #91AC9D;
    color: #ffffff;
    padding: 10px;
    -webkit-border-radius: 5px;
    -moz-border-radius: 5px;
    border-radius: 5px;
    transition: .4s;
    border: none;
    font-size: 20px;
    &:hover {
      background-color: #000000;
    }
  }

  .disabled {
    opacity: .5;
    &:hover {
      background-color: #91AC9D;
      opacity: .5;
    }
  }

  @media screen and (max-width: 450px){
    .button{
      font-size: 16px;
    }
  }
</style>
