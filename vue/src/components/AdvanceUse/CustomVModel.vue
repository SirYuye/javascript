<template>
  <div>
    <!-- 1. input 使用:value 而不是v-model 
         2. change和model.event要对应起来
         3. text属性对
    -->
    <input
      type="text"
      :value="text"
      @focus="$emit('focus')"
      @input="$emit('change', $event.target.value)"
    />
  </div>
</template>

<script>
export default {
  model: {
    prop: "text", //对应props text
    event: "change",
  },
  props: {
    text: {
      type: String,
      default() {
        return "";
      },
    },
  },
  data() {
    return {
      name: 'aa',
      f: function(e) {
        console.log(e);
      },
    };
  },
  mounted() {
    window.addEventListener("resize", this.f);
  },
  beforeDestroy() {
    // window.removeEventListener("resize", this.f);
  },
  destroyed() {
    console.log(this.name)
    window.removeEventListener("resize", this.f);
  },
};
</script>

<style></style>
