<template>
    <div :class="className">
      <slot name="item"></slot>
      <transition name="">
        <div class="preview_popover_container" v-if="currentIndex != null">
          <div class="preview_popover_container_bg" @click="currentIndex = null"></div>
          <div class="preview_popover_img_container">
            <span @click="preImage" class="pre_next_btn pre_btn">
              <template v-if="currentIndex<=0">
                没有上一张了
              </template>
              <template v-else>
                上一张
              </template>
            </span>
              <img class="preview_popover_img" :src="slots[currentIndex].componentOptions.propsData.src" alt="">
              <span @click="nextImage" class="pre_next_btn next_btn">
              <template v-if="currentIndex>=slots.length-1">
                没有下一张了
              </template>
              <template v-else>
                下一张
              </template>
            </span>
            <div class="thumbnail_container" v-if="thumb">
              <div class="thumbnail_item_box" v-for="(thumb, index) in slots" :key="index" :class="(currentIndex==index)?'current_thumb':'1'" @click="changeImage(index)">
                <img class="thumbnail_item_img" :src="thumb.componentOptions.propsData.src" alt="">
              </div>
            </div>
          </div>
        </div>
      </transition>
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
      currentIndex: null
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
    changeImage (index) {
      this.currentIndex = index
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
  mounted () {
    this.slots.map((item, index) => {
      item.componentInstance.itemId = index
    })
    window.addEventListener('keyUp', function (e) {
      console.log(e)
    })
  }
}
</script>
<style scoped>
  .preview_popover_container
  {
    position: fixed;
    left: 0;
    bottom: 0;
    right: 0;
    top: 0;
    overflow: auto;
    background-color: rgba(0,0,0,.8);
  }
  .preview_popover_container_bg
  {
    position: absolute;
    left: 0;
    bottom: 0;
    right: 0;
    top: 0;
  }
  .preview_popover_img_container
  {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
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
  .thumbnail_container
  {
    position: absolute;
    top: 100%;
    left: 50%;
    transform: translateX(-50%);
    white-space: nowrap;
    margin-top: 20px;
  }
  .thumbnail_item_box
  {
    display: inline-block;
    height: 60px;
    margin-left: 20px;
    border: 1px solid #ddd;
    transition: all .2s linear;
  }
  .thumbnail_item_box:hover
  {
    cursor: pointer;
    border-color: #ff0000;
  }
  .current_thumb
  {
    border-color: #ff0000;
  }
  .thumbnail_item_box:first-child{
    margin-left: 0;
  }
  .thumbnail_item_img
  {
    height: 60px;
  }
</style>
