<template lang="pug">
  .home
    v-container.fill-height(fluid='')
      v-row(align='center', justify='center')
        v-col(cols='12', sm='8', md='6' lg='4')
          Card
</template>

<script>
// @ is an alias to /src
import Card from "@/components/Card.vue";

export default {
  name: "Home",
  components: {
    Card
  },
  data: () => ({
    tracks: [
      { text: "All", volume: 10, mix: "Master", callback: () => {} },
      { text: "Cow Bell", volume: 10, callback: () => {} },
      { text: "Wood Block", volume: 10, callback: () => {} },
      { text: "Tamborine", volume: 10, callback: () => {} }
    ],
    selected: null,
    playing: false,
    mixer: false
  }),
  methods: {
    setTrack() {
      for (let t in this.tracks)
        this.tracks[t].volume =
          this.selected === this.tracks[t].text ||
          this.selected === this.tracks[0].text
            ? 10
            : 0;
    }
  }
};
</script>
