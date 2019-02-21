<template>
	<div id="team-composition">
		<div id="team" class="team" v-for="team in teams" v-model="teams">
			<div id="monster" class="monster" v-for="mon in team">
				<h2>{{ mon }}</h2>
			</div>
		</div>

		<div id="select-team" class="team">
			<div class="monster">
				<h2>Name</h2>
				
				<select v-model="selectedMonsters[0]" @change="updateMonsters(selectedMonsters[0], 0)" >
					<option value="" >Select first monster...</option>
					<option v-for="(monster, index) in monsterList" v-if="monster == false">
						{{index}}						
					</option>
				</select>
				<p>Selected: {{ monsters[0] }} </p>
			</div>
			<div class="monster">
				<h2>Name</h2>
				
				<select v-model="selectedMonsters[1]" @change="updateMonsters(selectedMonsters[1], 1)" >
					<option value="" >Select second monster...</option>
					<option v-for="(monster, index) in monsterList" v-if="monster == false">
						{{index}}						
					</option>
				</select>
				<p>Selected: {{ monsters[1] }} </p>
			</div>
			<div class="monster">
				<h2>Name</h2>
				
				<select v-model="selectedMonsters[2]" @change="updateMonsters(selectedMonsters[2], 2)" >
					<option value="" >Select third monster...</option>
					<option v-for="(monster, index) in monsterList" v-if="monster == false">
						{{index}}						
					</option>
				</select>
				<p>Selected: {{ monsters[2] }} </p>
			</div>
			<div class="monster">
				<h2>Name</h2>
				
				<select v-model="selectedMonsters[3]" @change="updateMonsters(selectedMonsters[3], 3)" >
					<option value="" >Select fourth monster...</option>
					<option v-for="(monster, index) in monsterList" v-if="monster == false">
						{{index}}						
					</option>
				</select>
				<p>Selected: {{ monsters[3] }} </p>
			</div>
			<div class="monster">
				<h2>Name</h2>
				
				<select v-model="selectedMonsters[4]" @change="updateMonsters(selectedMonsters[4], 4)" >
					<option value="" >Select fifth monster...</option>
					<option v-for="(monster, index) in monsterList" v-if="monster == false">
						{{index}}						
					</option>
				</select>
				<p>Selected: {{ monsters[4] }} </p>
			</div>
			<div class="monster">
				<h2>Name</h2>
				
				<select v-model="selectedMonsters[5]" @change="updateMonsters(selectedMonsters[5], 5)" >
					<option value="" >Select sixth monster...</option>
					<option v-for="(monster, index) in monsterList" v-if="monster == false">
						{{index}}						
					</option>
				</select>
				<p>Selected: {{ monsters[5] }} </p>
			</div>
			<button id="add-team" v-on:click="addTeam(monsters)">Add team</button>
			<button id="reset-team" v-on:click="resetTeam">Reset team</button>
		</div>

		<!-- I should probably change each of the above selected monster into a component -->

<!-- 		<div>
			<p v-for="mon in monsters">{{ mon }}</p>
		</div> -->

	</div>
</template>

<script>
	
import Vue from 'vue'

export default{
	data(){
		return{
			selectedMonsters: [
				"none",
				"none",
				"none",
				"none",
				"none",
				"none"
			],

			selected: true,
			teamSize: 0,
			teams: {
			},
			monsterList: {
				"A Monster name 1": false,
				"B Monster name 2": false,
				"K Monster name 3": false,
				"L Monster name 4": false,
				"P Monster name 5": false,
				"JJ Monster name 6": false,
				"JK Monster name 7": false,
				"JD Monster name 8": false,
				"none": false
			},
			monsters: [
				"none",
				"none",
				"none",
				"none",
				"none",
				"none"
			],

		}
	},
	methods:{
		addTeam(monsters){
			// this.teams.set('teamname', monsters);
			var newMonster = [];

			for(var monsterId in monsters){
				// console.log(monsters[monsterId]);
				newMonster.push(monsters[monsterId]);
			}

			this.teamSize ++;
			// this.teams.$set(("KEY" + this.teamSize),newMonster);
			// https://vuejs.org/v2/guide/reactivity.html#Change-Detection-Caveats
			Vue.set(this.teams, "KEY" + this.teamSize, newMonster);
			// this.teams.push(monsters);
			// console.log(monsters);
			console.log(newMonster);
			// console.log(this.teams);
			// https://stackoverflow.com/questions/48198234/v-for-loop-items-not-immediately-updating-in-vue

		},
		updateMonsters(selectedMonster, index){
			// console.log("Selected a monster")
			if(selectedMonster!=undefined){

				if(this.monsters[index]!=""){
					// console.log(this.monsters[index]);
					// console.log(this.monsterList[this.monsters[index]]);
					this.monsterList[this.monsters[index]] = false;
				}
				
				// console.log(selectedMonster);
				// this.monsters[index] = selectedMonster;

				Vue.set(this.monsters, index, selectedMonster);
				this.monsterList[selectedMonster] = true; // by changing the flag, the option gets updated, hence the function is fired twice
			} else {
				// console.log("somehow turned undefined")
			}
			
			
			// this.selected = false;
		},
		resetTeam(){
			for(var monsterId in this.monsters){
				// monster = false;
				this.monsterList[this.monsters[monsterId]] = false;
				this.monsters[monsterId] = "none";
				console.log(this.monsters[monsterId]);
			}
		}
	},
	filters:{
		removeChosen: function(value){
			// return value.toUpperCase();
		}
	}
}

</script>

<style scoped>
.team {
	display: flex;
	margin: 0 auto;
	padding: 10px;
	width: 90%;
	background-color: #333;
	color: #fefefe;
	border: solid #fefefe 3px;
}

.monster {
	width: 200px;
	height: 150px;
	margin: 2px;
	background-color: #fefefe;
	color: #333;
	text-align: center;
}
	
#add-team {
	margin: auto;
	height: 20px;
	width: 100px;
}	
#reset-team {
	margin: auto;
	height: 20px;
	width: 100px;
}	
</style>