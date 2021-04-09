<template>
  <div class="row">

      <div class="col-md-6">
          <h1>Nuevo Producto</h1>
          <form >
              <label for="">Nombre</label>
            <input type="text" v-model="nombre" class="form-control">
            <label for="">Precio</label>
          <input type="number" step="0.01" v-model="precio" class="form-control">

          <label for="">Cantidad</label>
          <input type="number" v-model="cantidad" class="form-control">

          <button type="button" v-on:click="addProducto()" class="btn btn-primary">Agregar Producto</button>
          </form>
          <h1>Lista de Productos</h1>
          <table class="table">
              <tr>
                  <td>NOMBRE</td>
                  <td>PRECIO</td>
                  <td>CANTIDAD</td>
                  <td>SUB T.</td>
                  <td>ACCIONES</td>
              </tr>
              <tr v-for="prod in productos" :key="prod.nombre">
                  <td>{{ prod.nombre }}</td>
                  <td>{{ prod.precio }}</td>
                  <td>{{ prod.cantidad }}</td>
                  <td>{{ prod.precio * prod.cantidad }}</td>
                  <td>
                      <button type="button" class="btn btn-success" v-on:click="addCarrito(prod)">+</button>
                  </td>
              </tr>
          </table>
      </div>
      <div class="col-md-6">
          <h1>Carrito</h1>

           <table class="table">
              <tr>
                  <td>NOMBRE</td>
                  <td>PRECIO</td>
                  <td>CANTIDAD</td>
                  <td>SUB T.</td>
                  <td>ACCIONES</td>
              </tr>
              <tr v-for="prod in carrito" :key="prod.nombre">
                  <td>{{ prod.nombre }}</td>
                  <td>{{ prod.precio }}</td>
                  <td>{{ prod.cantidad }}</td>
                  <td>{{ prod.precio * prod.cantidad }}</td>
                  <td>
                      <button>+</button>
                  </td>
              </tr>
          </table>
        </div>  

  </div>
</template>

<script>
export default {
    data(){
        return {
            productos: [
                {
                    nombre: "Mesa",
                    precio: 200,
                    cantidad: 6
                },
                {
                    nombre: "Silla",
                    precio: 140,
                    cantidad: 12
                }
            ],
            carrito: [],
            nombre: '',
            precio: '',
            cantidad: ''
        }
    },
    methods:{
        addCarrito(prod){
            this.carrito.push(prod);
        },

        addProducto(){
            this.productos.push({
                    nombre: this.nombre,
                    precio: this.precio,
                    cantidad: this.cantidad
                })
        }
    }

}
</script>

<style>

</style>