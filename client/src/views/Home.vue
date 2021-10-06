<template>
  <BasicLayouts>
<body>
  

  
            <div class="banner">
                <img src="../assets/banner.png" alt="Sisteling" width="1280" height="500" >
            </div>

       

       
         <div class="servicios">
             <h1>Soluciones Inteligentes</h1>
        </div>

        <section id="servicios" class="services-section">

           
          
            <article >
                <a href="redes.html"><img  src="../assets/redes.png"  alt="Redes Inalambricas"></a>
                    <h2 >Redes Inalambricas</h2>
                    <p >
                        Conectamos datos y video a largas distancias a través de redes inalámbricas usando tecnologías microondas
                    </p>
            </article>

            <article >
                <a href="seguridad.html"><img  src="../assets/camaras.jpg" alt="Seguridad Electronica"></a>
                <h2 >Seguridad Electronica</h2>
                <p >
                    Ofrecemos un sistema completo de seguridad electrónica para vigilar su negocio y hogar.
                </p>
            </article>

            <article >
                <a href="domotica.html"><img  src="../assets/domotica1.jpg" alt="Domotica"></a>
                <h2 >Domotica</h2>
                <p >
                    Diseñamos su casa inteligente con la mas avanzada tecnología de control e iluminación.
                </p>
            </article>

        </section>
       

    <footer class="footer">
        <article>
           <p>Copyright © 2021 SisteLing- soluciones inteligentes Todos los derechos reservados.</p>
        </article> 
    </footer>  

    </body>
    <h1>Estamos en Home</h1>

  </BasicLayouts>

</template>

<script>
import { ref, onMounted } from 'vue';
import BasicLayouts from '../layouts/BasicLayouts.vue';
import { getProducts } from '../api/pruduct';
export default {
  name: 'Home',
  components: {
    BasicLayouts,
  },
  setup() {
    let products = ref(null);

    onMounted(async () => {
      const response = await getProducts(1);
      products.value = response;
    });
    return {
      products,
    };
  },
};
</script>

<style >

.banner {
  width: 100%;
}

.banner > img {
  width: 1280px;
  height: 500px;
  max-width: 1500px;
  object-fit: cover;
  display: block;
  margin-left: auto;
  margin-right: auto;
  background-size: cover;
}

.servicios {
  background-color: #25294f;
  height: 100px;
  display: flex;
  color: white;
  justify-content: space-evenly;
}

.header-container {
  background-color: #f7f7f7;
}
.services-section {
  display: flex;
  text-align: center;
}

.services-section article {
  padding: 20px;
  text-align: center;
}

.services-section img {
  border-radius: 50%;
  margin-right: auto;
  margin-left: auto;
  width: 60%;
  height: 40%;
  margin-bottom: 40px;
}

.services-section p {
  font-size: 20px;
  text-align: center;
  display: block;
}

.footer {
  background-color: #25294f;
  height: 150px;
  display: flex;
  color: white;
  justify-content: space-evenly;
}

footer p {
  font-size: 20px;
}

</style>