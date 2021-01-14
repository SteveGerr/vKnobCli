<template>
  <div class="vknob">
    <div class="vknob__label">{{ label }}</div>
    <div class="vknob__wrap"
      :style="{backgroundImage:`url('${knobSplitterUrl}}')`}"
      >
    </div>
    <div class="vknob__control-wrap" @mousemove="emitChange">
      <div class="vknob__control"
        :style="{ backgroundImage:`url('${knobControlUrl}')`, transform: `rotate(${knobValue}deg)` }">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Vknob",

  props: {
    knobValue: {
      type: Number,
      required: true,
      default: 0
    },
    // Метод управляющий значением
    changeValue: {
      type: Function,
      // required: true
    },
    min: {
      type: Number,
      // required: true,
    },
    max: {
      type: Number,
      // required: true,
    },
    // Шаги увеличения значения
    step: {
      type: Number,
      default: 0.5,
    },
    // Возможность деактивировать на некоторых инструментах или например в бесплатной версии
    disable: {
      type: Boolean,
      default: false
    },
    // НАзвание регулятора
    label: {
      type: String,
      // required: true,
    },
    // Ссылка на изображение регулятора
    knobControlUrl: {
      type: String,
      required: true
    },
    // Ссылка на изображение делителей(указателей уровня)
    knobSplitterUrl: {
      type: String,
      required: true
    },

  },

  methods: {
    // Эмитим событие наверх
    emitChange (e) {
      // Передаём координаты мыши
      this.$emit('changeValue', e);

    }
  }
};
</script>
<style scoped>

  .vknob {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    max-width: 300px;
    height: 300px;
    margin: 20% auto;
    position: relative;
  }
  .vknob__wrap {
    display: flex;
    width: 100%;
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    position: absolute;
    top: 0;
    right: 0;
    left: 0;
    bottom: 0;
  }
  .vknob__label {
    display: flex;
    justify-content: center;
    width: 100%;
    padding: 10px 0;
    font-size: 16px;
    color: #075cac;
    z-index: 1;
  }
  .vknob__control {
    display: flex;
    width: 200px;
    height: 200px;
    z-index: 1;
    background-size: cover;
    transition: all 1s ease-out;
  }
  .vknob__control-wrap {
    display: flex;
    width: 200px;
    height: 200px;
    border: 1px solid #ffffff;
    z-index: 2;
  }
</style>

<style scoped>
  /* TODO  */
  /* 1. В темплейте в разметку добавляем стандартный range или его аналоги. В данном
  случае из bootstrap-vue компонент b-form-input
  2. Прописываем пропсы
  3. name: 'Vknob', - задаём имя
  компоненту
  4. Прописываем все аргументы, события и директивы:
  - id="range-vknob" для связи с лейблом;
  - v-model="knobValue" с переданным пропсом knobValue
  - @change="changeValue" через событие change управляем регулятором
  - :min="min" :max="max" - минимальное и максимальное значение, значения передаём из пропсов
  - :step="step" - шаг, также подтягиваем из пропсов
  - disable - для включения/выключения регулятора
  - lable - название регулятора. Может быть также, например звук, хор, тональность и т.д.

  5. Добавляем в разметку изображения регулятора и в пути указываем пропсы, например регулятора imgURL.knobControlUrl

  6. Используем компонент внутри родительского:
  - прописываем внутри компонента атрибуты пропсов
  - передаём в них необходимые значения
  - Пишем метод, управляющий регулятором и передаём его в changeValue
  - Передаём ссылки на изображения

  Дополнено!!!
  - Увеличиваем значение knobValue, используя метод родителя, например onChangeKnobValue, передав его в качестве аргумента.
  - Сохраняем текущее значение
  - Передаём текущее значение на сервер
  - Получаем текущее значение
  - поварачиваем изображение регулятора в зависимости от knobValue
  - Кликаем по регулятору vknob__control, запускается обработчик на событие mousedown:
    - тянем вверх/вниз, отслеживаем координаты Y, если больше нуля, увеличиваем knobValue на шаг step, если уменьшается, уменьшаем
   */
</style>

