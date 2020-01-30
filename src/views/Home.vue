<template>
  <div class="hello">
    <CardFront />
    <CardForm />
  </div>
</template>

<script>
import CardForm from "../components/CardForm.vue";
import CardFront from "../components/CardFront.vue";

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
