<template>
  <div>
    <Message :msg="msg" v-show="msg"/>
  </div>
  <form class="formulario p-4" @submit="createBurger">
    <div class="container col-4 mb-4">
      <label for="nome" class="form-label">Nome:</label>
      <input type="text" class="form-control" id="nome" v-model="nome" placeholder="Insira seu nome">
    </div>
    <div class="container col-4 mb-4">
      <label for="pao" class="form-label">Selecione o Pão:</label>
        <select class="form-select" name="pao" v-model="pao">
          <option 
            v-for="pao in paes"
            :key="pao.id"
            :value="pao.tipo">{{pao.tipo}}
          </option>
        </select>
    </div>
    <div class="container col-4 mb-4">
      <label for="carne" class="form-label">Selecione a Carne:</label>
        <select class="form-select" name="carne" v-model="carne">
          <!-- <option selected>Selecione a Carne</option> -->
          <option 
            v-for="carne in carnes"
            :key="carne.id"
            :value="carne.tipo">
            {{carne.tipo}}
          </option>
        </select>
    </div>
    <div class="container col-4 mb-4">
      <label for="opcionais">Selecione os Opcionais:</label>
      <div class="mt-2">
         <div class="form-check form-check-inline mb-2 mx-1" 
          v-for="opcional in opcionaisData"
          :key="opcional.id">
          <input type="checkbox" name="opcionais" class="form-check-input"
          v-model="opcionais"
          :value="opcional.tipo"
          >
          <label for="opcionais" class="form-check-label mx-0">
            {{opcional.tipo}}
          </label>
        </div>
      </div>
    </div>
    <div class="container col-4 d-flex justify-content-center">
      <button class="btn btn-warning">Criar Hamburger</button>
    </div>
  </form>
</template>
<script>
import Message from './Message.vue'

export default {
  components: { 
    Message
   },
  name: "BurgerForm",
  data() {
    return {
      paes: null,
      carnes: null,
      opcionaisData: null,
      nome: null,
      pao: null,
      carne: null,
      opcionais: [],
      status: "Solicitado",
      msg: null
    }
  },
  methods: {
    async getIngredientes() {
      const req = await fetch('http://localhost:3000/ingredientes')
      const data = await req.json()
      this.paes = data.paes
      this.carnes = data.carnes
      this.opcionaisData = data.opcionais
    },
    async createBurger(e) {
      e.preventDefault()
      const data = {
        nome: this.nome,
        carne: this.carne,
        pao: this.pao,
        opcionais: Array.from(this.opcionais),
        status: "Solicitado"
      }
      const dataJson = JSON.stringify(data)    
      const req = await fetch("http://localhost:3000/burgers", {
        method: "POST",
        headers: { "Content-Type" : "application/json" },
        body: dataJson
      });
      const res = await req.json()
      this.msg = "Pedido realizado com sucesso"
      console.log(res)

      //limpar msg
      setTimeout(() =>
        this.msg = "", 3000)
      
      // limpar campos
      this.nome = ""
      this.carne = ""
      this.pao = ""
      this.opcionais = []
    }
  },
  mounted() {
    this.getIngredientes()
  }
}
</script>
<style scoped>

  .form-check-label{
    margin-left: 10px;
    text-align: justify;
  }
  
  .form-check-input:checked{
    background-color: #222;
  }

  .form-label{
    padding-left: 5px;
    border-left: 4px gold;
    border-right: transparent;
    border-top: transparent;
    border-bottom: transparent;
    border-style: solid;
  }

</style>