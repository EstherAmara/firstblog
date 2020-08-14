<template>
    <div>
        <div>
            <div v-for="post in posts" :key="post.id">
                <div>
                    {{post.title}}
                </div>
                <div>
                    {{post.body}}
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        posts: Array
    }
}
</script>