<template>
<h1>{{ msg }}</h1>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  props: {
    bystander: { type: String, required: false },  // (Mere an innocent bystander)
    msg: {
      type: String,
      default: '[msg]',
      validator: (x: string) => x.length !== 0   // 1. Remove this validator
    },
    size: {
      type: Number,
      validator: function (x: number) { return x <= 100 }   // and this validator
    },
  },
  data () {
    return {
      numData: 111
    }
  },
  computed: {
    computedNumData (): string { return this.numData + '' },
    computedSize (): string { return this.size + '' },
    computedBystander (): string { return this.bystander + '' },
  },
  methods: {
    onClick () {
      window.alert(this.msg)
      window.alert(this.bystander)
    },
  },
  setup (props, ctx) { return {} }   // 2. Or remove this setup(props)
});
</script>

