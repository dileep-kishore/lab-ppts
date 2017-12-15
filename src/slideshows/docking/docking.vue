<template lang="pug">
#DockingPipeline.eg-theme-agrume
  .eg-slideshow

    slide(enter='fadeInUp')
      .center.frontpage
        h1 Metabolite Docking
        h4 Dileep Kishore

    slide
      h3 Background
      ul
        li AHR is a transcription factor implicated in many cancers
        li Ligand activated, best known for enabling the tumor-promoting properties of the carcinogen TCDD (tetrachlorodibenzo-p-dioxin).
        li It has been shown in tumors that AHR levels are usually elevated and are localized to the nucleus, suggesting that there is some sort of connection between AHR activation and tumor progression.
      .img-slide
        img(src="./images/ahr_biology.jpg")

    slide
      h3 Relationship to microbial metabolites
      ul
        li AHR activity can be modulated by microbial metabolites - Jin et al. (2014)
        li Showed that colonic bacteria metabolized tryptophan to produce a variety of metabolites that were potent AHR ligands
        ul
          li indole
          li indole-3-acetate
          li indole-3-aldehyde

    slide
      h3 Goals
      ul
       li Identify microbial metabolites that dock to the AHR active site
       li Screen these compounds experimetally
       li Use the docking energies and structural information to identify microbes that disregulate normal AHR activity

    slide
      h3 Docking
      ul
        li Predicts the position and orientation of a ligand when it is bound to a protein receptor
        li Is used for a variety of applications including virtual screening of drug candidates
        li In addition to the docking pose we can also infer the binding energy (affinity) of the interaction
      .img-slide
        img(src="./images/docking_biology.png")

    slide
      h3 Brief methodology
      ul
        li Given a list of microorganisms obtain their corresponding metabolites
        li Obtain the energy minimized 3D structures of these metabolites
        li Sample diverse microbial metabolites from the metabolite pool
        li Dock these metabolites to the PAS-B domain of the AHR homology model

    slide
      h3 Preliminary docking results
      .docking-grid
        .docking-pic
          p Tryptophan only
          img(src="./images/trp_only.png", width="400", height="300")
        .docking-pic
          p Phenazine only
          img(src="./images/phenazine_only.png", width="400", height="300")
        .docking-pic
          p CB7993113 only
          img(src="./images/cb_only.png", width="400", height="300")
        .docking-pic
          p All docked
          img(src="./images/trp_phe_cb.png", width="400", height="300")

    slide(enter="fadeIn")
      h4(style={'position': 'absolute', 'margin-top': '20%', 'margin-left': '-10%'}) Pipeline
      .img-slide(style={'margin-top': '10%'})
        img#pipeline-fig(src="./images/docking_pipeline.png", width="800", height="800")

    slide
      h3 Distance metrics and clustering
      ul
        li Similarity is calculated using the Morgan fingerprint
        .img-slide
          img(src="./images/similarity_map_fp1.png")
        li This creates a bit vector representation for the molecule
        li Diverse molecules are picked using a MaxMin dissimilarity approach

    slide
      h3 Structures of the top hits
      .docking-grid
        .docking-pic
          p 24-Methylenecycloartonal
          img(src="./images/24-Methylenecycloartanol.png", width="400", height="300")
        .docking-pic
          p Tetrahydropalmatine
          img(src="./images/Tetrahydropalmatine.png", width="400", height="300")
        .docking-pic
          p Deoxycortisone
          img(src="./images/DOC.png", width="400", height="300")
        .docking-pic
          p Gibberellin
          img(src="./images/Gibberellin.png", width="400", height="300")

    slide
      h3 Distribution of binding energies

    slide
      h3 Experimental Results
      .img-slide
        img(src="./images/experimental_results.png")

    slide(:steps=3)
      h3 Issues
      ul
        li(v-if="step == 1") Incorrect metabolite predictions
          ul
            li THP was wrongly identified as being produced by H. pylori
            li The corresponding gene was annotated to be a part of pyrimidine metabolism
            li The associated reaction was: <br /> Tetrahydropalmatine_c + 2.0 O2_c + H+_c <=> 2.0 H2O2_c + Palmatine_c
        li(v-if="step == 2") Accessibility of the AHR binding site
          .img-slide
            img(src="./images/ahr_accessibility.png")
        li(v-if="step == 3") Docking produces a large number of false positives
          .img-slide
            img(src="./images/cnn.png")

    slide
      h1 Thank you!

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
// @import 'node_modules/eagle.js/src/themes/agrume/agrume';
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
#DockingPipeline {
  h3 {
    font-weight: bolder;
  }
  .img-slide {
    margin-left: 20px;
    padding: 10px;
    display: flex;
    justify-content: center;
  }
  ul {
    padding: 6;
  }
  li {
    font-family: 'Delicious';
    padding: 3px;
  }
  h4 {
    margin: 0px;
    text-decoration: underline;
  }
  .frontpage {
    h4 {
      color: gray;
      text-decoration: none;
    }
  }
  .resizable-iframe {
    height: 950px;
    width: 130%;
    overflow-x: hidden;
    overflow-y: hidden;
    resize: both;
    z-index: 1;
    margin-left: -15%;
  }
  .docking-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
  }
  .docking-pic {
    position: relative;
    align-content: center;
    text-align: center;
    margin: auto;
    img {
      margin: auto;
    }
    p {
      margin: 0 auto;
      margin-top: 10px;
    }
  }
  #pipeline-fig {
    z-index: 1;
    position: absolute;
    // margin-top: -70px;
  }
  .img-exp {
    display: flex;

    img {
      margin-top: 50px;
      padding-right: 10px;
      border-right: dashed gray;
    }
  }
}
</style>
