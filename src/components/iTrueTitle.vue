<template>
    <h2><slot></slot></h2>
</template>

<style lang="scss">
@import "./css/mixins.scss";

h2 {
    font-family: Heebo;
    font-size: 50px;
    font-weight: 300;
    line-height: 1.4;
    color: $color-white;
    max-width: 750px;
    text-align: center;
    margin: 0 auto;    
    padding-bottom: 27px;
    span {
        color: $color-blue-light !important;        
    }
}
@media (max-width: 768px) {
    h2 {
        font-size: 35px;
        line-height: 1.37;        
        padding: 0 30px 0; 
    }
}
</style>