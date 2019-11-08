<template>
    <div id="courses-container" v-show="show">
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
                <tr v-for="(course, index) in courses" :key='index'>
                    <td>{{index + 1}}</td>
                    <td>{{ course.title }}</td>
                    <td>{{ course.semester }}</td>
                    <td>{{ course.grade }}</td>
                </tr>
            </tbody>
        </table>
        <br>
        <br>
        <div>
            <button id="add-course-button" @click="toggleAddCourse" class="blue-button">+</button>
            <span id="add-course" v-show="addCourseVisible">
                <input class="input" v-model="addedCourseTitle" type="text" placeholder="Course title" id="title">
                <input class="input" v-model="addedCourseSemester"  type="number" min="1" max="8" placeholder="Semester" id="semester">
                <input class="input" v-model="addedCourseGrade"  type="number" min="0" max="100" placeholder="Grade" id="grade">
                <button class="green-button" id="save-course" @click="addNewCourse">Save</button>
                <button class="grey-button" id="cancel-course" @click="clearAddCourseForm">Cancel</button>
            </span>
        </div>
    </div>
</template>

<script>
import Course from '../models/Course'

export default {
    name: 'Courses',
    data: function() {
        return {
            courses :[
                new Course("Agile software development", "1", "82"),
                new Course("System modeling", "1", "85"),
                new Course("Object-oriented programming", "2", "99"),
                new Course("Estonian language Level A2", "2", "65") ],
            addCourseVisible: false,

            addedCourseTitle: "",
            addedCourseSemester: "",
            addedCourseGrade: ""
        }
    },
    props: {
        show: Boolean
    },
    methods: {
        toggleAddCourse: function (){
            this.addCourseVisible= !this.addCourseVisible;
        },
        addNewCourse: function(){
            let newCourse = new Course(this.addedCourseTitle, this.addedCourseSemester, this.addedCourseGrade);
            this.courses.push(newCourse);
            this.clearAddCourseForm();
            this.$emit("courseAdded", this.recalculateGPA)
        },
        clearAddCourseForm: function(){
            this.addedCourseTitle = ""
            this.addedCourseSemester = ""
            this.addedCourseGrade = ""
        }
    },
    computed: {
        recalculateGPA: function(){
            var points = 0;
            for (let i = 0; i < this.courses.length; i++) {
                var point=0;
                if (this.courses[i].grade > 90) {
                    point = 4; 
                } else if (this.courses[i].grade > 80) {
                    point = 3;
                } else if (this.courses[i].grade > 70) {
                    point = 2;
                } else if (this.courses[i].grade > 60) {
                    point = 1;
                } else if (this.courses[i].grade > 50) {
                    point = 0.5;
                } 
                points += point;
            }
            return Math.round(points / this.courses.length* 100) / 100;
        }
    }   
}

</script>

<style>
    .input {
        border: 1px solid #cccccc;
        padding: 10px 20px;
        min-width: 135px;
        margin: 2px;
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
        margin-right: 2px;
    }

    .grey-button {
        background-color: #e1e8e6;
        color: #ffffff;
        border: none;
        padding: 10px 20px;
    }
</style>