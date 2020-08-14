<template>   
    <nav id="nav" class="navbar navbar-expand navbar-light bg-purple">
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav mr-auto">
                <li class="nav-item">
                    <router-link class="nav-link text-white" to="/"> Home </router-link> 
                </li>
                <li class="nav-item">
                    <router-link class="nav-link text-white" to="/posts"> Posts </router-link>
                </li>
            </ul>
        </div>
    </nav>
</template>

<style scoped>
    .bg-purple {
        background-color: rebeccapurple;
    }
</style>