<template>
  <div id="app">
    <img src="./assets/logo.png">
    <ticket-system/>
  </div>
</template>

<script>
import TicketSystem from './components/ticketSystem'

export default {
  name: 'app',
  components: {
    TicketSystem
  }
}
</script>
