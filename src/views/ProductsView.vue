<template lang="">
    <div>
        <h1>This is the Products page👌😁 </h1>
    </div>
    <product-comp></product-comp>

    <div>
        <section v-for="book,index in books " :key="index">{{book.title}} {{book.author}}</section>
    </div>
</template>
<script>
import ProductComp from '../components/ProductComp.vue'
export default {
    data(){
        return{
            books:[
 {    title: "The Great Gatsby",    author: "F. Scott Fitzgerald",    year: 1925,    genre: "Literary Fiction",    pages: 180,    publisher: "Charles Scribner's Sons",    isbn: "978-0743273565"  }, 
  {    title: "To Kill a Mockingbird",    author: "Harper Lee",    year: 1960,    genre: "Southern Gothic",    pages: 281,    publisher: "J. B. Lippincott & Co.",    isbn: "978-0446310789"  },
    {    title: "1984",    author: "George Orwell",    year: 1949,    genre: "Dystopian Fiction",    pages: 328,    publisher: "Secker & Warburg",    isbn: "978-0451524935"  }, 
     {    title: "Pride and Prejudice",    author: "Jane Austen",    year: 1813,    genre: "Romance",    pages: 279,    publisher: "Thomas Egerton",    isbn: "978-0141439513"  }, 
      {    title: "The Catcher in the Rye",    author: "J.D. Salinger",    year: 1951,    genre: "Coming-of-age Fiction",    pages: 214,    publisher: "Little, Brown and Company",    isbn: "978-0316769488"  }
            ]
        }
    },
     components:{ProductComp
}
}
</script>
<style scoped>
h1{
    color: blueviolet;
}

    
</style>