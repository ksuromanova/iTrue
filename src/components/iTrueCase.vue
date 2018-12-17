<template>
    <div class="cases_container">
        <div class="case" v-for="(item, i) in cases" :key="i">
             <h3>{{item.title}}</h3>
             <ul>
                <li v-for="(subItem, j) in item.list" :key="j">{{subItem}}</li>
            </ul>
        </div>
        <div class="btn">
            <iTrue-btn class="orange">Request Demo</iTrue-btn>
        </div>
        
    </div>
</template>

<script>
import iTrueBtn from './iTrueBtn'
export default {
    components: {
        iTrueBtn
    },
  data() {
      return {
          cases: [
              {
                  title: "Retail",                  
                  list: [
                      'Increase sales',
                      'Get full online analytics of your visitors and staff',
                      'Minimize risks'
                  ]                 
              },
              {
                  title: "Finance",                  
                  list: [
                      'Reduce staff related risks',
                      'Score potential borrowers',
                      'Identify VIPs and fraudsters'
                  ]                 
              },
              {
                  title: "Events and Venues",                  
                  list: [
                      'Identify security risks beforehand',
                      'Surprise your visitors with a unique experience',
                      'Get full traffic analysis of your events'
                  ]                 
              },
              {
                  title: "Casinos",                  
                  list: [
                      'Know everyone who enters the door',
                      'Understand customers’ average spending, number of visits and even favorite cocktail',
                      'Improve security and identify unwanted visitors'
                  ]                 
              },
              {
                  title: "Public Safety",                  
                  list: [
                      'Facial recognition and person identification in public areas',
                      'Minimize risks and prevent danger',
                      'Applications are endless: city streets, airports and railway stations, subway, transportation hubs, malls and government establishments, event venues and stadiums'
                  ]                 
              },
              {
                  title: "Corporate Safety",                  
                  list: [
                      'Prevent staff fraud with black and white lists',
                      'Facial access control and login to internal environment',
                      'Scale down your security costs'
                  ]                 
              }
          ]
      }
  }
}
</script>

<style lang="scss" >
@import "./css/mixins.scss";

.cases_container {
    display: flex;
    flex-wrap: wrap;  
    align-items: flex-start; 
    justify-content: center;        
    .case {
        margin: 15px;
        padding: 30px 30px;
        box-sizing: border-box;
        width: (400px - 30px);
        background-color: $color-white;
        border-radius: 15px;
        h3 {
            text-align: center;
            font-family: Inconsolata;
            font-size: 20px;
            font-weight: bold;
            color: $color-blue-light;
            text-transform: uppercase;
            padding: 5px 0;
                       
        }
        li {
            padding: 7px;
            font-family: Inconsolata;
            font-size: 18px;
            @include theme-color(color,$color-bg);
            padding-left: 18px;
            position: relative;
            &:before {
                content: "+";
                position: absolute;
                left: 0;
                font-family: Inconsolata;
                font-size: 18px;                
                @include theme-color(color, $color-bg-btn);
            }
        }        
        &:nth-child(2n){
            h3 {@include theme-color(color, $color-g-bl);}
        } 
    }        
    .btn {
        width: 400px;
        text-align: center;
         button {
            margin: 45px auto 0 !important;
        }
    }    
}
</style>