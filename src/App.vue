<template>
    <main id="app">
        <app-header></app-header>
        <section id="container">
            <section id="main">
                <div class="content">
                    <Profile :user="user" :show="profileActive"/>
                    <Courses :show="coursesActive"></Courses>
                </div>
                <div class="controls">
                    <button id="profile-button" @click="togglePill" :class="{pill: true, active: profileActive}">Profile</button>
                    <button id="courses-button" @click="togglePill" :class="{pill: true, active: coursesActive}">Courses</button>
                </div>
            </section>
        </section>
        <app-footer></app-footer>
    </main>
</template>

<script>
    import Header from './components/Header.vue'
    import Footer from './components/Footer.vue'
    import Profile from './components/Profile.vue'
    import Courses from './components/Courses.vue'
    import User from './models/User'

    export default {
        name: 'app',
        components: {
            'app-header': Header,
            'app-footer': Footer,
            Profile,
            Courses
        },
        data: () => {
            return { 
               user: new User("Johni", "Doe", "11/10/1990", "Software Engineering", "2.75"),
               profileActive: false,
               coursesActive: true
            }
        },
        methods: {
            togglePill: function(){
                this.coursesActive = !this.coursesActive;
                this.profileActive = !this.profileActive;
                // if(!this.profileActive){
                //     this.profileActive = true
                //     this.coursesActive =false
                // }else{
                //     this.profileActive = false
                //     this.coursesActive = true
                // }
            }
        }
    }
</script>

<style>
    * {
        box-sizing: border-box;
        font-family: 'Livvic', sans-serif;
    }

    html, body {
        padding: 0;
        margin: 0;
        width: 100%;
        height: 100%;
        background-color: #eaeaea;
    }

    main {
        position: relative;
        min-height: 100%;
        padding-bottom: 110px;
    }

    .clear-fix {
        clear: both;
    }

    footer {
        padding: 30px 0;
        background-color: #607D8B;
        margin-top: 10px;
        height: 100px;
        position: absolute;
        bottom: 0;
        width: 100%;
    }

    footer .links {
        display: block;
        width: 100%;
        max-width: 200px;
        margin: 0 auto;
        color: #acd7ff;
        font-size: 11px;
    }

    footer .links a {
        text-decoration: none;
        color: #acd7ff;
    }

    footer .links a:hover {
        text-decoration: underline;
    }

    #container {
        width: 80%;
        max-width: 900px;
        min-width: 320px;
        padding: 15px;
        background-color: #ffffff;
        margin: 0 auto;
    }


    .content {
        padding: 10px;
        border: 1px solid #cbcbcb;
    }

    table {
        width: 100%;
        border-collapse: collapse;

    }

    table th {
        padding: 8px 12px;
        text-align: left;
        border: 1px solid #cbcbcb;
        background-color: #03A9F4;
        color: #ffffff;
    }

    table td {
        padding: 8px 12px;
        border: 1px solid #cbcbcb;
    }

    .content .tab {
        display: none;
    }

    .content .tab.active {
        display: block;
    }

    .controls .pill {
        border: 1px solid #cbcbcb;
        background-color: #eaeaea;
        padding: 10px;
        border-bottom-left-radius: 4px;
        border-bottom-right-radius: 4px;
        border-top: none;
        margin-top: -1px;
        outline: none !important;
    }

    .controls .pill.active {
        background-color: #ffffff;
        border-top: 1px solid #ffffff;
    }

    .controls .pill:hover {
        cursor: pointer;
    }


</style>
