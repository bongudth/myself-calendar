<template>
  <div class="day-event" :style="getEventBackgroundColor">
    <div v-if="!event.edit">
      <span class="has-text-centered details">{{ event.details }}</span>
      <div class="has-text-centered icons">
        <i class="fas fa-pen" @click="editEvent(day.id, event.details)"></i>
        <i
          class="fas fa-trash-alt"
          @click="deleteEvent(day.id, event.details)"
        ></i>
      </div>
    </div>
    <div v-if="event.edit">
      <input
        type="text"
        :placeholder="event.details"
        v-model="newEventDetails"
      />
      <div class="has-text-centered icons">
        <i
          class="fas fa-check"
          @click="updateEvent(day.id, event.details, newEventDetails)"
        ></i>
      </div>
    </div>
  </div>
</template>

<script>
import { store } from "../store";

export default {
  name: "CalendarEvent",
  props: ["event", "day"],
  data() {
    return {
      newEventDetails: "",
    };
  },
  computed: {
    getEventBackgroundColor() {
      const colors = ["#D8C0CC", "#E5C5BB", "#C6ACAF"];
      let randomColor = colors[Math.floor(Math.random() * colors.length)];
      return `background-color: ${randomColor}`;
    },
  },
  methods: {
    editEvent(dayId, eventDetails) {
      store.editEvent(dayId, eventDetails);
    },
    updateEvent(dayId, originalEventDetails, updatedEventDetails) {
      if (updatedEventDetails === "")
        updatedEventDetails = originalEventDetails;
      store.updateEvent(dayId, originalEventDetails, updatedEventDetails);
      this.newEventDetails = "";
    },
    deleteEvent(dayId, eventDetails) {
      store.deleteEvent(dayId, eventDetails);
    },
  },
};
</script>

<style>
:root {
  --event-text: #000000;
  --border: #a5606c;
}
.day-event {
  color: var(--event-text);
  margin-top: 6px;
  margin-bottom: 6px;
  display: block;
  padding: 5px;
}

.details {
  display: block;
}

.icons .fas {
  padding: 0 5px;
}

input {
  background: none;
  width: 100%;
  border: 0;
  border-bottom: 1px solid var(--border);
}

input:focus {
  outline: none;
}
</style>