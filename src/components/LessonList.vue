<style>
  @import '../assets/css/styles.css';
</style>

<template> 
  <main>
    <div id="sort-section">
      <h1>Sorting By:</h1>
      <!--V-model - Sort will automatically pick up changes and update the data on screen-->
      <select v-model="sort" v-on:change="sortLessons">
        <!--Accroding to each value of the switch case it will execute that case/function and sort those subjects.-->
        <option :value="1">Subject Name: A to Z</option>
        <option :value="2">Subject Name: Z to A</option>
        <option :value="3">Location: A to Z</option>
        <option :value="4">Location: Z to A</option>
        <option :value="5">Price: Cheap to Expensive</option>
        <option :value="6">Price: Expensive to Cheap</option>
        <option :value="7">Availability: High to Low</option>
        <option :value="8">Availability: Low to High</option>
      </select>
    </div>
    <div id="main" v-for="(lesson, index) in lessons" :key="index">
      <h1>Subject Name: {{lesson.SubjectName}}</h1>
      <h2>Location: {{lesson.Location}}</h2>
      <h3>Price: £{{lesson.Price}}</h3>
      <h4 id="Space">Space: {{lesson.Space}}</h4>
      <figure>
        <img v-bind:src="lesson.Image" height="100" width="100" />
      </figure>
      <button id="add" @click="addLesson(lesson), reduce(index)">Add to cart</button>
    </div>
  </main>
</template>

<script>
export default {
  name: "LessonList",
  props: {
  },
  data() {
    return {
      sort: '',
      lessons: [
        {
          SubjectName: "Maths",
          Location: "London",
          Price: 50.0,
          Space: 5,
          Image: "maths.svg",
        },
        {
          SubjectName: "English",
          Location: "Manchester",
          Price: 30.0,
          Space: 5,
          Image: "english.png",
        },
        {
          SubjectName: "Science",
          Location: "New York",
          Price: 75.0,
          Space: 5,
          Image: "science.png",
        },
        {
          SubjectName: "Computer Science",
          Location: "Birmingham",
          Price: 100.0,
          Space: 5,
          Image: "cs.jpg",
        },
        {
          SubjectName: "History",
          Location: "London",
          Price: 85.0,
          Space: 5,
          Image: "history.png",
        },
        {
          SubjectName: "Geography",
          Location: "New York",
          Price: 85.0,
          Space: 5,
          Image: "geography.png",
        },
        {
          SubjectName: "Religious Education",
          Location: "Leeds",
          Price: 80.0,
          Space: 5,
          Image: "Re.png",
        },
        {
          SubjectName: "Phyical Education",
          Location: "Reading",
          Price: 110.0,
          Space: 5,
          Image: "PhyicalEducation.png",
        },
        {
          SubjectName: "Business",
          Location: "Cape Town",
          Price: 145.0,
          Space: 5,
          Image: "business.png",
        },
        {
          SubjectName: "Information Technology",
          Location: "Amsterdam",
          Price: 25.0,
          Space: 5,
          Image: "IT.png",
        },
      ],
    }
  },
  methods: {
    addLesson(lesson) {
        this.$emit('addLesson', lesson);
    },
    sortLessons() {
      switch(this.sort) {
        case 1:
          this.lessons.sort((a, b) => {    //For High to Low
            if (a.SubjectName > b.SubjectName) {    //If this statement is true then it will return 1.
              return 1;
            } else if (a.SubjectName < b.SubjectName) { //If this statement is true then it will return -1
              return -1;
            } else {
              return 0;   //Else it just returns 0. 
            }
          })
        break;
        case 2:
          this.lessons.sort((a, b) => {    //For Low to High
            if (a.SubjectName > b.SubjectName) {
              return -1;
            } else if (a.SubjectName < b.SubjectName) {
              return 1;
            } else {
              return 0;
            }
          })
        break;
        case 3:
          this.lessons.sort((a, b) => {    //For Low to High
            if (a.Location > b.Location) {
              return 1;
            } else if (a.Location < b.Location) {
              return -1;
            } else {
              return 0;
            }
          })
        break;
        case 4:
          this.lessons.sort((a, b) => {    //For Low to High
            if (a.Location > b.Location) {
              return -1;
            } else if (a.Location < b.Location) {
              return 1;
            } else {
              return 0;
            }
          })
        break;
        case 5:
          this.lessons.sort((a, b) => {    //For Low to High
            if (a.Price > b.Price) {
              return 1;
            } else if (a.Price < b.Price) {
              return -1;
            } else {
              return 0;
            }
          })
        break;
        case 6:
          this.lessons.sort((a, b) => {    //For Low to High
            if (a.Price > b.Price) {
              return -1;
            } else if (a.Price < b.Price) {
              return 1;
            } else {
              return 0;
            }
          })
        break;
        case 7:
          this.lessons.sort((a, b) => {    //For Low to High
            if (a.Space > b.Space) {
              return 1;
            } else if (a.Space < b.Space) {
              return -1;
            } else {
              return 0;
            }
          })
        break;
        case 8:
          this.lessons.sort((a, b) => {    //For Low to High
            if (a.Space > b.Space) {
              return -1;
            } else if (a.Space < b.Space) {
              return 1;
            } else {
              return 0;
            }
          })
        break;
      }
    },
    reduce(index) {
      this.lessons[index].Space--;
      if (this.lessons[index].Space == 0) {
        document.getElementById("Space").innerHTML = "<h4>Spaces Full</h4>"
        document.getElementById("add").style.visibility = "hidden";
      } 
    }
  },
};
</script>
