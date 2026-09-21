# 🛠️ DIY Sheet Metal Engineering Analytics & Flat Pattern Engine

A clean, responsive, browser-based blueprint engine designed specifically for independent content creators, tabletop filmmakers, and home studio builders. 

This tool eliminates the guesswork and wasted materials when fabricating custom camera rigs, slider brackets, overhead arms, or lighting mounts out of sheet metal.

👉 **[Launch the Calculator](https://clynshotimages-ops.github.io/diy-sheetmetal-bending-engine/)**

---

## 📸 Overview & Advanced Features
* **Multi-Alloy Engine:** Dropdown selection for **5052-H32 Aluminum**, **Mild Steel**, and **Stainless Steel**.
* **Smart Auto-Radius Calculation:** Automatically calculates the safe, non-cracking structural minimum bend radius based on your material type and sheet thickness ($T$).
* **Dynamic K-Factor & Setback Adjustments:** Automatically adjusts the layout physics and K-Factor values as you toggle between material alloys.
* **Real-Time Visualization:** Renders your flat pattern layout on an interactive canvas view instantly as you modify variables.
* **Mobile Responsive Setup:** Adaptive CSS structure so you can easily pull up math layouts directly on your phone or tablet at the workshop vise.

---

## 📐 How the Alloy Material Engine Works

The updated engine removes human error by applying standard engineering rules-of-thumb directly to your layouts:

### 1. K-Factor Baselines
The **K-Factor** represents how the neutral axis shifts as metal stretches during a bend. The engine updates this automatically:
* **Aluminum 5052-H32:** Generates a baseline **`0.45`**. This alloy is the gold standard for DIY creators—lightweight, strong, and highly formable.
* **Mild Steel (A36):** Generates a baseline **`0.42`** due to its high ductility.
* **Stainless Steel (304):** Generates a baseline **`0.38`** to account for how this rapidly work-hardening material resists flow.

### 2. Auto-Recommended Minimum Bend Radii ($R$)
To prevent structural grain tearing on the outside of your brackets, the tool applies thickness-scaled rules:
* **Aluminum 5052:** Uses a $1.0\times T$ radius for thin stock ($\le 1.6\text{mm}$), scaling up to $1.5\times T$ and $2.0\times T$ as the metal thickens.
* **Mild Steel:** Allows tighter, highly ductile profiles starting down at $0.5\times T$.
* **Stainless Steel:** Demands wider profiles ($1.0\times T$ to $2.0\times T$) to offset severe physical resistance during forming.

*Note: You can always manually type over the recommended radius value. The system will alert you by switching the UI label from blue to an amber `(Manual Overwrite)` warning indicator.*

---

## 🛠️ Local Development
If you want to tweak this tool locally on your computer:
1. Clone or download this repository.
2. Ensure your brand asset file (`logo.png`) is placed inside an `assets` folder situated in the same folder directory as your `index.html` file (`assets/logo.png`).
3. Open `index.html` inside Google Chrome or any modern browser.

---

## ⚖️ License & Credits
Designed and engineered for limited precision manufacturing by **Clynshotimages Production LLC**.

*Providing cost-effective techniques and free open-source tools to help independent creators build better film-studio rigging safely.*
