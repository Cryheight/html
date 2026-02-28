AURA Portfolio - Modification Guide

This guide explains how to customize and modify the AURA portfolio website. The code is extensively commented to help you understand what each section does.

---

Table of Contents

1. [Quick Start](#quick-start)
2. [File Structure](#file-structure)
3. [Changing Colors & Theme](#changing-colors--theme)
4. [Modifying Content](#modifying-content)
5. [Adding Projects](#adding-projects)
6. [Updating Social Media Links](#updating-social-media-links)
7. [Navigation & Sections](#navigation--sections)
8. [Images](#images)
9. [Typography](#typography)
10. [Troubleshooting](#troubleshooting)

---

Quick Start

To modify the website:

1. Open `aura-portfolio.html` in any text editor
2. Look for the comments (marked with `/* === SECTION NAME === */` or `<!-- === SECTION NAME === -->`)
3. Edit the content between the tags
4. Save and refresh your browser

No build process required - this is a standalone HTML file that works immediately in any browser.

---

File Structure

```
├── aura-portfolio.html    # Main website file (all HTML, CSS, JS in one file)
└── MODIFICATION_GUIDE.md  # This guide
```

The website is a single-page application with all code (HTML, CSS, JavaScript) in one file for simplicity.

---

Changing Colors & Theme

Color Variables

All colors are defined as CSS variables at the top of the `<style>` section:

```css
:root {
    --color-bg: #0A0A0A;        /* Main background - dark black */
    --color-surface: #141414;    /* Card backgrounds - slightly lighter */
    --color-gold: #C9A962;       /* Accent color - gold highlights */
    --color-text: #F5F5F5;       /* Primary text - off-white */
    --color-muted: #6B6B6B;      /* Secondary text - gray */
}
```

How to Change the Theme

1. Find the `:root` selector in the CSS (around line 50)
2. Modify the color values:

Example - Change to a Blue Theme:

```css
:root {
    --color-bg: #0a0a1a;
    --color-surface: #141428;
    --color-gold: #62a9c9;    /* Changed from gold to blue */
    --color-text: #F5F5F5;
    --color-muted: #6B6B8B;
}
```

Example - Light Theme:

```css
:root {
    --color-bg: #F5F5F5;
    --color-surface: #FFFFFF;
    --color-gold: #C9A962;
    --color-text: #0A0A0A;
    --color-muted: #6B6B6B;
}
```

> Note: For a light theme, you'll also need to adjust the `mix-blend-difference` on the navigation and cursor for visibility.

---

Modifying Content

Hero Section

Location: Look for `<!-- HERO SECTION -->` comment

Elements to modify:

1. Subtitle (line 520):
   
```html
   <span class="reveal-text">Creative Director & Visual Artist</span>
   ```

2. Main Title (lines 524-532):
   
```html
   <h1 class="hero-title mb-8">
       <div class="overflow-hidden">
           <span class="reveal-text block">Crafting</span>
       </div>
       <div class="overflow-hidden">
           <span class="reveal-text block">Digital <em class="gold-text not-italic">Experiences</em></span>
       </div>
       <div class="overflow-hidden">
           <span class="reveal-text block">That Matter</span>
       </div>
   </h1>
   ```

3. Description (line 535):
   
```html
   <p class="text-gray-400 max-w-xl text-lg mb-12 leading-relaxed opacity-0" id="hero-desc">
       Award-winning creative studio specializing in brand identity, art direction, and immersive web experiences for luxury brands and cultural institutions.
   </p>
   ```

4. CTA Button Text (line 540):
   
```html
   <span>View Selected Work</span>
   ```

About Section

Location: Look for `<!-- ABOUT SECTION -->` comment

Elements to modify:

1. Section Title (line 720):
   
```html
   <h2 class="text-5xl md:text-6xl font-light leading-tight mb-8" style="font-family: 'Playfair Display', serif;">
       Where vision meets <span class="gold-text">craft</span>
   </h2>
   ```

2. Paragraphs (lines 724-729):
   
```html
   <p class="text-gray-400 leading-relaxed mb-6">
       Founded in 2018, AURA is a creative studio dedicated to crafting exceptional brand experiences...
   </p>
   ```

3. Statistics (lines 734-737):
   
```html
   <div class="absolute -bottom-8 -left-8 bg-neutral-900 p-8 border border-white/10">
       <p class="text-4xl font-light gold-text mb-2">150+</p>
       <p class="text-sm text-gray-400 uppercase tracking-widest">Projects Delivered</p>
   </div>
   ```

Services Section

Location: Look for `<!-- SERVICES SECTION -->` comment

To modify a service:

1. Find the service block (e.g., Service 1 around line 640)
2. Edit the title, number, and description:
   
```html
   <div class="group border-b border-white/10 pb-8 hover:border-amber-400/50 transition-colors">
       <div class="flex justify-between items-start mb-4">
           <h3 class="text-2xl font-light">Brand Strategy</h3>  <!-- CHANGE TITLE -->
           <span class="text-amber-400 text-sm">01</span>         <!-- CHANGE NUMBER -->
       </div>
       <p class="text-gray-400 leading-relaxed">                 <!-- CHANGE DESCRIPTION -->
           Comprehensive brand positioning, visual identity systems, and strategic consulting for luxury markets.
       </p>
   </div>
   ```

To add a new service:

Copy an existing service block and paste it after the last one. Update:
- The service number (01, 02, 03, 04...)
- The service title
- The service description

---

Adding Projects

Location: Look for `<!-- FEATURED WORK / GALLERY SECTION -->` comment

Understanding the Project Card Structure

Each project is wrapped in a `project-card` div:

```html
<div class="project-card aspect-[4/5] group cursor-pointer" data-cursor="hover">
    <!-- Project Image -->
    <img src="IMAGE_URL" alt="Project Name">
    
    <!-- Hover Overlay -->
    <div class="project-overlay">
        <p class="text-xs uppercase tracking-widest text-amber-400 mb-2">Category</p>
        <h3 class="text-3xl font-light mb-2" style="font-family: 'Playfair Display', serif;">Project Title</h3>
        <p class="text-sm text-gray-400">Project Description</p>
    </div>
</div>
```

Steps to Add a New Project

1. Copy an existing project card (e.g., Project 1 or Project 4)

2. Update the image URL:
   
```html
   <img src="https://your-image-url.jpg" alt="Your Project Name">
   ```

   
   Image sources:
   - Unsplash: `https://images.unsplash.com/photo-XXXX?w=800&q=80`
   - Your own images: Upload to a CDN or hosting service
   - Local images: `./images/your-image.jpg` (create an `images` folder)

3. Update the overlay content:
   
```html
   <p class="text-xs uppercase tracking-widest text-amber-400 mb-2">Web Design</p>
   <h3 class="text-3xl font-light mb-2" style="font-family: 'Playfair Display', serif;">Your Project Name</h3>
   <p class="text-sm text-gray-400">Brief description of the project</p>
   ```

4. Position the card:
   - Cards 1 & 3: No offset (start at top)
   - Cards 2 & 4: Add `mt-0 md:mt-24` for staggered layout

Example - Adding Project 5

```html
<!-- Project 5 -->
<div class="project-card aspect-[4/5] group cursor-pointer" data-cursor="hover">
    <img src="https://images.unsplash.com/photo-1550745165-9bc0b252726f?w=800&q=80" alt="Project 5">
    <div class="project-overlay">
        <p class="text-xs uppercase tracking-widest text-amber-400 mb-2">UI/UX Design</p>
        <h3 class="text-3xl font-light mb-2" style="font-family: 'Playfair Display', serif;">Tech Startup</h3>
        <p class="text-sm text-gray-400">Mobile App Redesign</p>
    </div>
</div>
```

Image Recommendations

- Aspect ratio: 4:5 (portrait) works best
- Size: At least 800px wide
- Format: JPG for photos, PNG for graphics with transparency
- Style: The CSS applies grayscale by default, color on hover

---

Updating Social Media Links

Footer Social Links

Location: Look for `<!-- FOOTER / CONTACT SECTION -->` comment

Find the social links section (around line 780):

```html
<div class="social-links">
    <a href="https://instagram.com" target="_blank" rel="noopener" class="social-link" aria-label="Instagram">
        <!-- SVG icon -->
    </a>
    <!-- More social links... -->
</div>
```

How to Update Links

1. Find the social platform you want to update
2. Change the `href` attribute to your profile URL:
   
```html
   <a href="https://instagram.com/yourusername" target="_blank" rel="noopener" class="social-link" aria-label="Instagram">
   ```

Available Social Icons

The following platforms are included:
- Instagram - Photo sharing
- Behance - Creative portfolio
- LinkedIn - Professional network
- Twitter/X - Microblogging
- Dribbble - Design showcase

Adding a New Social Platform

1. Find an SVG icon for the platform (from [Simple Icons](https://simpleicons.org/) or [Iconify](https://icon-sets.iconify.design/))
2. Add a new anchor tag:
   
```html
   <a href="YOUR_URL" target="_blank" rel="noopener" class="social-link" aria-label="Platform Name">
       <svg width="20" height="20" fill="currentColor" viewBox="0 0 24 24">
           <path d="YOUR_SVG_PATH"/>
       </svg>
   </a>
   ```

Side Drawer Social Links

Location: Inside `<!-- SIDE DRAWER NAVIGATION -->` (around line 430)

The same process applies - update the `href` attributes in the `.drawer-social` div.

---

Navigation & Sections

Understanding Section IDs

Each major section has an `id` attribute for navigation:

Section	ID	Linked From	
Hero	(none)	Logo click	
Featured Work	`#work`	"Work" link, "Gallery" drawer link	
About	`#about`	"About" link	
Services	`#services`	"Services" link	
Contact	`#contact`	"Contact" link	

Adding a New Section

1. Create the section HTML:
   
```html
   <section id="newsection" class="py-32 px-8 md:px-16">
       <div class="max-w-7xl mx-auto">
           <!-- Your content here -->
       </div>
   </section>
   ```

2. Add to desktop navigation:
   
```html
   <div class="hidden md:flex gap-12">
       <a href="#work" class="nav-link">Work</a>
       <a href="#about" class="nav-link">About</a>
       <a href="#services" class="nav-link">Services</a>
       <a href="#newsection" class="nav-link">New Section</a>  <!-- ADD THIS -->
       <a href="#contact" class="nav-link">Contact</a>
   </div>
   ```

3. Add to side drawer:
   
```html
   <nav class="drawer-nav">
       <a href="#work" class="drawer-link" data-drawer-link>
           <span class="drawer-link-number">01</span>Gallery
       </a>
       <!-- ... other links ... -->
       <a href="#newsection" class="drawer-link" data-drawer-link>  <!-- ADD THIS -->
           <span class="drawer-link-number">05</span>New Section
       </a>
   </nav>
   ```

Reordering Sections

1. Move the entire `<section>` block in the HTML
2. Update the navigation links to match the new order
3. Update the drawer link numbers if you use sequential numbering

---

Images

Using Unsplash Images

The site uses Unsplash for placeholder images. To find your own:

1. Go to [unsplash.com](https://unsplash.com)
2. Find an image you like
3. Click "Download" or copy the image URL
4. Use format: `https://images.unsplash.com/photo-XXXX?w=800&q=80`

Parameters:
- `w=800` - Width in pixels
- `q=80` - Quality (0-100)

Using Your Own Images

1. Create an `images` folder in the same directory as your HTML file
2. Add your images: `images/project1.jpg`, `images/project2.jpg`, etc.
3. Update the src: `<img src="./images/project1.jpg" alt="Project 1">`

Image Optimization Tips

- Compress images using [TinyPNG](https://tinypng.com/) or [Squoosh](https://squoosh.app/)
- Use WebP format for smaller file sizes (with JPG fallback)
- Keep hero images under 500KB
- Keep project images under 300KB each

---

Typography

Font Families

Two fonts are used:

1. Inter - Body text, navigation, descriptions
   
```css
   font-family: 'Inter', sans-serif;
   ```

2. Playfair Display - Headlines, titles, elegant text
   
```css
   font-family: 'Playfair Display', serif;
   ```

Changing Fonts

1. Add new font import in the `<head>`:
   
```html
   <link href="https://fonts.googleapis.com/css2?family=Your+Font:wght@400;600&display=swap" rel="stylesheet">
   ```

2. Update CSS to use the new font:
   
```css
   .hero-title {
       font-family: 'Your Font', serif;
   }
   ```

Font Sizes

The site uses responsive font sizes with `clamp()`:

```css
font-size: clamp(MINIMUM, PREFERRED, MAXIMUM);
```

Example:

```css
font-size: clamp(3rem, 12vw, 10rem);
```

- Minimum: 3rem (48px)
- Preferred: 12vw (12% of viewport width)
- Maximum: 10rem (160px)

---

Troubleshooting

Custom Cursor Not Working

Problem: Cursor doesn't appear or follow mouse

Solutions:
1. Check that GSAP is loading (check browser console for errors)
2. On touch devices, the cursor is automatically hidden
3. Ensure no other CSS is overriding the cursor styles

Smooth Scroll Not Working

Problem: Clicking navigation links jumps instead of smooth scrolling

Solutions:
1. Verify GSAP ScrollToPlugin is loaded (line 18)
2. Check that section IDs match the href attributes exactly
3. Look for JavaScript errors in the console

Images Not Loading

Problem: Project images show as broken

Solutions:
1. Check the image URL is correct
2. For Unsplash images, ensure the photo ID is valid
3. For local images, verify the file path is correct
4. Check browser console for 404 errors

Drawer Not Opening

Problem: Menu button doesn't open the side drawer

Solutions:
1. Check that JavaScript is enabled in the browser
2. Verify the menu button has `id="menuBtn"`
3. Check browser console for JavaScript errors

Animations Not Playing

Problem: Text doesn't animate on page load

Solutions:
1. Ensure GSAP library is loading (check network tab)
2. Check for JavaScript errors in console
3. Verify the element IDs match in HTML and JavaScript

---

Advanced Modifications

Disabling the Custom Cursor

To use the default browser cursor:

1. Remove or comment out these lines:
   
```html
   <div class="cursor"></div>
   <div class="cursor-dot"></div>
   ```

2. Add this CSS:
   
```css
   body {
       cursor: auto !important;
   }
   .cursor, .cursor-dot {
       display: none !important;
   }
   ```

Changing Animation Speed

Find the GSAP animation and modify the `duration`:

```javascript
// Original (1.2 seconds)
duration: 1.2

// Faster (0.8 seconds)
duration: 0.8

// Slower (2 seconds)
duration: 2
```

Disabling Animations

To disable all animations:

1. Remove or comment out the entire `<script>` section
2. Add this CSS to show all content:
   
```css
   .reveal-text, #hero-desc, #hero-cta {
       opacity: 1 !important;
       transform: none !important;
   }
   ```

---

Need Help?

If you encounter issues:

1. Check the browser console (F12 → Console) for errors
2. Validate your HTML at [validator.w3.org](https://validator.w3.org/)
3. Ensure all external libraries (GSAP, Tailwind) are loading
4. Test in multiple browsers (Chrome, Firefox, Safari)

---

License

This template is free to use for personal and commercial projects. Attribution is appreciated but not required.

---

Last Updated: 2024
Template Version: 1.0
