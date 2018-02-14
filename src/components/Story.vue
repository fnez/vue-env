<template>
    <div class="container">
        <h2>Story List</h2>
        <div class="form-group">
            <label for="query">Search stories</label>
            <input v-model="query" class="form-control">            
        </div>
        <h3>Search Results: </h3>
        <ul class="list-group">
            <li v-for="story in search"
            class="list-group-item">
            {{ story.writer }} by {{ story.plot }}
        </li>
    </ul>
    
    <div class="container">
            <h3>All Writing</h3>
        <div class="row">
            <div class="col">
                <h4>Blog writing</h4>
                <ul class="list-group">
                    <li class="list-group-item" v-for="story in storiesBy('Blogger')">
                        {{ story.writer }} : "{{ story.plot }}"
                    </li>
                </ul>
            </div>
            <div class="col">
                <h4>Copy writing</h4>
                <ul class="list-group">
                    <li class="list-group-item" v-for="story in storiesBy('Copy Writer')">
                        {{ story.writer }} : "{{ story.plot }}"
                    </li>
                </ul>        
            </div>        
        </div>
    </div>
</div>
</template>

<script>

    export default {
        name: 'story',
        data() {
            return {
                stories: [
                { writer : 'Blogger', plot : 'Aliqua quis id et fugiat quis cupidatat exercitation. Consectetur nulla officia duis tempor. Officia sint fugiat incididunt nisi esse exercitation ipsum sint sint officia velit.'},
                { writer : 'Blogger', plot : 'Lorem ut aliqua ex sit labore eu veniam id amet sunt laboris ut est voluptate. Reprehenderit deserunt sit aliquip esse non. Dolor irure et commodo nisi velit commodo enim anim culpa. Veniam consequat id irure et laborum ex. Cillum sit labore.'},
                { writer : 'Copy Writer', plot : 'Duis in Lorem Lorem consequat et duis dolore pariatur labore ut tempor ut. Cupidatat ex cupidatat incididunt fugiat occ.'},
                { writer : 'Copy Writer', plot: 'Qui elit dolor do non deserunt eu. Commodo id cupidatat eu et sunt dolor eu Lorem. Lorem ea tempor laborum consectetur. Nostrud sunt enim proident velit nisi amet esse elit nisi nisi.'}
                ],
                query: ' ',
                props: ['story']
            }
        },
        methods: {
            storiesBy(writer) {
                return this.stories.filter( function( story ) {
                    return story.writer === writer;
                });
            },
            updateFavorite() {
                //'update' is just the name of the custom event
                this.$emit('update', this.story);
            }
        },
        computed: {
            search() {
                let query = this.query;
                return this.stories.filter(function(story) {
                    return story.plot.includes(query);
                });
            }
        }
    }



</script>
