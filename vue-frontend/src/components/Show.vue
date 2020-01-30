<template>
  <div class="show">
      {{this.name}}
      <Counter :count="this.episodesSeen" :id="id"/>
  </div>
</template>

<script>
import Counter from "./Counter";

export default {
  components: {
    Counter
  },
  props: {
    id: Number,
    name: String,
    episodesSeen: Number
  }
};
</script>

<style>
.show {
  margin-top: 2.4rem;
  margin-bottom: 2.4rem;
  background: lightcyan;
}
</style>
