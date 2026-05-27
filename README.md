
### ⚙️ &nbsp;GitHub Analytics

<p align="center">
  <a href="https://github.com/furknozg">
    <img height="180em" src="https://github-readme-stats-eight-theta.vercel.app/api?username=furknozg&show_icons=true&theme=algolia&include_all_commits=true&count_private=true" alt="Furkan Özgültekin's GitHub Stats"/>
    <img height="180em" src="https://github-readme-stats-eight-theta.vercel.app/api/top-langs/?username=furknozg&layout=compact&langs_count=8&theme=algolia" alt="Furkan Özgültekin's Top Languages"/>
  </a>
</p>

---

### ✨ &nbsp;My Tech Stack

<p align="center" style="display: flex; flex-wrap: wrap; gap: 10px;">
  <img src="https://user-images.githubusercontent.com/25181517/183897015-94a058a6-b86e-4e42-a37f-bf92061753e5.png" alt="C++" height="40" style="margin: 5px;"/>
  <img src="https://user-images.githubusercontent.com/25181517/117448124-a2da9800-af3e-11eb-85d2-bd1b69b65603.png" alt="Python" height="40" style="margin: 5px;"/>
  <img src="https://user-images.githubusercontent.com/25181517/202896760-337261ed-ee92-4979-84c4-d4b829c7355d.png" alt="C#" height="40" style="margin: 5px;"/>
  <img src="https://user-images.githubusercontent.com/25181517/183890598-19a0ac2d-e88a-4005-a8df-1ee36782fde1.png" alt="HTML5" height="40" style="margin: 5px;"/>
  <img src="https://user-images.githubusercontent.com/25181517/183859966-a3462d8d-1bc7-4880-b353-e2cbed900ed6.png" alt="CSS3" height="40" style="margin: 5px;"/>
  <img src="https://user-images.githubusercontent.com/25181517/192149581-88194d20-1a37-4be8-8801-5dc0017ffbbe.png" alt="JavaScript" height="40" style="margin: 5px;"/>
  <img src="https://user-images.githubusercontent.com/25181517/121405754-b4f48f80-c95d-11eb-8893-fc325bde617f.png" alt="React" height="40" style="margin: 5px;"/>
  <img src="https://user-images.githubusercontent.com/25181517/117208740-bfb78400-adf5-11eb-97bb-09072b6bedfc.png" alt="Node.js" height="40" style="margin: 5px;"/>
  <img src="https://user-images.githubusercontent.com/25181517/182884177-d48a8579-2cd0-447a-b9a6-ffc7cb02560e.png" alt="Git" height="40" style="margin: 5px;"/>
  <img src="https://user-images.githubusercontent.com/25181517/117207330-263ba280-adf4-11eb-9b97-0ac5b40bc3be.png" alt="MySQL" height="40" style="margin: 5px;"/>
  <img src="https://user-images.githubusercontent.com/25181517/182534006-037f08b5-8e7b-4e5f-96b6-5d2a5558fa85.png" alt="MongoDB" height="40" style="margin: 5px;"/>
  <img src="https://user-images.githubusercontent.com/25181517/183911547-990692bc-8411-4878-99a0-43506cdb69cf.png" alt="Firebase" height="40" style="margin: 5px;"/>
  <img src="https://cdn.simpleicons.org/threedotjs/000000" alt="Three.js" height="40" style="margin: 5px;"/>
</p>

---

### ⌨️ &nbsp;My Keeb

<p align="center">
  <img
    src="./mymanuform.png"
    alt="Custom ergonomic split mechanical keyboard build"
    width="850"
  />
</p>

<p align="center">
  <em>Here is my favourite keyboard that I currently use, a Dactyl Manuform. Hit me up if you need any help building one of your own from scratch.</em>
</p>

---

### 🧑‍🍳 &nbsp;Keyboard Wiring Recipe

#### 🔌 &nbsp;Matrix Wiring

<p align="center">
  <img
    src="./wiring.png"
    alt="Dactyl Manuform keyboard matrix wiring with rows and columns marked"
    width="850"
  />
</p>

The keyboard is wired as a matrix instead of giving every switch its own pin. In the diagram above, the **yellow lines are columns** (`c1` to `c6`) and the **green lines are rows** (`r1` to `r6`). Each key sits where one row and one column meet, so the firmware scans the columns and rows to figure out which switch is being pressed.

For this layout, keep each column as one clean vertical chain and each row as one clean horizontal-ish chain. The physical wire does not have to be perfectly straight inside a Dactyl shell, but the electrical idea should stay simple: every switch joins exactly one row and exactly one column.

<p align="center">
  <img
    src="./pro micro wiring.png"
    alt="Pro Micro wiring diagram for keyboard rows, columns, and TRRS or RJ9 data"
    width="420"
  />
</p>

The Pro Micro turns that matrix into USB keyboard input. The row wires connect to one group of controller pins, and the column wires connect to another group. In firmware, those same pins need to be listed in the same row and column order you physically wired.

For a split keyboard, the two halves talk through a **TRRS, TRS, or RJ9 cable**. One half is the main side plugged into USB, and the other half sends its key presses over the interconnect. A typical cable carries **GND**, **VCC**, and a **serial/data line**; a fourth conductor can be used for reset or another data line depending on your firmware setup. Whatever connector you choose, keep the pinout identical on both halves and avoid plugging or unplugging TRRS while the keyboard is powered, because the contacts can briefly short while sliding in.

---

#### ✅ &nbsp;Diode Row Connection

When hand-wiring a split keeb, each switch needs one diode so the matrix can tell exactly which key is pressed. Keep the diode direction consistent across the whole build before you start connecting rows.

**✅ DO:**

<p align="center">
  <img
    src="./anode wiring true.webp"
    alt="Correct diode row wiring example with the diode legs chained on the row side"
    width="650"
  />
</p>

- Put one diode on every switch before wiring the rows.
- Keep all diodes facing the same direction. In my builds, the **black stripe/cathode side goes toward the row wire**.
- Connect the non-striped/anode side to the switch leg, then chain the striped/cathode sides together as the row.
- Use solid core wire for row and column runs so the matrix stays tidy and easy to debug.
- Cover long exposed legs with heat shrink or electrical tape to avoid accidental shorts.
- Test continuity with a multimeter row by row before plugging the board into USB.
- Match the diode direction with your firmware setting, usually `DIODE_DIRECTION = COL2ROW` or `ROW2COL`.

**❌ DON'T:**

<p align="center">
  <img
    src="./anode wiring false.webp"
    alt="Incorrect diode row wiring example showing a row wire connected to the wrong side"
    width="650"
  />
</p>

- Mix diode directions within the same matrix. One flipped diode can make a key disappear.
- Let bare diode legs or row wires touch neighboring columns.
- Skip diodes; they are what prevent ghosting and weird multi-key behavior.
- Assume the row wire is correct just because it looks clean. Test it.
- Overheat diode legs while soldering; a quick, clean joint is enough.
- Wire the second half from memory if you mirrored the case. Re-check the row and column pins first.

---

#### 🧠 &nbsp;QMK Configuration

After the wiring is done, the firmware needs to describe the same matrix you built by hand. The important parts are the matrix size, the row pins, the column pins, the diode direction, and the split communication pin.

For this shape, you do not have to start from a blank keyboard every time. QMK already has a preconfigured Dactyl Manuform preset at `handwired/dactyl_manuform/5x6_5`, often referred to as `dactyl_manuform_5x6_5` in preset lists. Use it as the starting point when your layout matches a 5x6 main grid plus 5 thumb keys, then only adjust the pins, diode direction, and keymap if your wiring differs.

For a custom handwired Dactyl Manuform, the most flexible path is **QMK CLI** because it lets you define the custom wiring:

```bash
qmk setup
qmk compile -kb handwired/dactyl_manuform/5x6_5 -km default
qmk flash -kb handwired/dactyl_manuform/5x6_5 -km default
```

In your keyboard definition, mirror the physical wiring:

```c
#define MATRIX_ROWS 12
#define MATRIX_COLS 6

#define MATRIX_ROW_PINS { D0, D1, D2, D3, D4, C6 }
#define MATRIX_COL_PINS { B1, B2, B3, B4, B5, B6 }
#define DIODE_DIRECTION COL2ROW

#define SPLIT_HAND_PIN B7
#define SOFT_SERIAL_PIN D0
```

The exact pins above are examples, not a universal Pro Micro pinout. Use the pins from your own `pro micro wiring.png` plan, then keep the order consistent with your `LAYOUT` macro and keymap.

Use `ROW2COL` or `COL2ROW` based on which side of the switch your diode points toward. If your keys do not register, register backward, or whole rows act strange, diode direction and row/column pin order are the first things to check.

If you prefer the **QMK GUI** route, use **QMK Configurator** plus **QMK Toolbox**:

1. Open [QMK Configurator](https://config.qmk.fm/).
2. Pick `handwired/dactyl_manuform/5x6_5` (shown as `dactyl_manuform_5x6_5` in some preset lists).
3. Edit the keymap visually.
4. Compile and download the firmware file.
5. Open the file in [QMK Toolbox](https://qmk.fm/toolbox).
6. Put the Pro Micro into bootloader mode, then flash.

The GUI flow is great for changing keymaps and flashing firmware, but for a one-off handwired board you usually still need QMK source/CLI first because Configurator cannot guess your custom matrix pins, split wiring, or diode direction. After the keyboard definition exists, the GUI becomes much more useful.

Useful tip: add a firmware key for bootloader mode on a layer, usually with `QK_BOOT`. That can save you from needing a dedicated reset button every time you want to flash new firmware. For example, put it on a function layer key you will not hit by accident:

```c
[1] = LAYOUT(
    _______, _______, _______, _______, _______, QK_BOOT,
    _______, _______, _______, _______, _______, _______
)
```

On older QMK keymaps you may see `RESET`; `QK_BOOT` is the newer name for jumping into the bootloader.

Useful official QMK docs:
- [How a Keyboard Matrix Works](https://docs.qmk.fm/how_a_matrix_works)
- [Hand-Wiring Guide](https://docs.qmk.fm/hand_wire)
- [Split Keyboard](https://docs.qmk.fm/features/split_keyboard)
- [QMK CLI Commands](https://docs.qmk.fm/cli_commands)
- [QMK Configurator](https://docs.qmk.fm/newbs_building_firmware_configurator)
- [QMK Flashing and Toolbox](https://docs.qmk.fm/flashing)

Big shoutout to this guide for helping make Dactyl Manuform builds feel less mysterious: [Complete Idiot Guide for Building a Dactyl Manuform Keyboard](https://medium.com/swlh/complete-idiot-guide-for-building-a-dactyl-manuform-keyboard-53454845b06)

---

### 🤝🏻 &nbsp;Connect with Me

<p align="left">
  <a href="https://linkedin.com/in/furkan-özgültekin-367936199/">
    <img src="https://img.shields.io/badge/-Furkan%20Özgültekin-0077B5?style=flat&logo=Linkedin&logoColor=white" alt="LinkedIn Profile"/>
  </a>
  &nbsp;&nbsp;
  <a href="mailto:furkanozgultekin@gmail.com">
    <img src="https://img.shields.io/badge/-furkanozgultekin@gmail.com-D14836?style=flat&logo=Gmail&logoColor=white" alt="Email Me"/>
  </a>
</p>
