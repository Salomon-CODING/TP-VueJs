<script>
import ChildComponent from './ChildComponent.vue';

let id=0;

export default {
    mounted() {
        this.$refs.parag.textContent = 'Texte changé avec Mounted()';
    },
    data() {
        return {
            add: 0,
            button1_id: "",
            textInput: "",
            awesome: true,
            newTodo: '',
            saluer: 'Bonjour avec une propriété',
            todos: [
                { id: id++, text: 'Learn HTML' },
                { id: id++, text: 'Learn JavaScript' },
                { id: id++, text: 'Learn Vue' }
            ]
        }
    },
    methods: {
        increment() {
            this.add++;
            this.button1_id = "button1"
        },
        onInputFunction(e) {
            this.textInput = e.target.value
        },
        changeIf() {
            this.awesome = !this.awesome;
        },
        addTodo() {
            this.todos.push({id: id++, text: this.newTodo});
            this.newTodo = '';
        },
        removeTodo(todo) {
            this.todos = this.todos.filter((t) => t !== todo);
        }
    },
    components: {
    ChildComponent
}

}
</script>

<!-- 
    ------Notes------
    v-bind: pour ajouter des attributs depuis VueJs; exemple: v-bind:id="nomIDdansledata" (ou juste :id="nomIDdansledata")
    v-on: 
        pour ajouter des evenements; 
        exemple: v-on:click="nom_de_la_fonction" le nom de la fonction est mis sans les parentheses
        (ou juste @click="increment" par exemple)    
-->

<template>
    <div class="firstPart">
        <h1 :id="button1_id">Okay GO !</h1>
        <button @click="increment">Incrementer : {{ add }}</button> <br>
        <input id="input1" :value="textInput" @input="onInputFunction" placeholder="Entrer du texte.."/>
        <p>{{textInput}}</p>

        <button @click="changeIf">Changer</button>
        <h4 v-if="awesome">Vue est impressionnant</h4>
        <h4 v-else>C'est Parti..</h4>

        <h2>ToDo List</h2>
        <form @submit.prevent="addTodo">
            <input v-model="newTodo"> <!-- v-model: combine un v-bind et un v-on pour les Inputs -->
            <button>Add Todo</button>    
        </form>
        <ul>
            <li v-for="todo in todos" :key="todo.id">
            {{ todo.text }}
            <button @click="removeTodo(todo)">X</button>
            </li>
        </ul> 
        <p ref="parag">Text</p>
        <!-- <ChildComponent msg="Mon Bonjour avec une propriété." /> -->
        <ChildComponent :msg="saluer" />
    </div>
</template>

<style>
    #button1 {
        background-color: #4CAF50; /* Green */
        border: none;
        color: white;
        padding: 5px 15px;
        margin-right: 10px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 16px;
    }
    #input1 {
        padding: 5px 5px;
        margin: 8px 0;
    }

</style>