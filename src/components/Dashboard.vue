<template>
<Message :msg="msg" v-show="msg"/>
  <div class="container">
    <div class="text-center p-4">
      <h1>Gerenciamento de pedidos</h1>
    </div>
    
       <table class="table table-hover text-center">
	
        <thead>
          <tr>
          <th scope="col">ID</th>
	        <th scope="col">Cliente</th>	
          <th scope="col">Pão</th>
          <th scope="col">Carne</th>
          <th scope="col">Opcionais</th>
          <th scope="col">Status</th>
          <th scope="col">Ações</th>
          </tr>
        </thead>

        <tbody>
          <tr v-for="burger in burgers" :key="burger.id">
            <th scope="row">{{burger.id}}</th>
            <td>{{burger.nome}}</td>
            <td>{{burger.pao}}</td>
            <td>{{burger.carne}}</td> 
            <td>
              <ul>
                <span v-for="(opcional, index) in burger.opcionais" :key="index">
                  {{opcional + ', '}}
                </span>
              </ul>
            </td>
            <td>
              <select name="status" class="form-select" @change="updateBurger($event, burger.id)">
                <option value="">Selecione</option>
                <option 
                  :value="s.tipo"
                  v-for="s in status" 
                  :key="s.id" 
                  :selected="burger.status == s.tipo">
                  {{s.tipo}}
                </option>
              </select>
            </td>
            <td>
              <button class="btn btn-warning" @click="deleteBurger(burger.id)">Cancelar</button>
            </td>
          </tr>
        </tbody>
       </table>
      </div>
</template>
<script>
import Message from './Message.vue'

export default {
  name: "Dashboard",
  data(){
    return{
      burgers: null,
      burger_id: null,
      status: [],
      msg: null,
    }
  },
  components:{
    Message
  },
  methods: {
    async getPedidos(){
      const req = await fetch('http://localhost:3000/burgers')
      const data = await req.json()
      this.burgers = data

      console.log(data)

      //resgatar os status
      this.getStatus()
    },
    async getStatus(){
      const req = await fetch('http://localhost:3000/status')
      const data = await req.json()
      this.status = data
      console.log(data)
    },
    async deleteBurger(id){
      const req = await fetch(`http://localhost:3000/burgers/${id}`,{
        method: "DELETE"
      })

      const res = await req.json()

      this.msg = `Pedido Cancelado com sucesso!`

      setTimeout(() => this.msg = "", 3000)

      //atualiza diretamente do banco
      this.getPedidos()
    },
    async updateBurger(event, id){
      const option = event.target.value
      const dataJson = JSON.stringify({status: option})
      const req = await fetch(`http://localhost:3000/burgers/${id}`, {
        method: "PATCH",
        headers: {"Content-Type" : "application/json"},
        body: dataJson
      })

      const res = await req.json()

      this.msg = `O pedido foi atualizado para: ${res.status}`

      setTimeout(() => this.msg = "", 3000)

      console.log(res)
    }
  },
  mounted(){
    this.getPedidos()
  }
}
</script>
<style scoped>
*{
  list-style: none;
}

table{
  height: 100%;
}

table thead{
  background-color: rgb(36, 31, 8);
  color: #fff;
}

table border{
  background-color: blue;
}

.table-hover tr:hover{
  background-color: none;
  color: #fff;
}

.form-select{
  border-color: #ffc107;
  
}
 
/* .table-hover tbody tr:hover td, .table-hover tbody tr:hover th {
  background-color: #fff;
} */
</style>