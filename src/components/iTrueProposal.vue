<template>
    <div class="proposal_container">
        <div class="proposalItem" v-for="(item, i) in props" :key="i">
            <div class="text">
                <h3>{{item.title}}</h3>
                <h4>{{item.subTitle}}</h4>
                <ul>
                    <li v-for="(subItem, j) in item.list" :key="j">+ {{subItem}}</li>
                </ul>
                <iTrue-btn :class="item.btnColor">{{item.btnText}}</iTrue-btn>
            </div>
            <div class="img" :style="{backgroundImage: 'url('+item.imgUrl+')'}">                
            </div>           
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
          props: [
              {
                  title: "Biometric",
                  subTitle: "Identity",
                  list: [
                      'Protect transactions with face verification',
                      'Identify visitors and customers to reward or punish them',
                      'Detect and prevent fraud and unauthorized activity'
                  ],
                  btnText: "Get Started",
                  btnColor: "blue",
                  imgUrl: "../img/man.jpg"
              },
              {
                  title: "Distributed",
                  subTitle: "Ledgers",
                  list: [
                      'Verify authenticity of assets',
                      'Prevent data spoofing',
                      'De-risk data handling on-premises'
                  ],
                  btnText: "Show More",
                  btnColor: "green",
                  imgUrl: "../img/cloud.png"
              }
          ]
      }
  }
}
</script>

<style lang="scss" >
@import "./css/mixins.scss";

.proposal_container {
    display: flex;
    flex-direction: column;
    .proposalItem {
        display: flex;
        justify-content: space-between;
        width: 1170px;
        margin: 75px auto;
        .img {
            width: 470px;
            height: 500px;           
            background-size: cover;
            background-repeat: no-repeat;            
            border-radius: 20px;
            border-top-left-radius: 100px;
            position: relative;
            @include theme-color(filter, $bw);
            &:after {
                content: "";
                position: absolute;
                width: 270px;
                height: 500px;
                top:0; bottom: 0;
                left: 490px;
                background-image: url('/img/man.jpg');
                background-position-x: -480px;
                background-size: cover;    
                background-repeat: no-repeat;   
                border-radius: 20px; 
                @include theme-color(filter, $bw);        
            }           
        }
        h3, h4 {            
            font-family: Heebo;
            font-size: 50px;
            font-weight: 300;
            line-height: 1.4;                      
        }
        h3 {
            margin: 36px 0 0;
            @include theme-color(color, $color-b-b);
            position: relative;
            &:after {
                content: "";
                position: absolute;
                width: 60px;
                height: 1px;
                background-color: $color-blue;
                bottom: 16px;
                right: 230px;
            }
        }  
        h4 {
            margin: 0 0 26px;
            @include theme-color(color, $color-g-bl);
        }    
        li {
            font-family: Inconsolata;
            font-size: 18px;
            margin: 11px 0;
            @include theme-color(color, $color-bg);
        }  
        button {
            margin: 66px 0 0 !important;
        }
        &:nth-child(2n) {
            .text {
                order: 2;
                text-align: right; 
                h3:after {
                    right: unset;
                    left: 0;
                }              
            }
            .img {
                order: 1;
                background-position-x: 0;
                border-radius:0;
                width: 500px;
                &:after {
                    width: 200px;
                    height: 200px;
                    top:150px; 
                    left: 370px;
                    background-image: url('/img/cloud.png');
                    background-position: -270px -130px;
                    background-size: auto;    
                    background-repeat: no-repeat;   
                    border-radius: 50%;  
                    border: 10px solid $color-white;
                }
            }
        }
        @media (max-width: 1800px) {
            .img:after {
                width: 150px;
            }
        }
        @media (max-width: 1550px) {
           width: 950px;           
        }
        @media (max-width: 1365px) {                  
           margin-right: 180px;   
           width: calc(95vw - 180px); 
        }
        @media (max-width: 1260px) {                  
           .img {
               height: 300px;
               width: 290px;
               &:after {
                    height: 300px;
                    left: 300px;
                    background-position-x: -295px;
               }
           }
           &:nth-child(2n) {              
               .img {
                   width: 300px;
                   &:after {
                        height: 150px;
                        width: 150px;
                        left: 200px;
                        top: 75px;
                        background-position-x: -295px;
                    }                   
               }
           }
        }
        @media (max-width: 1000px) {   
            flex-direction: column;
            margin-right: 0;
            width: 600px;
            margin: 75px auto;
            .text {
                order:2;                                
            }
            .img {
                order: 1;
            }
             &:nth-child(2n) {
                 .text {
                     text-align: left;
                     h3:after {
                       right: 210px;
                       left: unset;
                   }
                 }
             }
        }
        @media (max-width: 660px) { 
            margin: 20px 50px;
            width: calc(100vw - 100px); 
            &:nth-child(2n), &:nth-child(2n+1) {               
                .img{
                    width: calc(100vw - 100px); 
                    &:after{
                        display: none;
                    }
                } 
            }
            &:nth-child(2n) {
                .img {
                    height: calc(100vw - 100px);
                }
            }
            
        }
        @media (max-width: 460px) {  
            &:nth-child(2n), &:nth-child(2n+1) {          
            .text {
                h3,h4 {
                    font-size: 35px;
                }
                h3 {
                    margin-top: 10px;
                    &:after {
                        right: 0;
                        width: 50px;
                    }
                }
                button {
                    margin-top: 15px !important;
                }
            }
            }
            &:nth-child(2n+1) {   
                .img {
                    background-position-x: -80px;
                }
            }
        }
    }    
}
</style>