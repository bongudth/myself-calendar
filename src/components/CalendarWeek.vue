<template>
  <div id="calendar-week" class="container">
    <div class="columns is-mobile">
      <CalendarDay
        class="column"
        v-for="day in sharedState.seedData"
        :key="day.id"
        :day="day"
      />
    </div>
  </div>
</template>

<script>
import { store } from "../store";
import CalendarDay from "./CalendarDay";

export default {
  name: "CalendarWeek",
  data() {
    return {
      sharedState: store.state,
    };
  },
  components: {
    CalendarDay,
  },
};
</script>

<style scoped>
#calendar-week {
  margin-bottom: 50px;
}
</style>
