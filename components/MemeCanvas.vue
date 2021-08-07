<template>
  <canvas id="sbobImage" width="50" height="100" class="border border-3">
    Meme with SpongeBob, titled with the text {{ message }}
  </canvas>
</template>

<script>
export default {
  props: {
    message: {
      type: String,
      default: ''
    }
  }
}
</script>
