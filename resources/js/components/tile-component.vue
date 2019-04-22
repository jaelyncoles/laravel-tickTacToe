<template>
	<div>
		<div id="button">
			<button size="lg" @click="click()">
                {{ tilevalue }}
            </button>
		</div>
	</div>
</template>

<script>
    export default {
        name: "tile-component",
        props: {
            tileid: Number,
            tilevalue: String
        },
        data() {
            return {
                title: "Let's Play a Game!",
                beenClicked:false,
                count:0,
            };
        },
        methods: {
            click(){
                console.log(this.tileid);
                this.$emit("onClickedTile", {id: this.tileid});
                    
            }
        },
    };
</script>
