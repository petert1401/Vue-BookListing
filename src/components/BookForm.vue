<template>
<form v-on:submit.prevent="bookSubmit(bookData)" class="" action="#" method="post">
    <input v-model="bookData.bookTitle" type="text" name="title" value="" placeholder="Book Title">
    <input v-model="bookData.bookAuthor" type="text" name="author" value="" placeholder="Book Author">
    <div>
        <label for='finishedRading'>Finished reading
            <input v-model='bookData.finishedReading' type='checkbox' />
        </label>
        <label for='borrowed'>Borrowed
            <input v-model='bookData.ownership' type='radio' value='borrowed'/>
        </label>
        <label for='bought'>Bought
            <input v-model='bookData.ownership' type='radio' value='bought'/>
        </label>
    </div>
    <button type="submit" name="button">Add Book</button>
</form></template>
<script>
    export default {
        name: 'BookForm',
        props: [
            'books'
        ],
        data() {
            return {
                bookData: {
                    bookTitle: '',
                    bookAuthor: '',
                    finishedReading: false,
                    ownership: []
                }
            }
        },
        methods: {
            bookSubmit(bookData) {
                this.$emit('addBook', bookData.bookTitle, bookData.bookAuthor);
            }
        }
    }
</script>
<style>
    li {
        display: block;
        margin: 0 10px;

    }
</style>