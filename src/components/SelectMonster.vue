<template>
	<div class="monster">
		<h2>Name</h2>
		
		<select v-model="selectedMonsters" @change="updateMonsters(selectedMonsters, 1)" >
			<option value="" >Select second monster...</option>
			<option v-for="(monster, index) in monsterList" v-if="monster == false">
				{{index}}						
			</option>
		</select>
		<p>Selected: {{ monsters[1] }} </p>
	</div>



	</div>
</template>

<script>
	
import Vue from 'vue'

export default{
	data(){
		return{
			selectedMonsters
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