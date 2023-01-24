<template>
  <div class="theme-toggle">
    <div class="theme-slider">
      <label class="switch">
        <input type="checkbox" v-model="isChecked" @click="changeMoonColor">
        <span class="slider round"></span>
      </label>
    </div>
    <div class="theme-id">
      <svg class="theme-icon" xmlns="http://www.w3.org/2000/svg" width="22" height="22" viewBox="0 0 22 22"><path fill="none" :stroke="moonColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M1 10.449a10.544 10.544 0 0 0 19.993 4.686C11.544 15.135 6.858 10.448 6.858 1A10.545 10.545 0 0 0 1 10.449Z"/></svg>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isChecked: false,
      moonColor: "#757575"
    }
  },
  methods: {
    changeMoonColor() {
      if (this.isChecked === true) {
        this.moonColor = "#757575"
      } else {
        this.moonColor = "#A445ED"
      }
    }
  }
}
</script>