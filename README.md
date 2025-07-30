# Klipper + Marlin Object Cancel/Exclude Support for Cura (with Safe Z-Hop Fix)

This Cura post-processing script adds **Klipper-compatible object exclusion** tags (`exclude_object_start` / `exclude_object_end`), allowing **mid-print object cancellation** via Fluidd or Mainsail. It also retains Marlin-style `M486` support.

Includes an improved Z-hop fix that **preserves the X and Y coordinates** by setting them to the current position, instead of removing them entirely — avoiding unintended diagonal moves or firmware motion errors after object cancellation.

---

## 🧠 Features

- 🛑 Cancel individual objects mid-print (no need to stop the whole job)
- ✅ Compatible with Klipper (`exclude_object`) and Marlin (`M486`)
- 🧼 Optional Z-hop fix to prevent dragging over canceled parts
- 🖥️ Works with Cura, Elegoo Cura, and Creality Slicer (Windows only)
- 👷 Built and tested by real-world 3D printing use cases

---

## 🖥️ Cura Setup (Windows Only)

### Step 1 – Open the Cura Scripts Folder
- Open Cura
- Go to: `Help > Show Configuration Folder`
- Navigate into: `scripts`  
  (Typically: `%APPDATA%\cura\<your-version>\scripts`)

### Step 2 – Add the Script
- Paste `klipper_marlin_cancelorexclude_object.py` into the `scripts` folder
- **Right-click the file > Properties > Unblock** (important!)

### Step 3 – Restart Cura

### Step 4 – Add the Script
- `Extensions > Post Processing > Modify G-Code`
- Click **Add a Script**
- Select: `Klipper/Marlin Cancel or Exclude Object`

### Step 5 – (Optional) Enable Z-hop Fix
- Enable “Z-hop fix” in the script’s settings to apply safe vertical-only lift after canceling an object

---

## 🛠️ Klipper Setup

### `printer.cfg`
Add this line to enable object exclusion:

```ini
[exclude_object]
```

### `moonraker.conf`
Ensure this is added:

```ini
[file_manager]
enable_object_processing: True
```

### 🔁 Important:
If you uploaded your G-code **before enabling `enable_object_processing`**, you must re-upload it to allow Moonraker to reprocess the object list.

---

## 🖨️ Printing & Cancelling Objects

1. Start the print from Fluidd
2. Go to the **“Job”** tab
3. Scroll to **"Cancelable Objects"**
4. Click **Cancel** on the object you want to skip

> ⚠️ Once an object is cancelled, it **cannot be undone**.

---

## 📜 License

Based on original work by Aapo Saaristo (AGPLv3)  
Modifications © 2025 by Ashley Pitt @Ash's 3D Studio
Released under **CC BY-NC-SA 4.0**
