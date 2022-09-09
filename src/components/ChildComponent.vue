<template>
  <div class="textChildComponent">
    Ce texte vient d'un composant importé.. - {{ msg }}
  </div>
</template>

<script>
export default {
    props: {
        msg: String
    }

}
</script>

<style>

</style>