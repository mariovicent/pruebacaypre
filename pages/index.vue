<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8 md6>
      <v-card>
        <v-card-title class="headline"
          >Breve prueba técnica - Saludos tributos</v-card-title
        >

        <hr class="my-3" />

        <v-card-text>
          <p>
            La siguiente prueba nos permitirá valorar la experiencia y la capacidad de los
            candidatos para desenvolverse con las tecnologías usadas en la empresa.
          </p>

          <p>
            <b>Requisitos: </b>Usar Visual Studio Code como IDE de programación, no
            modificar este ejemplo, todo lo que se complete debe ser añadido sin eliminar
            estas líneas de código. Los resultados se me harán llegar como máximo hasta el
            lunes 18 de Julio.
          </p>

          <p>
            Se trata de una prueba sencilla y asequible con una duración no mayor a una
            hora. Las tareas <b>mínimas</b> a realizar son las siguientes:
          </p>

          <ul>
            <li>
              Descargar y clonar el repositorio desde la
              <a href="https://github.com/sitokat/pruebateccaypre" target="new"
                >siguiente dirección de Git.</a
              >
            </li>

            <li>
              Al final del documento encontrareis una tabla con una serie de datos.
              <b
                >Sin modificar el código proporcionado en el repositorio y a continuación
                de la tabla,</b
              >
              se deben mostrar los datos como si se trataran de fichas de producto. El
              resultado debe ser parecido al de la
              <a href="https://prueba.caypre.es/img/captura1.jpg" target="new"
                >siguiente imagen</a
              >, podéis ser tan creativos como querais.
            </li>
          </ul>

          <br />

          <p>
            Podéis hacerme llegar el resultado de la prueba de la manera que considereis
            oportuno, teniendo en cuenta que debo ver el código y poner ejecutarlo en mi
            máquina. Podéis usar el método que considereis oportuno para resolver la
            prueba.
          </p>

          <p>
            Los apartados extra <b>son totalmente opcionales</b> y no son necesarios para
            completar la prueba, pero se valorará positivamente el ser capaz de completar
            <b>cualquiera</b> de los apartados, mientras mas apartados se completen, mejor
            valorado será el candidato. De igual forma se valorará la
            <b>creatividad</b> mostrada al resolver el problema.
          </p>

          <ul>
            <li>
              <b>Extra:</b> Subir el resultado a cualquier servidor web y proporcionar el
              enlace donde poder visualizarlo.
            </li>

            <li>
              <b>Extra:</b> Añadir campos extra a las tarjetas de producto, como por
              ejemplo una valoración con estrellas. Podéis añadir tantos como consideréis
              oportunos.
            </li>

            <li><b>Extra:</b> Añadir paginación a los "productos" mostrados.</li>

            <li>
              <b>Extra:</b> La paginación debe retornar un parametro en la URL y debe ser
              visitable de forma independiente. Ejemplo:
              (https://megahogar.es/informatica/monitor-pc/?page=3)
            </li>

            <li>
              <b>Extra:</b> Obtener los datos a mostrar desde una base de datos. Para ello
              se deberá crear la base de datos con los campos correspondientes, la cadena
              de conexión y el backend, en este caso para que pueda ser ejecutada en mi
              equipo será necesario hacerme llegar un dump de la BD para poder replicarla.
            </li>

            <li>
              <b>Extra:</b> Subir el resultado a un nuevo repositorio público con vuestro
              usuario de Git, manteniendo el código original como rama principal y vuestro
              trabajo como una nueva rama.
            </li>

            <li><b>Extra:</b> Reducir al máximo las líneas de código usado.</li>

            <li><b>Extra:</b> Trabajar la vista móvil.</li>

            <li>
              <b>Extra:</b> Añadir un botón de "Comprar" y que el producto se añada al
              carrito y pueda ser visualizado desde la página de carrito.
            </li>

            <li>
              <b>Super Extra Overkill:</b> Implementar un middleware con gestión de roles
              de usuario y que únicamente el rol administrador sea capaz de entrar a la
              interfaz de administración de la página. Además, desde el admin se podrán
              añadir nuevos productos que se mostraran en la HOME. Mantener la sesión del
              usuario mediante una cookie y destruirla al cerrar sesión.
              <i
                >Para resolver esta parte será necesario realizar varios de los puntos
                anteriores y demostrará un importante dominio del framework.</i
              >
            </li>
          </ul>

          <div class="text-xs-right">
            <em><small>&mdash; Andrés H.</small></em>
          </div>

          <hr class="my-3" />

          <p>Os dejo a continuación un par de enlaces de interés.</p>

          <a href="https://es.vuejs.org/" target="_blank">Documentación sobre Vue</a>

          <br />

          <a href="https://nuxtjs.org/" target="_blank">Documentación sobre NUXT</a>

          <br />

          <a href="https://vuetifyjs.com" target="_blank">Documentación sobre Vuetify</a>
        </v-card-text>
      </v-card>

      <br />

      <v-card>
        <v-card-title class="headline"
          >Datos a transformar en fichas de producto</v-card-title
        >

        <v-data-table
          :headers="headers"
          :items="articulos"
          :items-per-page="5"
          class="elevation-1"
        ></v-data-table>
      </v-card>

      <v-card class="py-5 mt-6" >
        <v-card-title class="text-h5 mt-2 font-weight-medium">Productos monitores Caypre</v-card-title>
        
        <v-container grid-list-md text-xs-center >
          <v-layout justify-space-around row wrap fill-height  >
          <v-flex class="p-10 my-6" v-for="(articulo, index) in historyList" :key="articulo.nombre+'_'+index" xs12 sm6 lg4 >
            <v-card height="100%" class="my-6 mx-10 text-center" >
              <v-img
                class="mx-auto"
                width="250"
                :src="articulo.imagen_url" :alt="articulo.nombre"></v-img>
              
              <v-chip color="blue white--text" >{{randomBadge()}}</v-chip>
              
              <v-card-title class="text-h5 justify-center " >{{articulo.nombre}}</v-card-title>
              <v-card-text class="title text-center"><strong class="red--text text--lighten-1">{{articulo.precio}}€</strong></v-card-text>
              
              <div class="text-center" >
                <v-rating
                  dense
                  background-color="orange lighten-3"
                  color="orange"
                  large
                  readonly
                  :value="randomNumber()"
                ></v-rating>
              </div>
              
              <v-card-actions class="justify-center" >
                <v-btn
                  color="warning"
                  dark
                >
                  Añadir al carrito
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-flex>
          </v-layout>
          
          <v-pagination class="pagination mb-2" v-model="page" :length="pages" @input="updatePage"></v-pagination>
        </v-container>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  data() {
    return {
      headers: [
        { text: "Nombre", align: "start", sortable: false, value: "nombre" },
        { text: "Descripción Corta", value: "desc_corta" },
        { text: "Precio", value: "precio" },
        { text: "URL de la Imagen", value: "imagen_url" },
      ],
      articulos: [
        {
          nombre: 'Monitor Xiaomi MI 23,8" Full HD Desktop 1C LED IPS',
          desc_corta:
            "Con su ángulo de visión de 178º, puedes lograr un rango de visión superior al de otros modelos, puedes tener las imágenes más espectaculares y maravillosas frente a tus ojos.",
          precio: 150,
          imagen_url: "https://dist.megahogar.es/fotos/BHR4510GL_1.jpg",
        },
        {
          nombre: 'Monitor LED 23.6" AOC 24B1H Negro',
          desc_corta:
            "Aspecto elegante y amplios ángulos de visión. Equipado con un panel VA, el 24B1H ofrece una asombrosa relación de contraste estático de 3000: 1 con negros oscuros profundos. ",
          precio: 159,
          imagen_url: "https://dist.megahogar.es/fotos/24B1H_1.jpg",
        },
        {
          nombre: 'Monitor Xiaomi MI 23,8" Full HD Desktop 1C LED IPS',
          desc_corta:
            "Con su ángulo de visión de 178º, puedes lograr un rango de visión superior al de otros modelos, puedes tener las imágenes más espectaculares y maravillosas frente a tus ojos.",
          precio: 150,
          imagen_url: "https://dist.megahogar.es/fotos/BHR4510GL_1.jpg",
        },
        {
          nombre: 'Monitor LED 23.6" AOC 24B1H Negro',
          desc_corta:
            "Aspecto elegante y amplios ángulos de visión. Equipado con un panel VA, el 24B1H ofrece una asombrosa relación de contraste estático de 3000: 1 con negros oscuros profundos. ",
          precio: 159,
          imagen_url: "https://dist.megahogar.es/fotos/24B1H_1.jpg",
        },
        {
          nombre: 'Monitor Xiaomi MI 23,8" Full HD Desktop 1C LED IPS',
          desc_corta:
            "Con su ángulo de visión de 178º, puedes lograr un rango de visión superior al de otros modelos, puedes tener las imágenes más espectaculares y maravillosas frente a tus ojos.",
          precio: 150,
          imagen_url: "https://dist.megahogar.es/fotos/BHR4510GL_1.jpg",
        },
        {
          nombre: 'Monitor LED 23.6" AOC 24B1H Negro',
          desc_corta:
            "Aspecto elegante y amplios ángulos de visión. Equipado con un panel VA, el 24B1H ofrece una asombrosa relación de contraste estático de 3000: 1 con negros oscuros profundos. ",
          precio: 159,
          imagen_url: "https://dist.megahogar.es/fotos/24B1H_1.jpg",
        },
        {
          nombre: 'Monitor Xiaomi MI 23,8" Full HD Desktop 1C LED IPS',
          desc_corta:
            "Con su ángulo de visión de 178º, puedes lograr un rango de visión superior al de otros modelos, puedes tener las imágenes más espectaculares y maravillosas frente a tus ojos.",
          precio: 150,
          imagen_url: "https://dist.megahogar.es/fotos/BHR4510GL_1.jpg",
        },
        {
          nombre: 'Monitor LED 23.6" AOC 24B1H Negro',
          desc_corta:
            "Aspecto elegante y amplios ángulos de visión. Equipado con un panel VA, el 24B1H ofrece una asombrosa relación de contraste estático de 3000: 1 con negros oscuros profundos. ",
          precio: 159,
          imagen_url: "https://dist.megahogar.es/fotos/24B1H_1.jpg",
        },
        {
          nombre: 'Monitor Xiaomi MI 23,8" Full HD Desktop 1C LED IPS',
          desc_corta:
            "Con su ángulo de visión de 178º, puedes lograr un rango de visión superior al de otros modelos, puedes tener las imágenes más espectaculares y maravillosas frente a tus ojos.",
          precio: 150,
          imagen_url: "https://dist.megahogar.es/fotos/BHR4510GL_1.jpg",
        },
        {
          nombre: 'Monitor LED 23.6" AOC 24B1H Negro',
          desc_corta:
            "Aspecto elegante y amplios ángulos de visión. Equipado con un panel VA, el 24B1H ofrece una asombrosa relación de contraste estático de 3000: 1 con negros oscuros profundos. ",
          precio: 159,
          imagen_url: "https://dist.megahogar.es/fotos/24B1H_1.jpg",
        },
      ],
      randomNumber: function () { // Proporciona un numero aletatorio y lo asigna a la valoración del producto.
        return Math.floor(Math.random() * (5 - 1 + 1)) + 1;
    },
    randomBadge: function () { // Proporciona una categoria para el producto y lo asigna.
        let badges = ["Nuevo", "Oferta", "Destacado",];
        return badges[Math.floor(Math.random() * badges.length)]
    },
    // Propiedades para el paginador
    page: 1,
    pageSize: 6,
    listCount: 0,    
    historyList: []
    };
  },
  created() { // Inicializa el paginador.
		let _this = this;
		_this.initPage();
		_this.updatePage(_this.page);
	},
  methods: { // Metodos para la inicialización y cambio de página
		initPage: function() {
			let _this = this;
			_this.listCount = _this.articulos.length;
			if (_this.listCount < _this.pageSize) {
				_this.historyList = _this.articulos;
			} else {
				_this.historyList = _this.articulos.slice(0, _this.pageSize);
			}      
		},
		updatePage: function(pageIndex) {
			let _this = this;
			let _start = (pageIndex - 1) * _this.pageSize;
			let _end = pageIndex * _this.pageSize;
			_this.historyList = _this.articulos.slice(_start, _end);
			_this.page = pageIndex;
		}
	},
  computed: { // Cálculo de paginas en total
		pages() {
			let _this = this;
			if (_this.pageSize == null || _this.listCount == null) return 0;
			return Math.ceil(_this.listCount / _this.pageSize);
		}
	}
};
</script>
