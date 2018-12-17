<template>
  <div id="app">
    <iTrue-header id="top"></iTrue-header> 
    <a href="#top"><i v-show="scrollPosition > rez[0]" class="icon-top"></i></a>
    <article :class="[(scrollPosition===null | scrollPosition < rez[0]) ? 'theme-color' : 'theme-bw']">
       <section class="title">
        <iTrue-title>The Future of <span>Biometrics</span> with Distributed Ledger Technologies</iTrue-title>
        <div class="row">
          <iTrue-btn class="orange">Show More</iTrue-btn>
          <iTrue-play-btn></iTrue-play-btn>
        </div>
        
      </section>
    </article>

    <article :class="[(scrollPosition < rez[1] & scrollPosition > rez[0]) ? 'theme-color' : 'theme-bw']">
      <section class="proposals">
        <iTrue-proposal></iTrue-proposal>
      </section>
    </article>

    <article :class="[(scrollPosition < rez[2] & scrollPosition > rez[1]) ? 'theme-color' : 'theme-bw']">
       <section class="cases">
         <iTrue-title>Use <span>Cases</span></iTrue-title>
         <iTrue-case></iTrue-case>
       </section>
    </article>

    <article :class="[(scrollPosition < rez[3] & scrollPosition > rez[2]) ? 'theme-color' : 'theme-bw']">
      <section class="contact">
        <iTrue-contact></iTrue-contact>
        </section>  
    </article>  
      
  </div>
</template>

<script>
import iTrueHeader from './components/itrueHeader'
import iTrueTitle from './components/iTrueTitle'
import iTrueBtn from './components/iTrueBtn'
import iTruePlayBtn from './components/iTruePlayBtn'
import iTrueProposal from './components/iTrueProposal'
import iTrueCase from './components/iTrueCase'
import iTrueContact from './components/iTrueContact'
export default {
  components: {
    iTrueHeader,
    iTrueTitle,
    iTrueBtn,
    iTruePlayBtn,
    iTrueProposal,
    iTrueCase,
    iTrueContact
  },
  data() {
    return {
      scrollPosition: null,      
      rez: []
    }
  },  
  methods: {
    updateScroll() {
      this.scrollPosition = window.scrollY; 
      
      var intElemScrollHeight = document.getElementsByTagName('section');
      var clientH = screen.height / 2 + 1;
      var sectionHeight = [];
      for(var j=0; j<intElemScrollHeight.length; j++) {
          sectionHeight.push(intElemScrollHeight[j].scrollHeight);
      }

      var result = [];
      var totalSum = sectionHeight.reduce(function(sum, item) {
        result.push(sum);
        return sum + item;
      });
      result.push(totalSum);

      this. rez = result.map( function(value) { 
        return value - clientH; 
      } );          
    }    
  },
  mounted() {
    window.addEventListener('scroll', this.updateScroll); 
console.log(this.scrollPosition);
  }
}
</script>

<style lang="scss" >
@import "./css/mixins.scss";

.icon-top {
  position: fixed;
  z-index: 10;
  bottom: 40px; right: 40px;
  height: 40px;
  width: 40px;
  line-height: 40px;
  font-size: 12px;
  background-color: $color-blue-light;
  border-radius: 50%;
  text-align: center;
  color: $color-white;

}
section {  
  display: flex;
  flex-direction: column;
  justify-content: center;
  .row {
    display: flex;
    align-items: center;
    justify-content: center;
  }
}
.title {    
  height: 900px;
  line-height: 900px;
  position: relative;
  &:before  {
    content: "";
    position: absolute;
    top: 0; bottom: 0;
    right: 0; left: 0;    
    height: 900px;
    background-image: url('../img/title-bg.png'); 
  } 
  @media (max-width: 768px) {
    height: 617px;
    line-height: 617px;    
    &:before  {
      height: 617px;
      background-position-x: 30%;
    }
  }
}
.cases {  
  padding: 155px 0 155px;  
  position: relative;
  &:before  {
    content: "";
    position: absolute;
    top: 0; bottom: 0;
    right: 0; left: 0;   
    height: 100%;
    background-image: url('../img/cases-bg.png');  
  }
}
.title, .cases {
  z-index: 2;
   &:before  {
     background-size: cover;
    background-repeat: no-repeat;  
     @include theme-color(filter, $bw);
    z-index: -1;
   }
  
  @include theme-color(background-color, $color-bg);   
   
}
.proposals {
  margin: 75px auto;
  @media (max-width: 460px) { 
    margin: 0 auto;
  }
}
</style>
