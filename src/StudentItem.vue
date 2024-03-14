<template>
  <div class="flex items-center gap-2">
    <div :class="`border ${imageStyle} rounded-full w-16 h-16 flex items-center justify-center transition-colors`">
      <div :class="`bg-gray-300 rounded-full w-14 h-14 bg-no-repeat bg-center bg-cover`" :style="bgImage">
      </div>
    </div>
    <div>
      <label :class="`koulen-regular uppercase transition-colors ${labelStyle}`" for="hours-old">{{ name }} is</label>
      <div class="flex gap-2">
        <span class="relative">
          <span class="px-3 inline-block min-w-[72px]" aria-hidden="true">{{ age }}</span>
          <input
            name="hours-old"
            id="hours-old"
            class="absolute w-full start-0 px-1 border-gray-300 hover:border-purple-500 focus:border-purple-700 border outline-0 rounded-md transition-colors"
            :value="age"
            @input="$emit('update:age', ($event.target as HTMLInputElement).value)"
            @focus="isFocused = true"
            @blur="isFocused = false"
            v-number="ageFormat"
            type="text"
          >
        </span>
        <div class="text">hours old</div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import { directive as VNumber } from '@coders-tm/vue-number-format'

export default defineComponent({
  directives: {
    number: VNumber,
  },

  props: {
    name: { type: String, required: true },
    age: { type: String },
    image: { type: String },
  },

  emits: ['update:age'],

  data () {
    return {
      ageFormat: {
        separator: ' ',
      },
      isFocused: false,
    }
  },

  computed: {
    labelStyle () {
      if (this.isFocused) {
        return 'text-purple-700'
      }
      return 'text-black'
    },

    imageStyle () {
      if (this.isFocused) {
        return 'border-purple-700'
      }
      return 'border-transparent'
    },

    bgImage () {
      return `background-image: url("${this.image}")`
    }
  },
})
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Koulen&display=swap');

.koulen-regular {
  font-family: "Koulen", sans-serif;
  font-weight: 400;
  font-style: normal;
}
</style>