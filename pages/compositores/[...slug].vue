<template>
    <main class="container-fluid px-4 px-md-0">
        <HeaderView />
        <div class="row g-0">
            <div class="col-12">
                <section>
                    <ContentDoc v-slot="{doc}">
                        <div class="row g-0 justify-content-md-center">
                            <div class="col-12 col-md-10 text-justify">
                                <h1>{{doc.title}}</h1>
                                <div class="row g-0 justify-content-center">
                                    <div class="col-8 col-md-4  text-center">
                                        <img class="img-fluid" :src="doc.image">
                                    </div>
                                    <div class="col-12 col-md-8 text-justify pt-3 ps-md-4">
                                        <h5>Peliculas:</h5>
                                        <ul>
                                            <li v-for="pelicula in doc.peliculas" :key="pelicula.id">
                                                <ContentQuery path="/peliculas" :where="{ id: pelicula.id }"
                                                    v-slot="{data}">
                                                    <NuxtLink v-show="data && data[0]" :to="'/peliculas/'+data[0].id">
                                                        {{data[0].title}}
                                                    </NuxtLink>
                                                </ContentQuery>
                                            </li>
                                        </ul>
                                        <h5>Álbumes de peliculas:</h5>
                                        <ul>
                                            <li v-for="album in doc.albumes" :key="album.id">
                                                <ContentQuery path="/albumes" :where="{ id: album.id }"
                                                    v-slot="{data}">
                                                    <NuxtLink v-show="data && data[0]" :to="'/albumes/'+data[0].id">
                                                        {{data[0].title}}
                                                    </NuxtLink>
                                                </ContentQuery>
                                            </li>
                                        </ul>
                                    </div>
                                    <hr class="mt-5">
                                </div>
                                <div class="row g-0 justify-content-center mt-4">
                                    <div class="col-12 col-md-12 text-justify">
                                        <ContentRenderer :value="doc" />
                                        <br>
                                        <NuxtLink to="/compositores">Regresar</NuxtLink>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </ContentDoc>
                </section>
            </div>
        </div>
        <FooterView />
    </main>
</template>