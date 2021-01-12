<template>
  <div class="vknob">
    <div class="vknob__wrap" :style="{backgroundImage:`url(${imgURL.knobSplitterUrl})`}">
      <div class="vknob__control"
        :style="{ backgroundImage:`url(${imgURL.knobControlUrl})`, transform: `rotate(${knobValue}deg)` }">
        Fggg
      </div>
    </div>
    <div class="vknob__lable">{{ lable }}</div>
  </div>
</template>

<script>
export default {
  name: "Vknob",

  props: {
    knobValue: {
      type: Number,
      required: true,
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
    lable: {
      type: String,
      // required: true,
    },
    imgURL: {
      // Ссылка на изображение регулятора
      knobControlUrl: String,
      // Ссылка на изображение делителей(указателей уровня)
      knobSplitterUrl: String,
    },

  },
};
</script>

<style></style>

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

