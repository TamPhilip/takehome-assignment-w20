<template>
  <div>
    <Instructions :complete="true"/>
    <Show
      v-for="show in shows"
      :key="show.id"
      :id="show.id"
      :name="show.name"
      :episodesSeen="show.episodesSeen"
    />
    <Input/>
  </div>
</template>

<script>
import Instructions from "./Instructions.vue";
import Show from "./Show.vue";
import Input from "./Input.vue"
import {eventBus} from "@/eventBus.js";

export default {
  components: {
    Instructions,
    Show,
    Input
  },
  data() {
    return {
      shows: [
        { id: 1, name: "Game of Thrones", episodesSeen: 0 },
        { id: 2, name: "Naruto", episodesSeen: 220 },
        { id: 3, name: "Black Mirror", episodesSeen: 3 }
      ]
    };
  },
  created() {
    eventBus.$on("incrementCount", (id) => {
      this.shows[id-1].episodesSeen += 1;
    });
    eventBus.$on("decreaseCount", (id) => {
      this.shows[id-1].episodesSeen -= 1;
    });
    eventBus.$on("createShow", (showName) => {
      const show = {
        id: this.shows.length + 1,
        name: showName,
        episodesSeen: 0
      }
      this.shows.push(show);
    })
  },
  beforeDestroy() {
    eventBus.$off("incrementCount");
    eventBus.$off("decreaseCount");
    eventBus.$off("createShow");
  },
};
</script>

<style scoped>

</style>


