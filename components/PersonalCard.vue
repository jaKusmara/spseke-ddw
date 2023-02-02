<script setup>

defineProps(['person', 'editBool', 'name'])

function age({birthday}){
	let currYear = new Date().getFullYear();

	return currYear - birthday.year
}

</script>

<template>

    <section v-bind:class="{'card-container':true,'card':true, 'baby':age(person)<=2, 'adult':age(person)>=18, 'old':age(person)>=100 }">
        <article class="info">
            <div class="name">{{ person.fname }} {{ person.lname }}</div>
			<input v-show="editBool == true" v-bind:model="name" placeholder="Name">
			<div class="birthday">{{ person.birthday.day }}.{{ person.birthday.month }}.{{ person.birthday.year }}</div>
            <div class="age"> {{ age(person) }} <span class="year-title">year</span></div>
          </article>
          <footer class="footer-card">
            <span class="btn edit" @click="$emit('editWasClicked', person)">Edit</span>
            <span class="btn remove" @click="$emit('removeWasClicked', person)">Remove</span>
          </footer>
    </section>

</template>

<style>
</style>