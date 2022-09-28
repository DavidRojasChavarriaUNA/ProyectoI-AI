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
                                        <h5>Banda sonora compuesta por:</h5>
                                        <ul>
                                            <li v-for="compositor in doc.compositores" :key="compositor.id">
                                                <ContentQuery path="/compositores" :where="{ id: compositor.id }"
                                                    v-slot="{data}">
                                                    <!-- <NuxtLink v-for="compositorData in data"
                                                            :key="compositorData.id"
                                                            :to="'/compositores/'+compositorData.id">
                                                            {{compositorData.title}}
                                                        </NuxtLink> -->
                                                    <NuxtLink v-show="data && data[0]"
                                                        :to="'/compositores/'+data[0].id">
                                                        {{data[0].title}}
                                                    </NuxtLink>
                                                </ContentQuery>
                                            </li>
                                        </ul>
                                        <h5>Pelicula:</h5>
                                        <ul>
                                            <!-- <ContentQuery path="/peliculas" :where="{ id: doc.pelicula.id }" v-slot="{data}">
                                                    <li v-for="pelicula in data" :key="pelicula.id">
                                                        <NuxtLink :to="'/peliculas/'+pelicula.id">
                                                            {{pelicula.title}}
                                                        </NuxtLink>
                                                    </li>
                                                </ContentQuery> -->
                                            <ContentQuery path="/peliculas" :where="{ id: doc.pelicula.id }"
                                                v-slot="{data}">
                                                <li v-for="pelicula in data" :key="pelicula.id">
                                                    <NuxtLink :to="'/peliculas/'+pelicula.id">
                                                        {{pelicula.title}}
                                                    </NuxtLink>
                                                </li>
                                            </ContentQuery>
                                        </ul>
                                        <h5>Discográfica</h5>
                                        <ul><li>{{doc.discografica}}</li></ul>
                                        <h5>Duración</h5>
                                        <ul><li>{{doc.duracion}}</li></ul>
                                    </div>
                                    <hr class="mt-5">
                                </div>
                                <div class="row g-0 justify-content-center mt-4">
                                    <div class="col-12 col-md-10 text-justify">
                                        <ContentRenderer :value="doc" />
                                        <br>
                                        <NuxtLink to="/albumes">Regresar</NuxtLink>
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