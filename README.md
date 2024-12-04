# Stardew Wiki System Python Project Documentation
---

## Overview
The Stardew Wiki System Python project provides a console-based interface to interact with two main categories of information in the game **Stardew Valley**:

- Living Things: Animals and crops in Stardew Valley.
- Recipes: Recipes and their associated ingredients.

The project is organized into subpackages (livingthings and recipes), each containing specific functionalities.

## Project Structure

stardew_wiki/
├── __init__.py          # Initializes the Stardew Wiki package
├── main.py              # Entry point for the entire package
├── livingthings/        # Subpackage for animals and crops
│   ├── __init__.py
│   ├── main.py
│   ├── animals.py       # Animal-related functionality
│   ├── crops.py         # Crop-related functionality
│   ├── data/            # Data files for animals and crops
│   │   ├── Animals.csv
│   │   ├── Crops.csv
├── recipes/             # Subpackage for recipes and ingredients
│   ├── __init__.py
│   ├── main.py
│   ├── recipe_search.py # Recipe search functionality
│   ├── ingredient_search.py # Ingredient search functionality
│   ├── data/            # Data files for recipes
│   │   ├── wiki.xlsx

---
## Main Features

### Living Things

- Search for animals by name or type (Barn/Coop).
- Search for crops by name or season.

### Recipes
- List all recipes.
- Search for recipes by name.
- Find recipes based on available ingredients.
- Suggest missing ingredients for a recipe.
- Explore ingredient details from crop and animal data.

---
## Modules and Functions
### Main Module

File: stardew_wiki/main.py

**Description:**

- Acts as the entry point for the entire package.
- Provides a menu-driven interface to access the livingthings and recipes subpackages.

**Functions**

- main(): Displays the main menu and navigates to subpackage functionalities.

---
### Living Things Subpackage

File: livingthings/main.py

#### Description:

- Provides access to animal and crop-related data.

#### Modules

1. animals.py:

- Defines Animal, BarnAnimal, CoopAnimal, and AnimalDatabase classes.
- Allows searching for animals by name or type.

**Functions:**
- `search_by_name(name)`: Finds an animal by name.
- `search_by_type(type)`: Filters animals by type (Barn/Coop).
- `input_animal()`: Interactive function for searching animals via a menu.

2. crops.py:

- Defines Crop and CropDatabase classes.
- Allows searching for crops by name or season.

**Functions:**
- `search_by_name(name)`: Finds a crop by name.
- `search_by_season(season)`: Lists crops for a specific season.
- `input_crop()`: Interactive function for searching crops via a menu.

---
### Recipes Subpackage
File: recipes/main.py

#### Description:

- Provides access to recipe and ingredient-related data.

#### Modules

1. recipe_search.py:

- Allows searching and listing of recipes.

**Functions:**
- `list_all_recipes(recipes_df)`: Lists all recipes.
    - **Example Usage:**
  ```python
  list_all_recipes(recipes_df)
  ```
    - **Output:**
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
- `search_recipe_by_name(recipes_df)`: Finds a recipe by name.
    - **Example Usage:**
    ```python
    search_recipe_by_name(recipes_df)
    ```
    - **Output 1:**
    ```
    Enter the name of the recipe to search: Pizza
    Recipe: Pizza
    Ingredients: Wheat Flour (1), Tomato (1), Cheese (1)
    ```
    - **Output 2:**
    ```
    Enter the name of the recipe to search: C
    Recipe: Cheese Cauliflower
    Ingredients: Cauliflower (1), Cheese (1)
    ```
    
- `ingredient_details(crops_df, animals_df)`: Fetches details of an ingredient from crop and animal data.
    - **Example Usage:**
    ```python
    ingredient_details(crops_df, animals_df)
    ```
    - **Output 1:**
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

    - **Output 2:**
    ```
    Enter the ingredient name to see details (or type 'STOP' to quit): c
    
    Ingredient not found in Crops or Animals.
    ```

2. ingredient_search.py:

- Finds recipes by available ingredients or suggests missing ones.

**Functions:**
- `list_all_ingredients(recipes_df)`: Lists all unique ingredients.
    - **Example Usage:**
    ```python
    list_all_ingredients(recipes_df)
    ```
    - **Output:**
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

- `search_recipes_by_ingredients(recipes_df)`: Finds recipes containing specific ingredients.
    - **Example Usage:**
    ```python
    search_recipes_by_ingredients(recipes_df)
    ```
    - **Output:**
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

- `suggest_missing_ingredients(recipes_df)`: Suggests missing ingredients for a recipe.
    - **Example Usage:**
    ```python
    suggest_missing_ingredients(recipes_df)
    ```
    - **Output:**
    ```
    Enter the name of the recipe: Pizza
    Enter the ingredients you already have (type 'STOP' to finish):
    Enter ingredient: Cheese
    Enter ingredient: STOP
    Missing Ingredients:
    - Wheat Flour
    - Tomato
    ```

#### **Menu Options**

##### **1. List All Recipes**
- **Function:** `list_all_recipes(recipes_df)`
- **Description:** Displays the names of all available recipes in the dataset.
- **How to Use:** Select option `1` from the menu.

##### **2. Search for a Recipe by Name**
- **Function:** `search_recipe_by_name(recipes_df)`
- **Description:** Prompts the user to input a recipe name and displays its required ingredients.
- **How to Use:** Select option `2` from the menu.

##### **3. View Details of Ingredients**
- **Function:** `ingredient_details(crops_df, animals_df)`
- **Description:** Allows the user to input an ingredient name and retrieves detailed information from the `Crops` and `Animals` datasets. Continues until the user inputs `STOP`.
- **How to Use:** Select option `3` from the menu.

##### **4. List All Unique Ingredients**
- **Function:** `list_all_ingredients(recipes_df)`
- **Description:** Extracts and displays a list of unique ingredients used across all recipes.
- **How to Use:** Select option `4` from the menu.

##### **5. Search Recipes by Ingredients**
- **Function:** `search_recipes_by_ingredients(recipes_df)`
- **Description:** Prompts the user to input ingredients one by one and searches for recipes containing those ingredients. Stops when the user inputs `STOP`.
- **How to Use:** Select option `5` from the menu.

##### **6. Suggest Missing Ingredients for a Recipe**
- **Function:** `suggest_missing_ingredients(recipes_df)`
- **Description:** Prompts the user to input the name of a recipe and the ingredients they already have. Suggests the missing ingredients required to complete the recipe.
- **How to Use:** Select option `6` from the menu.

##### **7. Exit**
- **Description:** Terminates the program.
- **How to Use:** Select option `7` from the menu.


## Usage

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

