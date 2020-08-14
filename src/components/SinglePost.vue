<template>
    <div class="container col-xl-12 text-left">
        <div class="row">
            <div class="col-xl-7 p-5">
                <div class="row">
                    <div class="col-xl-2">
                        <img v-if="post.id % 2 == 0" src="../assets/undraw_male_avatar_323b.svg" alt="">
                        <img v-else src="../assets/undraw_female_avatar_w3jk.svg" alt="">
                    </div>
                    <div class="col-xl-10">
                        <h3 class="title"> {{post.title}} </h3>
                        <div>
                            {{post.body}}
                        </div>
                    </div>
                </div>
                <div class="card mt-5">
                    <div class="card-header">Comments</div>
                    <div 
                    class="card-body"
                    v-for="comment in comments" :key="comment.id">
                        <div class="card-title"> <strong> {{comment.email}} </strong> says </div>
                        <div class="card-text"> {{comment.body}} </div>
                    </div>
                </div>
            </div>

            <div class="col-xl-5 p-5 card">
                    <div id="alert" class="alert alert-purple alert-dismissible fade show" role="alert">
                        <b>Great comment!</b> A pity we can't really push your comments live for now.
                        <button type="button" class="close" data-dismiss="alert" aria-label="Close">
                            <span aria-hidden="true">&times;</span>
                        </button>
                    </div>
                <div>
                    <div class="row">
                        <h3 class="col-xl-5"> Add Your Comment </h3>
                        <form class="form-group col-xl-7" @submit.prevent="comment()">
                            <input type="email" id="email" class="form-control m-3" placeholder="enter your email" required />
                            <input type="text" id="comment" class="form-control m-3" placeholder="enter your comment" required />
                            <input type="submit" class="btn btn-outline-purple ml-3" value="Submit"/>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import router from '../router'

    export default {
        name: 'Page2',
        data () {
            return {
                id: 0,
                post: {},
                comments: {}
            }
        },
        created() {
            this.id = this.$route.params.id;            
            fetch('https://jsonplaceholder.typicode.com/posts/'+this.id, {
                method: 'get'
            })
            .then(response => {
                return response.json()
            })
            .then(jsonData => {
                this.post = jsonData
            })
            fetch('https://jsonplaceholder.typicode.com/posts/' + this.id + '/comments', {
                method: 'get'
            })
            .then(response => {
                return response.json()
            })
            .then(data => {
                this.comments = data
            })
        },
        methods: {
            navigate() {
                router.go(-1);
            },
            comment() {
                let alert = document.querySelector('#alert');
                let email = document.querySelector('#email');
                let comment = document.querySelector('#comment');
                alert.style.display = 'block';
                email.value = '';
                comment.value = ''
            }
        }
    }
</script>

<style scoped>
    .title {
        text-transform: capitalize;
        font-size: 1.2em;
        font-weight: bolder;
    }
    #alert {
        display: none;
    }
    strong {
        text-transform: lowercase;
        color: rebeccapurple;
    }
    .card-text {
        padding-left: 20px;
    }
    img {
        width: 90%;
    }
    .alert-purple {
        background-color: #D0CDE1;
    }
</style>