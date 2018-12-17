<template>
    <header>
        <logo></logo>

        <div class="navBar" @click="navBarShow = !navBarShow">
            <i :class="[navBarShow ? 'icon-cancel' : 'icon-menu']"></i>
        </div>

        <div :class="[navBarShow ? 'navsMoblist' : 'navslist']" >
            <div v-for="(navItem, index) in navbarList"
                        :key="index" 
                        @click="callSubMenu(index)"  
                        class="navsItem"                 
                >+ {{ navItem.name }} 
                <ul class="subMenu" v-if="navItem.subNames.length >0">
                  <li v-for="(navSubItem, index) in navItem.subNames" :key="index">
                    <a>+ {{navSubItem}}</a>
                  </li>
                </ul>
            </div> 
                      
        </div>
    </header>
</template>
<script>
import logo from './logo';

export default {  
  data () {
    return {
      navbarList: [
          {
              name: "Solutions",
              subNames: [
                  'For Individual', 'For Business', 'For Developer'
              ]
          },
          {
              name: "Use Cases",
              subNames: [ 'test casses']
          },
          {
              name: "Technologies",
              subNames: ['test Technologies']
          },
          {
              name: "Company",
              subNames: ['test Company']
          },
          {
              name: "Documents",
              subNames: ['test Documents']
          }
      ],
      navBarShow: false      
    }
  }, 
  methods: {
      callSubMenu(index) {       
        var menuItems=document.getElementsByClassName('navsItem');    
        var dataItems=document.getElementsByClassName('subMenu');                 
        for(var i=0;i<menuItems.length; i++){           
          if(index===i) {               
            menuItems[i].classList.toggle('active');
            dataItems[i].classList.toggle('active');
          }     
            
        }
      }
  },
  components: {
    logo    
  }
}
</script>

<style lang="scss">
@import "./css/mixins.scss";

header {
  position: absolute;
  z-index: 100;
  top:0; left:0; right:0;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 40px;
  .navBar {
    display: none;
  }
  .navslist {
    font-family: 'Inconsolata', monospace;
    font-size: 18px;
    color: $color-white;  
    display: flex;
    cursor: pointer;
  }
   .navsItem {
      margin-left: 38px;
      position: relative; 
    } 
  .subMenu {
        display: none;
        position: absolute;
        font-family: 'Inconsolata', monospace;
        font-size: 18px;
        top: 45px;
        color: $color-blue;
        width: 240px;  
        margin-left: -18px;      
        border-radius: 15px;
        background-color: $color-white;
        li {
          padding: 16px 19px;
          border-bottom: 1px solid $light-sky-blue;
          &:last-child {
            border-bottom: none;
          }
          &:hover {
            color: $color-blue-light;
          }
        }
      &.active {
        display: block;
        color: $color-blue;
      }
    }
    .active {
      color: $color-blue-light;
    }   
  .navsMoblist {
    display: none;
  }
  @media (max-width: 900px) {
    position: relative;
    background-color: $color-white;
    padding: 0;
    height: 50px; 
    .navBar {
      display: block;
      background-color: $color-green;
      width: 50px;
      color: $color-white;
      text-align: center;
      i {
        font-size: 16px;
        line-height: 50px;
      }
    }
    .navslist {
      display: none;
    }
    .navsMoblist {
      display: flex;
      flex-direction: column; 
      position: absolute;     
      z-index: 100;
      top: 3rem;
      right: 0;
      padding-right: 1rem;
      box-sizing: border-box;     
      width:100%;
      background-color: $color-white; 
      color: $color-blue;
    }
    .navsItem {
      margin: 16px;
    }
    .subMenu {
      position: relative;
      top: 0;
      margin: 0 16px 10px 0;
      width: 100%;
    }
  }
}
</style>