<template> 
  <main>
    <div v-for="lesson in lessons" :key="lesson.SubjectName">
      <h1>Subject Name: {{lesson.SubjectName}}</h1>
      <h2>Location: {{lesson.Location}}</h2>
      <h3>Price: {{lesson.Price}}</h3>
      <h4>Space: {{lesson.Space}}</h4>
      <figure>
        <img v-bind:src="lesson.Image" height="100" width="100" />
      </figure>
      <button @click="addLesson(lesson)">Add to cart</button>
    </div>
  </main>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
  },
  data() {
    return{
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

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
