<script setup>
import { reactive } from 'vue';
//import HelloWorld from './components/HelloWorld.vue'

const estado = reactive({
  numero1: 0,
  numero2: 0,
  resultado: 0,
  operador: 'somar',
})

function getNumber1(evento) {
  estado.numero1 = evento.target.value;
  estado.numero1 = parseFloat(estado.numero1)
  getOperacao();
}

function getNumber2(evento) {
  estado.numero2 = evento.target.value;
  estado.numero2 = parseFloat(estado.numero2)
  getOperacao();
}

function getOperador(evento) {
  estado.operador = evento.target.value;
  getOperacao();
}

const getOperacao = () => {
  switch(estado.operador) {
    case 'subtrair':
      return estado.resultado = (estado.numero1 - estado.numero2);
    case 'somar':
      return estado.resultado = (estado.numero1 + estado.numero2);
    case 'dividir':
      return estado.resultado = (estado.numero1 / estado.numero2);
    case 'multiplicar':
      return estado.resultado = (estado.numero1 * estado.numero2);
  }
}
</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-dark rounded-4 text-center">
        <h1>Calculadora aritmética</h1>
        <p>Realize cálculos de maneira simples e rápida.</p>
    </header>
    <form class="text-center">
      <div class="row">
        <div class="col">
          <input required type="number" placeholder="0" class="form-control mb-4" @keyup="getNumber1"/> 
        </div>
        <div class="col-md-2 mb-4">
          <select class="form-control" @change="getOperador">
            <option class="subtrair text-center" value="subtrair">-</option>
            <option class="somar text-center" selected value="somar">+</option>
            <option class="dividir text-center" value="dividir">/</option>
            <option class="multiplicar text-center" value="multiplicar">x</option>
          </select>
        </div>
        <div class="col">
          <input required type="number" placeholder="0" class="form-control mb-4" @keyup="getNumber2"/>
        </div>
      </div>
      <div class="row">
        <div class="col">
          <h3 class="black-text">Resultado</h3>
        </div>>
      </div>
      <div class="row">
        <div class="col">
          <h2 class="black-text fs-1 fw-bold">{{ estado.resultado }}</h2>
        </div>>
      </div>
    </form>
    <footer class="text-center">
        <div>
            <ul class="list-unstyled d-flex justify-content-center align-items-center fs-3 mt-5">
                <li>
                    <a href="https://www.linkedin.com/in/guilherme-ferreira-camargo/">
                        <i class="bi bi-linkedin black-text pe-4"></i>
                    </a>
                </li>
                <li>
                    <a href="https://github.com/guicamargo19">
                        <i class="bi bi-github black-text pe-3"></i>
                    </a>
                </li>
            </ul>
            <p class="text-black">
                ® 2024 Guilherme Camargo. Todos os direitos reservados.
            </p>
            <p class="text-black">
                Página desenvolvida no curso de Full Stack Python na EBAC - Escola Britânica de Artes Criativas e Tecnologia.              
            </p>
        </div>
    </footer>
  </div>
</template>

<style scoped>
.container {
  max-width: 640px;
  width: 100%;
  color: #fff;
}
.black-text {
  color: #000;
}

input[type=number]::-webkit-inner-spin-button,
input[type=number]::-webkit-outer-spin-button {
        -webkit-appearance: none;
        margin: 0;
}
</style>
