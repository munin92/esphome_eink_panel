# 🧭 Instructions – Calendar Integration Setup for ESPHome E-Paper Display

This guide explains how to connect your **Home Assistant calendar** to the **ESP32 E-Paper Display** so that your next four events appear on the screen.

The required files (`helperscript.yaml` and `automation.yaml`) are already included in this repository — you just need to create the four text helpers and adjust the calendar IDs in your Home Assistant setup.

---

## 🪄 Step 1 – Create four text helpers

The display reads its event text from four text helpers in Home Assistant:

input_text.next_event_1
input_text.next_event_2
input_text.next_event_3
input_text.next_event_4

### How to create them

1. In Home Assistant, go to  
   **Settings → Devices & Services → Helpers → Create Helper → Text**.
2. Create **four** helpers with these names and IDs:
   - `Next Event 1` → `input_text.next_event_1`
   - `Next Event 2` → `input_text.next_event_2`
   - `Next Event 3` → `input_text.next_event_3`
   - `Next Event 4` → `input_text.next_event_4`
3. Set the **maximum length** to **255 characters** for each helper.

That’s it — no YAML editing required for this step.

---

## ⚙️ Step 2 – Adjust your calendar entity IDs

Open the included **`helperscript.yaml`** file, create a script out of it.  
Inside, you’ll find a section listing several example calendar entities:


Replace these with your own **calendar entity IDs** from Home Assistant.  
You can find them under **Settings → Entities → Calendar**.

The script automatically:
- Collects events from all calendars you list,
- Sorts them by start time,
- Updates the four text helpers with the next events.

---

## 🔁 Step 3 – Verify the automation

The included **`automation.yaml`** file automatically runs the helper script:
- at Home Assistant **startup**
- **every hour**
- whenever one of your calendar entities changes

You don’t need to edit it unless you want a different update schedule.

---

## 🧪 Step 4 – Test the setup

1. In Home Assistant, open **Developer Tools → Scripts**.
2. Run the script **“Update Next Events”** manually.
3. Check the four text helpers:
   - `input_text.next_event_1`
   - `input_text.next_event_2`
   - `input_text.next_event_3`
   - `input_text.next_event_4`
4. Each helper should now contain one upcoming event.
5. The ESPHome display will show these lines automatically at its next update.

---

## ✅ Done!

Your ESP32 e-paper display now automatically shows up to **four upcoming calendar events** from your Home Assistant calendars.

If you add or change events, the automation will update the display automatically every hour or when a calendar changes.

