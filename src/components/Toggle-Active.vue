<template>
  <q-btn class="row" flat @click="switchStatus" rounded color="transparent">
    <div class="row" :style="style2">
      <span :style="style"></span>
    </div>
    <span class="text">
      {{ text }}
    </span>
  </q-btn>
</template>
<script>
export default {
  name: "ToggleActive",

  data() {
    return {
      style:
        "width: 6px;height: 6px;background: white;border-radius: 100%;position: relative;top: 2px;left: 10px ",
      text: "active",
      active: true,
      style2:"background: #014dfe;width: 18px;height: 10px;border-radius: 20px;"
    };
  },
  methods: {
    switchStatus() {
      this.active = !this.active;
      if (this.active) {
        this.text = "active";
        this.style2 = "background: #014dfe;width: 18px;height: 10px;border-radius: 20px;" ;
                this.style =
          "width: 6px;height: 6px;background: white;border-radius: 100%;position: relative;top: 2px;left: 10px ";
      } else {
        this.text = "inactivate";
         this.style2 = "background: #bb0129;width: 18px;height: 10px;border-radius: 20px;" ;
        this.style =
          "width: 6px;height: 6px;background: white;border-radius: 100%;position: relative;top: 2px;left: 2px ";
      }
      console.log("toggle :" + this.active);
    },
  },
};
</script>
<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Righteous&family=Rubik:wght@300&display=swap");

.text {
  text-transform: capitalize;
  font-family: "Rubik", sans-serif;
  font-weight: 600;
  padding-left: 10px;
  font-size: 13px;
  color: #6b7783;
}
</style>
