<template>
    <div class="calculator">
      <div class="display">{{ display }}</div>
      <div class="keys">
        <button v-for="key in keys" :key="key" @click="handleClick(key)">
          {{ key }}
        </button>
      </div>
    </div>
  </template>
  
  <script lang="ts">
  import { Component, Vue } from 'vue-property-decorator';
  
  @Component
  export default class Calculator extends Vue {
    private display: string = '';

    // add calculator keys
    private keys: string[] = [
      'C', 'CE', '%', '/',
      '7', '8', '9', '*',
      '4', '5', '6', '-',
      '1', '2', '3', '+',
      '0', '.', '='
    ];
  
    // manage click event
    private handleClick(key: string): void {
      switch (key) {
        case 'C':
          this.display = '';
          break;
        case 'CE':
          this.display = this.display.slice(0, -1);
          break;
        case '=':
          this.display = eval(this.display);
          break;
        default:
          this.display += key;
          break;
      }
    }
  }
  </script>
  
  <style scoped>
  .calculator {
    max-width: 400px;
    margin: 0 auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.3);
  }
  
  .display {
    font-size: 2rem;
    margin-bottom: 10px;
    text-align: right;
    padding: 10px;
    background-color: #f8f8f8;
    border: 1px solid #ccc;
    border-radius: 5px;
  }
  
  .keys {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-gap: 10px;
  }
  
  button {
    font-size: 1.2rem;
    padding: 10px;
    border-radius: 5px;
    border: none;
    background-color: #f8f8f8;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.3);
    cursor: pointer;
  }
  
  button:active {
    transform: translateY(2px);
    box-shadow: none;
  }
  </style>
  