<template>
    <div v-if="src != null" @click="clickImg" class="preview_image_small_items">
      <img :class="className" :style="imageStyle" :src="thumb!=null?thumb:src" alt="">
    </div>
</template>
<script>
export default {
  props: {
    imageStyle: '',
    className: '',
    thumb: null,
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
  .preview_image_small_items
  {
    position:relative;
    cursor:pointer;
  }
</style>
