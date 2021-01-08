<template>
<div class="album py-5 bg-light">
    <section class="py-5 text-center container">
      <h1 class="fw-light">{{albumexample}}</h1>
        <p class="lead text-muted">{{leadtext}}</p>
  </section>
   </div>
</template>

<script>
export default {
  data(){
    return {
      albumexample: "Country",
      leadtext: "This information comes from the Web API."
    }
  }
}
</script>