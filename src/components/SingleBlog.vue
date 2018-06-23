<template>
    <div id="single-blog">
        <h1>{{blog.title}}</h1>
        <article>{{blog.content}}</article>
        <p>作者：<span>{{blog.author}}</span></p>
        <p class="category">分类：</p>
        <ul class="clear">
            <li v-for="category in blog.categories">
                {{category}}
            </li>
        </ul>
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
        this.$http.get("https://vuedemo-90dd3.firebaseio.com/blogs/"+ this.id + ".json").then(data => {
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
ul{
    list-style-type: none;
    margin: 0;
    padding: 0;
}
.category{
    float: left;
    margin: 0;
}
ul li{
    float: left;
}
</style>


