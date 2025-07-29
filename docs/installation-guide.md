# SMARTLOCKEG Shopify Theme Installation Guide

**Author:** youssefsaberr  
**Date:** 2025-07-29  
**Repository:** shopify-custom-themes  
**Store:** SMARTLOCKEG (thv1ip-dc.myshopify.com)

## Overview

This guide explains how to install and configure the custom Shopify theme components for SMARTLOCKEG smart lock products.

## 📁 Repository Structure

```
shopify-custom-themes/
├── sections/
│   └── custom-product-info.liquid     # Main product display section
├── templates/
│   └── product.smartlock.liquid       # Custom product template
├── assets/
│   └── smartlock-custom.css          # Custom styling
├── snippets/
│   └── product-metafields.liquid     # Reusable metafield component
├── docs/
│   └── installation-guide.md         # This guide
└── README.md                         # Project overview
```

## 🚀 Installation Steps

### Step 1: Access Your Shopify Theme

1. Go to your Shopify admin dashboard
2. Navigate to **Online Store** → **Themes**
3. Find your current theme and click **Actions** → **Edit code**

### Step 2: Add the Custom Files

#### 2.1 Add the CSS File
1. In the **Assets** folder, click **Add a new asset**
2. Choose **Create a blank file**
3. Name it: `smartlock-custom.css`
4. Copy the content from `assets/smartlock-custom.css` in this repository
5. Save the file

#### 2.2 Add the Product Section
1. In the **Sections** folder, click **Add a new section**
2. Name it: `custom-product-info`
3. Copy the content from `sections/custom-product-info.liquid`
4. Save the file

#### 2.3 Add the Snippet
1. In the **Snippets** folder, click **Add a new snippet**
2. Name it: `product-metafields`
3. Copy the content from `snippets/product-metafields.liquid`
4. Save the file

#### 2.4 Add Custom Product Template (Optional)
1. In the **Templates** folder, click **Add a new template**
2. Choose **product** as the template type
3. Name it: `product.smartlock`
4. Copy the content from `templates/product.smartlock.liquid`
5. Save the file

### Step 3: Configure Product Templates

#### Option A: Use the Complete Custom Template
1. Go to **Products** in your Shopify admin
2. Select a smart lock product
3. In the **Search engine listing preview** section, click **Edit website SEO**
4. Change the **Template suffix** to `smartlock`
5. Save the product

#### Option B: Add Section to Existing Template
1. Find your current product template (usually `sections/product-form.liquid`)
2. Add this line where you want the custom section to appear:
```liquid
{% section 'custom-product-info' %}
```

## 🏷️ Setting Up Metafields

To display custom content in the collapsible sections, you need to add metafields:

### Step 1: Access Metafields
1. Go to **Products** → Select a product
2. Scroll down to **Metafields** section
3. Click **Add metafield** if not visible

### Step 2: Create Required Metafields

Create these metafields with namespace `custom`:

| Metafield Key | Type | Description |
|---------------|------|-------------|
| `unlocking_functions_content` | Multi-line text | HTML content for unlocking functions |
| `key_features_content` | Multi-line text | HTML content for key features |
| `specs_content` | Multi-line text | HTML content for specifications |
| `installation_guide` | Multi-line text | Installation instructions |
| `warranty_info` | Multi-line text | Warranty information |
| `compatibility_info` | Multi-line text | Smart home compatibility |

### Step 3: Add Content Examples

#### Unlocking Functions Example:
```html
<h3>Advanced Unlocking Capabilities</h3>
<ul>
  <li>Smartphone app control with Bluetooth and WiFi</li>
  <li>Biometric fingerprint recognition (up to 100 fingerprints)</li>
  <li>Digital keypad with customizable codes</li>
  <li>Physical key backup option</li>
  <li>Voice control via Alexa and Google Assistant</li>
</ul>
```

#### Key Features Example:
```html
<h3>Smart Security Features</h3>
<ul>
  <li>Real-time notifications and activity logs</li>
  <li>Auto-lock functionality with timer settings</li>
  <li>Weather-resistant design (IP65 rating)</li>
  <li>Long-lasting battery (12+ months)</li>
  <li>Tamper alerts and forced entry detection</li>
</ul>
```

## 🎨 Customization Options

### Color Scheme
Edit `assets/smartlock-custom.css` to change colors:

```css
/* Primary brand color */
--smartlock-primary: #0066cc;

/* Success/security color */
--smartlock-success: #28a745;

/* Background colors */
--smartlock-bg-light: #f8f9fa;
--smartlock-bg-dark: #343a40;
```

### Typography
Adjust font sizes in the CSS file:

```css
.smartlock-title { font-size: 2.5em; }
.smartlock-price { font-size: 1.8em; }
```

### Layout
Modify the grid layout:

```css
.smartlock-product-wrap {
  display: flex;
  gap: 2rem; /* Adjust spacing */
}
```

## 🔧 Using the Snippet Component

The `product-metafields` snippet can be used in multiple ways:

### Basic Usage
```liquid
{% render 'product-metafields', 
   product: product, 
   section_type: 'features', 
   show_as_accordion: true %}
```

### Multiple Sections
```liquid
{% render 'product-metafields', product: product, section_type: 'functions' %}
{% render 'product-metafields', product: product, section_type: 'features' %}
{% render 'product-metafields', product: product, section_type: 'specs' %}
```

### Available Section Types
- `functions` - Unlocking Functions
- `features` - Key Features  
- `specs` - Technical Specifications
- `installation` - Installation Guide
- `warranty` - Warranty Information
- `compatibility` - Smart Home Compatibility

## 📱 Mobile Responsiveness

The theme automatically adapts to mobile devices:
- Stacked layout on screens < 768px
- Optimized touch targets
- Readable font sizes
- Compressed spacing

## 🧪 Testing Checklist

Before going live, test these features:

- [ ] Product images display correctly
- [ ] Collapsible sections open/close smoothly
- [ ] Metafield content appears properly
- [ ] Add to cart button functions
- [ ] Mobile layout looks good
- [ ] Page loads quickly
- [ ] CSS styles load properly

## 🐛 Troubleshooting

### Section Not Appearing
- Verify the section file is saved in `/sections/`
- Check that the section is added to your template
- Ensure there are no Liquid syntax errors

### Styles Not Loading
- Confirm CSS file is in `/assets/` folder
- Check that the CSS is linked in your template:
```liquid
{{ 'smartlock-custom.css' | asset_url | stylesheet_tag }}
```

### Metafields Not Showing
- Verify metafield namespace is `custom`
- Check metafield key names match exactly
- Ensure content is saved in the metafields

### Mobile Issues
- Clear browser cache
- Test on actual mobile devices
- Check CSS media queries are working

## 🔄 Updates and Maintenance

### Updating Code
1. Pull latest changes from this repository
2. Copy updated files to your Shopify theme
3. Test changes on a development theme first
4. Deploy to live theme after testing

### Version Control
- Keep track of changes in this repository
- Document any custom modifications
- Back up your theme before major updates

## 📞 Support

For issues with this custom theme:

1. Check this documentation first
2. Review the troubleshooting section
3. Test on a duplicate theme
4. Document the specific issue and steps to reproduce

## 📈 Performance Tips

- Optimize images before uploading
- Minimize custom CSS when possible
- Use lazy loading for images
- Test page speed regularly

---

**Last Updated:** 2025-07-29  
**Version:** 1.0.0  
**Compatible with:** Shopify 2.0 themes
