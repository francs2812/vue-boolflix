<template>
  <section>
            <h1> {{ title }} </h1>
            <h1> {{ originalTitle }} </h1>
            <h1> {{ originalLanguage }} </h1>
            <h1> {{ voteAverage }} </h1>
  </section>
</template>

<script>
export default {
    name:"Card",
    props: {
        "title": String,
        "originalTitle":String,
        "originalLanguage":String,
        "voteAverage":String

    }
}
</script>

<style>

</style>