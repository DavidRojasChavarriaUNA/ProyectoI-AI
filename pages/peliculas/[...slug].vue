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
                                        <h5>
                                            Banda sonora compuesta por:
                                            <ul>
                                                <li v-for="compositor in doc.compositores" :key="compositor.id">
                                                    <NuxtLink :to="'/compositores/'+compositor.id">{{compositor.nombre}}
                                                    </NuxtLink>
                                                </li>
                                            </ul>
                                        </h5>
                                        <h5>
                                            Album de la pelicula:
                                            <ul>
                                                <li>
                                                    <NuxtLink :to="'/albumes/'+doc.album.id">{{doc.album.nombre}}
                                                    </NuxtLink>
                                                </li>
                                            </ul>
                                        </h5>
                                        <ContentRenderer :value="doc" />
                                    </div>
                                    <hr>
                                </div>
                            </div>
                        </div>
                        <div class="row g-0 justify-content-center mt-4">
                            <div class="col-12 col-md-10 text-justify">
                                <h3>Trailer de la película</h3>
                                <div class="containerVideo">
                                    <iframe :src="doc.trailer" title="YouTube video player" frameborder="0"
                                        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
                                        allowfullscreen class="video"></iframe>
                                </div>
                                <br>
                                <NuxtLink to="/peliculas">Regresar</NuxtLink>
                            </div>
                        </div>
                    </ContentDoc>
                </section>
            </div>
        </div>
        <FooterView />
    </main>
</template>