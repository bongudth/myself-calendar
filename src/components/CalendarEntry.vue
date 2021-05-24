<template>
  <div id="calendar-entry">
    <div class="calendar-entry-note">
      <input
        type="text"
        placeholder="New Event"
        v-model="inputEntry"
        required
      />
      <p style="color: red; font-size: 13px" v-if="error">
        You must type something first!
      </p>
      <p class="calendar-entry-day">
        Day of event: <span class="bold">{{ titleOfActiveDay }}</span>
      </p>
      <a
        class="button is-small is-danger is-light is-outlined"
        @click="submitEvent(inputEntry)"
        >Submit</a
      >
    </div>
  </div>
</template>

<script>
import { store } from "../store";

export default {
  name: "CalendarEntry",
  data() {
    return {
      inputEntry: "",
      error: false,
    };
  },
  computed: {
    titleOfActiveDay() {
      return store.getActiveDay().fullTitle;
    },
  },
  methods: {
    submitEvent(eventDetails) {
      if (eventDetails === "") return (this.error = true);
      store.submitEvent(eventDetails);
      this.inputEntry = "";
      this.error = false;
    },
  },
};
</script>

<style scoped>
#calendar-entry {
  background-color: #fff4f5;
  border: 1px solid #a5606c;
  padding: 10px;
}

.calendar-entry-note {
  text-align: center;
}

.button {
  color: #a5606c;
}
</style>
