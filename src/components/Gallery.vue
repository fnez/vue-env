<template>
    <div class="card">
        <div class="card-body">
            <h4 class="card-title">{{ subtitle }}</h4>
            <img v-bind:src="storyImg" alt="main-img"> 
            <h5>{{ customSubtitle }}</h5>
            <p>{{ msg }}</p>
            <p><b>{{ plot }}</b></p>
            <button class="btn btn-primary">Click</button>
        </div>
    </div>  
</template>

<script>
    export default {
        name: 'gallery',
        props: ['plot', 'storyImg', 'customSubtitle'],
        data() {
            return {
                msg: 'Incididunt mollit aute elit anim id anim cupidatat enim nostrud ex. Velit mollit deserunt aliqua deserunt culpa laborum esse qui non labore.',
                subtitle: 'Welcome to story section',
            }
        }
    }    
</script>


