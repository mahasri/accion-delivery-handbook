# Handbook Integration Guide

## Overview
This guide explains how to integrate the Accion Delivery Handbook as a menu item in your main website, with special optimizations for embedded views.

## Option 1: Subdirectory Integration (Recommended)

### Step 1: Build the Handbook
```bash
# In the handbook directory
mkdocs build
```

### Step 2: Copy to Main Website
```bash
# Copy the built site to your main website
cp -r site/ /path/to/your-main-website/handbook/
```

### Step 3: Add Menu Item
Add this to your main website's navigation:

```html
<!-- Example navigation structure -->
<nav>
    <a href="/">Home</a>
    <a href="/about">About</a>
    <a href="/services">Services</a>
    <a href="/handbook/">Delivery Handbook</a>  <!-- Add this line -->
    <a href="/contact">Contact</a>
</nav>
```

### Step 4: Update Configuration
The handbook is already configured with:
- `site_url: https://your-main-website.com/`
- `base_path: /handbook/`

## Option 2: Iframe Embed (Enhanced for Embedded View)

### Step 1: Create Handbook Page
```html
<!-- handbook.html in your main website -->
<!DOCTYPE html>
<html>
<head>
    <title>Delivery Handbook - Your Company</title>
    <style>
        .handbook-container {
            width: 100%;
            height: 100vh;
            border: none;
            overflow: hidden;
        }
        
        /* Responsive iframe container */
        @media (max-width: 768px) {
            .handbook-container {
                height: 90vh;
            }
        }
    </style>
</head>
<body>
    <iframe src="/handbook/" class="handbook-container"></iframe>
</body>
</html>
```

### Step 2: Add to Navigation
```html
<a href="/handbook.html">Delivery Handbook</a>
```

## 🆕 Option 3: Embedded-Friendly Layout (NEW!)

The handbook now includes **automatic embedded view detection** and **responsive layout optimization**:

### Features for Embedded View:
- ✅ **Left sidebar always visible** (280px width)
- ✅ **Right sidebar repositioned** (fixed on right side)
- ✅ **Responsive design** (adapts to iframe size)
- ✅ **Mobile navigation toggle** (for small screens)
- ✅ **Compact typography** (optimized for embedded view)
- ✅ **Header/footer hidden** (saves space)

### Layout Behavior:

#### **Large Screens (>1200px):**
```
┌─────────────┬─────────────────────┬─────────────┐
│   Left      │      Content        │   Right     │
│ Sidebar     │      Area           │  Sidebar    │
│ (280px)     │                     │  (280px)    │
│             │                     │             │
└─────────────┴─────────────────────┴─────────────┘
```

#### **Medium Screens (768px-1200px):**
```
┌─────────────┬─────────────────────┐
│   Left      │      Content        │
│ Sidebar     │      Area           │
│ (280px)     │                     │
│             │                     │
│             ├─────────────────────┤
│             │   Right Sidebar     │
│             │   (at top)          │
└─────────────┴─────────────────────┘
```

#### **Small Screens (<768px):**
```
┌─────────────────────────────────┐
│ [☰] Content Area               │
│                                │
│                                │
│                                │
│                                │
└─────────────────────────────────┘
```
*Left sidebar hidden, toggle button shows*

### Automatic Detection:
The handbook automatically detects when it's embedded in an iframe and:
- Hides header and footer
- Optimizes typography for compact view
- Enables mobile navigation toggle
- Adjusts layout responsively

## Option 4: Custom Integration

### Step 1: Extract Content
Use MkDocs' search API to access handbook content:

```javascript
// Example: Fetch handbook search index
fetch('/handbook/search/search_index.json')
    .then(response => response.json())
    .then(data => {
        // Process handbook content
        console.log(data);
    });
```

### Step 2: Build Custom UI
Create custom components to display handbook content with your site's styling.

## Configuration Options

### For Different Base Paths
Update `mkdocs.yml`:

```yaml
# For /docs/ path
base_path: /docs/

# For /resources/handbook/ path
base_path: /resources/handbook/

# For root path
base_path: /
```

### For Different Domains
```yaml
# For subdomain
site_url: https://handbook.yourcompany.com/

# For different domain
site_url: https://docs.yourcompany.com/
```

## Styling Integration

### Option A: Match Main Site Theme
Update `overrides/main.html` to match your main site's colors and fonts.

### Option B: Custom CSS
Add custom CSS to integrate with your main site's design system.

### Option C: Embedded-Specific Styling
The handbook includes embedded-specific optimizations:
- Compact typography
- Optimized spacing
- Mobile-friendly navigation
- Responsive layout

## Search Integration

### Global Search
Include handbook content in your main site's search:

```javascript
// Example: Integrate handbook search
const handbookSearchIndex = await fetch('/handbook/search/search_index.json');
// Merge with main site search results
```

## Deployment

### Static Hosting
- Netlify, Vercel, GitHub Pages
- Copy `site/` contents to hosting platform

### Server Hosting
- Apache: Copy to web root
- Nginx: Configure location block
- Node.js: Serve static files

## Maintenance

### Updates
1. Make changes to handbook content
2. Run `mkdocs build`
3. Copy new `site/` contents to main website
4. Deploy main website

### Version Control
- Keep handbook in separate repository
- Use CI/CD to auto-deploy changes
- Tag releases for version management

## Troubleshooting

### Common Issues
1. **Broken links**: Check `base_path` configuration
2. **Missing assets**: Ensure all files copied to correct location
3. **Styling conflicts**: Use CSS isolation techniques
4. **Search not working**: Verify search index is accessible
5. **Embedded layout issues**: Check iframe dimensions and responsive breakpoints

### Debug Steps
1. Check browser console for errors
2. Verify file paths and permissions
3. Test handbook in isolation first
4. Check network requests for missing resources
5. Test embedded view in different screen sizes

## Best Practices

1. **Keep handbook separate**: Maintain as independent project
2. **Use consistent URLs**: Plan URL structure carefully
3. **Test thoroughly**: Verify all links and functionality
4. **Monitor performance**: Optimize loading times
5. **Backup regularly**: Keep copies of working configurations
6. **Test embedded view**: Verify layout works in iframe scenarios
7. **Responsive testing**: Test on different screen sizes

## Support

For issues with:
- **Handbook content**: Update markdown files
- **Configuration**: Modify `mkdocs.yml`
- **Styling**: Edit `overrides/main.html`
- **Embedded layout**: Check responsive breakpoints and iframe settings
- **Integration**: Follow this guide
