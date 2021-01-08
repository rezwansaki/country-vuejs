<template>
    <footer class="text-muted pt-5">
  <div class="container">
    <p class="text-center">
      {{ptextone}} <br>
      <small>{{ptexttwo}}</small>
    </p>
  </div>
</footer>
</template>

<script>
export default {
  data(){
    return {
      ptextone: "© Country 2021",
      ptexttwo: "Developed by Md. Rezwan Saki Alin. (Vue JS 3 - Practice Work)",
    }
  }
}
</script>