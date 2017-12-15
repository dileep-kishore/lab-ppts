<template lang="pug">
#PipelineMethods.eg-theme-agrume
  .eg-slideshow

    slide(enter='fadeInUp')
      .center.frontpage
        h1 Methods in 16S data-analysis
        h4 Dileep Kishore

    slide(:steps=3)
      h3 Introduction
      ul
        li(v-show="step >= 2").
          Operational Taxonomic Units: Clusters of micro-organisms grouped by DNA sequence similarity usually in the 16S region
        li(v-show="step >= 3").
          Co-occurence Networks: Networks obtained from correlation matrices of 16S rDNA samples from various environments

    slide(:steps=4)
      h3 Goals
      .img-slide(v-if="step == 1")
        img(src='./images/logo.svg')
      h4(v-if="step == 2") Data Collection
      ul(v-if="step == 2")
        li Collect 16S rDNA sequence data from publications and databases
        li Databases:
          ul
            li Human Microbiome Project
            li Human Oral Microbiome
            li American Gut
        li Publications:
          ul
            li RISK cohort
            li Joslin dataset
        li Focus is on cross-sectional studies
      h4(v-if="step == 3") User data analysis
      ul(v-if="step == 3")
        li Provide access to a pipeline for 16S data analysis
        li Data is processed using a standardized pipeline and parameters
        li Metrics like
          ul
            li Abundance
            li Diversity
            li Co-occurrence interactions
        li These are already provided by some website like:
          ul
            li MGRAST
            li Qiita
            li Metaviz
      h4(v-if="step == 4") Exploration of data
      ul(v-if="step == 4")
        li Provide access to a database of microbial interactions from various databases
        li All the data in the database would be processed using a standardized pipeline and parameters
        li Users can compare and contrast:
          ul
            li Disease vs. Healthy microbiome
            li Identify core or differential microbiota
            li Query microbial interactions by taxa level or based on environment or across

    slide(enter="zoomIn", exit="zoomOut")
      h1 Demonstration

    slide(enter="zoomIn", exit="ZoomOut")
      .resizable-iframe
        iframe(src="http://microbialnet.org/mindex_x2.html" height="100%" width="100%")

    slide(:steps=6, enter="fadeIn")
      h3 Issues
      h4(v-if="step == 2") Sequencing method
      .img-exp(v-if="step == 2")
        img(src='./images/2_samples.svg', height="50%", width="50%")
        ul
          li Older studies and datasets
          li Issues:
          ul
            li Different sequencing depth
            li Different pre-processing and quality filtering
      h4(v-if="step == 3") Clustering methods
      .img-exp(v-if="step == 3")
        img(src='./images/3_clusteringOTUs.svg', height="50%", width="50%")
        ul
          li Closed reference
          li Open reference (Sub)
          li Denovo clustering
      h4(v-if="step == 4") Alignment to databases
      .img-exp(v-if="step == 4")
        img(src='./images/4_alignmenttodatabases.svg', height="50%", width="50%")
        ul
          li Greengenes
          li Silva
          li RDP
      h4(v-if="step == 5") Processing methods
      .img-exp(v-if="step == 5")
        img(src="http://journals.plos.org/ploscompbiol/article/figure/image?size=large&id=10.1371/journal.pcbi.1003531.g001", height="50%", width="50%")
        ul
          li Varying library sizes
          ul
            li Normalization
            li Rarefying
            li Mixture Models
          li Varying sparsity
            ul
              li Sparse samples
              li Sparse OTUs
      h4(v-if="step == 6") Calculation of correlations
      .img-exp(v-if="step == 6")
        img(src='./images/7_pairwisecorrelation.svg', height="50%", width="50%")
        ul
          li Compositionality
          li Sparsity
          li Pairwise associations
          ul
            li Pearson
            li Spearman
            li SparCC
          li Direct associations
          ul
            li SpiecEasi
            li CCLasso
            li mLDM
      //- .img-exp(v-if="step == 7")
      //-   eg-transition(enter='fadeIn', leave='fadeOut')
      //-     .corr-tools
      //-       .quarter(v-if="step >= 7")
      //-         p Pearson
      //-       .quarter(v-if="step >= 7")
      //-         p Spearman
      //-       .quarter(v-if="step >= 7")
      //-         p SparCC
      //-       .quarter(v-if="step >= 7")
      //-         p SpiecEasi

    slide(:steps=2)
      h3 Goals - Pipeline Methods Paper
      ul
        li Develop a standard pipeline for the whole process
        li Study how different parameters affect the various steps in the pipeline
        div(v-if="step == 1")
          li Tools
          ul
            li dada2
            li deblur
            li iped
            li Qiime2 (uses dada2 for the error model)
            li SparCC
            li SpiecEasi
            li mLDM
        div(v-if="step == 2")
          li Voting method
          li Decision tree
          li Dynamic computation graph
          //- .img-slide
          //-   img(src="")

    slide(enter="fadeIn")
      h4(style={'position': 'absolute', 'margin-top': '20%'}) Pipeline
      .img-slide
        img#pipeline-fig(src='./images/pipeline.svg', width="1000", height="1000")

    networks-slide(enter='fadeIn', leave='fadeOut')

    slide(enter="slideInUp")
      h3 Correlations
      .img-slide
        img(src="./images/network_comp_paper.png")

    slide
      h3 What metrics do we use to compare?
      ul
        li Diversity
        li Abundances
        li Motifs in the network
        li Degree distributions
        li Connected components
        li Metabolic modeling

    slide(enter="zoomIn", exit="zoomOut")
      .resizable-iframe
        iframe(src="http://127.0.0.1:8050/" height="100%" width="100%")

    slide
      h1 Thank you!
      .center.frontpage
        img(src="https://imgs.xkcd.com/comics/standards.png")

</template>

<script>
import eagle from 'eagle.js'

export default {
  mixins: [eagle.slideshow],
  infos: {
    title: 'Microbial Interaction Database',
    description: 'Studying microbial co-occurrence networks',
    date: '[12-15-2017]',
    path: 'mind'
  },
  components: {
    'networks-slide': require('./components/NetworksSlide')
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
#PipelineMethods {
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

