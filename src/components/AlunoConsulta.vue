<template>
  <div>

    <table>
        <tr>
            <th>Nome</th>
            <th>Situação</th>
        </tr>
        <tr v-for="a in alunos" :key="a.nome" 
            :class="{'aprovado' : isAprovado(a), 
                     'reprovado': !isAprovado(a) } ">
            <td>{{a.nome}}</td>
            <td>{{a.situacao}}</td>
        </tr>
    </table>
  </div>
</template>

<script>
export default {
    props: {
        alunos: Array
    },
    methods: {
        isAprovado(aluno) {
            return aluno.media >= 7
        }
    }

}
</script>

<style>

    .aprovado {
        background-color: blue;
        color: white
    }
    .reprovado {
        background-color: red;
        color: white;
    }

</style>