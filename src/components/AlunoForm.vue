<template>
  <div class="form">
    <form @submit.prevent="salvar()">
        <label>Nome</label>
        <input type="text" v-model="nome" size="50" required/>
        <br/>

        <label>Nota 1</label>
        <input type="number" step="0.01" v-model="nota1" size="50"/>
        <br/>

        <label>Nota 2</label>
        <input type="number" step="0.01" v-model="nota2" size="50"/>
        <br/>

        <label>Nota 3</label>
        <input type="number" step="0.01" v-model="nota3" size="50"/>
        <br/>


        <input type="submit" value="Salvar"/>
    </form>

  </div>
</template>

<script>
export default {
    data() {
        return {
            nome: '',
            nota1: null,
            nota2: null,
            nota3: null
        }
    },
    methods: {
        salvar() {
            // validações
            const aluno = {
                nome: this.nome,
                media: this.getMedia(),
                situacao: this.getMedia() >= 7 
                            ? 'Aprovado' 
                            : 'Reprovado'
            }
            this.$emit('onSalvar', aluno)
            this.limparForm()    
        },
        limparForm() {
            this.nome = ''
            this.nota1 = null
            this.nota2 = null
            this.nota3 = null
        },
        getMedia() {
            return (this.nota1 + (this.nota2 * 2) 
                    + (this.nota3 * 3)) / 6
        }
    }

}
</script>

<style>

    .form {
        background-color: antiquewhite;
        border: 1px solid silver;
        padding: 24px;
    }

</style>