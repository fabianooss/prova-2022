<template>
    <div>
        <h1>Aluno</h1>

        <aluno-form @onSalvar="salvar"></aluno-form>

        <aluno-consulta :alunos="alunos"></aluno-consulta> 

    </div>
</template>

<script>
import AlunoForm from './AlunoForm.vue';
import AlunoConsulta from './AlunoConsulta.vue';
export default {

    data() {
        return {
            alunos: []
        }
    },
    components: {
        AlunoForm, AlunoConsulta
    },
    methods: {
        salvar(aluno){
            this.alunos.push(aluno)
        }
    }

}
</script>

<style>

</style>