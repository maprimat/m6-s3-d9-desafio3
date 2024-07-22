<!-- TEMPLATE -->
<template>
    <div id="app">
        <div class="container">
            <div class="row">
                
                <!-- COLUMNA CAMBIOS -->
                <div class="col-4 container-cambios px-5 py-5">
                    <form class="d-flex flex-column">

                        <!-- COLOR FONDO -->
                        <label for="colorFondo">Color de fondo</label>
                        <input class="mb-3 w-100" type="text" id="colorFondo" v-model="colorFondo" />

                        <!-- COLOR TEXTO -->
                        <label for="colorTexto">Color de texto</label>
                        <input class="mb-3 w-100" type="text" id="colorTexto" v-model="colorTexto" />

                        <!-- CHECKBOX TEXTO-->
                        <div class="mb-3">
                            <label for="mostrarTexto">Mostrar texto</label>
                            <input class="mx-2" type="checkbox" id="mostrarTexto" v-model="mostrarTexto" />
                        </div>

                        <!-- BORDE RANGO -->
                        <div class="mb-3">
                            <label for="rangeborde">Borde</label><br />
                            <input class="w-100" type="range" id="rangeborde" name="rangeborde" min="0" max="50" step="1"
                                v-model="borde" />
                        </div>

                        <!-- TEXTAREA TEXTO -->
                        <div class="mb-3">
                            <label for="contenidoTextual">Contenido textual</label>
                            <textarea class="w-100" name="text" id="contenidoTextual" rows="2"
                                v-model="contenidoTextual"></textarea>
                        </div>

                        <!-- TIPOGRAFIA -->
                        <div class="mb-3">
                            <label for="tipografias">Tipografías</label>
                            <br />
                            <select name="tipografias" class="w-100" id="tipografias" v-model="tipografias">
                                <option :value="tipografia" v-for="(tipografia, index) in tipografiaArray" :key="index">
                                    {{ tipografia }}
                                </option>
                            </select>
                        </div>

                        <!-- CHECKBOX OPACO -->
                        <div class="mb-3">
                            <label for="opaco">Opaco</label>
                            <input class="mx-2" type="checkbox" name="opaco" id="opaco" v-model="opaco" />
                        </div>

                        <!-- TAMAÑO TEXTO -->
                        <div>
                            <label>Tamaño de letra</label>
                            <div class="row">
                                <div class="col-4">
                                    <input type="radio" id="pequeño" name="fav_language" value="pequeno"
                                        v-model="tamanoLetra" />
                                    <label for="pequeño">Pequeño</label>
                                </div>
                                <div class="col-4">
                                    <input type="radio" id="mediano" name="fav_language" value="mediano"
                                        v-model="tamanoLetra" />
                                    <label for="mediano">Mediano</label>
                                </div>
                                <div class="col-4">
                                    <input type="radio" id="grande" name="fav_language" value="grande"
                                        v-model="tamanoLetra" />
                                    <label for="grande">Grande</label>
                                </div>
                            </div>
                        </div>
                    </form>
                </div>

                <!-- COLUMNA RESULTADO -->
                <div class="container-resultado col-8 container py-5 d-flex align-items-center justify-content-center">
                    <div id="" class="h-75 w-75 d-flex align-items-center justify-content-center" :style="{borderRadius: borde + '%',backgroundColor: colorFondo,}" :class="[opaco ? opacoClass : '']">
                        <p :style="{color: colorTexto, fontStyle: tipografias}" :class="[tamanoLetra == 'grande' ? largeClass : tamanoLetra == 'pequeno' ? smallClass : mediumClass]" v-show="mostrarTexto">
                            {{ contenidoTextual }}
                        </p>
                    </div>
                </div>

            </div>
        </div>
    </div>
</template>

<!-- SCRIPT -->
<script>
export default {
    name: "App",
    components: {},
    data() {
        return {
            colorFondo: "",
            colorTexto: "",
            mostrarTexto: true,
            borde: 0,
            contenidoTextual: "",
            tipografias: "normal",
            opaco: false,
            opacoClass: "opaco",
            tamanoLetra: "",
            tipografiaArray: ["italic", "normal", "oblique"],
            smallClass: "smallText",
            mediumClass: "mediumText",
            largeClass: "largeText",
        };
    },

    methods: {
        colFondo2: function () {
            return `${this.colFondo + this.opaco} `;
        },
    },
};
</script>

<!-- STYLE -->
<style>
.container-cambios {
    background-color: #2f4f4f;
    color: white;
}

.smallText {
    font-size: 16px;
}

.mediumText {
    font-size: 24px;
}

.largeText {
    font-size: 32px;
}

.opaco{
    opacity: 0.5;
}
</style>