<template>
  <div>
    <h1>StringBob</h1>
    <p>Backstory: I had never made an NPM package before, so I decided to start small. And who doesn't enjoy SpongeBob, internet wit, and sarcasm? Input a string in the field below to see it's spongey, sarcastic equivalent.</p>
    <p>Interested in the NPM package? <a href="https://www.npmjs.com/package/stringbob">Check it out!</a></p>
    <label for="bobInput">Make your text sarcastic</label>
    <input id="bobInput" v-model="message" type="text">
    <code>{{ bobString }}</code>
    <button @click="copyToClipboard(bobString)">
      Copy to clipboard
    </button>
    <MemeCanvas :message="bobString" />

    <p>Resource: <a href="https://medium.com/@scottmatthew/using-html-canvas-with-vue-js-493e5ae60887">Scott Cook's article on building a rectangle in canvas</a></p>
  </div>
</template>

<script>
import { stringbobify } from 'stringbob'
import copy from 'copy-to-clipboard'
import MemeCanvas from '~/components/MemeCanvas.vue'
export default {
  components: {
    MemeCanvas
  },
  data () {
    return {
      message: 'Oh, really?!'
    }
  },
  computed: {
    bobString () {
      return stringbobify(this.message)
    }
  },
  methods: {
    copyToClipboard (stuffToCopy) {
      copy(stuffToCopy, {
        message: 'Press #{key} to copy',
        format: 'text/plain'
      })
    }
  }
}
</script>
