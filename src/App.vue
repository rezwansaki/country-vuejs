<template>
    <div>
        <header>
            <div class="container">
                <nav class="navbar navbar-expand-lg navbar-light bg-light">
                    <a class="navbar-brand d-flex align-items-center">
                        <img :src="siteLogo" alt="logo" height="32">
                        <strong>{{siteTitle}}</strong>
                    </a>
                    <div class="navbar-nav">
                        <button class="nav-item nav-link btn btn-sm" @click.prevent="componentToRender='compHome'">Home</button>
                        <button class="nav-item nav-link btn btn-sm" @click.prevent="componentToRender='compAbout'">About</button>
                        <button class="nav-item nav-link btn btn-sm" @click.prevent="componentToRender='compContact'">Contact</button>
                    </div>
                </nav>
            </div>
        </header>

        <component :is="componentToRender"></component>
        <compFooter></compFooter>
    </div>
</template>

<script>
import compHome from './Components/HomePage'
import compAbout from './Components/About'
import compContact from './Components/Contact'
import compFooter from './Components/Footer'
export default {
    data(){
        return{
            siteTitle: 'Country',
            siteLogo: 'earth.png',
            componentToRender: 'compHome'
        }
    },
    components: {
        compHome,
        compAbout,
        compContact,
        compFooter
    }
}
</script>

<style>

</style>