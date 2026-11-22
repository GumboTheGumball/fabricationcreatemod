# Create Fabricator

**Create Fabricator** is a Create addon for Minecraft 1.21.1 (NeoForge) that adds the **Fabricator**—a kinetic processing machine used to craft **Fabrilite** and custom datapack recipes.

---

## Getting Started

### 1. Powering the Fabricator
* Place down the **Fabricator** and connect a spinning shaft or cogwheel to its rotational axis.
* The machine requires at least **128 RPM** to operate.
* Running it faster speeds up crafting:
  * **128 RPM:** Standard speed (e.g., 8 seconds for Fabrilite Nuggets)
  * **256 RPM:** Double speed (4 seconds for Fabrilite Nuggets)
* Put on **Engineer's Goggles** and look at the Fabricator to see its live RPM and crafting progress on the left of your crosshair.

### 2. Using the Machine & Automation
* **Manual Use:** Right-click the Fabricator to open its GUI. Place your ingredients into the **3 input slots** on the left (`Slots 0, 1, 2`), and collect finished items from the **output slot** on the right (`Slot 3`).
* **Funnels, Belts & Hoppers:**
  * Point **Andesite or Brass Funnels** (or hoppers/chutes) into any side of the Fabricator to automatically load ingredients into the 3 input slots.
  * Attach an outgoing **Funnel** onto a **Depot** or **Mechanical Belt** to automatically pull finished items out of the output slot.

---

## Crafting Fabrilite

To make **1 Fabrilite Nugget**, load the following into the Fabricator's 3 input slots at **128+ RPM**:
* **8x Blue Dye**
* **1x Stone**
* **2x Iron Nuggets**

Combine **9 Fabrilite Nuggets** in a crafting table to make a **Fabrilite Ingot**, or 9 ingots to make a **Block of Fabrilite**.

---

## Adding Custom Recipes (Datapacks & Modpacks)

Create Fabricator uses its own recipe type: `create_fabricator:fabricating`.

1. Inside your datapack, create a JSON file at:
   `data/<your_namespace>/recipe/<recipe_name>.json`
2. Use the template below:

```json
{
  "type": "create_fabricator:fabricating",
  "ingredients": [
    {
      "item": "minecraft:iron_ingot"
    },
    {
      "item": "minecraft:redstone"
    }
  ],
  "results": [
    {
      "id": "create_fabricator:fabrilite_ingot",
      "count": 1
    }
  ],
  "processingTime": 20480
}
```

### Recipe Rules & Tips
* **Multiple of the Same Item:** Repeat `{ "item": "..." }` in the `ingredients` list for each item required (up to **16 total items** across the 3 input slots). Tags like `{ "tag": "c:ingots/iron" }` also work.
* **Output Format:** Make sure `"results"` uses `"id"` (not `"item"`) and `"count"`.
* **Calculating `processingTime`:** Processing time divides by the machine's current RPM every tick (20 ticks = 1 second):
  * `20480` = **8 seconds** at 128 RPM / **4 seconds** at 256 RPM
  * `10240` = **4 seconds** at 128 RPM / **2 seconds** at 256 RPM
  * `5120` = **2 seconds** at 128 RPM / **1 second** at 256 RPM

---

## Requirements
* **Minecraft:** 1.21.1
* **Mod Loader:** NeoForge
* **Dependencies:** Create (6.0.7+)
