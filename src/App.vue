<template>
    <main id="app">
        <app-header></app-header>
        <section id="container">
            <section id="main">
                <div class="content">
                    <Profile :user="user"/>
                    <div id="courses-container" class="tab">
                        <h1 class="title">Courses</h1>
                        <table id="courses">
                            <thead>
                            <tr>
                                <th>#</th>
                                <th>Course Title</th>
                                <th>Semester</th>
                                <th>Grade</th>
                            </tr>
                            </thead>
                            <tbody>
                            <tr>
                                <td>1</td>
                                <td>Agile software development</td>
                                <td>1</td>
                                <td>82</td>
                            </tr>
                            <tr>
                                <td>2</td>
                                <td>System modeling</td>
                                <td>1</td>
                                <td>85</td>
                            </tr>
                            <tr>
                                <td>3</td>
                                <td>Object-oriented programming</td>
                                <td>2</td>
                                <td>99</td>
                            </tr>
                            <tr>
                                <td>4</td>
                                <td>Estonian language Level A2</td>
                                <td>2</td>
                                <td>65</td>
                            </tr>
                            </tbody>
                        </table>
                        <br>
                        <br>
                        <div>
                            <button id="add-course-button" class="blue-button">+</button>
                            <span id="add-course">
                                <input class="input" type="text" placeholder="Course title" id="title">
                                <input class="input" type="number" min="1" max="8" placeholder="Semester" id="semester">
                                <input class="input" type="number" min="0" max="100" placeholder="Grade" id="grade">
                                <button class="green-button" id="save-course">Save</button>
                                <button class="grey-button" id="cancel-course">Cancel</button>
                            </span>
                        </div>
                    </div>
                </div>
                <div class="controls">
                    <button id="profile-button" class="pill active">Profile</button>
                    <button id="courses-button" class="pill">Courses</button>
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
    import User from './models/User'

    export default {
        name: 'app',
        components: {
            'app-header': Header,
            'app-footer': Footer,
            Profile
        },
        data: () => {
            return { 
               user: new User("Johni", "Doe", "11/10/1990", "Software Engineering", "2.75")
                
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

    .blue-button {
        background-color: #2196F3;
        color: #ffffff;
        border: none;
        padding: 10px 20px;
    }

    .green-button {
        background-color: #69f378;
        color: #ffffff;
        border: none;
        padding: 10px 10px;
    }

    .grey-button {
        background-color: #e1e8e6;
        color: #ffffff;
        border: none;
        padding: 10px 20px;
    }

    .input {
        border: 1px solid #cccccc;
        padding: 10px 20px;
        min-width: 135px;
    }

    #add-course {
        display: none;
    }
</style>
