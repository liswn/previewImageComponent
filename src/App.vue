<template>
  <div id="app">
    <div class="wapper">
      <lw-image-box>
        <lw-image-item slot="item" class="imageBox" className="image" thumb="http://image.cloud.zqcj.net.cn/image/1526970325735RHaN3YZtrKij6T5awTTGUzyskYJUhWBl.jpg?x-oss-process=image/resize,w_266,h_225,m_fill,limit_0" src="http://image.cloud.zqcj.net.cn/image/1526970325735RHaN3YZtrKij6T5awTTGUzyskYJUhWBl.jpg?x-oss-process=image/resize,w_400,h_225,m_fill,limit_0"></lw-image-item>
        <lw-image-item slot="item" class="imageBox" className="image" src="http://image.cloud.zqcj.net.cn/image/1527062121919i2y2kuyxTl7uvCX3VQcZ6OcNyIOQK3Sf.jpg?x-oss-process=image/resize,w_266,h_225,m_fill,limit_0"></lw-image-item>
        <lw-image-item slot="item" class="imageBox" className="image" src="http://image.cloud.zqcj.net.cn/image/1527062951944BmjiJlwaWiZzzKyz6KDvYjbA39MKDVEP.jpg?x-oss-process=image/resize,w_266,h_225,m_fill,limit_0"></lw-image-item>
        <lw-image-item slot="item" class="imageBox" className="image" src="http://image.cloud.zqcj.net.cn/image/1527062951944BmjiJlwaWiZzzKyz6KDvYjbA39MKDVEP.jpg?x-oss-process=image/resize,w_266,h_225,m_fill,limit_0"></lw-image-item>
        <lw-image-item slot="item" class="imageBox" className="image" src="http://image.cloud.zqcj.net.cn/image/1527062951944BmjiJlwaWiZzzKyz6KDvYjbA39MKDVEP.jpg?x-oss-process=image/resize,w_266,h_225,m_fill,limit_0"></lw-image-item>
        <lw-image-item slot="item" class="imageBox" className="image" src="http://image.cloud.zqcj.net.cn/image/1527062951944BmjiJlwaWiZzzKyz6KDvYjbA39MKDVEP.jpg?x-oss-process=image/resize,w_266,h_225,m_fill,limit_0"></lw-image-item>
        <lw-image-item slot="item" class="imageBox" className="image" src="http://image.cloud.zqcj.net.cn/image/1527062951944BmjiJlwaWiZzzKyz6KDvYjbA39MKDVEP.jpg?x-oss-process=image/resize,w_266,h_225,m_fill,limit_0"></lw-image-item>
      </lw-image-box>
    </div>
  </div>
</template>

<script>
import lwImageBox from '@/lib/previewImage/box'
import lwImageItem from '@/lib/previewImage/item'
export default {
  name: 'App',
  components: {
    lwImageBox,
    lwImageItem
  }
}

</script>
<style>
  .wapper
  {
    width: 800px;
    height: 400px;
    background-color: #f0f0f0;
    margin: 40px auto 0;
  }
  .imageBox
  {
    float: left;
  }
  .image
  {
    width: 160px;
  }
</style>
