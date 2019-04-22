<template>
    <div>
    {{howdy}}
    </div>
</template>

<script>
    export default {
        data() {
            return {
                howdy:"string howdy hello"
            }
        },
        methods: {
            putOnScreen(){
                this.howdy = "has been updated to say goodbye"
            }
        },
    }
</script>

<style lang="scss" scoped>
div{
    color:blue
}

</style>