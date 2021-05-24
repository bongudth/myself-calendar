<template>
  <div id="app">
    <CalendarWeek />
    <CalendarEntry />
  </div>
</template>

<script>
import CalendarWeek from "./components/CalendarWeek";
import CalendarEntry from "./components/CalendarEntry";

export default {
  name: "App",
  components: {
    CalendarWeek,
    CalendarEntry,
  },
};
</script>

<style scoped>
#app {
  background-color: #ffffff;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 100px;
}
</style>
