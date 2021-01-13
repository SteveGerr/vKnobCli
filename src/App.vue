<template>
  <div id="app">
    <Vknob 
      :label="vknobLable"
      :knobValue="knobValueData"
      :knobSplitterUrl="splitterLink"
      :knobControlUrl="controlLink"
      @changeValue="onChangeValue"      
    ></Vknob>
  </div>
</template>

<script>
import Vknob from './components/Vknob'

export default {
  name: 'App',
  components: {
    Vknob
  },

  data() {
    return {
      vknobLable: 'Reverb',
      controlLink: 'https://upload.wikimedia.org/wikipedia/commons/thumb/c/cb/Cercle_bleu_barre.svg/220px-Cercle_bleu_barre.svg.png',
      splitterLink: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQIzN9ZAPlkO_nV9FePzUo1u9vzHovk9vTQQw&usqp=CAU',
      knobValueData: 0,
    }
  },

  methods: {
    // cMouseY - координаты по оси Y
    onChangeValue (cMouseY) {
      this.knobValueData = cMouseY
    },

  }
}
</script>

<style>
</style>
