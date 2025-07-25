# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Seeing Theory is an educational web application that makes statistics accessible through interactive D3.js visualizations. Created by Daniel Kunin with support from Brown University, it visualizes fundamental concepts from introductory college statistics courses.

## Architecture

### Technology Stack
- **Frontend Only**: No build system, server-side components, or package manager
- **D3.js v3**: Primary visualization library (older version - be aware of API differences)
- **jQuery**: DOM manipulation and event handling
- **jStat**: Statistical computations with custom extensions
- **Bootstrap v3**: Responsive UI framework
- **MathJax**: Mathematical notation rendering

### Module Structure
The project consists of 5 educational modules, each with 3 sub-topics:
- `basic-probability/`: Likelihood, Expectation, Estimation
- `compound-probability/`: Set Theory, Combinatorics, Conditional Probability
- `distributions/`: Random Variables, Discrete/Continuous, Central Limit Theorem
- `statistical-inference/`: Confidence Intervals, p-Values, Hypothesis Testing
- `regression/`: OLS, Correlation, ANOVA

### File Organization
```
/
├── index.html                    # Main landing page
├── [module-name]/
│   ├── index.html               # Module page with 3 sections
│   ├── [module-name].js         # Module-specific visualizations
│   └── [module-name].css        # Module-specific styles
├── js/
│   ├── main.js                  # Global utilities and D3 extensions
│   ├── home.js                  # Landing page particle animation
│   └── [libraries].min.js       # Third-party libraries
├── css/
│   ├── main.css                 # Global styles
│   └── [module-name].css        # Module-specific styles
└── img/                         # Icons and assets
```

## Key Development Patterns

### D3.js Visualization Pattern
Each module follows a consistent D3 pattern:
```javascript
// SVG creation
var svg = d3.select("#container").append("svg");

// Scales
var xScale = d3.scale.linear().domain([min, max]).range([0, width]);

// Data binding
svg.selectAll("element")
   .data(data)
   .enter().append("element")
   .attr("attribute", function(d) { return scale(d); });

// Transitions
selection.transition().duration(500).attr("attribute", value);
```

### jStat Extensions
The project extends jStat with custom distributions in module JS files:
```javascript
jStat.binomialDiscrete = {
  pdf: function(k,n,p) { /* implementation */ },
  cdf: function(k,n,p) { /* implementation */ },
  mean: function(n,p) { return n*p; }
}
```

### Interactive Elements
Common patterns for user interaction:
- Drag behavior for adjusting probabilities
- Button clicks for simulations (coin flips, dice rolls)
- Sliders for parameter adjustment
- Real-time chart updates based on user input

## Common Commands

### Local Development
```bash
# No build process - open HTML files directly in browser
# For local development with proper CORS headers:
python -m http.server 8000
# or
python3 -m http.server 8000
```

### Testing Changes
1. Open the relevant module's index.html in a browser
2. Use browser developer tools for debugging
3. Check console for errors - visualizations often fail silently

### Adding New Visualizations
1. Create visualization in the module's JS file
2. Add corresponding HTML container in index.html
3. Style in the module's CSS file
4. Follow existing D3 patterns and color scheme

## Important Constraints

### Browser Compatibility
- Designed for desktop browsers (minimum 800px width)
- Limited mobile support with warning modal
- Uses D3.js v3 syntax (not v4+ - check documentation)

### No Modern JavaScript
- No ES6+ features (use var, not let/const)
- No module imports/exports
- jQuery for DOM manipulation
- Callback-based async patterns

### Consistent Visual Language
- Colors: #00d0a1 (green/observed), #64bdff (blue/theoretical), #FF1300 (red)
- Fonts: Avenir primary
- Margins and transitions should match existing patterns

### Educational Focus
- Visualizations must be mathematically accurate
- Favor clarity over complexity
- Include both theoretical and observed values where applicable
- Interactive elements should reinforce learning concepts

## Embedding Visualizations
To embed a specific visualization:
```html
<iframe 
    src="http://students.brown.edu/seeing-theory/[module]/index.html#[section]" 
    width="100%" 
    height="700px" 
    scrolling="no"
    style="margin-top: -70px;"
    frameborder="0">
</iframe>
```
Where [section] is: first, second, or third

## Future Vision: AI-Powered Educational Platform

### Project Goal
Transform Seeing-Theory's approach into an AI-powered platform that generates interactive educational visualizations for ANY subject. The vision is to build a billion-dollar EdTech company where students can request "teach me photosynthesis interactively" and receive custom D3.js visualizations.

### Key Insights from Research
Based on extensive research into Lovable, v0, Bolt, and Cursor architectures:
- **AI Layer**: Use Claude 3.5 Sonnet with educational prompt templates
- **Execution**: WebContainers API for browser-based code execution
- **Tech Stack**: Keep it simple like Seeing-Theory (D3.js + vanilla JS)
- **Differentiator**: Subject-specific visualization templates

### Development Roadmap
1. **Study this codebase**: Understand D3.js patterns and educational visualization principles
2. **Build MVP**: Start with physics/math using Seeing-Theory's patterns
3. **Add AI generation**: Integrate Claude API to generate similar visualizations
4. **Scale**: Expand to all subjects with teacher tools and customization

### Architecture Evolution
From static (current) → AI-generated (future):
```javascript
// Current: Manual coding each visualization
var svg = d3.select("#likelihood").append("svg");

// Future: AI generates based on prompt
prompt: "Create interactive visualization for photosynthesis"
→ AI generates complete D3.js code following Seeing-Theory patterns
```

### Resources Created
- `AI_CODE_GENERATION_RESEARCH.md`: Complete analysis of AI code platforms
- `EXPERT_AI_SEARCH_PROMPT.md`: Prompts for deeper market/technical research
- `AI_CODE_PLATFORM_ARCHITECTURE_PROMPT.md`: Reverse-engineering prompt for implementation details

The goal is to make Seeing-Theory's beautiful approach to statistics education available for every subject through AI generation.