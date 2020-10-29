<template>
  <div>
    <button @click="timezone = 0">Moscow</button>
    <button @click="timezone = 1">New-York</button>
      {{time}}
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      time: 'asdf',
      timezone: 0
    }
  },
  created () {
    setInterval(() => {
      axios.get(this.timezone ? 'https://worldtimeapi.org/api/timezone/America/New_York' : 'https://worldtimeapi.org/api/timezone/Europe/Moscow')
        .then(response => {
          this.time = response.data.datetime.substring(11, 19)
        })
    }, 1000)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
