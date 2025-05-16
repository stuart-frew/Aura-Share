# Aura Share

> Forked from <https://github.com/FionaBrightgrass/Aura-Share>

![image](https://i.imgur.com/Up1jqTJ.png)

**This mod is presently compatible with Pathfinder 1e**

Aura Share: Automates the sharing of buffs between tokens. This makes handling auras easier. The conditions for automating the auras are listed in the notes below. (It's pretty simple)

> Manifest URL: [https://github.com/stuart-frew/Aura-Share/raw/main/module.json]

## Instructions

Create a buff (item on a character sheet) with the dictionary flag: "radius" of atleast 0.

The buff now automatically shares depending on the flags below:

Mandatory flags for the buff to share

| Flag   | Type       | Value                                                       |
| ------ | ---------- | ----------------------------------------------------------- |
| radius | Dictionary | setting this above -1 triggers the buff or "aura" to share. |

Optional flags that can be added to the buff:

| Flag             | Type    | Value                                                                                                                              |
| ---------------- | ------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| shareInactive    | Boolean | shares the buff even if it is toggled off. Great for buffs that only impact allies.                                                |
| shareEnemies     | Boolean | shares the buff with enemies (instead of allies). Typically combined with shareInactive.                                           |
| shareNeutral     | Boolean | shares the buff with targets with neutral disposition.                                                                             |
| shareAll         | Boolean | shares the buff with everyone regardless of disposition.                                                                           |
| shareUnconscious | Boolean | shares the buff even if you're unconscious. (This works like the Diehard feat, but allows DMs more control over individual auras.) |

> **note:** these are case sensitive.

Example:
![image](https://i.imgur.com/zRj6ITb.png)

## Conditions for Applying Auras

### Adds the buff to allies if

- The source actor has a buff with a radius > 0.
- The buff is enabled, OR if the source actor's buff has
  the "shareInactive" Boolean flag.

### Adds the buff to allies when

- They enter range (either actor can move).
- The buff is toggled on.
- A Token is created in the scene, and allies are in range.
- The aura actor's HP rises above 0.

### Adds the buff to enemies if:<

- The buff also has a "shareEnemies" Boolean Flag. Note: You typically would combine this with "shareInactive" so that the buff doesn't hurt the source actor. <br>

### Deactives or Deletes the buff when

> _NOTE:_ These can be toggled between activate auras and delete auras in the module settings

- The source moves out of range.
- The recipient moves out of range.
- The source disables the buff, and the buff does not have the "alliesOnly" Boolean Flag
- The source's HP falls below zero, unless: It has the Diehard feat -OR- Unconscious Auras is toggled OFF in the menus.

### Deletes the buff when

- the source is deleted.
