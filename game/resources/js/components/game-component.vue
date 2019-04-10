<template>
    <div class="container">
        <div> <h1>{{changeTurnTitle}}</h1></div>
        <div class="row">
            <div class="col-4" v-for="tile in sTiles" :key="tile.id">
                <tilecomponent v-bind:tileid="tile.id" v-bind:tilevalue="tile.value" v-on:onClickedTile="changeTileValue"></tilecomponent>
            </div>
        <div id="resetButton">
			<button size="lg" @click="resetAll()"> Reset</button>
        </div>
        </div>
    </div>
</template>

<script>
    import tilecomponent from "./tile-component"
    export default {
        name: "game-component",
        data() {
            return {
                sTiles: [
                    {id:1, value:""},
                    {id:2, value:""},
                    {id:3, value:""},
                    {id:4, value:""},
                    {id:5, value:""},
                    {id:6, value:""},
                    {id:7, value:""},
                    {id:8, value:""},
                    {id:9, value:""}],
                title:"Let's Play a Game!",
                turns: ["O", "X"],
                count: 0,
            };
        },
        components:{
            tilecomponent
        },
        methods: {
            changeTileValue(tileObject){
                if (this.sTiles[tileObject.id - 1].value==""){
                    console.log(tileObject.id);
                    this.count++;
                    this.sTiles[tileObject.id - 1].value = this.turns[this.count % 2];
                    this.winner();
                }
            },
            resetAll (){
                // loop thru the sTiles array and change all values to ""
                for (var i=0; i<this.sTiles.length; i++){
                  this.sTiles[i].value = "";
                  this.count =0;
                }

            },
            winner (){
                console.log("im at the top of winner");
                for (var i=0;i<3;i++){
                    if (this.sTiles[i].value   == "O" && 
                        this.sTiles[i+3].value == "O" && 
                        this.sTiles[i+6].value == "O"){
                        alert("O Wins!");
                    }
                    else if (this.sTiles[i].value == "X" && 
                        this.sTiles[i+3].value == "X" && 
                        this.sTiles[i+6].value == "X"){
                        
                        alert("X Wins!");
                    }
                    console.log("end of first loop")
                }
                for (var i=0;i<3;i++){
                    if (this.sTiles[(i*3)].value   == "O" && 
                        this.sTiles[(i*3)+1].value == "O" && 
                        this.sTiles[(i*3)+2].value == "O"){
                        alert("O Wins!");
                    }
                    else if (this.sTiles[(i*3)].value   == "X" && 
                        this.sTiles[(i*3)+1].value == "X" && 
                        this.sTiles[(i*3)+2].value == "X"){
                        alert("X Wins!");
                    }
                }   
                if (this.sTiles[2].value   == "O" && 
                    this.sTiles[4].value == "O" && 
                    this.sTiles[6].value == "O"){
                    alert("O Wins!");
                }
                else if (this.sTiles[2].value   == "X" && 
                    this.sTiles[4].value == "X" && 
                    this.sTiles[6].value == "X"){
                    alert("X Wins!");
                }
                if (this.sTiles[0].value   == "O" && 
                    this.sTiles[4].value == "O" && 
                    this.sTiles[8].value == "O"){
                    alert("O Wins!");
                }
                else if (this.sTiles[0].value   == "X" && 
                    this.sTiles[4].value == "X" && 
                    this.sTiles[8].value == "X") {
                        console.log("x won in last diag");
                    alert("X Wins!");
                }
            console.log("im in the winner")
            }


        
        },
        computed: {
            changeTurnTitle (){
                var str = this.title;
                if(this.count != 0){
                    var i = this.count % 2; // 1, 0
                    if(i == 0){
                        i = 1;
                    } else {
                        i = 0;
                    }
                    str = "Player " + this.turns[i] + "'s Turn";
                }
                return str;
            }
        }
    }
</script>
