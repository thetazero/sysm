<template>
  <div class="centered">
    <div class="usage">{{usage}}</div>
  </div>
</template>

<script>
import SystemInformation from "./LandingPage/SystemInformation";
import { setInterval } from "timers";
let usage = require("os-usage");
let cpuMonitor;
export default {
  name: "landing-page",
  components: { SystemInformation },
  data() {
    return {
      usage: process.getCPUUsage().percentCPUUsage
    };
  },
  methods: {
    open(link) {
      this.$electron.shell.openExternal(link);
    }
  },
  created() {
    console.log(usage);
    cpuMonitor = new usage.CpuMonitor();
    cpuMonitor.on("cpuUsage", data => {
      console.log(data);
      this.usage = Math.round((data.user - -data.sys) * 100) / 100 + "%";
      console.log(data);

      // { user: '9.33', sys: '56.0', idle: '34.66' }
    });
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Source+Sans+Pro");
body {
  font-family: "Source Sans Pro", sans-serif;
}
* {
  color: #ccc;
}
.centered {
  position: absolute;
  text-align: center;
  position: fixed; /* or absolute */
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 1.4em;
}
.usage {
  font-size: 2.4em;
}
</style>
