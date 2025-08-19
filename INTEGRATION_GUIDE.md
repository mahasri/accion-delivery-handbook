# Handbook Integration Guide

## Overview
This guide explains how to integrate the Accion Delivery Handbook as a menu item in your main website.

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

## Option 2: Iframe Embed

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

## Option 3: Custom Integration

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

### Debug Steps
1. Check browser console for errors
2. Verify file paths and permissions
3. Test handbook in isolation first
4. Check network requests for missing resources

## Best Practices

1. **Keep handbook separate**: Maintain as independent project
2. **Use consistent URLs**: Plan URL structure carefully
3. **Test thoroughly**: Verify all links and functionality
4. **Monitor performance**: Optimize loading times
5. **Backup regularly**: Keep copies of working configurations

## Support

For issues with:
- **Handbook content**: Update markdown files
- **Configuration**: Modify `mkdocs.yml`
- **Styling**: Edit `overrides/main.html`
- **Integration**: Follow this guide
