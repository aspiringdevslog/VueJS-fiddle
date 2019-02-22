<template>
	<div id="optimize-monster-rune">
		<h2>{{ title }}</h2>
		<button v-on:click="optimizeRune" > Optimize</button>

		<div class="monster-holder">
			{{ computeTotalStats() }}
			<div id="monster-status" v-for="(monster, index) in equippedrunes">
				<h2>{{ index }}</h2>
				<p>Total Speed: 
					{{    
						totalSpeed
					}} 
					
				</p>
				 <!-- {{ monster }} -->
				<div id="equipped-runes" v-for="(runes, key) in monster" >
					<!-- Key: {{ key }} -->
					<div v-if="key == 'totalStats'">
						{{ key }}
						<div v-for="(value, stat) in runes">
							{{stat}}: {{value}}
						</div>
					</div>

					<ul v-else-if="key == 'equipped'">
						<li id="individual-rune" v-for="(rune, index) in runes">
							<!-- {{ rune }} -->
							<h3> Rune Slot {{ index +1 }} </h3>
							<div v-for="(value, stat) in rune">
								{{ stat }} : {{ value }}
								<!-- {{ computeSpeed(stat, value) }} -->
							</div>
						</li>
					</ul>

					
				</div>
			</div>	
		</div>
		


		<div id="runes">

			<div id="runes-slot" class="runes-slot" v-for="(runes, runeslot) in runesList">
				{{ runeslot }}
				
				<ul>
					<li v-for="rune in runes"> 
						<div v-for="(value, key) in rune"><strong>{{ key }} </strong>: {{ value }} </div>
					</li>
				</ul>
				
			</div>
			
		</div>



	</div>
</template>

<script>
	
	export default{
		data(){
			return{
				totalSpeed : 0,
				title: 'Optimize Runes',
				
				equippedrunes: {
					monsterName1: {
						equipped: [
							{
								Atkf: 100,
								Spd: 20,
								HPp: 10,
								HPf: 10,
								Acc: 7,
								MonsterID: ""
							},
							{
								Atkf: 100,
								Spd: 20,
								HPp: 10,
								HPf: 10,
								Acc: 7,
								MonsterID: ""
							},
							{
								Atkf: 100,
								Spd: 20,
								HPp: 10,
								HPf: 10,
								Acc: 7,
								MonsterID: ""
							},
							{
								Atkf: 100,
								Spd: 20,
								HPp: 10,
								HPf: 10,
								Acc: 7,
								MonsterID: ""
							},
							{
								Atkf: 100,
								Spd: 20,
								HPp: 10,
								HPf: 10,
								Acc: 7,
								MonsterID: ""
							},
							{
								Atkf: 100,
								Spd: 20,
								HPp: 10,
								HPf: 10,
								Acc: 7,
								MonsterID: ""
							},
						],
						totalStats: {
							Speed: 10,
							'HP%' : 60,
							'DEF%' : 123,
							DEFflat : 608
						}

					},
					monsterName2: {
						equipped: [
							"a",
							"b",
							"c",
							"d",
							"e",
							"f"
						]
					},
					monsterName3: {
						equipped: [
							"a",
							"b",
							"c",
							"d",
							"e",
							"f"
						]
					},
					monsterName4: {
						equipped: [
							"a",
							"b",
							"c",
							"d",
							"e",
							"f"
						]
					},
					monsterName5: {
						equipped: [
							"a",
							"b",
							"c",
							"d",
							"e",
							"f"
						]
					},
					monsterName6: {
						equipped: [
							"a",
							"b",
							"c",
							"d",
							"e",
							"f"
						]
					},
					monsterName7: {
						equipped: [
							"a",
							"b",
							"c",
							"d",
							"e",
							"f"
						]
					},
					monsterName8: {
						equipped: [
							"a",
							"b",
							"c",
							"d",
							"e",
							"f"
						]
					},
					monsterName9: {
						equipped: [
							"a",
							"b",
							"c",
							"d",
							"e",
							"f"
						]
					}
				},
				runesList: {
					slotOne:{
						1: {
							Atkf: 100,
							Spd: 20,
							HPp: 10,
							HPf: 10,
							Acc: 7,
							MonsterID: ""
						},
						2: {
							Atkf: Math.random(1,100),
							Spd: Math.random(10,100),
							AtkP: Math.random(10,100),
							Acc: Math.random(10,100),
							Res: Math.random(10,100),
							MonsterID: ""
						}, 
						3: {
							Atkf: Math.random(10,100),
							Spd: Math.random(10,100),
							AtkP: Math.random(10,100),
							Acc: Math.random(10,100),
							Res: Math.random(10,100),
							MonsterID: ""
						}, 
						4: {
							Atkf: Math.random(10,100),
							Spd: Math.random(10,100),
							AtkP: Math.random(10,100),
							Acc: Math.random(10,100),
							Res: Math.random(10,100),
							MonsterID: ""
						}, 
						5: {
							Atkf: Math.random(10,100),
							Spd: Math.random(10,100),
							AtkP: Math.random(10,100),
							Acc: Math.random(10,100),
							Res: Math.random(10,100),
							MonsterID: ""
						}, 
						6:{
							Atkf: Math.random(10,100),
							Spd: Math.random(10,100),
							AtkP: Math.random(10,100),
							Acc: Math.random(10,100),
							Res: Math.random(10,100),
							MonsterID: ""
						}
					}, 
					slotTwo:{
						1: {
							Atkf: 100,
							Spd: 20,
							HPp: 10,
							HPf: 10,
							Acc: 7,
							MonsterID: ""
						},
						2: {
							Atkf: Math.random(1,100),
							Spd: Math.random(10,100),
							AtkP: Math.random(10,100),
							Acc: Math.random(10,100),
							Res: Math.random(10,100),
							MonsterID: ""
						}, 
						3: {
							Atkf: Math.random(10,100),
							Spd: Math.random(10,100),
							AtkP: Math.random(10,100),
							Acc: Math.random(10,100),
							Res: Math.random(10,100),
							MonsterID: ""
						}, 
						4: {
							Atkf: Math.random(10,100),
							Spd: Math.random(10,100),
							AtkP: Math.random(10,100),
							Acc: Math.random(10,100),
							Res: Math.random(10,100),
							MonsterID: ""
						}, 
						5: {
							Atkf: Math.random(10,100),
							Spd: Math.random(10,100),
							AtkP: Math.random(10,100),
							Acc: Math.random(10,100),
							Res: Math.random(10,100),
							MonsterID: ""
						}, 
						6:{
							Atkf: Math.random(10,100),
							Spd: Math.random(10,100),
							AtkP: Math.random(10,100),
							Acc: Math.random(10,100),
							Res: Math.random(10,100),
							MonsterID: ""
						}
					}, 
				}
			
			}
		},
		methods: {
			optimizeRune(){

			},
			computeSpeed(stat, value){
				if(stat == "Spd"){
					console.log(value);
					this.totalSpeed += Number(value);
				}
			},
			computeTotalStats(){
				for(var monsterkey in this.equippedrunes){
					console.log(monsterkey);
					for(var rune in this.equippedrunes[monsterkey]){
						console.log(this.equippedrunes[monsterkey][rune]);
						for(var stat in rune){
							console.log(this.equippedrunes[monsterkey][rune][stat]);
						}
					}
				}
			}
		}
	}

</script>

<style scoped>
#optimize-monster-rune {
	background-color: #fdfdfd;
	border: 2px solid #333;
	padding: 20px;
}

#runes {
	display: flex;
	flex-direction: 
}

.monster-holder{
	display: flex;
	flex-wrap: wrap;
	width: 100%;
	border: 2px solid #222;
}

#monster-status {
	width: 20%;
	background-color: #222;
	color: #fdfdfd;
	padding: 20px;
	border: 2px solid #fdfdfd;
	margin: auto;
}

.runes-slot {
	width: 200px;
	border: 2px solid #333;
	padding: 10px;
	margin: 10px;
}
ul {
	padding: 0;
}

li {
	border: 1px solid #555;
	padding: 2px;
	list-style: none;
	margin: 0 auto;
	text-align: center;
}
</style>