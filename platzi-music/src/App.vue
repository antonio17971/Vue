
<template lang="pug">
  #app
    section.section
      nav.nav.has-shadow
        .container
          input.input.is-large(type="text", placeholder="Buscar Canciones")
          a.button.is-info.is-large buscar
          a.button.is-danger.is-large x

        
      .container
        .columns
          .cloumn

</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      
    }
  },
  methods:{
  }

  
}
</script>

<style lang="scss">
@import './scss/main.scss';
</style>
