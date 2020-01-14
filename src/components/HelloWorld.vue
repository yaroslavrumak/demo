<template>
  <div class="hello">
    <CardFront />
    <CardForm />
  </div>
</template>

<script>
import CardForm from "./CardForm.vue";
import CardFront from "./CardFront.vue";

export default {
  name: "HelloWorld",
  components: {
    CardFront,
    CardForm
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
