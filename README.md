# Quartz - Interactive About Section Component

## Overview

**Quartz** is a sophisticated about section component featuring animated statistics, responsive image grids, and clean typography. Designed for corporate websites, agency portfolios, and startup landing pages, Quartz combines visual storytelling with data-driven credibility through interactive number animations.
<img width="1920" height="1012" alt="quartz" src="https://github.com/user-attachments/assets/8e7aef43-f59c-4d99-a6e4-126ecf67ae75" />

## Live Demo

[View Live Demo](https://lefajmofokeng.github.io/Quartz/)

## Technical Architecture

### Core Stack
- **Vanilla JavaScript** - Pure ES6 with Intersection Observer API
- **CSS Grid & Flexbox** - Modern layout techniques
- **Inter Font** - Clean, geometric typeface
- **Pure HTML/CSS/JS** - Zero external dependencies
- **Responsive Design** - Mobile-first adaptive layout

### Component Structure

```
Quartz Component/
├── Two-column Grid Layout
│   ├── Image Grid Section
│   │   ├── Large Primary Image
│   │   ├── Secondary Image 1
│   │   └── Secondary Image 2
│   └── Content Section
│       ├── Section Header
│       ├── Main Headline
│       ├── Description Text
│       └── Statistics Container
│           ├── Animated Stat 1
│           └── Animated Stat 2
```

## Design Specifications

### Typography System
- **Font Family:** Inter (400-700 weights)
- **Section Header:** 14px uppercase with letter-spacing
- **Main Headline:** 52px desktop (scaling to 36px mobile)
- **Description Text:** 18px with optimal line-height
- **Stat Values:** 64px bold numbers with animation
- **Stat Labels:** 16px supporting text

### Color Palette
```css
Primary Text: #000000
Highlight: #999999 (muted gray for emphasis)
Secondary Text: #333333
Subdued Text: #666666 (headers)
Border: #e0e0e0
Background: #ffffff
```

### Layout Grid
- **Main Grid:** 2-column desktop (1fr 1fr), 1-column mobile
- **Image Grid:** 2x2 layout with large primary cell
- **Stats Grid:** 2-column desktop, 1-column mobile
- **Gap System:** Consistent spacing (8px, 40px, 60px, 80px)

### Image Specifications
- **Large Image:** Spans 2 rows (grid-row: span 2)
- **Small Images:** Square/cropped ratio
- **Object-fit:** Cover for consistent cropping
- **Border Radius:** 6px subtle rounding
- **Gap:** 8px between images

## Interactive Features

### Animated Number Counter
```javascript
// Key animation parameters
const duration = 2000;    // 2-second animation
const steps = 60;         // 60 frames for smoothness
const increment = target / steps;
const stepDuration = duration / steps;
```

### Intersection Observer Integration
- **Threshold:** 0.5 (50% visibility)
- **Root Margin:** 0px
- **Trigger:** Single animation per stat
- **State Tracking:** `.animated` class prevents re-triggering

### Data Attributes API
```html
<div class="stat-value" 
     data-target="5" 
     data-prefix="$" 
     data-suffix="B">
    $0B
</div>
```

## Integration Guide

### Basic Implementation

1. **Include Dependencies:**
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
<link rel="stylesheet" href="quartz.css">
```

2. **HTML Structure:**
```html
<section class="about-section">
    <div class="image-grid">
        <div class="image-card image-card--large">
            <img src="primary-image.jpg" alt="Description">
        </div>
        <div class="image-card">
            <img src="secondary-1.jpg" alt="Description">
        </div>
        <div class="image-card">
            <img src="secondary-2.jpg" alt="Description">
        </div>
    </div>

    <div class="content-section">
        <div>
            <h2 class="section-header">Section Title</h2>
            <h1 class="main-heading">
                Your <span class="highlight">headline</span> with emphasis
            </h1>
            <p class="description-text">Your description text here.</p>
        </div>

        <div class="stats-container">
            <div class="stat-item">
                <div class="stat-value" data-target="5" data-prefix="$" data-suffix="B">$0B</div>
                <div class="stat-label">Your stat description</div>
            </div>
            <!-- Additional stats -->
        </div>
    </div>
</section>

<script src="quartz.js"></script>
```

## Customization Options

### JavaScript Configuration
```javascript
// Custom animation parameters
const quartzConfig = {
    animationDuration: 2000,    // ms
    animationSteps: 60,         // frames
    observerThreshold: 0.5,     // visibility %
    observerRootMargin: '0px',
    easingFunction: 'linear'    // 'ease', 'ease-in-out', etc.
};
```

### CSS Theming
```css
:root {
    /* Color overrides */
    --quartz-primary: #000000;
    --quartz-highlight: #999999;
    --quartz-secondary: #333333;
    --quartz-border: #e0e0e0;
    
    /* Typography overrides */
    --quartz-font-size-heading: 52px;
    --quartz-font-size-stat: 64px;
    
    /* Layout overrides */
    --quartz-grid-gap: 80px;
    --quartz-image-gap: 8px;
}
```

### Layout Variants
```html
<!-- Reversed layout (content left, images right) -->
<section class="about-section about-section--reversed">
    <!-- Content first, images second -->
</section>

<!-- Vertical layout (stacked) -->
<section class="about-section about-section--stacked">
    <!-- Single column flow -->
</section>

<!-- Alternative image grid -->
<div class="image-grid image-grid--three">
    <!-- 3 equal columns -->
</div>
```

## Performance Optimization

### Image Loading Strategy
```html
<!-- Lazy loading implementation -->
<img src="image.jpg" 
     loading="lazy"
     decoding="async"
     width="600"
     height="400"
     alt="Description"
     class="image-card__img"
     onerror="this.src='fallback.jpg'">
```

### JavaScript Optimization
```javascript
// Debounced scroll handler for performance
const debouncedObserver = debounce(() => {
    // Animation logic
}, 100);

// Efficient DOM selection
const statElements = document.querySelectorAll('.stat-value');
const observer = new IntersectionObserver(callback, options);
```

### Font Optimization
```css
/* Font loading strategy */
@font-face {
    font-family: 'Inter';
    font-style: normal;
    font-weight: 400;
    font-display: swap;
    src: url('/fonts/inter.woff2') format('woff2');
}
```

## Accessibility Features

### Semantic Structure
```html
<section class="about-section" role="region" aria-labelledby="about-heading">
    <div class="image-grid" aria-label="Company team and work">
        <!-- Images with proper alt text -->
    </div>
    
    <div class="content-section">
        <h2 id="about-heading" class="section-header">Who we are</h2>
        <h1 class="main-heading">
            We unite <span class="highlight">diverse skills</span>
        </h1>
        
        <!-- Animated stats with ARIA labels -->
        <div class="stats-container" role="status" aria-live="polite">
            <div class="stat-item">
                <div class="stat-value" 
                     aria-label="5 billion dollars invested"
                     data-target="5" 
                     data-prefix="$" 
                     data-suffix="B">
                    $0B
                </div>
            </div>
        </div>
    </div>
</section>
```

### Focus Management
```css
/* Focus styles for interactive elements */
.stat-item:focus-within {
    outline: 2px solid #0066cc;
    outline-offset: 4px;
}

/* Reduced motion preferences */
@media (prefers-reduced-motion: reduce) {
    .stat-value {
        animation: none;
        transition: none;
    }
}
```

## Framework Integration

### React Component
```jsx
import React, { useEffect, useRef } from 'react';
import './Quartz.css';

const QuartzAbout = ({ 
    header = "Who we are",
    headline = "We unite diverse skills",
    description,
    stats = [],
    images = []
}) => {
    const statRefs = useRef([]);
    
    useEffect(() => {
        // Initialize Intersection Observer
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    animateNumber(entry.target);
                }
            });
        }, { threshold: 0.5 });
        
        statRefs.current.forEach(stat => observer.observe(stat));
        
        return () => observer.disconnect();
    }, []);
    
    return (
        <section className="about-section">
            {/* Component JSX */}
        </section>
    );
};
```

### Vue.js Component
```vue
<template>
    <section class="about-section">
        <div class="image-grid">
            <!-- Image grid -->
        </div>
        <div class="content-section">
            <h2 class="section-header">{{ header }}</h2>
            <h1 class="main-heading" v-html="headline"></h1>
            <p class="description-text">{{ description }}</p>
            <div class="stats-container">
                <div v-for="stat in stats" :key="stat.id" class="stat-item">
                    <div class="stat-value" 
                         :data-target="stat.value"
                         :data-prefix="stat.prefix"
                         :data-suffix="stat.suffix"
                         ref="statElements">
                        {{ stat.initial }}
                    </div>
                    <div class="stat-label">{{ stat.label }}</div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
export default {
    mounted() {
        this.initAnimations();
    },
    methods: {
        initAnimations() {
            // Intersection Observer setup
        }
    }
}
</script>
```

## Development Guidelines

### File Structure
```
quartz/
├── index.html          # Main component
├── quartz.css          # Component styles
├── quartz.js           # Interactive animations
├── README.md           # Documentation
├── examples/           # Implementation examples
│   ├── react/
│   ├── vue/
│   └── vanilla/
└── assets/             # Images and fonts
```

### Code Standards
- **CSS:** BEM methodology with consistent naming
- **JavaScript:** ES6+ with proper error handling
- **HTML:** Semantic structure with ARIA attributes
- **Performance:** Lazy loading and efficient animations
- **Accessibility:** WCAG 2.1 AA compliance

### Testing Checklist
- [ ] Animated numbers trigger correctly
- [ ] Responsive breakpoints function properly
- [ ] Images load with appropriate fallbacks
- [ ] Accessibility audit passes
- [ ] Performance metrics meet targets
- [ ] Browser compatibility verified

## Browser Compatibility

### Supported Features
- **CSS Grid:** Full support in modern browsers
- **Intersection Observer:** Chrome 51+, Firefox 55+, Safari 12.1+
- **CSS Variables:** Chrome 49+, Firefox 31+, Safari 9.1+
- **ES6 Modules:** Modern browsers with transpilation option

### Polyfill Recommendations
```html
<!-- Intersection Observer polyfill for older browsers -->
<script src="https://polyfill.io/v3/polyfill.min.js?features=IntersectionObserver"></script>
```

## License & Usage

Quartz is released under the MIT License, allowing free use, modification, and distribution in both personal and commercial projects.

## Support Resources

- **Documentation:** Inline code comments and examples
- **Issue Tracking:** GitHub repository issues
- **Examples:** Framework-specific implementations
- **Performance:** Lighthouse optimization guide

---

*Quartz provides a production-ready about section component that combines compelling visuals with interactive data presentation, making it ideal for modern business websites and digital portfolios.*



