<template>
    <button><slot></slot></button>
</template>

<style lang="scss">
@import "./css/mixins.scss";

button {
    font-family: Inconsolata;
    font-size: 20px;
    font-weight: bold;
    line-height: 60px;
    text-align: center;
    border-radius: 30px;
    margin: 33px 15px;
    min-width: 180px;
    border:none;
}
button.orange {
    @include theme-color(color ,$color-text-btn);
    @include theme-color(background-color ,$color-bg-btn);
}
button.blue {
    @include theme-color(background-color ,$color-bl-b);
    color: $color-white;
}
button.green {
     @include theme-color(background-color ,$color-g-b);
     color: $color-white;
}
</style>