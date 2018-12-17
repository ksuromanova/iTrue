<template>
    <div class="contact_container">
        <div class="contact" v-for="(item, i) in contacts" :key="i">
             <h3><span>{{item.country}}</span> {{item.text}}</h3>
             <p>{{item.adress}}</p>
             <h4>{{item.phone}}</h4>
             <h5>{{item.email}}</h5>
        </div>   

        <div class="contact">
            <h3><span>Contact</span> Us</h3>
            <div class="unit-h" v-for="(item, j) in sites" :key="j">
                <h4>{{item.title}}</h4>
                <h5>{{item.email}}</h5>
            </div>            
        </div>
    </div>
</template>

<script>
export default {
  data() {
      return {
          contacts: [
              {
                  country: "Hong Kong",
                  text: "Head office",
                  adress: "Unit 1503, 15/F, Tung Seng Commercial Building, 69 Jervois St, Sheung Wan",
                  phone: "+1 650 300 4335",
                  email: "head-office@itrue.com"
              },
              {
                  country: "India",
                  text: "Subsidiarie",
                  adress: "1115, Tower-B4 Spaze i-Tech Park, Sector 49, Gurgaon Haryana, India, 122018",
                  phone: "+91 8000 161 161",
                  email: "india@itrue.com"
              },
              {
                  country: "Lebanon",
                  text: "Subsidiarie",
                  adress: "A.4878 Building, 11th Floor President Elias Hraoui St, Achrafieh, Beirut, Lebanon",
                  phone: "+44 20 3575 1008",
                  email: "lebanon@itrue.com"
              }
          ],
          sites:  [
                  {
                  title: "For General Purposes",
                  email: "general@itrue.com"
              },
              {
                  title: "For Investor Requests",
                  email: "investors@itrue.com"
              },
              {
                  title: "For Business",
                  email: "business@itrue.com"
              }
            ] 
      }
  }
}
</script>

<style lang="scss" >
@import "./css/mixins.scss";

.contact_container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    margin: 86px auto;
    .contact {
        margin: 15px;        
        box-sizing: border-box;
        width: (300px - 30px);
        h3 {
            font-family: 'Inconsolata';
            font-size: 20px;
            font-weight: 700;
            @include theme-color(color, $color-b-b);
            margin: 9px 0;
            span {
                color: $color-blue-light;
            }
        }
        p {
            font-family: 'Inconsolata';
            font-size: 18px;
            color: $color-blue-gray;
            margin: 9px 0;
        }
        h4 {
            font-family: 'Inconsolata';
            font-size: 18px;
            font-weight: 700;
            @include theme-color(color, $color-b-b);
            margin: 7px 0;
        }
        h5 {
            margin: 9px 0;
            font-family: Inconsolata;
            font-size: 18px;
            color: $color-blue-light;
        }
        .unit-h {
            margin: 8px 0;
            h4,h5 {
                margin: 0;
            }
        }
    }
     @media (max-width: 1200px) {       
         margin: 0 auto;
    }  
}
</style>