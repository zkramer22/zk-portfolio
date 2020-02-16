<template lang="html">
  <section id="portfolio">
    <div class="container">
      <h2>~ projects ~</h2>
    </div>
    <div id="projects">
      <Project v-for="project in projects" v-bind:key="project.id" :project="project"/>
    </div>

  </section>
</template>

<script>
import Project from './Project.vue'
export default {
  name: 'Portfolio',
  components: { Project },
  props: [],
  methods: {},
  data: () => ({
    projects: [
      {
        id: 0,
        name: 'Spotifly',
        description: 'music player web app with Spotify-inspired UX design',
        images: [
          { id: 0, name: 'spotifly-home.png' },
          { id: 1, name: 'spotifly-playlist.png' },
          { id: 2, name: 'spotifly-search.png' },
          { id: 3, name: 'spotifly-albums.png' }
        ],
        github: 'https://github.com/zkramer22/spotifly',
        liveSite: 'http://spotifly.site',
        arrows: true,
        gif: false
      },
      {
        id: 1,
        name: 'Zenscillator',
        description: 'javascript-powered synthesizer & visualizer',
        images: [
          { id: 0, name: 'zenscillator-0.png' },
          { id: 1, name: 'zenscillator-1.png' },
          // 'zen-linear-720.gif',
        ],
        github: 'https://github.com/zkramer22/zenscillator',
        liveSite: 'http://zenscillator.site',
        arrows: true,
        gif: false
      },
      {
        id: 2,
        name: 'Legend Biotech',
        description: 'landing page for worldwide biotech company making innovations in oncology pharmaceuticals',
        images: [
          { id: 0, name: 'legend-home.png' },
          { id: 1, name: 'legend-diagram.png'}
        ],
        // github: 'https://github.com',
        liveSite: 'http://legendbiotech.com',
        arrows: true,
        gif: false
      },
      {
        id: 3,
        name: 'Celgene: AML Disease Education',
        description: 'landing page for healthcare practitioners to learn more about Acute Myeloid Leukemia',
        images: [
          { id: 0, name: 'aml-relapse.png' }
        ],
        // github: '',
        liveSite: 'http://understandingamlrelapse-stg.navicorner.com/',
        arrows: false,
        gif: false
      },
      {
        id: 4,
        name: 'Drag & drop game',
        description: 'mini-game utilizing drag & drop functionality, matching acronyms and phrases',
        images: [
          { id: 0, name: 'dragdrop-game.png' }
        ],
        gifs: [
          { id: 0, name: 'dragdrop-720.gif' }
        ],
        github: 'https://github.com/zkramer22/dragdrop-game',
        liveSite: 'https://zkramer22.github.io/dragdrop-game/',
        arrows: false,
        gif: true
      },
      {
        id: 5,
        name: 'Memory game',
        description: 'mini-game for memory testing purposes, matching letters to phrases',
        images: [
          { id: 0, name: 'memory-game.png' }
        ],
        gifs: [
          { id: 0, name: 'memory-game-720.gif' }
        ],
        github: 'https://github.com/zkramer22/memory-game',
        liveSite: 'https://zkramer22.github.io/memory-game/',
        arrows: false,
        gif: true
      },
      {
        id: 6,
        name: 'Data Dashboard',
        description: 'Python / React.JS powered interface for analyzing data spikes. Example data is ~100k lines of mock music streaming data.',
        images: [
          { id: 0, name: 'stream-data.png' }
        ],
        github: 'https://github.com/zkramer22/streamingDataDashboard/',
        liveSite: 'https://zkramer22.github.io/streamingDataDashboard/',
        arrows: false,
        gif: false
      },
    ]
  })
}
</script>

<style lang="scss" scoped>
  section {
    user-select: none;
    $grad2: #f8f9e3;
    background-color: rgba(216,216,216,0.9);
    z-index: 3;
    padding: 10px 0 0 0;
    .container {
      padding: 1px 0;
    }
  }
</style>
