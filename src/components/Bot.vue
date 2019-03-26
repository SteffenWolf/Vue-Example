<template>
  <section>
    <h3>{{botObj.botName}}</h3>
    <p>{{botObj.attackVal}}</p>
    <p>{{botObj.healthVal}}</p>
    <button>Select</button>
    <button>Retire</button>


  </section>

</template>

<script>
export default {
  props: ['botObj']
}
</script>