# SharePoint Integration Guide

## 🌐 Embedding the Accion Delivery Handbook in SharePoint

This guide explains how to integrate the MkDocs handbook into your SharePoint site.

## 📋 Prerequisites

1. **GitHub Pages Deployment**: The handbook must be deployed to GitHub Pages
2. **SharePoint Admin Access**: You need permissions to add web parts
3. **Public URL**: The handbook should be accessible via public URL

## 🚀 Method 1: Iframe Embed (Recommended)

### Step 1: Get the Handbook URL
```
https://mahasri.github.io/accion-delivery-handbook/
```

### Step 2: Add to SharePoint Page
1. **Edit your SharePoint page**
2. **Add "Embed" web part**
3. **Paste the handbook URL**
4. **Save and publish**

### Step 3: Custom Iframe Code (Optional)
For more control, use this HTML in the Embed web part:

```html
<iframe 
  src="https://mahasri.github.io/accion-delivery-handbook/" 
  width="100%" 
  height="800px" 
  frameborder="0"
  style="border: none; box-shadow: 0 2px 8px rgba(0,0,0,0.1);">
  <p>Your browser does not support iframes. 
  <a href="https://mahasri.github.io/accion-delivery-handbook/" target="_blank">Open handbook in new window</a></p>
</iframe>
```

## 🔗 Method 2: Navigation Link

### Add to SharePoint Navigation
1. **Go to Site Settings**
2. **Navigation**
3. **Add link to handbook URL**
4. **Set to open in new window**

## 📱 Method 3: SharePoint App/Web Part

### Custom Web Part Development
If you have development resources, create a custom SharePoint web part:

```typescript
// Example SharePoint Framework web part
export default class HandbookWebPart extends BaseClientSideWebPart<IHandbookWebPartProps> {
  public render(): void {
    this.domElement.innerHTML = `
      <div style="height: 100vh;">
        <iframe 
          src="https://mahasri.github.io/accion-delivery-handbook/"
          style="width: 100%; height: 100%; border: none;">
        </iframe>
      </div>
    `;
  }
}
```

## ⚙️ Configuration Options

### Responsive Design
The handbook is already optimized for embedded viewing:
- ✅ **Mobile-friendly** layout
- ✅ **Responsive** design
- ✅ **Smaller fonts** for iframe viewing
- ✅ **Collapsible** navigation

### SharePoint-Specific Settings

#### 1. **Page Layout**
- Use **Full-width** page layout
- Set **minimum height** to 600px
- Enable **responsive** design

#### 2. **Security Settings**
- Ensure **CSP (Content Security Policy)** allows iframe embedding
- Add handbook domain to **trusted sites** if needed

#### 3. **Performance**
- **Lazy load** the iframe for better performance
- Consider **caching** strategies

## 🔧 Troubleshooting

### Common Issues

#### 1. **Iframe Not Loading**
- Check if the handbook URL is accessible
- Verify SharePoint allows iframe embedding
- Check browser console for errors

#### 2. **Layout Issues**
- Adjust iframe height/width
- Check responsive design settings
- Test on different screen sizes

#### 3. **Authentication Issues**
- Ensure handbook is publicly accessible
- Check SharePoint authentication settings
- Verify URL permissions

### Debug Steps
1. **Test URL** in browser directly
2. **Check browser console** for errors
3. **Verify SharePoint permissions**
4. **Test on different devices**

## 📊 Best Practices

### 1. **User Experience**
- Provide **fallback link** if iframe fails
- Add **loading indicator**
- Ensure **keyboard navigation** works

### 2. **Performance**
- **Preload** handbook for faster access
- Use **CDN** for better performance
- Implement **caching** strategies

### 3. **Accessibility**
- Ensure **screen reader** compatibility
- Provide **alternative text**
- Test **keyboard navigation**

### 4. **Security**
- Use **HTTPS** URLs only
- Implement **CSP** headers
- Regular **security updates**

## 🎯 Integration Examples

### Example 1: Team Site Integration
```
SharePoint Team Site
├── Home
├── Documents
├── Handbook (Embedded)
├── Calendar
└── Tasks
```

### Example 2: Communication Site
```
SharePoint Communication Site
├── News
├── Resources
│   └── Delivery Handbook (Embedded)
├── About
└── Contact
```

### Example 3: Hub Site
```
SharePoint Hub Site
├── Hub Navigation
├── Associated Sites
│   ├── Project Management
│   │   └── Handbook (Embedded)
│   ├── Development
│   └── Operations
└── Shared Resources
```

## 📞 Support

For technical support:
1. **Check this guide** first
2. **Review troubleshooting** section
3. **Contact your SharePoint admin**
4. **Check GitHub issues** for the handbook

## 🔄 Updates and Maintenance

### Regular Updates
- **Monitor** handbook updates
- **Test** integration after updates
- **Update** iframe URLs if needed
- **Backup** custom configurations

### Version Control
- **Track** SharePoint changes
- **Document** customizations
- **Maintain** integration guide
- **Update** this documentation

---

**Last Updated**: December 2024
**Version**: 1.0
**Compatibility**: SharePoint Online, SharePoint 2019, SharePoint 2016
