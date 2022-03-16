<template>
    <div id="app">
        <h1>Pesquisa de Desenvolvedores</h1>
        <div class="cabecalho">
            <div>
                <label for="name">Por nome:</label>
                <input class="search" id="name" placeholder="Digite aqui...">
            </div>
            <div class="filtros">
                <div class="opcao">
                    <label>Por linguagem:</label>
                    <input type="radio" name="opcao" value="e">E
                    <input type="radio" name="opcao" value="ou">Ou
                </div>
                <div class="linguagens">
                    <div>
                        <input type="checkbox" name="linguagem" value="java">java
                        <input type="checkbox" name="linguagem" value="javascript">javascript
                    </div>
                    <div>
                        <input type="checkbox" name="linguagem" value="php">PHP
                        <input type="checkbox" name="linguagem" value="python">Python
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
  padding:20px;
}
label {
    font-weight: bold;
}
.cabecalho {
    display: grid;
    grid-template-columns: 70% 30%;
}
.opcao {
    display:block;
}
.filtros {
    display:grid;
    grid-template-columns: 30% 70%;
}
.linguagens {
    display: inline-block;
}
</style>
