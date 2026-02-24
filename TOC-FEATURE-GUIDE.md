# 📑 Table of Contents (TOC) Feature - Documentation

## ✅ Feature Complete!

An automatic, sticky Table of Contents has been added to your Blogger theme. It appears on single post pages (desktop only) and automatically generates from your H2 and H3 headings.

---

## 🎯 Key Features

### ✓ **Automatic Generation**
- Scans post content for `<h2>` and `<h3>` tags automatically
- Generates unique IDs for headings without IDs
- Creates nested structure (H2 sections with H3 subsections)
- No manual configuration needed

### ✓ **Smart Display**
- Only shows on single post pages (not blog homepage)
- Desktop only (hidden on tablets and mobile < 1280px)
- Fixed position on right sidebar
- Sticky behavior - stays visible while scrolling

### ✓ **Beautiful Design**
- Dark mode glassmorphic design matching your theme
- Smooth hover animations
- Active section highlighting
- Custom scrollbar styling
- Fade-in animation on load

### ✓ **Enhanced UX**
- Smooth scroll to sections on click
- Active section highlighting based on scroll position
- URL hash updates when clicking sections
- Respects initial URL hash (deep linking)

---

## 📍 Display Location

```
┌──────────────────────────────────────────────────┐
│                                         ┌────────┤
│  Post Content                           │  TOC   │
│                                         │        │
│  # Main Heading                         │ • Sec1 │
│                                         │   - 1A │
│  ## Section 1                           │   - 1B │
│  Content here...                        │ • Sec2 │
│                                         │ • Sec3 │
│  ### Subsection 1A                      │        │
│  More content...                        └────────┤
│                                                   │
└───────────────────────────────────────────────────┘
```

**Position:** Fixed to the right side, 40px from edge, 120px from top

---

## 🎨 Visual Design

### Glassmorphic Card
- Semi-transparent dark background: `rgba(15, 15, 25, 0.7)`
- Backdrop blur: `12px`
- Blue border: `rgba(59, 130, 246, 0.2)`
- Hover effect: Brighter border and glow shadow

### Link States
- **Default:** Secondary text color, transparent border
- **Hover:** Primary blue color, light blue background, animated indent
- **Active:** Primary blue, darker background, bold font, left border

### Smooth Animations
- Fade-in on page load (0.5s delay)
- Hover transitions (0.2s)
- Smooth scroll to sections

---

## ⚙️ How It Works

### Detection Process

1. **Page Check:** Script checks if it's a single post page
   - Looks for `.post-body`, `[itemprop="articleBody"]`, etc.
   - Checks URL for `.html` extension
   - Verifies body has item/post view class

2. **Content Scan:** Finds post content container
   - Searches multiple selectors in priority order
   - Confirms container has H2 or H3 tags

3. **Heading Extraction:** Gets all H2 and H3 tags
   - Extracts text content
   - Generates URL-friendly IDs (slugified)
   - Ensures unique IDs (adds counter if duplicate)

4. **Structure Build:** Creates nested hierarchy
   - H2 tags are top-level items
   - H3 tags are nested under the preceding H2

5. **Render:** Injects TOC into page
   - Creates aside element with `.toc-container` class
   - Appends to document body
   - Positions fixed on right side

### Scroll Behavior

- **Scroll Spy:** Tracks scroll position every 100ms (throttled)
- **Active Detection:** Highlights section you're currently reading
- **Smooth Scroll:** Animated scrolling when clicking TOC links (accounts for 100px header offset)

---

## 🔧 Customization Options

### Change Position

```css
.toc-container {
  /* Default: right side */
  right: 40px;
  
  /* Move to left side */
  left: 40px;
  right: auto;
  
  /* Adjust vertical position */
  top: 100px; /* Closer to header */
}
```

### Change Width

```css
.toc-container {
  width: 320px; /* Wider */
  width: 240px; /* Narrower */
}
```

### Change Colors

```css
.toc-container {
  /* Background */
  background: rgba(20, 20, 30, 0.8);
  
  /* Border */
  border-color: rgba(139, 92, 246, 0.2); /* Purple */
}

.toc-link.active {
  /* Active link color */
  color: #10b981; /* Green */
  border-left-color: #10b981;
}
```

### Show on Smaller Screens

```css
/* Change breakpoint from 1280px to 1024px */
@media (max-width: 1024px) {
  .toc-container {
    display: none;
  }
}

/* Or show on all screens but adjust position */
@media (max-width: 768px) {
  .toc-container {
    position: relative;
    width: 100%;
    right: 0;
    top: 0;
    margin: var(--spacing-xl) 0;
  }
}
```

### Adjust Scroll Offset

In the JavaScript section, find the `smoothScrollTo` function:

```javascript
function smoothScrollTo(targetId) {
  const offset = 100; // Change this value
  // 80 = less space from top
  // 120 = more space from top
}
```

---

## 📝 Writing Posts for TOC

### Heading Structure

**Good Structure:**
```html
<h2>Introduction</h2>
<p>Content here...</p>

<h2>Main Section</h2>
<p>Content here...</p>

<h3>Subsection A</h3>
<p>More specific content...</p>

<h3>Subsection B</h3>
<p>More specific content...</p>

<h2>Conclusion</h2>
<p>Closing thoughts...</p>
```

This creates:
```
• Introduction
• Main Section
  - Subsection A
  - Subsection B
• Conclusion
```

**Avoid:**
- Starting with H3 before any H2 (orphaned subsections)
- Skipping heading levels (H2 → H4)
- Having only one heading in the entire post

### Heading Best Practices

1. **Use descriptive text:** "Getting Started" not "Part 1"
2. **Keep them concise:** 3-8 words ideal
3. **Use parallel structure:** Start with verbs or nouns consistently
4. **Avoid special characters:** IDs are generated from heading text
5. **Don't duplicate:** Each heading should be unique

---

## 🐛 Troubleshooting

### TOC doesn't appear

**Possible causes:**
1. Not on a single post page (only shows on `.html` posts, not homepage)
2. Screen width < 1280px (TOC hidden on smaller screens)
3. No H2 or H3 tags in post content
4. JavaScript error (check browser console)

**Solution:**
- Verify URL has `.html` extension
- Test on desktop with wide viewport
- Add H2/H3 headings to your post
- Check browser console for errors

### TOC is empty

**Cause:** No H2 or H3 headings found in post body

**Solution:**
Structure your post with proper headings:
```html
<h2>First Section</h2>
<p>Content...</p>

<h2>Second Section</h2>
<p>Content...</p>
```

### Headings not clickable

**Cause:** JavaScript may not be finding the post content container

**Solution:**
Check the `findPostContent()` function selectors. Your theme might use a different class name for post body. Common selectors are already included:
- `.post-body`
- `[itemprop="articleBody"]`  
- `.entry-content`
- `article`

### Active highlighting not working

**Cause:** Scroll position calculation may need adjustment

**Solution:**
In the JavaScript, adjust the `updateActiveSection` function:
```javascript
const scrollPosition = window.scrollY + 150; // Change this offset
```

### TOC blocks content

**Cause:** Fixed positioning might overlap post content on narrower screens

**Solution:**
- Adjust the breakpoint in CSS (change 1280px to higher value)
- Or add padding to post content on medium screens

---

## 📱 Responsive Behavior

### Desktop (> 1280px)
✅ **TOC visible** as fixed sidebar on right

### Tablet (768px - 1280px)
❌ **TOC hidden** to prevent overlap and preserve reading space

### Mobile (< 768px)
❌ **TOC hidden** for optimal mobile reading experience

---

## ⚡ Performance

- **Lightweight:** ~5KB of JavaScript
- **Efficient:** Throttled scroll listeners (100ms)
- **No dependencies:** Pure vanilla JavaScript
- **Smart detection:** Only initializes on post pages
- **Smooth:** GPU-accelerated animations (backdrop-filter)

---

## 🎯 Browser Support

### Full Support
- ✅ Chrome/Edge (88+)
- ✅ Firefox (90+)
- ✅ Safari (14+)
- ✅ Opera (75+)

### Partial Support
- ⚠️ Older browsers: TOC will work but without glassmorphic blur effect

---

## 💡 Usage Tips

### For Readers
- Click any section in TOC to jump instantly
- Current section is highlighted in blue
- Scroll naturally - TOC follows your position

### For Writers
1. **Structure your posts:** Use H2 for main sections, H3 for subsections
2. **Descriptive headings:** Make them meaningful for skimming
3. **Logical flow:** Organize content hierarchically
4. **Preview:** Check TOC appearance after publishing

### For Designers
- TOC inherits your theme's CSS variables
- Customize via `.toc-container` and `.toc-link` classes
- Matches dark mode and glassmorphism aesthetic
- Animations can be disabled by removing keyframes

---

## 🔍 Technical Details

### Selectors Used

**Post Content Detection:**
```javascript
'.post-body'
'[itemprop="articleBody"]'
'.entry-content'
'article .content'
'.post-content'
'article'
'.blog-post'
'main article'
```

**Heading Extraction:**
```javascript
container.querySelectorAll('h2, h3')
```

### ID Generation Algorithm

1. Convert text to lowercase
2. Trim whitespace
3. Replace spaces with hyphens
4. Remove non-word characters
5. Remove duplicate hyphens
6. Trim hyphens from start/end
7. Add counter suffix if duplicate exists

**Example:**
```
"Getting Started with React" → "getting-started-with-react"
"API Integration (Part 2)" → "api-integration-part-2"
"User Management" → "user-management"
"User Management" (duplicate) → "user-management-1"
```

### Z-Index Layering
- TOC: `z-index: 100`
- Header: `z-index: var(--z-header)` (typically 1000)
- TOC stays below header but above content

---

## 🚀 What's Next?

The TOC is now fully functional! To test it:

1. **Create a post** with several H2 and H3 headings
2. **Publish** the post
3. **View** on desktop (viewport > 1280px wide)
4. **See** the TOC appear on the right side
5. **Click** sections to jump smoothly
6. **Scroll** to see active highlighting

### Enhancement Ideas

If you want to extend this feature:
- Add collapse/expand functionality
- Add progress indicator
- Make it closable/toggleable
- Add keyboard navigation
- Add reading progress percentage
- Create mobile version (bottom drawer)

---

## ✨ Feature Summary

**What it does:**
- Automatically generates Table of Contents from post headings
- Shows as fixed sidebar on desktop
- Highlights current section while reading
- Smooth scrolls to sections when clicked

**When it appears:**
- Single post pages only
- Desktop screens (> 1280px)
- Posts with H2 or H3 headings

**Visual style:**
- Dark glassmorphic card
- Blue accent colors
- Smooth animations
- Modern minimal design

---

## 📞 Need Help?

- **JavaScript console:** Check for TOC debug messages
- **Inspect element:** Look for `.toc-container` in DOM
- **Network tab:** Ensure no script loading errors
- **Responsive mode:** Test different viewport widths

The TOC feature is production-ready and will enhance your readers' experience on long-form content! 🎉
