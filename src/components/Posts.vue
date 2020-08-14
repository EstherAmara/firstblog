<template>
    <section>
        <div class="container">
            <h3 class="p-4"> All Posts </h3>
            <router-link 
            v-for="post in posts" :key="post.id"
            :to="{ name: 'SinglePost', params: { id: post.id }}"
            class="card text-left mt-3 mb-3">
                <div class="row card-body">
                    <div class="col-xl-10">
                        <h5 class="card-title">{{post.title}}</h5>
                        <p class="card-text">{{post.body}}</p>
                    </div>
                    <div class="col-xl-2">
                        <img v-if="post.id % 2 == 0" src="../assets/undraw_male_avatar_323b.svg" alt="">
                        <img v-else src="../assets/undraw_female_avatar_w3jk.svg" alt="">
                    </div>
                </div>
            </router-link>

        </div>
    </section>
</template>

<script>
export default {
    props: {
        posts: Array
    },
    
    mounted: function() {
        fetch('https://jsonplaceholder.typicode.com/posts', {
            method: 'get'
            })
            .then(response => {
            return response.json()
            })
            .then(jsonData => {
            this.posts = jsonData
            })
        }
}
</script>

<style scoped>
    .container a {
        text-decoration: none;
        color: #0a0a0a;
    }
    .container a:hover {
        box-shadow: 0px 0px 2px purple;
    }
    img {
        width: 70%;
    }
</style>