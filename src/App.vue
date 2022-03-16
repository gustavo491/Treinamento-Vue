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
        <div>
            <h4 v-text="devs.length + ' resultados'"/>
        </div>
        <div class="listagem">
            <div class="card" v-for="dev in devs" :key="dev.key">
                <div>
                    <img class="user-image" :src="dev.picture">
                </div>
                <div class="info">
                    <h4 class="name" v-text="dev.name"/>
                    <span class="age" v-text="dev.age + ' anos'"/>
                    <span class="email" v-text="dev.email"/>
                    <div>
                        <img class="languages" v-for="lang in dev.programmingLanguages" :key="lang.key" :src="imgLang[lang.id]">
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'App',
  data () {
      return {
            devs: [],
            imgLang: {
                'JavaScript': 'https://upload.wikimedia.org/wikipedia/commons/thumb/9/99/Unofficial_JavaScript_logo_2.svg/640px-Unofficial_JavaScript_logo_2.svg.png',
                'Python': 'https://upload.wikimedia.org/wikipedia/commons/thumb/c/c3/Python-logo-notext.svg/800px-Python-logo-notext.svg.png',
                'Java': 'https://upload.wikimedia.org/wikipedia/en/3/30/Java_programming_language_logo.svg',
                'Php': 'https://upload.wikimedia.org/wikipedia/commons/thumb/2/27/PHP-logo.svg/800px-PHP-logo.svg.png'
            }
      }
  },
  created () {
    axios.get('https://bernardosantos.zeedhi.com/workfolder/dev.php').then((response) => {
        this.devs = response.data.devs
    })
  }
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
.card {
    width:500px;
    display: grid;
    grid-template-columns: 28% 72%;
}
.languages {
    width:30px;
    height: 30px;;
}
</style>
