<template>
  <div class="exercisePage">
    <!-- For the template part you need to work inside the TODO don't touche to the instructions line part 
    --------- Instructions-->
    <div class="requirementContent">
      <div class="titleRequirement">Instructions</div>
      <div class="requirements">
        <ol>
          <li>Display the recipe's title in the middle of the page and in bold</li>
          <li>Display the ingredients using 'v-for'</li>
          <li>
            Add to the recipe object a element for know the complexity of the recipe,
            this complexity need to be a number between 0 and 10.
          </li>
          <li>
            If the complexity is between 0 and 3 you need to display : "difficulty : EASY"
            <br>If the complexity is more than 3 and less or equal than 7 you need to display : "difficulty : NORMAL"
            <br>If the complexity is more than 7 you need to display : "difficulty : DIFFICULT"
            <br>Use 'v-if'
          </li>
          <li>Oops ! I forget the milk, add this ingredient when you click on a button.</li>
        </ol>
      </div>
    </div>
<!-- --------- End Of the Instructions part -->

    <div class="exerciseResultPart">
      <center>
        <h1>{{recipe.title}}</h1>
      </center>
      <ul>
        <li v-for="ingredient in recipe.ingredients" :key="ingredient">{{ingredient}}</li>
      </ul>
      <h2 v-if="recipe.complexity <= 3">Difficulty: EASY</h2>
      <h2 v-else-if="recipe.complexity > 3 && recipe.complexity <= 7">Difficulty: NORMAL</h2>
      <h2 v-else>Difficulty: DIFFICULT</h2>
      <button v-if="!isClick" v-on:click="addMilk">Add Milk</button>
            <button v-if="isClick">Add Milk</button>

    </div>
  </div>
</template>

<script>
export default {
  name: "Exercise",
  data() {
    return {
      isClick: false,
      recipe: {
        title: "Crêpes",
        ingredients: ["eggs", "flour", "sugar"],
        complexity: 6
      }
    }
  },
  methods: {
    addMilk(){
      let milk = "milk"
      this.recipe.ingredients.push(milk);
      this.isClick = true;
    }
  }
};
</script>

<style scoped>
.exercisePage {
  display: grid;
  grid-template-columns: 1fr 2fr;
  height: calc(100% - 50px);
}

.requirementContent {
  padding: 20px;
  background-color: var(--guide-line-bg);
}

.exerciseResultPart {
  padding: 20px;
}

li {
  padding-bottom: 10px;
}

/* .exerciseResultPart {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  font-weight: bold;
} */
</style>