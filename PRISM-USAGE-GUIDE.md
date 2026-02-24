# Prism.js Integration - Usage Guide

## ✅ Integration Complete!

Prism.js syntax highlighting has been successfully added to your theme.xml with:
- **Theme**: Tomorrow Night (modern dark theme)
- **Features**: Line numbers, copy button, auto-initialization
- **Supported Languages**: JavaScript, TypeScript, JSX, TSX, Python, CSS, Bash, JSON, SQL, Markdown, HTML

---

## 📝 How to Use in Blog Posts

### Basic Code Block

```html
<pre><code class="language-javascript">
function greet(name) {
  return `Hello, ${name}!`;
}
</code></pre>
```

### With Different Languages

**Python:**
```html
<pre><code class="language-python">
def calculate_sum(a, b):
    return a + b
</code></pre>
```

**TypeScript:**
```html
<pre><code class="language-typescript">
interface User {
  name: string;
  age: number;
}

const user: User = {
  name: "John",
  age: 30
};
</code></pre>
```

**Bash:**
```html
<pre><code class="language-bash">
npm install
npm run dev
</code></pre>
```

**CSS:**
```html
<pre><code class="language-css">
.button {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  padding: 12px 24px;
  border-radius: 8px;
}
</code></pre>
```

### Inline Code

For inline code, use:
```html
<code class="language-javascript">const x = 5;</code>
```

Or without language class:
```html
<code>npm install</code>
```

---

## 🎨 Features Included

### ✓ Line Numbers
Automatically added to all code blocks

### ✓ Copy to Clipboard
Hover over code block to see copy button in top-right

### ✓ Syntax Highlighting
Colors optimized for dark mode with Tomorrow Night theme

### ✓ Responsive Design
Code blocks adapt to mobile screens with horizontal scroll

### ✓ Custom Scrollbars
Styled scrollbars matching your theme

---

## 📋 Supported Languages

| Language | Class Name |
|----------|-----------|
| HTML | `language-markup` |
| CSS | `language-css` |
| JavaScript | `language-javascript` |
| TypeScript | `language-typescript` |
| JSX | `language-jsx` |
| TSX | `language-tsx` |
| Python | `language-python` |
| Bash | `language-bash` |
| JSON | `language-json` |
| SQL | `language-sql` |
| Markdown | `language-markdown` |

---

## 🎯 Pro Tips

1. **Always specify language** for better highlighting:
   ```html
   <code class="language-javascript">code here</code>
   ```

2. **Use proper indentation** in your code blocks for readability

3. **Escape HTML entities** when showing HTML code:
   - `<` becomes `&lt;`
   - `>` becomes `&gt;`
   - `&` becomes `&amp;`

4. **Test in Blogger's HTML view** before publishing

---

## 🔧 Customization Options

### Change Theme
To use a different Prism theme, replace in `<head>`:
```html
<!-- Current: Tomorrow Night -->
<link href='https://cdnjs.cloudflare.com/ajax/libs/prism/1.29.0/themes/prism-tomorrow.min.css' rel='stylesheet'/>

<!-- Alternative Dark Themes: -->
<!-- Okaidia -->
<link href='https://cdnjs.cloudflare.com/ajax/libs/prism/1.29.0/themes/prism-okaidia.min.css' rel='stylesheet'/>

<!-- Twilight -->
<link href='https://cdnjs.cloudflare.com/ajax/libs/prism/1.29.0/themes/prism-twilight.min.css' rel='stylesheet'/>

<!-- Dracula -->
<link href='https://cdnjs.cloudflare.com/ajax/libs/prism/1.29.0/themes/prism-dracula.min.css' rel='stylesheet'/>
```

### Add More Languages
Add new language support by including additional scripts before `</head>`:
```html
<script src='https://cdnjs.cloudflare.com/ajax/libs/prism/1.29.0/components/prism-php.min.js'></script>
<script src='https://cdnjs.cloudflare.com/ajax/libs/prism/1.29.0/components/prism-go.min.js'></script>
<script src='https://cdnjs.cloudflare.com/ajax/libs/prism/1.29.0/components/prism-rust.min.js'></script>
```

---

## 📱 Mobile Optimization

Code blocks are fully responsive with:
- Horizontal scrolling on mobile
- Reduced font size for better fit
- Touch-friendly copy button
- Optimized line height

---

## 🚀 Example Blog Post

```html
<h2>Building a REST API with Node.js</h2>

<p>Here's how to create a simple Express server:</p>

<pre><code class="language-javascript">
const express = require('express');
const app = express();

app.get('/api/users', (req, res) => {
  res.json({ 
    users: [
      { id: 1, name: 'John' },
      { id: 2, name: 'Jane' }
    ]
  });
});

app.listen(3000, () => {
  console.log('Server running on port 3000');
});
</code></pre>

<p>Install dependencies with:</p>

<pre><code class="language-bash">
npm install express
npm start
</code></pre>
```

---

## ✅ What's Been Added to Your Theme

1. **CSS Files** (in `<head>`):
   - Prism Tomorrow Night theme
   - Line numbers plugin styles
   - Toolbar plugin styles

2. **JavaScript Files** (before `</head>`):
   - Prism core library
   - Language support files
   - Line numbers plugin
   - Toolbar plugin
   - Copy to clipboard plugin
   - Auto-initialization script

3. **Custom CSS** (in `<b:skin>`):
   - Dark theme optimization
   - Inline code styling
   - Scrollbar styling
   - Toolbar button styling
   - Responsive media queries

---

## 🎉 You're All Set!

Start writing technical blog posts with beautiful code highlighting! The syntax highlighting will work automatically whenever you use `<pre><code>` tags with the appropriate language class.
