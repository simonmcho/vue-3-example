<script>
export default {
  data() {
    return {
      count: 0,
      console: console,
      rawHtml: '<span style="color: red">This should be red.</span>',
      idKey: 'some-id',
      seen: false,
      toggleSeen: () => {
        this.seen = !this.seen
      } 
    }
  }
}
</script>

<template>
  <button @click="count++">Click me for count: {{  count  }}{{  console.log({ count }) }}</button>
  <p>Using text interpolation: {{ rawHtml }}</p>
  <p>Using v-html directive: <span v-html="rawHtml"></span></p>
  <div v-bind:id="idKey">HELLO</div>
  <div>
    <button @click="toggleSeen">Click me to see/hide element below</button>
    <div v-if="seen">
      SEEN
    </div>
  </div>
</template>