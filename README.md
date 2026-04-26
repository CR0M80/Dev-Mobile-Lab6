# 📋 PizzaRecipesApp — By SAAD

Application Android permettant d’afficher une **liste de pizzas 🍕**, consulter leurs détails et naviguer entre les écrans avec une interface moderne et fluide.

---

## 📽️ Démonstration



https://github.com/user-attachments/assets/5d6442b4-ac99-4840-ba36-9f44ea2ccc12


---

# 🖼️ Interface — `activity_splash.xml`

## 🎯 Écran de démarrage

```xml
<FrameLayout>
    <LinearLayout>
        <ImageView />
        <TextView />
    </LinearLayout>
</FrameLayout>
```

### ✨ Composants

| Composant   | Rôle                    |
| ----------- | ----------------------- |
| `ImageView` | Affiche le logo pizza   |
| `TextView`  | Nom de l'application    |
| `Animation` | Rotation + fade + scale |

👉 Écran affiché au lancement avec animation avant redirection.

---

# 🖼️ Interface — `activity_main.xml`

## 🍕 Liste des pizzas

```xml
<LinearLayout>
    <TextView />
    <ListView />
</LinearLayout>
```

### 📋 Composants

| Composant  | Rôle               |
| ---------- | ------------------ |
| `TextView` | Titre "Pizza Menu" |
| `ListView` | Liste des pizzas   |

👉 Affichage simple et efficace de toutes les pizzas.

---

# 🖼️ Interface — `activity_pizza_detail.xml`

## 📄 Détails d'une pizza

```xml
<LinearLayout>
    <ImageView />
    <TextView />
    <TextView />
</LinearLayout>
```

### 📋 Composants

| Composant   | Rôle              |
| ----------- | ----------------- |
| `ImageView` | Image de la pizza |
| `TextView`  | Nom               |
| `TextView`  | Description       |

👉 Affichage des informations après clic sur une pizza.

---

# ☕ Logique — `SplashActivity.java`

## 🚀 Animation + redirection

```java
logo.animate().rotation(360f).setDuration(2000);
logo.animate().alpha(0f).setDuration(4000);

new Handler().postDelayed(() -> {
    startActivity(new Intent(this, MainActivity.class));
    finish();
}, 3000);
```

### 🎯 Rôle

| Fonction    | Description          |
| ----------- | -------------------- |
| `animate()` | Effets visuels       |
| `Handler`   | Temporisation        |
| `Intent`    | Navigation vers Main |

👉 Expérience utilisateur plus professionnelle dès le lancement.

---

# ☕ Logique — `MainActivity.java`

## 📋 Gestion de la liste

```java
ListView listView = findViewById(R.id.lvPizzas);

ArrayList<String> pizzas = new ArrayList<>();
pizzas.add("Margherita");
pizzas.add("Pepperoni");

ArrayAdapter<String> adapter =
    new ArrayAdapter<>(this, android.R.layout.simple_list_item_1, pizzas);

listView.setAdapter(adapter);
```

---

## 👉 Gestion du clic

```java
listView.setOnItemClickListener((parent, view, position, id) -> {
    Intent intent = new Intent(this, PizzaDetailActivity.class);
    intent.putExtra("name", pizzas.get(position));
    startActivity(intent);
});
```

### 🎯 Rôle

| Méthode                    | Rôle             |
| -------------------------- | ---------------- |
| `setAdapter()`             | Remplit la liste |
| `setOnItemClickListener()` | Gère le clic     |
| `Intent`                   | Envoie données   |

👉 Navigation fluide entre liste et détail.

---

# ☕ Logique — `PizzaDetailActivity.java`

## 📄 Affichage des données

```java
String name = getIntent().getStringExtra("name");

TextView tvName = findViewById(R.id.tvName);
tvName.setText(name);
```

### 🎯 Rôle

| Élément    | Description          |
| ---------- | -------------------- |
| `Intent`   | Récupère les données |
| `TextView` | Affiche le contenu   |

👉 Chaque pizza a son écran dédié.

---

# 🧠 Fonctionnement global

### 🔁 Flux utilisateur

| Action        | Résultat               |
| ------------- | ---------------------- |
| Lancement app | Splash animé           |
| Fin animation | Redirection vers liste |
| Clic pizza    | Détail affiché         |
| Retour        | Retour à la liste      |

---

# 📚 Concepts clés

| Concept       | Explication             |
| ------------- | ----------------------- |
| Activity      | Écran Android           |
| Intent        | Navigation entre écrans |
| ListView      | Liste simple            |
| ArrayAdapter  | Liaison données/UI      |
| Splash Screen | Écran d’accueil         |
| Animation     | Effets visuels          |
| Layout XML    | Structure UI            |


---

*Projet Android réalisé par SAAD — Keep building 🔥🍕*
