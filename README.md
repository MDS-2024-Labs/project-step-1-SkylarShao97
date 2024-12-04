# Recipe Management System

This project provides a set of tools for exploring and managing recipe-related data. It includes subpackages and a main script for running various operations interactively.

---

## **Main Script: `main.py`**

The `main.py` script serves as the entry point for the recipe management system. It loads the data and provides a menu-driven interface for the user to interact with recipes and ingredients.

### **Features**

1. **Load Data:**
   - Reads data from an Excel file (`DATA581 Project csv.xlsx`) containing three sheets:
     - `Recipes`: Contains recipe names, ingredients, and selling prices.
     - `Crops`: Contains crop names, seasons, prices, and growth details.
     - `Animals`: Contains animal products, types, and associated prices.
   - The `load_data()` function loads and returns these datasets as Pandas DataFrames.

2. **Interactive Menu:**
   - Users can choose from multiple options to explore recipes and ingredients.

---

### **Menu Options**

#### **1. List All Recipes**
- **Function:** `list_all_recipes(recipes_df)`
- **Description:** Displays the names of all available recipes in the dataset.
- **How to Use:** Select option `1` from the menu.

#### **2. Search for a Recipe by Name**
- **Function:** `search_recipe_by_name(recipes_df)`
- **Description:** Prompts the user to input a recipe name and displays its required ingredients.
- **How to Use:** Select option `2` from the menu.

#### **3. View Details of Ingredients**
- **Function:** `ingredient_details(crops_df, animals_df)`
- **Description:** Allows the user to input an ingredient name and retrieves detailed information from the `Crops` and `Animals` datasets. Continues until the user inputs `STOP`.
- **How to Use:** Select option `3` from the menu.

#### **4. List All Unique Ingredients**
- **Function:** `list_all_ingredients(recipes_df)`
- **Description:** Extracts and displays a list of unique ingredients used across all recipes.
- **How to Use:** Select option `4` from the menu.

#### **5. Search Recipes by Ingredients**
- **Function:** `search_recipes_by_ingredients(recipes_df)`
- **Description:** Prompts the user to input ingredients one by one and searches for recipes containing those ingredients. Stops when the user inputs `STOP`.
- **How to Use:** Select option `5` from the menu.

#### **6. Suggest Missing Ingredients for a Recipe**
- **Function:** `suggest_missing_ingredients(recipes_df)`
- **Description:** Prompts the user to input the name of a recipe and the ingredients they already have. Suggests the missing ingredients required to complete the recipe.
- **How to Use:** Select option `6` from the menu.

#### **7. Exit**
- **Description:** Terminates the program.
- **How to Use:** Select option `7` from the menu.

---

### **How to Run**

1. **Prerequisites:**
   - Python 3.x
   - Required Libraries:
     - `pandas`
     - `openpyxl` (for reading Excel files)

2. **Run the Script:**
   - Place the Excel file (`DATA581 Project csv.xlsx`) in the `data/` directory.
   - Execute the script:
     ```bash
     python main.py
     ```

3. **Follow the Menu:**
   - Interact with the program by selecting options from the menu and following the prompts.

---

### **Example Usage**

```plaintext
Loading data...

What would you like to do?
1. List all recipes
2. Search for a recipe by name
3. View details of ingredients
4. List all unique ingredients
5. Search recipes by ingredients
6. Suggest missing ingredients for a recipe
7. Exit
Enter your choice: 1
Available Recipes:
- Fried Egg
- Omelet
- Pizza
```

### Data Requirements
- Excel File Structure:
  - Recipes: Contains columns name_recipe, ingredients, sell_price.
  - Crops: Contains columns name_crop, season, crop_price, growth_crop, craft_crop.
  - Animals: Contains columns name_animal, type, growth_animal, product_animal, product_animal_price.

### Project Structure
```
recipe_project/
│
├── data/
│   └── DATA581 Project csv.xlsx
│
├── subpackage_recipes/
│   ├── recipe_search.py
│   └── ingredient_search.py
│
└── main.py
```

# Subpackage 1














# Subpackage 2: Recipes

The `recipes` subpackage provides tools for exploring and managing recipe-related data. 
It is divided into two modules: `recipe_search` and `ingredient_search`, each contains 3 functions.
- `recipe_search`:
1. `list_all_recipes(recipes)`
2. `search_recipe_by_name(recipes)`
3. `ingredient_details(crops, animals)`.
   
- `ingredient_search`:
1. `list_all_ingredients(recipes)`
2. `search_recipes_by_ingredients(recipes)`
3. `suggest_missing_ingredients(recipes)`.
---

## **Module 1: recipe_search**

This module provides functions to search recipes, list all available recipes, and fetch detailed ingredient information.

### Functions:

#### **1. list_all_recipes()**
- **Purpose:** Lists all recipes available in the dataset.
- **How It Works:**
  - Retrieves all recipe names from the `name_recipe` column of the recipes dataset.
  - Prints the names of all available recipes for easy browsing.
- **Example Usage:**
  ```python
  list_all_recipes(recipes_df)
  ```
  **Output:**
  ```
    Available Recipes:
  - Fried Egg
  - Omelet
  - Cheese Cauliflower
  - Vegetable Medley
  - Pizza
  - Bean Hotpot
  - Glazed Yams
  - Hashbrowns
  - Bread
  ```

#### **2. search_recipe_by_name(name)**
- **Purpose:** Searches for a recipe by its name and displays its ingredients.
- **How It Works:**
  - Accepts user input for the recipe name.
  - Searches for the recipe in the `name_recipe` column and retrieves its corresponding ingredients.
  - Prints the recipe name and its ingredients if found, or an error message if not.
- **Example Usage:**
  ```python
  search_recipe_by_name(recipes_df)
  ```
  **Output 1:**
  ```
  Enter the name of the recipe to search: Pizza
  Recipe: Pizza
  Ingredients: Wheat Flour (1), Tomato (1), Cheese (1)
  ```
  **Output 2:**
  ```
  Enter the name of the recipe to search: C
  Recipe: Cheese Cauliflower
  Ingredients: Cauliflower (1), Cheese (1)
  ```

#### **3. ingredient_details()**
- **Purpose:** Provides detailed information about an ingredient from the `crops` or `animals` dataset.
- **How It Works:**
  - Prompts the user to input an ingredient name.
  - Searches for the ingredient in both the `Crops` (using `name_crop` and `craft_crop`) and `Animals` datasets.
  - Prints details about the ingredient (e.g., season, price, growth time, or animal products).
  - Continues until the user inputs `STOP`.
- **Example Usage:**
  ```python
  ingredient_details(crops_df, animals_df)
  ```
  **Output 1:**
  ```
  Enter the ingredient name to see details (or type 'STOP' to quit): Wheat
  
  Ingredient found in Crops:
  Name: Wheat
  Craft Name: Wheat Flour
  Season: Summer/Fall
  Growth Time: 4 days
  Regrowth Time: nan days
  Price: 25
  Craft Price: 50.0
  ```

  **Output 2:**
  ```
  Enter the ingredient name to see details (or type 'STOP' to quit): c
  
  Ingredient not found in Crops or Animals.
  ```

---

## **Module 2: ingredient_search**

This module provides functions to analyze and work with ingredients, such as listing unique ingredients, searching recipes by ingredients, and suggesting missing ingredients.

### Functions:

#### **1. list_all_ingredients()**
- **Purpose:** Displays a list of all unique ingredients used in the recipes, excluding numbers and parentheses.
- **How It Works:**
  - Splits the `ingredients` column into individual items.
  - Removes content within parentheses (e.g., `(1)`) and any numeric values.
  - Prints a sorted list of unique ingredient names.
- **Example Usage:**
  ```python
  list_all_ingredients(recipes_df)
  ```
  **Output:**
  ```
  Unique Ingredients:
  - Beet
  - Cauliflower
  - Cheese
  - Egg
  - Green Bean
  - Milk
  - Oil
  - Potato
  - Sugar
  - Tomato
  - Wheat Flour
  - Yam
  ```

#### **2. search_recipes_by_ingredients(ingredient_list)**
- **Purpose:** Finds recipes that use specific ingredients.
- **How It Works:**
  - Prompts the user to input ingredients one at a time.
  - Searches the `ingredients` column for each input and retrieves matching recipes.
  - Stops when the user inputs `STOP`.
- **Example Usage:**
  ```python
  search_recipes_by_ingredients(recipes_df)
  ```
  **Output:**
  ```
  Enter ingredients one by one (type 'STOP' to finish):
  Enter ingredient: Egg
  Enter ingredient: Cheese
  Enter ingredient: STOP
  Recipes containing the ingredients:
  - Cheese Cauliflower
  - Fried Egg
  - Pizza
  - Omelet
  ```

#### **3. suggest_missing_ingredients(partial_ingredients)**
- **Purpose:** Suggests missing ingredients for a recipe based on the user's partial ingredients.
- **How It Works:**
  - Prompts the user to input the name of a recipe.
  - Retrieves all ingredients required for the recipe.
  - Prompts the user to input the ingredients they already have.
  - Compares the two lists and suggests the missing ingredients.
- **Example Usage:**
  ```python
  suggest_missing_ingredients(recipes_df)
  ```
  **Output:**
  ```
  Enter the name of the recipe: Pizza
  Enter the ingredients you already have (type 'STOP' to finish):
  Enter ingredient: Cheese
  Enter ingredient: STOP
  Missing Ingredients:
  - Wheat Flour
  - Tomato
  ```

---



