<template>
  <div class="kalkulator-container">
    <h1>Kalkulator Sederhana</h1>

    <div class="form-bagian">
      <input type="number" v-model.number="bilangan1" placeholder="Bilangan 1" />
      <input type="number" v-model.number="bilangan2" placeholder="Bilangan 2" />
    </div>

    <div class="hasil-bagian">
      <label>Hasil:</label>
      <input type="text" :value="hasil" readonly class="hasil-input" />
    </div>

    <div class="operasi-bagian">
      <button @click="setOperasi('tambah')">+</button>
      <button @click="setOperasi('kurang')">-</button>
      <button @click="setOperasi('kali')">×</button>
      <button @click="setOperasi('bagi')">÷</button>
    </div>

    <button @click="hitung">Hitung</button>
  </div>
</template>

<script>
export default {
  data() {
    return { bilangan1: 0, bilangan2: 0, hasil: 0, operasi: null };
  },
  methods: {
    setOperasi(op) { this.operasi = op; },
    hitung() {
      this.hasil = this.operasi === 'tambah' ? this.bilangan1 + this.bilangan2 :
                   this.operasi === 'kurang' ? this.bilangan1 - this.bilangan2 :
                   this.operasi === 'kali' ? this.bilangan1 * this.bilangan2 :
                   this.operasi === 'bagi' ? (this.bilangan2 !== 0 ? this.bilangan1 / this.bilangan2 : 'Tidak terdefinisi') :
                   'Pilih operasi';
    }
  }
};
</script>

<style scoped>
.kalkulator-container {
  max-width: 400px;
  margin: 100px auto;
  padding: 20px;
  background: #000000;
  border: 1px solid #ddd;
  border-radius: 8px;
  text-align: center;
}
input {
  width: calc(50% - 10px);
  padding: 10px;
  margin: 10px 5px;
  border: 1px solid #ccc;
  border-radius: 5px;
}
.hasil-input {
  color: black; /* Warna hasil menjadi hitam */
}
button {
  padding: 10px;
  margin: 5px;
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
button:hover {
  background-color: #369970;
}
</style>
