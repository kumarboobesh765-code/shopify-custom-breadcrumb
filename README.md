# Custom Breadcrumb – Shopify (Product & Collection Aware)

A **lightweight custom breadcrumb navigation** for Shopify that automatically detects the **current collection** and displays a clean breadcrumb path for **product pages**.

Designed to improve **UX, navigation clarity, and SEO context**.

---

## ✨ Features

* ✅ Works on **product pages**
* ✅ Automatically detects the active collection
* ✅ Falls back to product’s first collection if needed
* ✅ Clean & minimal markup
* ✅ SEO-friendly breadcrumb structure
* ✅ No JavaScript required
* ✅ Can be pasted **anywhere**
* ✅ Works with **Custom Liquid blocks or Snippets**

---

## 📂 Usage Options

You can use this breadcrumb in **two ways**:

1. **Paste directly into a Custom Liquid block** (quickest)
2. **Create a reusable snippet** and include it in product templates

---

## 🚀 Option 1: Paste Directly (Custom Liquid Block)

### Steps

1. Go to **Shopify Admin → Online Store → Themes**
2. Click **Customize**
3. Open a **Product page**
4. Click **Add block**
5. Choose **Custom Liquid**
6. Paste the code below
7. Click **Save**

### ✅ Code (Copy–Paste Ready)

```liquid
{% assign crumb_collection = collection %}

{% if crumb_collection == nil or crumb_collection.handle == blank %}
  {% assign crumb_collection = product.collections.first %}
{% endif %}

{% if crumb_collection %}
<nav class="custom-breadcrumb" aria-label="Breadcrumb">
  <a href="/" class="crumb-home">Home</a>

  <span class="crumb-separator">/</span>
  <a href="{{ crumb_collection.url }}" class="crumb-collection">
    {{ crumb_collection.title }}
  </a>

  <br>

  <span class="crumb-separator">/</span>
  <span class="crumb-current">{{ product.title }}</span>
</nav>
{% endif %}

<style>
.custom-breadcrumb {
  font-size: 16px;
  font-weight: 500;
  margin: 5px 0 10px 0;
  font-family: inherit;
  color: #ffffff !important;
}

.custom-breadcrumb a {
  color: #ffffff !important;
  text-decoration: underline;
  font-style: italic;
}

.custom-breadcrumb a:hover {
  text-decoration: none;
}

.custom-breadcrumb .crumb-separator {
  margin: 0 6px;
  opacity: 0.7;
  color: #ffffff !important;
}

.custom-breadcrumb .crumb-current {
  font-weight: 600;
  font-style: italic;
  color: #ffffff !important;
}
</style>
```

---

## 🚀 Option 2: Create a Reusable Snippet (Recommended)

### Step 1: Create Snippet

1. Go to **Online Store → Themes → Edit code**
2. Open **Snippets**
3. Click **Add a new snippet**
4. Name it:

```
breadcrumb.liquid
```

5. Paste the same code above
6. Click **Save**

---

### Step 2: Use Snippet in Product Template

Add this line wherever you want the breadcrumb to appear:

```liquid
{% render 'breadcrumb' %}
```

You can place it in:

* `main-product.liquid`
* `product.liquid`
* Any product section file
* Custom blocks

---

## 🧩 How It Works

* Uses `collection` object when available
* Falls back to `product.collections.first` if accessed directly
* Ensures breadcrumb always shows **Home → Collection → Product**
* Automatically hides if no collection is found

---

## 🎨 Customization

You can easily change:

* Font size
* Colors
* Separator style
* Line break (`<br>`) placement

All styling is included inline for **plug-and-play usage**.

---

## 🛒 Best Use Cases

* Product pages
* SEO-friendly navigation
* Improved user journey
* Stores with deep collection structures

---

## ⭐ Support

If this breadcrumb helped you, consider **starring ⭐ the repository**.
Feel free to fork and customize it for your Shopify projects.

---
