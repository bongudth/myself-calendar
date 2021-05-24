<template>
  <div class="day" @click="setActiveDay(day.id)">
    <div class="day-banner has-text-centered">{{ day.abbvTitle }}</div>
    <div class="day-details">
      <div class="day-number">{{ day.id }}</div>
      <CalendarEvent
        v-for="(event, index) in day.events"
        :key="index"
        :event="event"
        :day="day"
      />
    </div>
  </div>
</template>

<script>
import { store } from "../store";
import CalendarEvent from "./CalendarEvent";

export default {
  name: "CalendarDay",
  props: ["day"],
  methods: {
    setActiveDay(dayId) {
      store.setActiveDay(dayId);
    },
  },
  components: {
    CalendarEvent,
  },
};
</script>

<style>
:root {
  --day-background: #ffabc3;
  --day-text: #ff5072;
  --details-background: #fff4f5;
  --border: #a5606c;
  --highlight: #ff8099;
}

.day {
  background-color: var(--details-background);
  color: var(--day-text);
  border-top: 1px solid var(--border);
  border-left: 1px solid var(--border);
  border-bottom: 1px solid var(--border);
  font-size: 12px;
  cursor: pointer;
}

.day:hover {
  background: var(--highlight);
}

.day:last-child {
  border-right: 1px solid var(--border);
}

.day-banner {
  background-color: var(--day-background);
  color: var(--day-text);
  padding: 10px;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-size: 14px;
  font-weight: 600;
}

.day-details {
  padding: 10px;
}
</style>