<template lang="pug">
#DockingPipeline.eg-theme-agrume
  .eg-slideshow

    slide(enter='fadeInUp')
      .center.frontpage
        h1 Metabolite Docking
        h4 Dileep Kishore

    slide
      h3 Empty

</template>

<script>
import eagle from 'eagle.js'

export default {
  mixins: [eagle.slideshow],
  infos: {
    title: 'Metabolite Docking',
    description: 'Docking microbial metabolites to the AHR',
    date: '[12-15-2017]',
    path: 'docking'
  },
  components: {

  },
  data () {
    return {
      title: ''
    }
  }
}
</script>

<style lang="scss">
@import 'node_modules/eagle.js/src/themes/agrume/agrume';
@font-face {
  font-family: 'Delicious';
  src: url('./assets/fonts/Delicious-Roman.otf');
}
.eg-slide{
  background-color: white;
}
.eg-theme-agrume .eg-slideshow{
  background-image: none;
  background-color: white;
}
.eg-slideshow{
  background-color: white;
  background-image: none;
}
.subslide{
  max-width: 100%;
}
</style>
