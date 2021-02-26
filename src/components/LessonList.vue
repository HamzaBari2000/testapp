<style>
  @import '../assets/css/styles.css';
</style>

<template> 
  <main>
    <div id="main" v-for="(lesson, index) in lessons" :key="index">
      <h1>Subject Name: {{lesson.SubjectName}}</h1>
      <h2>Location: {{lesson.Location}}</h2>
      <h3>Price: {{lesson.Price}}</h3>
      <h4>Space: {{lesson.Space}}</h4>
      <span v-if='lesson.Space === 0'>
        <h4>Spaces Full</h4>
      </span>
      <span v-else-if="lesson.Space - cartCount(lesson) < 5">
        <h4>Available Spaces: {{lesson.Space - cartCount(lesson)}}</h4>
      </span>
      <figure>
        <img v-bind:src="lesson.Image" height="100" width="100" />
      </figure>
      <button @click="addLesson(lesson)">Add to cart</button>
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
  },
};
</script>
