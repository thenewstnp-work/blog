<template>
    <div id="single-blog">
        <h1>{{blog.title}}</h1>
        <article>{{blog.body}}</article>
    </div>
</template>

<script>
export default {
    name: "single-blog",
    data() {
        return {
           id: this.$route.params.id,
           blog: {} 
        }
    },
    created() {
        this.$http.get("http://jsonplaceholder.typicode.com/posts/"+ this.id).then(data => {
            // console.log(data);
            this.blog = data.body;
        })
    }
}
</script>

<style scoped>
#single-blog{
    max-width: 840px;
    margin: 0 auto;
    padding: 10px 20px;
    background: #eee;
    border: 1px dotted #eee;
}
</style>


