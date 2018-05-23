<template>
  <div id="app">
    <lw-image-box>
      <lw-image-item slot="item" class="imageBox" className="image" src="http://image.cloud.zqcj.net.cn/image/1526970325735RHaN3YZtrKij6T5awTTGUzyskYJUhWBl.jpg?x-oss-process=image/resize,w_400,h_225,m_fill,limit_0"></lw-image-item>
      <lw-image-item slot="item" class="imageBox" className="image" src="https://i0.hdslb.com/bfs/bangumi/8ff39c776f473d8f4fe77910cec59e87ebd1e275.jpg@240w_320h.jpg"></lw-image-item>
    </lw-image-box>
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
  .imageBox
  {
    float: left;
  }
  .image
  {
    width: 160px;
  }
</style>
