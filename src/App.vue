<template>
  <div class="max-w-lg mx-auto py-20">
    <StudentItem v-for="(student, idx) in students" :key="idx" class="mb-4" :name="student.name" v-model:age="student.age" :image="student.image" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import StudentItem from './StudentItem.vue'

export default defineComponent({

  components: {
    StudentItem
  },

  data () {
    const students = [
      {
        name: "Maxime",
        age: "1000",
        image: "/img/maxime.png"
      },
      {
        name: "Vladimir",
        age: "1000000",
        image: "/img/vladimir.jpeg"
      }
    ]
    
    return {
      students
    }
  }
})
</script>

<style>
</style>
