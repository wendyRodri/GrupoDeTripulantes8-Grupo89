<template>
  <!-- <div class="ui secondary menu">
    <div class="ui container">
      <div class="left menu">
        <router-link class="item" to="/">
          <img
            class="ui small image"
            src="../assets/logo.png"
            alt="Ecommerce"
          />
        </router-link>
        <template v-for="category in categories" :key="category.id">
          <router-link class="item" :to="category.slug">
            {{ category.title }}
          </router-link>
        </template>
      </div>
      <div class="right menu">
        <router-link class="item" to="/login" v-if="!token">
          Iniciar Sesión
        </router-link>

        <template v-if="token">
          <router-link class="item" to="/orders">Pedidos</router-link>
          <span class="ui item cart">
            <i class="shopping cart icon"></i>
          </span>
          <span class="ui item logout" @click="logout">
            <i class="sign-out icon"></i>
          </span>
        </template>
      </div>
    </div>
  </div> -->

  <head>

    <title>Sisteling Sistemas Inteligentes</title>
    <link href="https://fonts.googleapis.com/css?family=Poppins&display=swap" rel="stylesheet">

   <!-- <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.1/dist/css/bootstrap.min.css" rel="stylesheet" 
    integrity="sha384-F3w7mX95PdgyTmZZMECAngseQB83DfGTowi0iMjiWaeVhAn4FJkqJByhZMI3AhiU" crossorigin="anonymous">    -->
    
 </head>

  
  
   
        
            <div class="contenedor">

                <div class="menu-container">

                    <div class="logo-container">
                        <img class="logo" src="../assets/sistema/logo.png">
                        <h2>SisteLing</h2>
                    </div>
                        <h1>SisteLing</h1>
                    <div>
                        <nav id="menu">
                            <ul>
                                <li><a>Nuestra Empresa</a></li>
                                <li>
                                    <a href="#categorias">Categorias</a>
                                    <ul> 
                                   <li v-for="category in categories" :key="category.id">
                                      <router-link class="item" :to="category.slug">
                                        {{ category.title }}
                                      </router-link>
                                    </li>
                                    </ul>
                                </li> 

                      
       
      
                                <li> <router-link class="item" to="/login" v-if="!token">
          Iniciar Sesión
        </router-link>

        <template v-if="token">
          <router-link class="item" to="/orders">Pedidos</router-link>
          <span class="ui item cart">
            <i class="shopping cart icon"></i>
          </span>
          <span class="ui item logout" @click="logout">
            <i class="sign-out icon"></i>
          </span>
        </template>
      
                                
                                </li>
                            

                         

                            </ul> 
                        </nav>
                            
                   </div>

            </div>
       </div>
       

 
 
</template>


<script>
import { ref, onMounted } from 'vue';
import { getTokenApi, deleteTokenApi } from '../api/token';
import { getCategoriesApi } from '../api/category';

export default {
  name: 'Menu',

  setup() {
    let categories = ref(null);

    onMounted(async () => {
      const response = await getCategoriesApi();
      categories.value = response;
    });

    const token = getTokenApi();

    const logout = () => {
      deleteTokenApi();
      location.replace('/');
    };
    return {
      token,
      logout,
      categories,
    };
  },
};
</script>

<style>

.ui.menu.secondary {
  background: #0995d6;
 
  .item {
    color: #ffffff;
    &:hover {
      color: #1fa1f1;
    }
  }
  .menu.left {
    width: 50%;
    .ui.image {
      width: 120px;
       
    }
  }
  .menu.right {
    
    width: 50%;
    justify-content: flex-end;
    .logout,
    .cart {
      &:hover {
        cursor: pointer;
      }
    }
  }
}

body {
  max-width: 1280;
  min-width: 800px;
  margin-right: auto;
  margin-left: auto;
  margin-top: 0;
  margin-bottom: 0;
  color: #222222;
  font-family: "Poppins";
}
p {
  font-size: 20px;
  text-align: center;
}


h1 {
  font-size: 50px;
  margin: 0;
  color: #222222;
}

h2 {
  font-size: 30px;
  margin-bottom: 40px;
  color: #7423be;
}


.header-section {
  margin-bottom: 50px;
}

.contenedor {
  width: 100%;
  margin: auto;
  
}

.logo-container {
  width: 10%;
  text-align: center;
}

.logo {
  height: 100px;
}

.menu-container {
  padding-right: 30px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  width:95%;
}

/* menu */

#menu ul {
  list-style: none;
  margin: 0;
  padding: 0;
 
}

/* items del menu */

#menu ul li {
  background-color: #7423be;
}

/* enlaces del menu */

#menu ul a{
  display: block;
  color: rgb(240, 243, 232);
  text-decoration: none;
  font-weight: 400;
  font-size: 15px;
  padding: 10px;
  font-family: "HelveticaNeue", "Helvetica Neue", Helvetica, Arial, sans-serif;
  text-transform: uppercase;
  letter-spacing: 1px;
}

/* items del menu */

#menu ul li {
  position: relative;
  float: left;
  margin: 0;
  padding: 0;
}

/* efecto al pasar el ratón por los items del menu */

#menu ul li:hover {
  background: #5b78a7;
}

/* menu desplegable */

#menu ul ul {
  display: none;
  position: absolute;
  top: 100%;
  left: 0;
  background: #eee;
  padding: 0;
}

/* items del menu desplegable */

#menu ul ul li {
  float: none;
  width: 150px;
}

/* enlaces de los items del menu desplegable */

#menu ul ul a {
  line-height: 120%;
  padding: 10px 15px;
}

/* items del menu desplegable al pasar el ratón */

#menu ul li:hover > ul {
  display: block;
}

</style>


