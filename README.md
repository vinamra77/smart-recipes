# smart-recipes
recipe generator app
<!DOCTYPE html>
<html>
<head>
  <title>Smart Recipe App</title>
  <style>
    body { font-family: Arial; padding: 20px; }
    button { margin: 5px; }
    .recipe { border: 1px solid #ccc; padding: 10px; margin: 10px 0; }
  </style>
</head>
<body>

<h2>Smart Recipe Finder</h2>

<input id="ingredientInput" placeholder="Enter ingredient">
<button onclick="addIngredient()">Add</button>

<h3>Your Ingredients:</h3>
<ul id="ingredientList"></ul>

<button onclick="findRecipes()">Find Recipes</button>

<h3>Recipes You Can Make:</h3>
<div id="recipes"></div>

<script>
const recipes = [
  { name: "Omelette", ingredients: ["egg", "salt", "oil"] },
  { name: "Sandwich", ingredients: ["bread", "butter"] },
  { name: "Tea", ingredients: ["water", "tea", "sugar"] }
];

let userIngredients = [];

function addIngredient() {
  const input = document.getElementById("ingredientInput");
  if (input.value.trim() !== "") {
    userIngredients.push(input.value.toLowerCase());
    document.getElementById("ingredientList").innerHTML += "<li>" + input.value + "</li>";
    input.value = "";
  }
}

function findRecipes() {
  const resultDiv = document.getElementById("recipes");
  resultDiv.innerHTML = "";

  recipes.forEach(r => {
    const canMake = r.ingredients.every(i => userIngredients.includes(i));
    if (canMake) {
      resultDiv.innerHTML += `<div class="recipe"><b>${r.name}</b></div>`;
    }
  });

  if (resultDiv.innerHTML === "") {
    resultDiv.innerHTML = "No recipes found.";
  }
}
</script>

</body>
</html>
