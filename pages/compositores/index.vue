<template>
  <main class="container-fluid px-4 px-md-0">
    <HeaderView />
    <div class="row g-0">
      <div class="col-12">
        <section>
          <div class="row g-0 justify-content-md-center">
            <div class="col-12 col-md-10 text-justify">
              <h1>Catálogo de peliculas</h1>
              <p class="text-justify">
                Conoce la información de los compositores de las bandas sonoras de las peliculas y sus álbumes, te invitamos a que selecciones un compositor
                de nuestro catálogo para descubrirlo.
              </p>
            </div>
          </div>
          <div class="row g-0 justify-content-md-center">
            <div class="col-12 col-md-10 text-justify">
              <div class="row g-0 justify-content-center">
                <ContentList path="/compositores" v-slot="{ list }">
                  <div class="col-10 col-sm-6 col-md-4" v-for="pelicula in list" :key="pelicula.id">
                    <div class="card m-3">
                      <img :src="pelicula.image" class="card-img-top" :alt="'Imagen ' + pelicula.title" />
                      <div class="card-body">
                        <h5 class="card-title">{{ pelicula.title }}</h5>
                        <p class="card-text">
                          {{pelicula.Resumen}}
                        </p>
                        <NuxtLink class="btn btn-primary" :to="pelicula._path">Ver detalle</NuxtLink>
                      </div>
                    </div>
                  </div>
                </ContentList>
              </div>
            </div>
          </div>
        </section>
      </div>
    </div>
    <FooterView />
  </main>
</template>