# Hanboost Easter Hunt Game — Source Files

## Quick Start
Open `index.html` in a browser. The game works immediately with built-in Canvas graphics.
To customize visuals, replace the placeholder PNG files in `assets/`.

## Project Structure
```
easter-game/
├── index.html              ← Main game file (HTML + CSS + JS, single file)
├── README.md               ← This file
└── assets/                 ← Designer-replaceable image assets
    ├── level1-bg.png       ← Level 1 background (Egg Hunt)
    ├── level2-bg-far.png   ← Level 2 far background (Runner, parallax)
    ├── level2-ground.png   ← Level 2 ground/floor texture
    ├── level3-bg.png       ← Level 3 background (Sky Shooter)
    ├── plane-sprite.png    ← Level 3 plane sprite
    ├── runner-sprite.png   ← Level 2 character spritesheet
    ├── obstacles.png       ← Level 2 obstacles spritesheet
    ├── eggs-sprite.png     ← Shared egg sprites (7 colors)
    └── home-bg.png         ← Optional home screen background
```

## How Image Replacement Works

The game has a **dual rendering system**:
- If an image file exists in `assets/`, it will be loaded and used
- If the image fails to load (missing / broken), the game automatically falls back to built-in Canvas-drawn graphics

This means **the game always works**, even before designers replace any images.

## Asset Specifications

### Level 1 Background — `level1-bg.png`
| Property | Value |
|----------|-------|
| Size | **1120 × 760 px** (renders at 560×380, @2x for retina) |
| Format | PNG or JPG (recommend WebP for production, <200KB) |
| Scene | Spring outdoor garden — grass, bushes, rocks, flowers |
| Notes | Easter eggs will be overlaid on top. Include hiding spots (bushes, rocks, shadows) for eggs to blend into. Use greens as dominant color so colored eggs pop. |

### Level 2 Far Background — `level2-bg-far.png`
| Property | Value |
|----------|-------|
| Size | **1120 × 760 px** |
| Scene | Workshop / workbench wall — shelves, tools, pegboard |
| Notes | Scrolls left at 0.3× game speed (parallax). Should tile seamlessly or be wide enough that the seam isn't visible in 60s. |

### Level 2 Ground — `level2-ground.png`
| Property | Value |
|----------|-------|
| Size | **1120 × 120 px** |
| Scene | Floor / workbench surface texture |
| Notes | Must tile seamlessly horizontally. Scrolls at 1× game speed. Rendered at y=320, height=60px on canvas. |

### Level 3 Background — `level3-bg.png`
| Property | Value |
|----------|-------|
| Size | **1120 × 760 px** |
| Scene | Sky — blue gradient, clouds, atmospheric |
| Notes | Static (doesn't scroll). Eggs fall from top, plane flies near bottom. Keep bottom area relatively clear. |

### Plane Sprite — `plane-sprite.png`
| Property | Value |
|----------|-------|
| Size | **80 × 88 px** (@2x, displays at 40×44) |
| Scene | Top-down aircraft — brand colors (blue body, amber cockpit) |
| Notes | Currently drawn with Canvas shapes. Not yet wired to replace programmatic drawing — for future sprint. |

### Runner Sprite — `runner-sprite.png`
| Property | Value |
|----------|-------|
| Size | **128 × 48 px** (4 frames, each 32×48) |
| Layout | 4 frames side by side: Run1, Run2, Run3, Run4 |
| Notes | Currently drawn with Canvas shapes. Not yet wired — for future sprint. |

### Obstacles — `obstacles.png`
| Property | Value |
|----------|-------|
| Size | **360 × 60 px** (10 obstacles, each 36×60) |
| Layout | 10 obstacles side by side |
| Types | Toolbox, Screwdriver, Spring, Cone, Barrel, Gear, Wrench, Paint Can, Sawhorse, Bolt Stack |
| Notes | Currently drawn with Canvas shapes. Not yet wired — for future sprint. |

### Egg Sprites — `eggs-sprite.png`
| Property | Value |
|----------|-------|
| Size | **126 × 24 px** (7 eggs, each 18×24) |
| Colors | Amber, Pink, Blue, Green, Purple, Orange, Cyan |
| Notes | Currently drawn with Canvas ellipse. Not yet wired — for future sprint. |

## Color Palette (Brand)
| Color | Hex | Usage |
|-------|-----|-------|
| Amber | `#EF9F27` | Primary — buttons, eggs, accents |
| Blue | `#185FA5` | Brand blue — plane, links, headers |
| Green | `#3B6D11` | Success — pass states |
| Red | `#A32D2D` | Fail — timer, warnings |
| Background | `#FAEEDA` | Page background (warm cream) |

## Game Rules Summary
| Level | Name | Time | Goal | Fail |
|-------|------|------|------|------|
| 1 | Egg Hunt | 30s | Find 20 hidden eggs | Time out |
| 2 | Tool Runner | 60s | Collect 20 eggs | Time out or 3 hits |
| 3 | Sky Shooter | 60s | Shoot 30 eggs | Time out or 5 leaked |

## Deployment
For Shopify: upload all files to `assets/` in your theme, or host on a CDN and embed via iframe.

```html
<iframe src="/pages/easter-game/index.html" 
        width="640" height="435" 
        frameborder="0" 
        style="max-width:100%; border-radius:16px;">
</iframe>
```

## Technical Notes
- Canvas logical resolution: 560×380px
- 60fps via requestAnimationFrame
- Audio: Web Audio API (synthesized, no audio files needed)
- Mobile: responsive + touch controls
- No external dependencies (fonts loaded from Google Fonts CDN)
