<template>
  <div class="pswp" tabindex="-1" role="dialog" aria-hidden="true">
    很好
    <!-- Background of PhotoSwipe.
    It's a separate element as animating opacity is faster than rgba().-->
    <div class="pswp__bg"></div>

    <!-- Slides wrapper with overflow:hidden. -->
    <div class="pswp__scroll-wrap">
      <!-- Container that holds slides.
          PhotoSwipe keeps only 3 of them in the DOM to save memory.
      Don't modify these 3 pswp__item elements, data is added later on.-->
      <div class="pswp__container">
        <div class="pswp__item"></div>
        <div class="pswp__item"></div>
        <div class="pswp__item"></div>
      </div>

      <!-- Default (PhotoSwipeUI_Default) interface on top of sliding area. Can be changed. -->
      <div class="pswp__ui pswp__ui--hidden">
        <div class="pswp__top-bar">
          <!--  Controls are self-explanatory. Order can be changed. -->
          <div class="pswp__counter"></div>

          <button class="pswp__button pswp__button--close" title="Close (Esc)"></button>
          
          <button class="pswp__button pswp__button--share" title="Share"></button>
          
          <button class="pswp__button pswp__button--fs" title="Toggle fullscreen"></button>
          
          <button class="pswp__button pswp__button--zoom" title="Zoom in/out"></button>

          <!-- Preloader demo http://codepen.io/dimsemenov/pen/yyBWoR -->
          <!-- element will get class pswp__preloader--active when preloader is running -->
          <div class="pswp__preloader">
            <div class="pswp__preloader__icn">
              <div class="pswp__preloader__cut">
                <div class="pswp__preloader__donut"></div>
              </div>
            </div>
          </div>
        </div>

        <div class="pswp__share-modal pswp__share-modal--hidden pswp__single-tap">
          <div class="pswp__share-tooltip"></div>
        </div>

        <button class="pswp__button pswp__button--arrow--left" title="Previous (arrow left)"></button>
        
        <button class="pswp__button pswp__button--arrow--right" title="Next (arrow right)"></button>

        <div class="pswp__caption">
          <div class="pswp__caption__center"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import PhotoSwipe from "photoswipe/dist/photoswipe";
import UI from "photoswipe/dist/photoswipe-ui-default";
export default {
  methods: {
    open(
      index,
      list,
      params = {
        captionEl: false,
        fullscreenEl: false,
        history: false,
        shareEl: false,
        tapToClose: true
      }
    ) {
      let options = Object.assign(
        {
          index: index,
          getThumbBoundsFn(index) {
            let thumbnail = document.querySelectorAll(".preview-img")[index];
            let pageYScroll =
              window.pageYOffset || document.documentElement.scrollTop;
            let rect = thumbnail.getBoundingClientRect();
            return { x: rect.left, y: rect.top + pageYScroll, w: rect.width };
          }
        },
        params
      );
      this.photoswipe = new PhotoSwipe(this.$el, UI, list, options);
      this.photoswipe.init();
    },
    close() {
      this.photoswipe.close();
    }
  }
};
</script>

<style>
@import "photoswipe/dist/photoswipe.css";
@import "photoswipe/dist/default-skin/default-skin.css";
</style>
