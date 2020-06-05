<template lang="pug">
    v-card.elevation-12
        v-toolbar(color='deep-purple', dark='', flat='')
            v-toolbar-title Project Floyd
            v-spacer
            v-tooltip(bottom='')
            template(v-slot:activator='{ on }')
                v-btn(href='' icon large target='_blank' v-on='on' @click="mixer = !mixer")
                v-icon mdi-tune-vertical
            span Mix Tracks
            v-tooltip(bottom='')
            template(v-slot:activator='{ on }')
                v-btn(href='' icon large target='_blank' v-on='on')
                v-icon mdi-download
            span Save Offline
            v-tooltip(bottom='')
            template(v-slot:activator='{ on }')
                v-btn(href='' icon large target='_blank' v-on='on')
                v-icon mdi-help
            span Help
            v-tooltip(bottom='')
            template(v-slot:activator='{ on }')
                v-btn(href='' icon large target='_blank' v-on='on')
                v-icon mdi-github
            span Source
        v-card-text
            v-btn.sync-btn(height="200px" color="amber")
            v-icon(large) mdi-gesture-double-tap
            span Tap to Sync
            .vol-ctrls(v-if="mixer")
            v-divider
            h5 Mix Tracks
            v-slider(v-for="i in tracks" :value="i.volume"
                :key="i.text"
                :label="i.mix ? i.mix : i.text"
                prepend-icon="mdi-volume-medium"
                append-icon="mdi-volume-high"
                @click:prepend="i.volume--"
                @click:append="i.volume++"
                min="0"
                max="11"
                hide-details)
        v-card-actions
            v-overflow-btn.track-select(v-model="selected" @change="setTrack" :items="tracks" item-text="text" item-value="text" label="Pick a track" menu-props="top" hide-details)
            v-spacer
            v-btn.play-btn(@click="playing = !playing" :disabled="selected === null" fab color='light-green')
            v-icon {{ playing ? 'mdi-pause' : 'mdi-play' }}

</template>

<style lang="sass">
.sync-btn
    width: 100%
span
    font-size: 2.4rem
.vol-ctrls
    margin-top: 1rem
.track-select
    width: 100%
    margin: 1rem 2rem 0.5rem 0.5rem
.play-btn
    margin-right: 0.5rem
.v-card__text
    padding-bottom: 0
</style>
