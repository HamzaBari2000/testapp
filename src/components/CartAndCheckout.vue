<style>
  @import '../assets/css/styles.css';
</style>

<template>
    <div>
        <center>
            <h1>cart</h1>
        </center>
        <div id="display-cart" v-for='(lesson, index) in cart' :key="index">
            <!--cart is one elemnt of the displayLessonsCart Array-->
            <h1>{{lesson.SubjectName}}</h1>
            <p>Location: {{lesson.Location}}</p>
            <h3>Price: £{{lesson.Price}}</h3>
            <h4>Spaces: {{lesson.Space}}</h4>
            <img v-bind:src="lesson.Image" height="60px" width="60px"><br><br>
            <!--This button removes the lesson from the cart, cart is know as one lesson inside the cart array-->
            <button @click="remove(lesson)">Remove</button>
        </div>
        <div id="checkout-section">
            <!--Displaying Cart Props-->
            <br>
            <h2>Checkout</h2>

            <p>
                <strong>Name:</strong>
                <!-- This input field is for entering the Name. -->
                <input v-model.trim="name" />
            </p>
             <p>
                <strong>Phone Number:</strong>
                <!-- This input field is for entering the Phonenumber. -->
                <input v-model.trim="Phonenumber" />
            </p>

            <h2>Order Information</h2>
            <p>First Name: {{name}}</p>
            <p>Phone Number: {{Phonenumber}}</p>
            <!--If the users inputted name and phoneNo is both true it will display the checkout button else it won't-->
            <!--Once it's true then, the user can purchase-->
            <button>Checkout</button>
        </div>
    </div>

</template>

<script>
export default {
    name: "CartAndCheckout",
    props: ['cart'],
    data() {
        return {
            name: "",
            Phonenumber: "",
        };
    },
    methods: {
        remove(lesson) {
            this.$emit("removeFromCart", lesson);
        }
    },
};
</script>