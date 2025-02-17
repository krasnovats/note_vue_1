<script>
export default {
    data () {
        return {
           isActive: false, 
        }
    },
    methods: {
        toggleMenu () {
            this.isActive = !this.isActive;
            this.$emit('toggle-style');
        }
    }
}
</script>

<template>
    <div class="header">
        <div class="container">
            <div @click="toggleMenu" class="burger">
                <span class="burger_line" :class="{'active': isActive}"></span>
                <span class="burger_line" :class="{'active': isActive}"></span>
                <span class="burger_line" :class="{'active': isActive}"></span>
            </div>
        </div>
    </div>
</template>


<style>
    .header {
        padding: 20px 0;
        background-color: rgb(225, 234, 253);
    }

    .container {
        max-width: 1200px;
        margin: 0 auto;
        padding-inline: 20px;
    }
    .burger {
        width: 26px;
        height: 20px;
        cursor: pointer;
        display: flex;
        flex-direction: column;
        justify-content: center;
        gap: 7px;
    }

    .burger_line {
        display: block;
        height: 2px;
        width: 100%;
        background-color: black;       
        transition: all 0.3s ease;     
    }

    .burger_line.active:nth-child(2) {
        opacity: 0;
    }

    .burger_line.active:nth-child(1) {
        transform: translateY(9px) rotate(45deg);
    }

    .burger_line.active:nth-child(3) {
        transform: translateY(-8px) rotate(-45deg);
    }

</style>