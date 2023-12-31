# Lovelace-mushroom-button-cards

Forked from [Lovelace-mushroom-button-card](https://github.com/hcoohb/lovelace-mushroom-button-card) repository to expand the collection with custom cards suitable for my needs. But maybe someone find them usefull too.

### Original description:

> The intention is to build a collection of [button-card](https://github.com/custom-cards/button-card) templates to match the theme of the [mushroom-cards](https://github.com/piitaya/lovelace-mushroom) for the cards not present in lovelace-mushroom, or cards adding some features/customization.  
> Note that a key difference with the nice [UI Lovelace Minimalist](https://github.com/UI-Lovelace-Minimalist/UI/) is that you can still use the lovelace UI editor.  
> Primarily for my personnal use but sharing in case it helps someone.

## Usage

Requirements:

- [HACS](https://hacs.xyz/) installed
- [mushrooom-ui](https://github.com/piitaya/lovelace-mushroom)
- [Button card](https://github.com/custom-cards/button-card)

1. Ensure all requirements are met
2. In the `Raw configuration editor` in the Lovelace UI editor, copy the code from the `templates.yml` file at the top (adapt if you already have some button-card templates).
3. In the dashboard, add a `Manual card` and place the usage code provided below tweaking as necessary.

## Cards

### 1. Irrigation card for HunterX

![image](images/irrigation_idle.png)
![image](images/irrigation_active.png)

<details><summary>See usage</summary>
  
> Requirements:
> - Button-card
> 
> Manual card code:
> ```yaml
> type: custom:button-card
> template: mushroom_irrigation
> entity: timer.irrigation_time_remaining
> ```
>
> Variables:
> - `toggle_switch`: switch entity, toggles irrigation on/off
> - `active_zone`: input_text entity, contains currently selected watering zone
> - `response`: input_text entity, used to display messages from irrigation service
> 
> Manual card code - example with variables:
> ```yaml
> type: custom:button-card
> template: mushroom_irrigation
> entity: timer.irrigation_time_remaining
> variables:
>   toggle_switch: switch.irrigate_lawn
>   active_zone: input_text.irrigation_active_zone
>   response: input_text.zone_action_result
> ```
</details>

### 2. 🌡 Climate card

![image](https://user-images.githubusercontent.com/12975783/154590201-6b472286-c60c-4a86-b7e8-60bf63aa4a89.png)
![image](https://user-images.githubusercontent.com/12975783/154589300-45531ded-2632-4932-b203-450009b755b3.png)

<details><summary>See usage</summary>
  
> Requirements:
> - Button-card
> 
> Manual card code:
> ```yaml
> type: custom:button-card
> template: mushroom_climate
> entity: climate.main_ac
> ```
>
> Variables:
> - `default_hvac_mode`: set the default mode when card is clicked. (if variable not set: cool)
> 
> Manual card code - example with variables:
> ```yaml
> type: custom:button-card
> template: mushroom_climate
> entity: climate.main_ac
> variables:
>  default_hvac_mode: heat
> ```
</details>

### 3. Timer card

![image](https://user-images.githubusercontent.com/12975783/154589587-462e79e5-05e1-4e1f-b7a0-1290b755bd7f.png)
![image](https://user-images.githubusercontent.com/12975783/154589622-2ddd500b-029a-4ab4-bbf1-a721ee1a57ab.png)

<details><summary>See usage</summary>
  
> Requirements:
> - Button-card
> - [Card-mod](https://github.com/thomasloven/lovelace-card-mod)
> 
> Manual card code:
> ```yaml
> type: custom:button-card
> template: mushroom_timer
> name: Bedside Music Timer
> entity: timer.bedside_music_timer
> variables:
>   input_datetime_id: input_datetime.bedside_music_timer_time
> ```
> 
> Details:
> - The entity must be a timer (Configuration>Automation&Scenes>Helpers>Add helper>Timer)
> - variable `input_datetime_id` is the input_datetime that must be created (Configuration>Automation&Scenes>Helpers>Add helper>Date&Time>Time) to be able to configure the duration of the timer from the UI.
> - Create any automation for what you want to happen, using the trigger: Event> timer.finished
</details>
