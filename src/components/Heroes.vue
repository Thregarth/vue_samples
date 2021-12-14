<template>
    <div class="container">
        <div class="form-group">
            <label for>New Hero</label>
            <input type="text" class="form-control" name id aria-describedby="helpId" placeholder v-model="newHero.name" />
            <small id="helpId" class="form-text text-muted" v-if="newHero.length === 0" >hero name should not be empty</small>
        </div>
        <div class="form-group">
            <label for>Hero Descripcion</label>
            <input type="text" class="form-control" name id aria-describedby="helpId" placeholder v-model="newHero.description" />
            <small id="helpId" class="form-text text-muted">(Optional)</small>
        </div>
        <button type="button" class="btn btn-primary" @click="addHero()" v-bind:disabled="newHero.length === 0">Add Hero</button>

        <ul class="list-group mt-3">
            <li class="list-group-item" v-for="(hero, index) in heroes" :key="index">
               <span>{{hero.name}}</span> <br/>
               <small>{{hero.description}}</small>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'Heroes',
    data() {
        return {
            newHero: {},       
            heroes: [
                {name:'Spiderman', description: 'Peter Parker'}, 
                {name:'Ironman', description: 'Tony Stark'},
                {name:'Hulk', description: 'Bruce Banner'},
                {name:'Thor', description: 'Odin\'s son'}]
        }
    },
    methods: {
        addHero() {
            if(this.newHero.name.length > 0) {
                this.heroes.push(this.newHero);
                this.newHero = {}
            }
        }
    }
}
</script>

<style lang="scss" scoped>
</style>