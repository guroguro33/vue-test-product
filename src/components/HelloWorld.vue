<template>
  <div class="hello">
    <h1>{{ book.title }}</h1>
    <h2>{{ book.author }}</h2>
    <h2>{{ book.year }}</h2>
    <h3>{{ msg }}</h3>

    <h2>{{ fullName }} {{ this.user.age }}</h2>
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';

interface Book{
  title: string;
  author: string;
  year: number;
}

export interface User {
  firstName: string;
  lastName: string;
  age: number;
}

export default defineComponent({
  name: 'HelloWorld',
  data() {
    return {
      book: {
        title: 'Vue 3 Guide',
        author: 'Vue Team',
        year: 2021,
      } as Book
    }
  },
  props:{
    msg:{
      type: Number as PropType<number>
    },
    user: {
      type: Object as PropType<User>,
      required: true,
    }
  },
  computed: {
  getLength(): number{
    return this.book.title.length
  },
  fullName(): string {
    return this.user.firstName + ' ' + this.user.lastName;
  },
  // methods:{
  //   changeMsg(){
  //     this.book.year = 2022;
  //   }
  // },
  }
});
</script>