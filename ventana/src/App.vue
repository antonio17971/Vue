<template>
  <div id="app">

<nav class="navbar navbar-expand-lg navbar-light style=background-color: #e3f2fd;" style="background-color: #e3f2fd;">
          <a class="navbar-brand" href="#">Sis.Narval</a>
          <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarText" aria-controls="navbarText"
            aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>
          <div class="collapse navbar-collapse">
            <ul class="navbar-nav mr-auto">
              <li class="nav-item ">
                <a class="nav-link" href="#">Home <span class="sr-only">(current)</span></a>
              </li>
              <li class="nav-item ">
                <a class="nav-link" href="#">Usuario <span class="sr-only">(current)</span></a>
              </li>
              <li class="nav-item">
                <a class="nav-link active" href="#">Ventas<span class="sr-only">(current)</span></a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="#">Inventario<span class="sr-only">(current)</span></a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="#">Clientes<span class="sr-only">(current)</span></a>
              </li>
            </ul>
      
            <ul class="nav navbar-nav pull-right">
              <li class="nav-item dropdown">
                <a class="nav-link dropdown-toggle" href="#/home" id="navbarDropdown" role="button" data-toggle="dropdown"
                  aria-haspopup="true" aria-expanded="false">
                </a>
                <div class="dropdown-menu" aria-labelledby="navbarDropdown">
                  <a class="dropdown-item" href="#">Action</a>
                  <a class="dropdown-item" href="#">Another action</a>
                  <div class="dropdown-divider"></div>
                  <a class="dropdown-item" href="#">Something else here</a>
                </div>
              </li>
            </ul>
            <span class="navbar-text">
            </span>
      
          </div>
        </nav>


    <div>
      <h1>Ventas</h1>
    </div>

    <div class="row">
      <div  class="col">

      </div>
      <div class="col-8">
        <div class="row">
            <div class="col-7">
            <form action="">
              <div class="form-grup row">
                <label class="col-sm-2 col-form-label">Encargado del evento</label>
                <div class="col-sm-5">
                  <label class="col-sm-2 col-form-label"> {{usuario}} </label>
                </div>
              </div>

              <div class="form-grup row">
                <label class="col-sm-2 col-form-label">Cliente</label>
                <div class="col-sm-5">
                  <input class="form-control" type="text" placeholder="Nombre de la empresa" v-model="txtEmpresa" v-on:focusin="poderVerEmpresas"><br>
                  <div v-for="(empresa, index) in filteredEmpresa" :key="index">
                      <ul v-show="verEmpresa">
                        Nombre: {{empresa.name}}    Telefono: {{empresa.telefono}}    Correo: {{empresa.correo}}
                      </ul>
                  </div>
                </div>
              
              </div>
              
              <div class="form-grup row">
                <label class="col-sm-2 col-form-label">Contacto</label>
                <div class="col-sm-5">
                    <input class="form-control" type="text" placeholder="Persona de Contacto"  v-model="txtCliente" v-on:focus="poderVer"><br>
                    <div v-for="(Cliente, index) in filteredCliente" :key="index">
                      <ul v-show="verClientes">
                        Nombre: {{Cliente.name}}    Telefono: {{Cliente.telefono}}    Correo: {{Cliente.correo}}
                      </ul>
                  </div>
                </div>
              </div>

              <div class="form-grup row">
                <label class="col-sm-2 col-form-label">Buscar Articulo</label>
                <div class="col-sm-5">
                  <input class="form-control" type="text" v-model="txtArticulo">
                </div>
                <div class="col-sm-5">
                  <button type="button" class="btn btn-primary" v-on:click="poderVerArti">Buscar</button>
                </div>
                <div v-for="(articulo, index) in filteredArticulos" :key="index">
                      <ul v-show="verArticulos">
                        <button type="button" class="btn btn-primary" v-on:click="guardar (articulo)" >
                            Nombre: {{articulo.name}}    Descripcion: {{articulo.descripcion}}
                        </button>
                          
                      </ul>
                    </div>
              </div>
              
            </form>
          </div>

          <div class="col">
            <form >
              <div class="form-grup row">
              <label class="col-sm-2 col-form-label">Fecha del evento</label>
              <div class="col-sm-5">
                <input class="form-control" type="date"> <br>
              </div>
            </div>

            <div class="form-grup row">
              <label class="col-sm-2 col-form-label">Fecha de Montaje</label>
              <div class="col-sm-5">
                <input class="form-control" type="date"> <br>
              </div>
            </div>

            <div class="form-grup row">
              <label class="col-sm-2 col-form-label">Fin del evento</label>
              <div class="col-sm-5">
                <input class="form-control" type="date"> <br>
              </div>
            </div>
            </form>
              
          </div>

        </div>
       
        <div>
            <table class="table">
              <thead class="thead-light">
                <tr>
                  <th scope="col">#</th>
                  <th scope="col">Producto</th>
                  <th scope="col">Descripcion</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="(i , msg) in articulos" :key="msg" >
                  <th scope="row"> {{msg +1}} </th>
                  <td> {{i.name}} </td>
                  <td> {{i.descripcion}} </td>
                </tr>

                </tbody>
              </table>
          </div>
        <button type="button" class="btn btn-primary">Guardar peticion</button>
      </div>
       <div class="col">
        
      </div>
    </div>
    
  </div>
</template>

<script>
 const articulos=[
    {name:'Tros', descripcion:'Es de 2 metros'},
    {name:'Luz blanca', descripcion:'Alto voltaje'},
    {name:'Pantalla',descripcion:'Tamaño 20 pulgdas'}
  ]
export default {
  name: 'app',
 
  data () {
    return {
      msg: 1,
      usuario:'Jose quesada',
      txtCliente:'',
      txtEmpresa:'',
      txtArticulo:'',
      verClientes:false,
      verArticulos:false,
      verEmpresa:false,
      articulos:[] = articulos,
      Clientes:[
        {name:'Jose arturo', telefono:'89792734', correo:'jose17971@outlook.es'},
        {name:'Jose antonio', telefono:'89792734', correo:'jose17971@outlook.es'},
        {name:'Mario', telefono:'8888888', correo:'mario123@gmailcom'},
      ],
      empresas:[
        {name:'Coca Cola', telefono:'1111', correo:'1122@gmail.com'},
        {name:'Nisan',telefono:'2222', correo:'222222@gmail.com'}
      ]
    }
  },
  computed:{
     filteredCliente:function (){
       return this.Clientes.filter((Cliente)=>{
         return Cliente.name.match(this.txtCliente)
       })
     },
     filteredEmpresa:function (){
       return this.empresas.filter((empresa)=>{
         return empresa.name.match(this.txtEmpresa)
       })
     },
     filteredArticulos:function (){
       return this.articulos.filter((articulo)=>{
         return articulo.name.match(this.txtArticulo)
       })
     }
  },
  watch:{
    txtCliente() {
      console.log(this.txtCliente)
    }
  }, 
  methods:{
    datos(){
      this.articulos=articulos
    },
    poderVer(){
      this.verClientes=true
    },
    noVer(){
      this.verClientes=false
    },
    poderVerArti(){
      this.verArticulos=true
    },
    noVerArti(){
      this.verArticulos=false
    },
     poderVerEmpresas(){
      this.verEmpresa=true
    },
    noVerEmpresa(){
      this.verEmpresa=false
    },
    guardar(item){
      this.articulos.push(item)
    }
  }
}
</script>

<style>

</style>
