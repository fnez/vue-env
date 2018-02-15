<template>
    <div class="container">
        <h2>Story Component</h2>
        <div class="form-group">
            <label for="query">Search stories</label>
            <input v-model="query" class="form-control">            
        </div>
        <h3>Search Results: </h3>
        <ul class="list-group">
            <li v-for="story in search" class="list-group-item">
            {{ story.writer }} by {{ story.plot }}
            </li>
        </ul>
    
    <div class="container" style="padding: 30px 0;">
        <div class="row">
            <div class="col">
                <h4>Blog writing</h4>
                <ul class="list-group">
                    <li class="list-group-item" v-for="story in storiesBy('Blogger')">
                        {{ story.writer }} : "{{ story.plot }}"
                        <button v-show="!story.voted" @click="upvote" class="btn btn-default">Upvote</button>
                        <button v-show="!isFavorite"  @click="markAsFavorite" class="btn btn-primary">Favorite</button>
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
            <div class="col">
                <h4>Social Media Writer</h4>
                <ul class="list-group">
                    <li class="list-group-item" v-for="story in storiesBy('Social Media Writer')">
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
                { writer : 'Blogger', plot : 'Aliqua quis id et fugiat quis cupidatat exercitation. Consectetur nulla officia duis tempor.'},
                { writer : 'Blogger', plot : 'Lorem ut aliqua ex sit labore eu veniam id amet sunt laboris ut est voluptate. Reprehenderit deseru'},
                { writer : 'Copy Writer', plot : 'Duis in Lorem Lorem consequat et duis dolore pariatur labore ut tempor ut.'},
                { writer : 'Copy Writer', plot: 'Qui elit dolor do non deserunt eu. Commodo id cupidatat eu et sunt dolor eu Lorem.'},
                { writer : 'Social Media Writer', plot : 'Duis in Lorem Lorem consequat et duis dolore pariatur labore ut tempor ut'},
                { writer : 'Social Media Writer', plot: 'Qui elit dolor do non deserunt eu. Commodo id cupidatat eu et sunt.'}
                ],
                query: ' ',
            }
        },
        props: ['story', 'favorite'],
        methods: {
            storiesBy(writer) {
                return this.stories.filter( function( story ) {
                    return story.writer === writer;
                });
            },
            upvote() {
                this.story.upvotes++;
                this.story.voted = true;
            },
            markAsFavorite() {
                this.$emit('update', this.story);
            }
        },
        computed: {
            search() {
                let query = this.query;
                return this.stories.filter(function(story) {
                    return story.plot.includes(query);
                });
            },
            isFavorite() {
                return this.story === this.favorite;
            }
        }
    }

</script>
