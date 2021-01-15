/* eslint-disable no-unused-vars */
<template>
  <div id="app">
    <Vknob
      :label="vknobLable"
      :knobValue="knobValueDeg"
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
      controlLink: '',
      splitterLink: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQIzN9ZAPlkO_nV9FePzUo1u9vzHovk9vTQQw&usqp=CAU',
      knobValueData: 0,
      knobValueDeg: 0,
    }
  },

  methods: {
    onChangeValue (cMouse) {
      const { offsetY, offsetX } = cMouse;
      console.log(offsetY, offsetX);

      // ЗАписываем предыдущее значение
      let prevVal = this.knobValueData;
      // Записываем текущее значение
      let currVal = offsetY
      // Присваиваем текущее значение в дату преобразуя в градусы
      this.knobValueData = offsetY

      // console.log("prevVal", prevVal);
      // console.log("currVal", currVal);
      console.log(this.knobValueDeg);

      // Ежели предыдущее значение меньше чем текущее
      if (prevVal < currVal) {
        this.knobValueDeg+=3;
      console.log("after", this.knobValueDeg);

        if (this.knobValueDeg < 0) {
          this.knobValueDeg = 0
        }
      }
      if (prevVal > currVal) {
        this.knobValueDeg-=3;
        if (this.knobValueDeg > 360) {
          this.knobValueDeg = 360
        }
      }

    },

  }
}
</script>

<style>
</style>
