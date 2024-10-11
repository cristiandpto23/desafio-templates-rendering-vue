<script>
export default {
    name: 'AwesomeVue',
    data() {
        return {
            backgroundColor: 'darkgreen',
            textColor: 'white',
            showText: true,
            borde: '0',
            text: 'Awesome Vue.js',
            fontFamily: '',
            fonts: ['Cursive', 'Arial', 'Verdana', 'Courier New', 'Georgia', 'Times New Roman'],
            opaco: false,
            fontSize: '',
        };
    },
};
</script>

<template>
    <main>
        <section class="instrucciones">
            <div class="instrucciones__subcontainer">
                <label for="">Color de Fondo</label>
                <input class="instrucciones__input" type="text" v-model="backgroundColor" />
            </div>
            <div class="instrucciones__subcontainer">
                <label for="">Color de Texto</label>
                <input class="instrucciones__input" type="text" v-model="textColor" />
            </div>
            <div class="instrucciones__subcontainer instrucciones__subcontainer--checkbox">
                <label for="">Mostrar Texto</label>
                <input class="instrucciones__input" type="checkbox" v-model="showText" />
            </div>
            <div class="instrucciones__subcontainer">
                <label for="">Borde</label>
                <input class="instrucciones__input instrucciones__input--range" type="range" v-model="borde" min="0" max="50" />
            </div>
            <div class="instrucciones__subcontainer">
                <label for="">Contenido textual</label>
                <textarea v-model="text"></textarea>
            </div>
            <div class="instrucciones__subcontainer">
                <label class="instrucciones__subcontainer">Tipografía</label>
                <select v-model="fontFamily" class="instrucciones__input">
                    <option v-for="font in fonts" :value="font">{{ font }}</option>
                </select>
            </div>
            <div class="instrucciones__subcontainer instrucciones__subcontainer--checkbox">
                <label for="">Opaco</label>
                <input type="checkbox" v-model="opaco" />
            </div>
            <div class="instrucciones__subcontainer">
                <label for="">Tamaño de letra</label>
                <div class="instrucciones__subcontainer--radio">
                    <div class="instrucciones__tamaño-letra">
                        <input type="radio" v-model="fontSize" value="8px" id="pequenyo" />
                        <label for="pequenyo">Pequeño</label>
                    </div>
                    <div class="instrucciones__tamaño-letra">
                        <input type="radio" v-model="fontSize" value="16px" id="medio" />
                        <label for="medio">Medio</label>
                    </div>
                    <div class="instrucciones__tamaño-letra">
                        <input type="radio" v-model="fontSize" value="32px" id="grande" />
                        <label for="grande">Grande</label>
                    </div>
                </div>
            </div>
        </section>
        <section class="creacion" :style="{ backgroundColor, borderRadius: borde + '%', fontFamily, opacity: opaco ? 0.5 : 1 }">
            <div :style="{ backgroundColor }">
                <p :style="{ color: textColor, fontSize }" v-show="showText">{{ text }}</p>
            </div>
        </section>
    </main>
</template>

<style scoped>
main {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    gap: 25px;
}
.instrucciones {
    display: flex;
    flex-direction: column;
    gap: 10px;
    width: 300px;
    background-color: #2f4f4f;
    padding: 25px 20px;
    border-radius: 10px;
    color: white;
}
.instrucciones__subcontainer {
    display: flex;
    flex-direction: column;
    gap: 4px;
    text-align: left;
}
.instrucciones__input {
    padding: 6px;
    border: 1px solid #ccc;
}
.instrucciones__input--range {
    padding: 0;
}
.instrucciones__subcontainer--checkbox {
    flex-direction: row;
}
.instrucciones__subcontainer--radio {
    display: flex;
    flex-direction: row;
    gap: 4px;
}
.instrucciones__tamaño-letra {
    display: flex;
    gap: 6px;
}
.creacion {
    box-sizing: border-box;
    border-radius: 100px;
    display: flex;
    justify-content: center;
    align-items: center;
    min-width: 350px;
    min-height: 350px;
    transition: opacity 0.3s ease-in-out;
    opacity: none;
}
.creacion div p {
    width: 200px;
    white-space: initial;
    overflow: hidden;
    text-overflow: '-';
}
@media (max-width: 768px) {
    main {
        flex-direction: column;
    }
    .instrucciones {
        min-width: 100%;
    }
    .creacion {
        min-width: 100%;
    }
}
@media (max-width: 425px) {
    .instrucciones {
        width: 300px;
    }
}
</style>
