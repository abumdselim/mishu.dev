# 📖 Automatic Reading Time Calculator - Documentation

## ✅ Integration Complete!

An automatic reading time calculator has been added to your Blogger theme. It displays "⏳ X min read" below the post title in all blog post cards.

---

## 🎯 Features

### ✓ **Automatic Calculation**
- Calculates reading time based on 200 words per minute (average reading speed)
- Shows minimum 1 minute for very short posts
- Rounds up to nearest minute

### ✓ **Smart Detection**
- Works on post list pages (blog homepage)
- Works on individual post pages
- Uses post snippet for quick approximation on list pages
- Fetches full content for accurate calculation when needed

### ✓ **Beautiful Display**
- Clock icon (⏳) with reading time
- Monospace font matching your theme
- Positioned below post title
- Responsive design

---

## 📍 Display Location

The reading time appears in this structure:

```
┌─────────────────────────────────┐
│  [Category Badge]               │
│                                 │
│  Post Title                     │
│  ⏳ 4 min read                  │  ← Reading Time
│                                 │
│  Post snippet text...           │
│                                 │
│  [Read Case Study →]            │
└─────────────────────────────────┘
```

---

## ⚙️ How It Works

1. **On Page Load**: Script scans all `.post-reading-time` elements
2. **For Blog Lists**: Uses post snippet and multiplies by 10 for approximation
3. **For Individual Posts**: Calculates from full post body text
4. **Word Counting**: Splits text by whitespace and counts words
5. **Calculation**: `Reading Time = ⌈Word Count ÷ 200⌉` (rounded up)

---

## 🔧 Configuration

You can customize the reading speed in the script:

```javascript
// Default: 200 words per minute
const WORDS_PER_MINUTE = 200;

// Slower reading (more technical content): 150 WPM
const WORDS_PER_MINUTE = 150;

// Faster reading (casual content): 250 WPM
const WORDS_PER_MINUTE = 250;
```

### Where to Edit:
1. Open your `theme.xml`
2. Find the `Reading Time Calculator Script` section (near end of file)
3. Change the `WORDS_PER_MINUTE` constant
4. Save and upload

---

## 🎨 Styling

The reading time display uses these CSS classes:

```css
.post-reading-time {
  display: flex;
  align-items: center;
  gap: var(--spacing-xs);
  font-size: var(--text-sm);
  color: var(--text-secondary);
  font-family: var(--font-mono);
  margin-bottom: var(--spacing-md);
}
```

### Customization Examples:

**Change Icon Color:**
```css
.post-reading-time svg {
  color: #10b981; /* Green */
}
```

**Change Text Size:**
```css
.post-reading-time {
  font-size: var(--text-base); /* Larger */
}
```

**Change Position:**
Move the reading time element in the HTML structure within the `<b:includable id='post'>` section.

---

## 📊 Reading Speed Reference

| Content Type | Words Per Minute |
|--------------|------------------|
| Casual blog posts | 250-300 WPM |
| Average reading | 200-250 WPM |
| Technical articles | 150-200 WPM |
| Academic papers | 100-150 WPM |

---

## 🔍 Technical Details

### Supported Post Selectors:
The script automatically detects post content using these selectors:
- `.post-body`
- `[itemprop="articleBody"]`
- `.entry-content`
- `article .post-content`

### Calculation Formula:
```
Reading Time (minutes) = ⌈ Word Count ÷ Words Per Minute ⌉
Minimum = 1 minute
```

### Word Counting Method:
1. Gets text content from post body
2. Removes scripts and style tags
3. Trims whitespace
4. Splits by whitespace: `/\s+/`
5. Filters empty strings
6. Counts remaining words

---

## 🐛 Troubleshooting

### Reading time shows "Calculating..." forever:

**Possible causes:**
1. Post body selector not matching your theme structure
2. JavaScript error in console

**Solution:**
Check browser console for errors. If needed, update the post body selector:

```javascript
const postBody = doc.querySelector('.YOUR-POST-BODY-CLASS');
```

### Reading time is inaccurate:

**For too short estimates:**
- Decrease `WORDS_PER_MINUTE` value

**For too long estimates:**
- Increase `WORDS_PER_MINUTE` value

### Not appearing on some posts:

**Check that:**
1. Post has the `.post-card` class
2. Post has a link with `.post-title a` or `.read-more-btn`
3. JavaScript console shows no errors

---

## 🚀 Performance

- **Fast**: Calculations happen client-side
- **No server load**: Pure JavaScript
- **Cached**: Runs once per page load
- **Lightweight**: ~3KB of JavaScript code

---

## 📱 Mobile Support

Fully responsive with optimized display on:
- ✅ Desktop
- ✅ Tablet  
- ✅ Mobile phones
- ✅ Small screens (320px+)

---

## 💡 Examples

### Short Post (100 words):
```
⏳ 1 min read
```

### Medium Post (800 words):
```
⏳ 4 min read
```

### Long Post (2500 words):
```
⏳ 13 min read
```

---

## 🎉 That's It!

The reading time calculator is now active on all your blog posts. It will automatically calculate and display the estimated reading time for every post without any additional configuration needed!

### Need Help?
- Check browser console for JavaScript errors
- Verify post structure matches expected selectors
- Adjust `WORDS_PER_MINUTE` if estimates seem off
