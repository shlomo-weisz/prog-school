<template>

  <div>
    <Student v-for="student in students.users" :key="student.id" :nameStudent="student.lastName" :idStudent="student.id"></Student>
  </div>  
</template>
  
  <script>
  import Student from './components/Student.vue';
  export default {
    name: "App",
    components: {
      Student,
      
    },
    data() {
      return {
        students : [],
      };
    },
    methods: {
      
    },
    mounted() {
      fetch('https://dummyjson.com/users?limit=0')
        .then((response) => response.json())
        .then((data) => {
          this.students = data;
        });
       
    }
  };
  
  </script>
  
  <style>
  div {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background-color: blanchedalmond;
  }
  
  </style>