[README.md](https://github.com/user-attachments/files/33076601/README.md)


# 🛠️ DIY Sheet Metal Engineering Analytics & Flat Pattern Engine

A browser-based sheet-metal engineering and fabrication utility developed by **Clynshotimages Production LLC** for creators, makers, filmmakers, home-studio builders, and DIY fabricators.

The calculator connects finished dimensions, bend geometry, material properties, flat-pattern development, formed-profile visualization, and SVG export for CAD/Tinkercad development.

**Calculator / GitHub Pages:**

https://clynshotimages-ops.github.io/diy-sheetmetal-bending-engine/

---

## 🌐 Overview

The **DIY Sheet Metal Engineering Analytics & Flat Pattern Engine** allows users to develop and visualize sheet-metal parts before fabrication.

The calculator combines:

* Finished segment dimensions

* Bend angles

* Inside bend radii

* Material thickness

* K-factor

* Setback

* Bend allowance

* Developed flat length

* True-radius formed geometry

* Flat-pattern visualization

* Side-profile visualization

* SVG export for CAD development

> **Important:** This calculator is a design and engineering aid, not a replacement for tooling-specific manufacturing data. Actual bend results depend on material temper, grain direction, tooling, press-brake setup, die width, punch geometry, bend sequence, springback, machine calibration, and fabrication tolerances.

---

# 🔩 Current Capabilities

The current calculator supports:

* 📐 Sheet-metal bend calculations

* 📏 Flat-pattern development

* 🧮 Setback calculations

* 🧮 Bend-allowance calculations

* ⚙️ Material-specific K-factor presets

* 📐 Automatic bend-radius recommendations

* ⚠️ Per-bend radius override warnings

* 🔢 1–4 bend configurations

* 📊 Flat Pattern visualization

* 🧱 True-radius Side Profile visualization

* ⭕ True inner and outer circular bend arcs

* 🔗 Tangent-connected straight and curved geometry

* 🧩 Canonical geometry shared by the Side Profile canvas and SVG exporter

* 🛠️ Side Profile SVG export

* 📄 Flat Pattern SVG export

* 📏 Millimeter-based SVG dimensions

* 🧰 CAD development workflow

* 📱 Responsive browser interface

* 💻 Courier New engineering-style interface

* 🚫 No external JavaScript framework required

---

# 🧱 Materials & K-Factors

The calculator currently provides three material presets:

| Material | K-factor |

| --------------------- | -------: |

| 5052-H32 Aluminum | 0.45 |

| Mild Steel (A36) | 0.42 |

| Stainless Steel (304) | 0.38 |

These values are practical starting points and should be replaced or calibrated with manufacturer, tooling, or shop-specific bend data when greater accuracy is required.

---

# 🛠️ Automatic Bend-Radius Recommendation

The recommended inside bend radius is calculated from the selected material and sheet thickness.

### 5052-H32 Aluminum


T ≤ 1.6 → R = 1.0 × T

1.6 < T ≤ 10 → R = 1.5 × T

T > 10 → R = 2.0 × T


### Mild Steel (A36)


T ≤ 3 → R = 0.5 × T

3 < T ≤ 6 → R = 1.0 × T

T > 6 → R = 1.5 × T


### Stainless Steel (304)


T ≤ 2 → R = 1.0 × T

2 < T ≤ 6 → R = 1.5 × T

T > 6 → R = 2.0 × T


These are starting recommendations rather than universal manufacturing limits.

## ⚠️ Radius Override Protection

Users can manually enter a different radius.

The calculator does **not** silently replace a user-entered radius with the recommended value.

Each bend reports its current condition:

### ✓ Recommended Radius

The selected radius matches the calculated recommendation.

### ℹ User Override

The selected radius is larger than the recommended starting value.

### ⚠ Warning — Below Recommended Minimum

The selected radius is below the calculator's recommended starting value.

A below-recommendation radius is not automatically rejected. The warning indicates that the selected geometry should be verified against the actual material, tooling, and forming process.

---

# 🧮 Bend Calculations

## Bend Allowance

The calculator uses:


BA = θ × (R + K × T)


Where:

* `BA` = Bend Allowance

* `θ` = Bend angle in radians

* `R` = Inside bend radius

* `K` = K-factor

* `T` = Material thickness

The user enters the bend angle in degrees. The calculator converts it to radians for the calculation.

---

## 📐 Setback

The calculator uses:


SB = (R + T) × tan(θ / 2)


Where:

* `SB` = Setback

* `R` = Inside bend radius

* `T` = Material thickness

* `θ` = Bend angle

Each bend receives its own setback value.

---

## 📏 Developed Flat Length

The current flat-pattern calculation is:


Flat Length =

Σ Finished Segment Lengths

− 2 × Σ Setbacks

+ Σ Bend Allowances

The entered segment dimensions are treated as finished dimensions.

Conceptually:


Finished dimensions

    ↓
Remove bend setbacks

    ↓
Add developed bend allowances

    ↓
Calculate flat blank


The calculator reports:

* Total Flat Length

* Total Bend Allowance

* Total Setback

---

# 🔢 Multi-Bend Configuration

The calculator supports up to **four bends**.

The number of straight segments is automatically:


Number of Segments = Number of Bends + 1


### 1 Bendt

S1 ─── B1 ─── S2


### 2 Bends

S1 ─── B1 ─── S2 ─── B2 ─── S3

### 3 Bends


S1 ─── B1 ─── S2 ─── B2 ─── S3 ─── B3 ─── S4


### 4 Bends


S1 ─── B1 ─── S2 ─── B2 ─── S3 ─── B3 ─── S4 ─── B4 ─── S5


Each bend has its own:

* Angle

* Inside radius

* Setback

* Bend allowance

* Radius recommendation status

Different bends can therefore use different angles and radii within the same part.

---

# 📐 Flat Pattern Visualization

The Flat Pattern viewer provides a visual representation of the developed blank.

It displays:

* Straight segments

* Bend locations

* Bend numbers

* Bend angles

* Overall calculated flat length

* Relative segment proportions

The visualization updates as the user changes the part parameters.

The Flat Pattern SVG exporter provides the developed blank together with bend-reference locations for further CAD or fabrication development.

---

# 🧱 True-Radius Side Profile

The Side Profile has been developed beyond a simple centerline representation.

Each bend uses actual material-thickness geometry based on three concentric radii:


Inside radius = R

Centerline radius = R + T/2

Outside radius = R + T


All three radii share the same bend center.

The straight sections terminate at the exact tangent points of the circular bend arcs.

This produces a closed formed profile representing the material's inner and outer surfaces.

---

# ⭕ Tangent Circular Bend Geometry

For every bend, the geometry establishes:

1. Incoming straight tangent point

2. Common bend center

3. True inner circular arc

4. True outer circular arc

5. Outgoing straight tangent point

6. Exact outgoing segment direction

The inner and outer arcs remain concentric throughout the bend.

This replaces approximate arc reconstruction based on setback positions and is intended to prevent:

* Broken line-to-arc connections

* Arc intersections

* Non-tangent transitions

* Duplicate bend-reference geometry

* Differences between the calculator profile and exported profile

---

# 🔗 Canonical Side-Profile Geometry

The Side Profile canvas and Side Profile SVG exporter use the same canonical geometry model.

The architecture is:


User Inputs

↓
Bend Data

↓
Tangent Geometry

↓
Canonical Formed Geometry

↓
┌─────────────────────┐

│ Side Profile Canvas │

└─────────────────────┘

      \+
┌─────────────────────┐

│ Side Profile SVG │

└─────────────────────┘

```

The SVG exporter does not independently approximate the bend after the canvas has been generated.

Both outputs therefore use the same:

* Tangent points

* Bend centers

* Inner radii

* Outer radii

* Bend angles

* Segment directions

* Material thickness

This keeps the visual profile and exported geometry consistent.

---

# 🧭 Side-Profile Orientation

The physical convention begins with the first segment oriented upward.

Each subsequent bend rotates the following segment clockwise according to its entered bend angle.

The geometry is calculated dynamically from the bend sequence rather than being based on a fixed illustration.

Conceptually:



    S1

    │

    │

    │

    ●

     ╲

      ╲

       ───── S2


Additional bends continue from the exact outgoing tangent direction of the preceding bend.

---

# 🛠️ Tinkercad / CAD SVG Export

The calculator includes a dedicated **TINKERCAD EXPORT** section with two export options:


EXPORT SIDE PROFILE SVG

EXPORT FLAT PATTERN SVG


All exported dimensions are expressed in millimeters.

---

## 🧱 Side Profile SVG

The Side Profile SVG represents the calculated closed formed profile.

It contains:

* Closed inner/outer material outline

* True inner circular bend arcs

* True outer circular bend arcs

* Exact tangent connections

* Entered bend radii

* Entered bend angles

* Material thickness

* Up to four bends

The exporter:

* Uses the canonical Side Profile geometry

* Uses the entered inside radius

* Uses `R + T` for the outside radius

* Uses a shared bend center

* Connects straight sections directly to tangent points

* Produces one closed manufacturing outline

* Does not export bend-center diagnostic circles

* Does not rely on a vertical-flip SVG transform

The bend-center markers shown on the calculator are diagnostic/reference graphics only and are not included in the production Side Profile SVG.

---

# 📄 Flat Pattern SVG

The Flat Pattern SVG represents the calculated developed blank.

It contains:

* Flat blank geometry

* Calculated flat length

* Calculated blank width

* Bend reference lines

* Bend locations

* One reference line per bend

The bend reference position is calculated using:


Tangent Length + (Bend Allowance / 2)


This places the reference line at the center of the developed bend allowance.

The SVG metadata records the selected:

* Material

* Thickness

* Flat length

* Blank width

* Bend count

---

# 📦 SVG Export Naming

### Side Profile

sheet-metal-1-bend-side-profile.svg

sheet-metal-2-bend-side-profile.svg

sheet-metal-3-bend-side-profile.svg

sheet-metal-4-bend-side-profile.svg


### Flat Pattern

sheet-metal-1-bend-flat-pattern.svg

sheet-metal-2-bend-flat-pattern.svg

sheet-metal-3-bend-flat-pattern.svg

sheet-metal-4-bend-flat-pattern.svg


---

# 🧰 Suggested Tinkercad / CAD Workflow

### 1. Calculate the Part

Enter:

* Material

* Thickness

* Bend count

* Segment lengths

* Bend angles

* Bend radii

### 2. Review the Side Profile

Confirm:

* Overall shape

* Bend direction

* Bend angles

* Bend radii

* Material thickness

### 3. Export the Side Profile

Select:

EXPORT SIDE PROFILE SVG

Use the resulting closed profile as a starting cross-section for further CAD/Tinkercad development.

### 4. Export the Flat Pattern

Select:

EXPORT FLAT PATTERN SVG


Use the resulting geometry as the developed blank and bend-location reference.

### 5. Verify Before Fabrication

Compare the calculated geometry against:

* Actual material

* Tooling

* Forming method

* Machine setup

* Test bends

* Required fabrication tolerances

---

# 📊 Bend Data Summary

The calculator provides a bend-by-bend summary containing:

BEND 1

Angle | Radius | Direction | SB | BA

BEND 2

Angle | Radius | Direction | SB | BA

BEND 3

Angle | Radius | Direction | SB | BA

BEND 4

Angle | Radius | Direction | SB | BA


Only the bends used by the current configuration are displayed.

---

# 🧪 Example Workflow

A typical two-bend design can be configured as:


Material: 5052-H32 Aluminum

Thickness: 2.00 mm

Bends: 2


### Finished Segments


S1 = 120 mm

S2 = 80 mm

S3 = 60 mm


### Bend Angles


B1 = 90° CW

B2 = 45° CCW


### Workflow

1. Select material

2. Enter thickness

3. Select bend count

4. Enter finished segment lengths

5. Enter bend angles

6. Review recommended radii

7. Override radii if required

8. Review radius warnings

9. Compute the part

10. Review the Flat Pattern

11. Review the true-radius Side Profile

12. Export the required SVG

---

# ⚙️ Engineering Parameters

| Parameter | Description |

| --------- | ------------------------ |

| `T` | Material thickness |

| `K` | K-factor |

| `R` | Inside bend radius |

| `R + T/2` | Centerline bend radius |

| `R + T` | Outside bend radius |

| `θ` | Bend angle |

| `SB` | Setback |

| `BA` | Bend allowance |

| `S1–S5` | Finished segment lengths |

| `B1–B4` | Individual bends |

### Maximum Current Configuration



5 straight segments

4 bends

---

# 📱 Responsive Interface

The calculator is designed for:

* Desktop computers

* Laptops

* Tablets

* Mobile devices

At smaller screen widths, the calculation and visualization panels stack vertically.

The existing **Courier New engineering-style interface** is retained throughout the application.

---

# 🧰 Intended Applications

The engine can support early-stage development of:

* 🎥 Camera brackets

* 🎬 Tabletop filming equipment

* 📷 Camera mounts

* 🎞️ Slider components

* 🦾 Jib and overhead-rig components

* 💡 Lighting brackets

* 🛠️ Studio hardware

* 📐 Sheet-metal prototypes

* 🧱 Custom mounting plates

* 🔩 General DIY fabrication projects

* 🧩 CAD/Tinkercad concept development

The calculator is particularly useful for exploring multiple dimensions and bend configurations before committing material to fabrication.

---

# ⚠️ Engineering & Fabrication Disclaimer

This calculator provides mathematical estimates based on the formulas and geometry implemented in the application.

Actual manufactured dimensions can vary because of:

* Material composition

* Material temper

* Grain direction

* Tooling geometry

* Press-brake setup

* Die width

* Punch geometry

* Forming method

* Springback

* Bend sequence

* Machine calibration

* Material thickness tolerance

* Fabrication tolerance

The recommended bend radius should therefore be treated as a **starting recommendation**, not a guaranteed manufacturing limit.

Likewise, an SVG generated by the calculator represents calculated geometry and should be verified against the actual manufacturing process before fabrication.

Always verify critical dimensions using appropriate manufacturing references, tooling data, test bends, and physical measurements.

**Do not rely on this calculator alone for safety-critical, structural, lifting, or load-bearing components.**

---

# 🚀 Project

**Clynshotimages Production LLC**

DIY engineering tools for creators, filmmakers, independent fabricators, and makers.

The project combines practical fabrication calculations with visual engineering tools intended to make technical prototyping more accessible.


2026 **Clynshotimages Production LLC**

Designed and engineered for practical DIY fabrication, technical prototyping, and precision-oriented development.

