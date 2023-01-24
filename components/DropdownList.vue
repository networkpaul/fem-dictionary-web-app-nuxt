<template>
  <div class="font-choice">
    <div @click="show = !show" class="font-choiceArrow" :class="selectedClass">{{ selected }}</div>
    <div v-if="show" class="font-dropdownList">
      <div v-for="option in options" :key="option.id" :class="option.className" @click="select(option.font, option.className)">
        {{ option.font }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      options: [
        {
          "font": "Sans Serif",
          "className": "sansSerif",
          "id": "1"
        },
        {
          "font": "Serif",
          "className": "serif",
          "id": "2"
        },
        {
          "font": "Mono",
          "className": "mono",
          "id": "3"
        }
      ],
      show: false,
      selected: 'Sans Serif',
      selectedClass: '',
    }
  },
  methods: {
    select(font, className) {
      this.selected = font
      this.selectedClass = className
      this.show = false
    }
  }
}
</script>