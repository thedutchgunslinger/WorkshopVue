<template>
  <!-- header -->
  <header>
    <h1>{{ title }}</h1>
  </header>
</template>

<script>
export default {
    data(){
        return {
           title: 'Bronnen lijst'
        };
    },
    
};
</script>

<style lang="scss" scoped>
@import "./../assets/_variables.scss";

header {
  background-color: $primaryColor;
  height: 100px;
  font-family: $mainTextFont;
  h1 {
      color: $textColor;
        font-size: 2rem;
        padding: 1rem;
  }
}
</style>
