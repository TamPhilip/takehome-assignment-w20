<template>
  <div class="counter">
    <p> Episodes seen: {{count}}</p>
    <button v-on:click="addIncrement">Add +1 </button>
    <button v-on:click="decreaseIncrement">Add -1 </button>
  </div>
</template>

<script>
import {eventBus} from "@/eventBus.js"
export default {
  props: {
    count: {
      Type: Number,
      default: 0
    },
    id: Number
  },
  methods: {
    addIncrement() {
      if(this.id === null) {
        eventBus.$emit("incrementCount", this.id);
      } else {
        this.count += 1;
      }
    },
    decreaseIncrement() {
      if(this.id === null) {
        eventBus.$emit("decreaseCount", this.id);
      } else {
        this.count -= 1;
      }      
    }
  },
};
</script>

<style scoped>
.counter {
  display: block;
}
</style>

