<template>
    <div id="app">
        <div class="container">
          <h1>People in data</h1>
          <ul class="list-group">
            <li v-for="person in orderedPeople()" class="list-group-item">
              {{ person.name }} {{ person.age }
            </li>
          </ul>
          <h1>Greater than 65</h1>
          <ul class="list-group">
            <li v-for="person in old" class="list-group-item">
              {{ person.name }} {{ person.age }}
            </li>
          </ul>
          
          <!-- GALLERY COMPONENT WITH CUSTOM PROPS -->
          <gallery customSubtitle="From the Blog Post" plot="Welcome to the photo gallery" storyImg="https://picsum.photos/286/180?image=137"></gallery>
          <gallery customSubtitle="Join Our Team" plot="Custom props passes to story component" storyImg="https://picsum.photos/286/180?image=127"></gallery>     
        </div>
        
        <!-- STORY COMPONENT -->
        <story></story>

        <div>
          <pre>{{$data}}</pre>
        </div>
      </div>
  </template>
      <script>
        import Vue from 'vue';
        import gallery from './components/Gallery.vue';
        import story from './components/Story.vue';

        export default {
          name: 'App',
          data() {
            return {
              people: [
              { name: "Obelix", age: 33 },
              { name: "Asterix", age: 32 },
              { name: "Majestix", age: 82 },
              { name: "Methusalix", age: 103 },
              { name: "Julius Caesar", age: 64 },
              { name: "Random", age: Math.floor( Math.random() * 100 ) + 1 },
              ],
              favorite: {}
            }
          },
          methods: {
            orderedPeople() {
              return _.orderBy(this.people, 'age')
            },
            updateFavorite(story) {
              //update the empty favorite object with the child component
              this.favorite = story;
            }
          },
          computed: {
            old() {
              return this.people.filter(function (person) {
                return person.age > 65;
              });
            }
          },
          components: {
            gallery,
            story
          }
        }
      </script> 
      
      <style>
        #app {
          font-family: 'Avenir', Helvetica, Arial, sans-serif;
          -moz-osx-font-smoothing: grayscale;
          color: #2c3e50;
          margin-top: 60px;
        }
      </style>
      