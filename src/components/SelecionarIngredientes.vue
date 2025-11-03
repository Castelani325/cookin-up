<script lang="ts">
import { obterCategoria } from '@/assets/http'; 
import ICategorias from '@/interfaces/ICategoria';

export default {
    data() {
        return {
            categorias: [] as ICategorias[]
        }
    },
    async created () {
        this.categorias = await obterCategoria();
    }


  }

</script>
<template>
    <section class="selecionar-ingredientes">
        <h1 class="cabecalho titulo-ingredientes">Ingredientes</h1>
        <p class="paragrafo-lg instrucoes">
            Selecione os ingredientes que você tem em casa para encontrar receitas deliciosas!
        </p>

        <ul class="categorias">
            <li v-for="categoria in categorias"  key="categoria.nome">
            {{ categoria.nome }}
            </li>
        </ul>

        <p class="paragrafo dicas">
            *Atenção : consideraremos que você tem água, sal e pimenta em casa.
        </p>

    </section>

</template>

<style>
.selecionar-ingredientes {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.titulo-ingredientes {
    color: var(--verde-medio, #3D6D4A);
    display: block;
    margin-bottom: 1.5rem;
}

.instrucoes {
    margin-bottom: 2rem;
}

.categorias {
    margin-bottom: 1rem;
    display: flex;
    justify-content: center;
    gap: 1.5rem;
    flex-wrap: wrap;
}

.dica {
    align-self: flex-start;
    margin-bottom: 3.5rem;
}

@media only screen and (max-width: 767px) {
    .dica {
        margin-bottom: 2.5rem;
    }
}
</style>