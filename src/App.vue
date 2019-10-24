<template>
  <drawer></drawer>
</template>

<script>
import { version } from "ant-design-vue/es";
import Drawer from "./components/Drawer";
export default {
  name: "App",
  data() {
    return {
      version
    };
  },
  components: { Drawer }
};
</script>

<style></style>
