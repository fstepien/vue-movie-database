<template>
    <header>
    <router-link to="/">
        <h1>{{ title }}</h1>
            </router-link>
    </header>
</template>

<script>
export default {
    name: "Header",
    props: {
        title: String
    }
}
</script>

<style scoped>
header {
  background-color: #111;
  padding: 20px;
  color: white;
}
h1 {
  margin: 0;
}
</style>
