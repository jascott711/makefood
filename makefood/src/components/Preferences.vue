<template>
  <div id="preferences">
    <div class="option option-1">Color Scheme</div>
  </div>
</template>

<script>

</script>

<style lang="scss">
  @import '../scss/variables';

  #preferences {
    position: absolute;
    background: $grey3;
    top: 115px;
    left: 0;
    right: 0;
    padding: 10px;

    .option {
      color: $white;
      padding: 10px;
      margin: 0 10px 10px;
    }
  }

  @media(min-width: 600px) {
    #preferences {
      top: 73px;
    }
  }
</style>