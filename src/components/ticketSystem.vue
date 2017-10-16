<template>
  <div class="container" id="app">
    <form>
      <div
        class="row justify-content-center"
        v-for="(attendee, index) in attendees"
        :key="index"
      >
        <div class="col-sm-3">
          <div class="form-group">
            <label class="sr-only">Name</label>
            <input
              class="form-control"
              aria-describedby="emailHelp"
              placeholder="Enter name"
              v-model="attendee.name"
              name="attendees[][name]"
              required
            >
          </div>
        </div>
        <div class="col-sm-2 text-left">
          <button type="button" class="btn btn-light">
            <span aria-hidden="true">×</span> Remove</button>
        </div>
      </div>
      <div class="row justify-content-center">
        <div class="col-sm-6"></div>
        <div class="col-sm-2">
          <button type="button" class="btn btn-secondary" @click.prevent="addAttendee">Add</button>
        </div>
      </div>
      <hr>
      <div class="row justify-content-center">
        <div class="col-sm-6">
          <span class="unit-price">£{{ cost }}</span>
        </div>
        <div class="col-sm-2 text-left">
          <button type="submit" class="btn btn-primary">Pay £{{ checkoutTotal }}</button>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'TicketSystem',
  data () {
    return {
      attendees: [{ name: '' }],
      cost: 9.99
    }
  },
  computed: {
    quantity: function () {
      return this.attendees.length
    },
    checkoutTotal: function () {
      return this.cost * this.quantity
    }
  },
  methods: {
    addAttendee: function (event) {
      event.preventDefault()
      this.attendees.push({
        name: ''
      })
    }
  }
}
</script>
