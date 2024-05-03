<script>
export default {
  name: 'App',
  data() {
    return {
      greeting: 'Random!',
      inputText: '',
      isRed: false,
      isBold: false
    };
  },
  computed: {
    dynamicText() {
      return this.inputText !== '' ? 'Input: ' + this.inputText : 'Silakan ketik apa saja';
    }
  },
  methods: {
    updateGreeting() {
      this.greeting = 'Hai, ' + this.inputText + '😉';
      this.isRed = this.inputText.length > 5; // Jika panjang teks lebih dari 5 karakter, ubah warna menjadi biru
      this.isBold = this.inputText.length % 2 === 0; // Jika panjang teks genap, buat teks menjadi tebal
    }
  }
};
</script>

<template>
  <div id="app">
    <h1>{{ greeting }}</h1>
    
    <input type="text" v-model="inputText" @input="updateGreeting">
    
    <div :class="{ 'red-text': isRed }" :style="{ 'font-weight': isBold ? 'bold' : 'normal' }">
        {{ dynamicText }}
    </div>
  </div>
</template>

<style scoped>
#app {
  text-align: center;
  margin-top: 50px;
}

.red-text {
  color: rgb(35, 0, 163);
}
</style>
