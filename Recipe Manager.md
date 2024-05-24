

## 🍽️ Recipes
- [[Breakfast/Protein Pancakes]]
- [[Breakfast Borrito]]
- [[Dinner/Quinoa Bowl]]
- [[Snack/Protein Smoothie]]

## 📚 Categories
- [[Cuisine/Italian]]
- [[Cuisine/Mexican]]
- [[Diet/Protein]]

## 🗄️ Vault Info
- 📂 Recent recipe updates
  `$=dv.list(dv.pages('#recipe').sort(f=>f.file.mtime.ts,"desc").limit(4).file.link)`

- 🔖 Tagged: favorite
  `$=dv.list(dv.pages('#favorite').sort(f=>f.file.name,"desc").limit(4).file.link)`

- 〽️ Stats
  - Recipe Count: `$=dv.list(dv.pages('').filter(p => p.file.link || p.file.tag?.includes('recipe')).length`
  - Protein Recipes: `$=dv.list(dv.pages('Diet/Protein').filter(p => p.file.link || p.file.tag?.includes('recipe')).length`
