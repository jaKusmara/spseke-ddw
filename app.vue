<template>
    <main>
      <h1>Zoznam ľudí</h1>
      <section class="list">
        <section v-for="person of persons" v-bind:key="person"
        v-bind:class="{'card-container':true,'card':true, 'baby':age(person)<=2, 'adult':age(person)>=18, 'old':age(person)>=100 }"><!--v tomto prípade clase priradíme objekt, ktorého vlastnosti predstavujú jednotlivé triedy a ich hodnoti predstavujú bool vyjadrujúci, kedy sa má daná trieda pridať danému elemntu-->
		<!--alebo takto tu to poriešime ternárnym operátorom...
		<section v-for="person of persons" v-bind:key="person" 
		v-bind:class="person.age>=18 ? 'adult card-container card' : 'card-container card'">
		-->
          <article class="info">
            <div class="name">{{person.fname}} {{person.lname}}</div>
			<div class="birthday">{{person.birthday.day}}.{{person.birthday.month}}.{{person.birthday.year}}</div>
            <div class="age">{{age(person)}} <span class="year-title">year</span></div>
          </article>
          <footer class="footer-card">
            <span class="btn edit">Edit</span>
            <span class="btn remove">Remove</span>
          </footer>
        </section>
      </section>
    </main>
</template>

<script setup>

function age({birthday}){
	let currentDate = new Date();
	let currYear = currentDate.getFullYear();

	return currYear - birthday.year
}

let persons = [
		{
			fname: "Magdalena",
			lname: "Mikulova",
			birthday: {
				day: 25,
				month: 8,
				year: 2000,
			},
		},
		{
			fname: "Mirka",
			lname: "Makovicova",
			birthday: {
				day: 10,
				month: 8,
				year: 2005,
			},
			year: 2010,
		},
		{
			fname: "Hugo",
			lname: "Hugovic",
			birthday: {
				day: 1,
				month: 5,
				year: 2001,
			},
		},
		{
			fname: "Miki",
			lname: "Hric",
			birthday: {
				day: 14,
				month: 4,
				year: 2020,
			},
		},
		{
			fname: "Andrea",
			lname: "Veresova",
			birthday: {
				day: 4,
				month: 5,
				year: 1205,
			},
		},
		{
			fname: "Nora",
			lname: "Mojsejova",
			birthday: {
				day: 1,
				month: 1,
				year: 1111,
			},
		},
	]
</script>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Oswald:wght@200;300;500;600;700&display=swap');
	body {
		font-size: 10px;	
		font-family: 'Oswald', sans-serif;
		padding: 1rem;
		background: rgb(41, 41, 41);
	}
	main {
		display: flex;
		flex-direction: column;
		gap: .75rem;
	}
	.list {
		display: flex;
		gap: 20px;
		flex-direction: row;
		flex-wrap: wrap;
		justify-content: stretch;
		font-size: 1.2rem;
	}

	.btn.edit {
		background: rgb(43, 117, 43);
		border-radius: 0px 0px 0px 10px;
	}
	.btn.remove {
		background: rgb(110, 1, 1);
		border-radius: 0px 0px 10px 0px;
	}

	.card-container {
		flex-grow: 1;
	}
	.card {
		background: rgb(75, 75, 75);
		border: 1px solid #bbb;
		color: rgb(255, 255, 255);
		box-shadow: 0 3px 5px rgba(255, 255, 255, 0.2);
		border-top-width: 5px;
		border-top-color: rgb(26, 102, 179);
		border-radius: 10px;
	}
	.card.adult {
		border-top-color: orange;
	}
	.card.old{
		border-top-color: black;
	}
	.card.baby{
		border-top-color: pink;
	}
	.card:hover {}
	.info {
		padding: 1rem;
		text-align: center;
		font-size: 1.3rem;
	}
	.name {}
	.age {
		font-weight: 300;
		font-size: 1rem;
	}
	.year-title {
		color: #bbbbbb;
	}
	.footer-card {
		display: flex;
	}
	.btn {
		padding: .75rem 2rem;
		color: white;
		width: 50px;
		flex-grow: 1;
		text-align: center;
		transition: .5s;
		font-size: 1rem;
	}

	.btn:hover {
		opacity: .3;
		cursor: pointer;;
	}

	h1{
		text-align: center;
		color: #bbb;
		font-size: 24px;
	}
</style>

