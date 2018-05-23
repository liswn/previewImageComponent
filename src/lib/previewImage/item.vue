<template>
    <div v-if="src != null" @click="clickImg">
      <img :class="className" :style="imageStyle" :src="src" alt="">
    </div>
</template>
<script>
export default {
  props: {
    imageStyle: '',
    className: '',
    src: null
  },
  data () {
    return {
      itemId: null
    }
  },
  inject: ['click'],
  methods: {
    clickImg () {
      this.click(this.itemId)
    }
  }
}
</script>
<style>
</style>
