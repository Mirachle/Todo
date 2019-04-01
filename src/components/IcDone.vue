<template>
  <svg
    :class="allTime"
    @click="itemClicked()"
    :id="imagClass"
    width="15px"
    height="15px"
    viewBox="0 0 28 28"
    version="1.1"
    xmlns="http://www.w3.org/2000/svg"
    xmlns:xlink="http://www.w3.org/1999/xlink"
  >
    <g id="Symbols" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
      <g
        id="todo-item"
        transform="translate(-20.000000, -24.000000)"
        :fill="imagFill"
        fill-rule="nonzero"
      >
        <g id="ic-done" transform="translate(20.000000, 24.000000)">
          <path
            d="M14,0 C6.26875,0 0,6.26875 0,14 C0,21.73125 6.26875,28 14,28 C21.73125,28 28,21.73125 28,14 C28,6.26875 21.73125,0 14,0 Z M21.18125,9.31875 L12.4875,20.475 C12.41875,20.54375 12.30625,20.69375 12.16875,20.69375 C12.025,20.69375 11.93125,20.59375 11.85,20.5125 C11.76875,20.43125 6.91875,15.76875 6.91875,15.76875 L6.825,15.675 C6.7875,15.61875 6.75625,15.55 6.75625,15.475 C6.75625,15.4 6.7875,15.33125 6.825,15.275 C6.85,15.25 6.86875,15.23125 6.89375,15.2 C7.375,14.69375 8.35,13.66875 8.4125,13.60625 C8.49375,13.525 8.5625,13.41875 8.7125,13.41875 C8.86875,13.41875 8.96875,13.55 9.04375,13.625 C9.11875,13.7 11.85625,16.33125 11.85625,16.33125 L18.8125,7.39375 C18.875,7.34375 18.95,7.30625 19.03125,7.30625 C19.1125,7.30625 19.1875,7.3375 19.25,7.3875 L21.1625,8.89375 C21.2125,8.95625 21.24375,9.03125 21.24375,9.1125 C21.25,9.19375 21.21875,9.2625 21.18125,9.31875 Z"
            id="Shape"
          ></path>
        </g>
      </g>
    </g>
  </svg>
</template>

<script>
export default {
  name: "IcDone",
  props: ["item"],
  data() {
    return {
      imagClass: "pipe",
      imagFill: "#ADADAD"
    };
  },
  methods: {
    itemClicked() {
      if (this.item.isDone) {
        this.item.isDone = false;
      } else {
        this.item.isDone = true;
      }
     /*this.$emit("isDone", this.item.isDone); */
    }
  },
  computed: {
    allTime() {
      if (this.item.isDone) {
        this.imagFill = "#00FF00";
      } else {
        this.imagFill = "#ADADAD";
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#pipe {
  margin-right: 5px;
  position: relative;
  top: 1.5px;
  cursor: pointer;
}
</style>
