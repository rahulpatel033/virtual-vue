<template>
<div class="image-gallery">
    <section>
        <div class="parent">
        <div class="image-display" @click="removeSelected">
            <div class="panzoom">
              <div class="owl-carousels" id="image-gallerys">
                  <div class="item">
                    <i class="fa fa-angle-left fa-5 fl" aria-hidden="true"></i>
                    <div class="obv-product-main-images">
                      <img  ref="image" :src="url" alt="" height="500" id="image"  >
                      <image-select></image-select>
                    </div>
                    <i class="fa fa-angle-right fa-5 fr" aria-hidden="true"></i>
                  </div>

              </div>

            </div>
        </div>

        </div>
        <div class="zoom-btn">
            <button class="zoom-in"><i class="icon-Plus"> </i> </button>
            <button class="zoom-out"> <i class="icon-Minus"> </i></button>
            <button class="reset"> <i class="fa fa-repeat" aria-hidden="true"></i></button>

            <a href="http://demo.officebrain.com/html/virtual-desktop/product_detail.php" target="_blank" class="close-full-view js-close-full-view">
                <span class="icon-shrink"></span>
            </a>
        </div>
    </section>
</div>
</template>
<style>
.obv-product-main-images{
  width: 412px;
  height: 502px;
  padding-right: 2px;
  margin: 0 auto;
  position: relative;
}
.item:before {
    content: "";
    height: 100%;
}
.item:before, .obv-product-main-images {
    display: inline-block;
    vertical-align: middle;
}
.fa-5 {
  font-size: 5em !important;
  cursor: pointer;
}
.fl {
  float: left;
  width: 10%;
}
.fr {
  float: right;
  width: 10%;
}
.parent .cropper-wrap-box {
  overflow: inherit;
}

.parent .owl-carousel .owl-stage-outer {
  overflow: inherit;
}
.hide {
  display: none;
}
.show {
  display: block;
}
</style>
<script>
import { mapGetters } from 'vuex'
import ImageSelect from '../image-select/ImageSelect.vue'
import { imageProcessingUrl } from '../../constants'

export default {
  name: 'product-gallery',
  data () {
    return {
      open: true,
      imageProcessingUrl: imageProcessingUrl,
      data: null
    }
  },
  components: {'image-select': ImageSelect},

  computed: {
    ...mapGetters({
      url: 'getImageUrl'
    })
  },
  methods: {
    removeSelected: function () {
      let target = $(event.target)
      if (!target.is('.vj-hotspot-selected')) {
        $('.vj-hotspot-selected').removeClass('vj-hotspot-selected')
        this.$store.dispatch('setIsSelectedArea', null)
      }
    }
  },
  watch: {
    url: function (val) {
      // alert(val)
    }
  }
}
</script>
