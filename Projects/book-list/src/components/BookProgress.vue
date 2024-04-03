<script setup>
import { computed } from "vue"


const props = defineProps(['books'])


const booksRead = computed(() => {
    return props.books.filter(book => book.isRead).length
})

const booksReadMessage = computed(() => {
    return booksRead.value >= props.books.length ? 
    'Congrats! You read all books!' :
    `${booksRead.value} of ${props.books.length} read books`
})


</script>

<template>

    <div class="books-read">
        <label for="progress">your progress</label>
        <br>
        <progress :value="booksRead" :max="books.length"></progress>
        <p>{{ booksReadMessage }}</p>
    </div>
    
</template>