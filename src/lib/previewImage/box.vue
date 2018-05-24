<template>
    <div :class="className">
      <slot name="item"></slot>
      <div class="preview_popover_container_bg" v-if="currentIndex != null" @click="currentIndex = null"></div>
      <div class="preview_popover_container" v-if="currentIndex != null">
        <div class="preview_popover_imgs_container">
          <div  v-for="(viewImage, index) in slots" class="preview_popover_img_container"  :key="index" v-show="index == currentIndex">
            <img class="preview_popover_img"  :src="viewImage.componentOptions.propsData.src" alt="">
          </div>
        </div>
        <div class="thumbnail_container" v-if="thumb">
          <ul :style="{left: prewthumbUlLeft+'px'}">
            <li class="thumbnail_item_box" v-for="(thumb, index) in slots" :key="index" :class="(currentIndex==index)?'current_thumb':'1'" @click="changeImage(index,$event)">
              <img class="thumbnail_item_img" :src="thumb.componentOptions.propsData.src" alt="">
            </li>
          </ul>
        </div>
      </div>
    </div>
</template>
<script>
export default {
  name: 'LwPreImageBox',
  props: {
    className: '',
    thumb: {
      type: Boolean,
      default: true
    }
  },
  data () {
    return {
      currentIndex: null,
      prewthumbUlLeft: 0
    }
  },
  methods: {
    preImage () {
      this.currentIndex = this.currentIndex <= 0 ? 0 : this.currentIndex - 1
    },
    nextImage () {
      let maxIndex = this.slots.length - 1
      this.currentIndex = this.currentIndex >= maxIndex ? maxIndex : this.currentIndex + 1
    },
    changeImage (index, event) {
      console.log(event)
      this.currentIndex = index
    },
    keyboardControl (e) {
      const that = this
      if (e.keyCode === 37) {
        that.preImage()
      }
      if (e.keyCode === 39) {
        that.nextImage()
      }
    }
  },
  computed: {
    slots () {
      return this.$slots.item
    }
  },
  provide () {
    return {
      click: (_uid) => {
        this.currentIndex = _uid
      }
    }
  },
  watch: {
    currentIndex (val) {
      const that = this
      if (val == null) {
        document.removeEventListener('keyup', that.keyboardControl, false)
      } else {
        document.addEventListener('keyup', that.keyboardControl, false)
      }
    }
  },
  mounted () {
    const that = this
    that.slots.map((item, index) => {
      item.componentInstance.itemId = index
    })
  }
}
</script>
<style scoped>
  .preview_popover_container_bg
  {
    position: fixed;
    left: 0;
    bottom: 0;
    right: 0;
    top: 0;
    z-index: 19891018;
    background-color: rgba(0,0,0,.8);
  }
  .preview_popover_container
  {
    position: absolute;
    top: 50%;
    left: 50%;
    height: 100%;
    width: 800px;
    background-color: #000;
    display: flex;
    padding: 20px;
    flex-flow: column;
    z-index: 19891019;
    transform: translate(-50%, -50%);
  }
  .preview_popover_imgs_container
  {
    display: flex;
    align-content: center;
    align-items: center;
    justify-content: center;
    flex: 1;
  }
  .thumbnail_container
  {
    position: relative;
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    width: 100%;
    flex: 0 0 60px;
    margin-top: 20px;
    overflow: hidden;
  }
  .thumbnail_container ul
  {
    position: relative;
    left: 40px;
    display: flex;
    flex-flow: nowrap;
    align-content: center;
    align-items: center;
    justify-content: left;
    padding: 0;
    width: 100%;
    margin: 0;
  }
  .preview_popover_img_container
  {
  }
  .preview_popover_img
  {
    min-width: 250px;
  }
  .pre_next_btn
  {
    display: block;
    white-space: nowrap;
    height: 35px;
    line-height: 35px;
    color: #ffffff;
    font-size: 16px;
    border: 1px solid #fff;
    border-radius: 5px;
    padding: 0 20px;
    position: absolute;
    top: 50%;
    user-select: none;
    transform: translateY(-50%);
  }
  .pre_next_btn:hover
  {
    cursor: pointer;
    background-color: rgba(255,255,255,.3);
  }
  .pre_btn
  {
    right: 100%;
    margin-right: 20px;
  }
  .next_btn
  {
    left: 100%;
    margin-left: 20px;
  }
  .thumbnail_item_box
  {
    position: relative;
    display: block;
    height: 56px;
    margin-left: 20px;
    border: 2px solid transparent;
    transition: all .2s linear;
  }
  .thumbnail_item_box:hover
  {
    cursor: pointer;
    border-color: #fff;
  }
  .current_thumb
  {
    border-color: #fff;
  }
  .thumbnail_item_box:first-child{
    margin-left: 0;
  }
  .thumbnail_item_img
  {
    height: 56px;
  }
  .slide-fade-enter-active {
    transition: all .8s ease;
  }
  .slide-fade-leave-active {
    transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
  }
  .slide-fade-enter
   {
    transform: translateX(10px);
    opacity: 0;
  }
  .slide-fade-leave-to
  {
    transform: translateX(-10px);
    opacity: 0;
  }
</style>
