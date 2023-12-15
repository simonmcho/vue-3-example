<script>
export default {
  data() {
    return {
      count: 0,
      console: console,
      rawHtml: '<span style="color: red">This should be red.</span>',
      idKey: 'some-id',
      seen: false,
      toggleSeen: (e) => {
        // console.log(e)
        this.seen = !this.seen
      },
      testUrl: 'www.google.ca',
      onSubmit: () => {
        console.log("submission")
      },
      someObj: {
        nested: {
          value: 'init'
        },
        arr: ['nestedArrIndex0', 'nestedArrIndex1']
      }
    }
  },
  methods: {
    incrementCount() {
      // No this access using arrow functions
      this.count++
    },
    mutateSomeObj() {
      this.someObj.nested.value = 'second';
      this.someObj.arr[1] = 'newIndex1Value'
    }
  },
  mounted(e) {
    console.log({ e });
    console.log('mounted count: ', this.count);
    this.count = this.count++;
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
  <a :href="testUrl">LINK</a>
  <form @submit.prevent="onSubmit">
    <button type="submit">Submit!</button>
  </form>
  <div>
    <button type="button" @click="mutateSomeObj">Nested object click</button>
    <div>
      <span>nested obj value: {{  someObj.nested.value }}</span>
    </div>
    <div>
      <span>nested obj arr index 1: {{  someObj.arr[1] }}</span>
    </div>
  </div>
</template>