
<template lang="pug">
  #app
    section.section
      nav.nav.has-shadow
        .container
          input.input.is-large(type="text", placeholder="Buscar Canciones", v-model="searchQuery")
          a.button.is-info.is-large(@click="search") buscar
          a.button.is-danger.is-large x
          p 
            small {{searchMessage}}
        
      .container
        .columns.space
          .cloumn(v-for="t in tracks") {{t.name}} - {{t.artista}} 

</template>

<script>
const tracks=[
  {name:'la cucaracha', artista:'don juan'},
  {name:'maria jose', artista:'don arturo'},
  {name:'yo no se ', artista:'jajajajajaj'},
]
export default {
  name: 'app',
  data () {
    return {
      searchQuery:'',
      tracks:[]
    }
  },
  methods:{
    search(){
      this.tracks=tracks
    }
  },
  computed:{
    searchMessage(){
      return "Encontrados: " + this.tracks.length
    }
  }

  
}
</script>

<style lang="scss">
@import './scss/main.scss';

.space{
  margin-top: 50px
}
</style>
