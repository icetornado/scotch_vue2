<template>
  <div>
    <div class="col-sm-6">
    <div class="panel panel-default">
      <div class="panel-heading">
        <h3>Add an Event</h3>
      </div>
      <div class="panel-body">

        <div class="form-group">
          <input class="form-control" placeholder="Event Name" v-model="event.name">
        </div>

        <div class="form-group">
          <textarea class="form-control" placeholder="Event Description" v-model="event.description"></textarea>
        </div>

        <div class="form-group">
          <input type="date" class="form-control" placeholder="Date" v-model="event.date">
        </div>

        <button class="btn btn-primary" v-on:click="addEvent">Submit</button>
      </div>
    </div>
  </div>
    <div class="col-sm-6">
      <div class="list-group">

        <a href="#" class="list-group-item" v-for="(ev, index) in events">
          <h4 class="list-group-item-heading">
            <i class="glyphicon glyphicon-bullhorn"></i>
            {{ ev.name }}
          </h4>

          <h5>
            <i class="glyphicon glyphicon-calendar" v-if="ev.date"></i>
            {{ ev.date }}
          </h5>

          <p class="list-group-item-text" v-if="ev.description">{{ ev.description }}</p>

          <button class="btn btn-xs btn-danger" v-on:click="deleteEvent(index)">Delete</button>
        </a>

      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Events',
    data () {
      return {
        event: { name: '', description: '', date: '' },
        events: [
          {
            id: 1,
            name: 'TIFF',
            description: 'Toronto International Film Festival',
            date: '2015-09-10'
          },
          {
            id: 2,
            name: 'The Martian Premiere',
            description: 'The Martian comes to theatres.',
            date: '2015-10-02'
          },
          {
            id: 3,
            name: 'SXSW',
            description: 'Music, film and interactive festival in Austin, TX.',
            date: '2016-03-11'
          }
        ]}
    },
    methods: {
      addEvent () {
        if (this.event.name) {
          this.events.push(this.event)
          this.event = { name: '', description: '', date: '' }
        }
        console.log('big events', this.events)
      },
      deleteEvent (idx) {
        console.log('about to delete ' + idx)
        this.events.splice(idx - 1, 1)
        console.log('after events', this.events)
      }
    }
  }
</script>

<style scoped>

</style>
