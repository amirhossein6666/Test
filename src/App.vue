<template>
  <input type="text" ref="name">
  <button @click="addClass">add class</button>
  <button @click="removeClass">remove class</button>
  <button @click.shift="shwoTempOnly">show the temp contains (shift)</button>
  <button @click="showSecondTemp">create another temp</button>
  <button @click="changeShowTeleportContains"> show/hide teleport</button>
  <div v-if="showTemp">
    <Temp  theme = "sale"  @close="changeTempShow">
      <template v-slot:links>
        <p>using slot for pass links</p>
        <a href="https://github.com/">github</a>
        <a href="https://github.com/amirhossein6666">my github> </a>
      </template>
        <p>its a without name slot</p>
      </Temp>
  </div>
  <div v-if="ShowSecondTemp">
    <Temp @close=changeSecondTempShow>
      <p>second Temp with slots</p>
      <template v-slot:image>
        <img src="./assets/images/download.png" alt="ying yong">
        <img src="./assets/images/download.jpeg" alt="Soghrat">
      </template>
    </Temp>
  </div>
  <teleport to=".teleport" v-if="ShowTeleport">
    <!-- this section teleport to index.html -->
    <p>use teleport</p>
  </teleport>
</template>

<script>
import Temp from './components/Temp.vue'
export default {
  name: 'App',
  components: {
    Temp
  },
  data() {
    return {
      title : "amir",
      showTemp : false,
      ShowSecondTemp : false,
      ShowTeleport : false
    }
  },
  methods : {
    addClass() {
      this.$refs.name.classList.add('active')
      console.log(this.$refs.name)
    },
    removeClass() {
      this.$refs.name.classList.remove('active')
      console.log(this.$refs.name)
    },
    changeTempShow() {
      this.showTemp = !this.showTemp
    },
    shwoTempOnly() {
      this.showTemp = true
    },
    showSecondTemp() {
      this.ShowSecondTemp = true
    },
    changeSecondTempShow() {
      this.ShowSecondTemp = !this.ShowSecondTemp
    },
    changeShowTeleportContains() {
      this.ShowTeleport = !this.ShowTeleport
    }
  }
  }

</script>