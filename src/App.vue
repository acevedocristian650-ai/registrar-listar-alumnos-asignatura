<script setup>
import { reactive } from "vue";

 const alumnos = reactive([])

 const alumno = reactive({
  cedula : "",
  nombre: "",
  apellido: "",
  edad: 0,
  correo : ""
 })

function registaralumno(){
  alumnos.push({...alumno});
  alert("Alumno registrado correctamente");
  limpiar()
}

function limpiar(){
  alumno.cedula = "";
  alumno.nombre = "";
  alumno.apellido = "";
  alumno.edad = 0;
  alumno.correo = "";
}


 const asignaturas = reactive([])

 const asignatura = reactive({
  asignatura : "",
  codigo : "",

 })

function registarasignatura(){
  asignaturas.push({...asignatura});
  alert("Asignatura registrada correctamente");
  limpiarasignatura()
}

function limpiarasignatura(){
  asignatura.asignatura = "";
  asignatura.codigo = "";

}

</script>

<template>
  <div>
   <nav class="navbar navbar-expand-lg navbar-light bg-light">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">SISTEMA DE CALIFICACIONES</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
       
        
        <li class="nav-item dropdown">
          <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-bs-toggle="dropdown" aria-expanded="false">
            Alumnos
          </a>
          <ul class="dropdown-menu" aria-labelledby="navbarDropdown">
            <li><a class="dropdown-item" data-bs-toggle="modal" data-bs-target="#modalalumno">Registrar</a></li>
            <li><a class="dropdown-item" data-bs-toggle="modal" data-bs-target="#modallistaralumno">Listar</a></li>
            
          </ul>
        </li>
       <!-- Boton asignatura -->
        <li class="nav-item dropdown">
          <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-bs-toggle="dropdown" aria-expanded="false">
            Asignatura
          </a>
          <ul class="dropdown-menu" aria-labelledby="navbarDropdown">
            <li><a class="dropdown-item" data-bs-toggle="modal" data-bs-target="#modalasignatura">Registrar</a></li>
            <li><a class="dropdown-item" data-bs-toggle="modal" data-bs-target="#listarasignatura">Listar</a></li>
            
          </ul>
        </li>
        
      </ul>
      <form class="d-flex">
        <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
        <button class="btn btn-outline-success" type="submit">Search</button>
      </form>
    </div>
  </div>
</nav>
      

      <!-- Modal Alumno -->
<div class="modal fade" id="modalalumno" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">Registro de Alumnos</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
          <div class="form-floating mb-3">
            <input type="number" class="form-control" id="floatingInput" placeholder="Cedula" v-model="alumno.cedula">
            <label for="floatingInput">Cedula</label>
          </div>
          <div class="form-floating mb-3">
            <input type="text" class="form-control" id="floatingPassword" placeholder="Nombre" v-model="alumno.nombre">
            <label for="floatingPassword">Nombre</label>
          </div>
          <div class="form-floating mb-3">
            <input type="text" class="form-control" id="floatingInput" placeholder="Apellido" v-model="alumno.apellido">
            <label for="floatingInput">Apellido</label>
          </div>
          <div class="form-floating mb-3">
            <input type="number" class="form-control" id="floatingPassword" placeholder="Edad" v-model="alumno.edad">
            <label for="floatingPassword">Edad</label>
          </div>
          <div class="form-floating mb-3">
            <input type="email" class="form-control" id="floatingInput" placeholder="correo" v-model="alumno.correo">
            <label for="floatingInput">Correo</label>
          </div>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary" @click="registaralumno">Guardar Alumno</button>
      </div>
    </div>
  </div>
</div>
<!-- Listar alumno -->

<div class="modal fade" id="modallistaralumno" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">Listado Alumnos</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
         <table class="table table-hover">
          <thead>
             <th>Cédula</th>
              <th>Nombre</th>
               <th>Apellido</th>
                <th>Edad</th>
                 <th>Correo</th>
           </thead>
            <tr v-for="data in alumnos" :key="data.cedula">
             <td>{{ data.cedula }}</td>
             <td>{{ data.nombre }}</td>
             <td>{{ data.apellido }}</td>
             <td>{{ data.edad }}</td>
             <td>{{ data.correo }}</td>

            </tr>
        </table>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary" @click="registaralumno">Guardar Alumno</button>
      </div>

      
    </div>
  </div>

</div>




      <!-- Modal Asignatura -->
<div class="modal fade" id="modalasignatura" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">Registro de Asignatura</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
          <div class="form-floating mb-3">
            <input type="text" class="form-control" id="floatingInput" placeholder="Asignatura" v-model="asignatura.asignatura">
            <label for="floatingInput">Asignatura</label>
          </div>
          <div class="form-floating mb-3">
            <input type="number" class="form-control" id="floatingPassword" placeholder="Codigo" v-model="asignatura.codigo">
            <label for="floatingPassword">Codigo</label>
          </div>
         
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary" @click="registarasignatura">Guardar Asignatura</button>
      </div>
    </div>
  </div>
</div>

<!-- Listar Asignatura -->

<div class="modal fade" id="listarasignatura" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">Listado Asignatura</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
         <table class="table table-hover">
          <thead>
             <th>Asignatura</th>
              <th>Codigo</th>
               
           </thead>
            <tr v-for="data in asignaturas" :key="data.asignatura">
             <td>{{ data.asignatura }}</td>
             <td>{{ data.codigo }}</td>
            

            </tr>
        </table>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary" @click="registarasignatura">Guardar Asignatura</button>
      </div>
    </div>
  </div>
</div>


  </div>
</template>

<style scoped></style>




