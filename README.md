<h1>
Theatre
&nbsp;
<a href="https://godotengine.org/" target="_blank"><img src="https://img.shields.io/badge/Godot%204.3-white?style=flat-square&logo=godotengine&logoColor=white&color=%23478CBF"></a>
<a href="https://nndda.github.io/Theatre/" target="_blank"><img src="https://img.shields.io/badge/Documentation-white?style=flat-square"></a>
</h1>

<img src="/addons/Theatre/assets/icons/Theatre.svg" height="160" align="right">

Text-based linear dialogue system for Godot 4.3.
- ✍️ Written in human-readable syntax.
- ✨ Focused on presentation and delivery of your story.
- 📝 100% written in GDScript.

> [!IMPORTANT]
> This project is still in development, and is subject to frequent and breaking changes, and bugs.

<table align="center">
<tr align="center">
<td>
    <b> Rendered </b>
</td>
<td>
    <b> Written </b>
</td>
</tr>
<tr>
<td>

<img src="https://github.com/user-attachments/assets/5bbefeed-61bb-4b9d-89a0-69d8300a3c08" width="364">

</td>
<td>
    
```
Dia:
    "Welcome! {d=0.8}to the
    [fx1]Theatre[/fx1]!
        d=0.9
    yet another text-based dialogue addon
        d=0.3
    developed for Godot {gd_ver}."


    ＼(^ ▽ ^)
```

</td>
</tr>
</table>

# Features

## Dialogue tags

Fine-tune your dialogue flow with `{delay}` and `{speed}`.
```
Godette:
    "Hello!{delay = 0.7} nice to meet you"
```
```
Godette:
    "Hello!
        delay=0.7
    nice to meet you"
```

## Function calls

Connect your story to the game with function calls.
```
{player_name}:
    "Thanks! that feels so much better"

    Player.heal(20)
```
```
Ritsu:
    "Cheers!"

    Portrait.set("ritsu_smile.png")
```

Call functions only at specific points in the Dialogue.
```
Dia:
    "
    Let me brighten up the room a little...{d = 1.1}
    {0}
    there we go.
    "

# Call this function using its index: {0}
    Background.set_brightness(1.0)
```

# Quick Start

Write your epic Dialogue!
```gdscript
# write it directly with triple quotation marks
var epic_dialogue = Dialogue.new("""

Dia:
    "For performance reason, I'd recommend
    using the method below instead."

""")

# alternatively, write it in a *.dlg.txt or *.dlg  file, and load it
var epic_dialogue = Dialogue.load("res://epic_dialogue.dlg")
```

Set the Stage! Add `Stage` and `DialogueLabel` node to your scene. Structure your scene like the following:

<div align="center">
<img src="https://github.com/user-attachments/assets/05e5e3ba-adfb-4208-81bc-adbbf6b6c571">
</div>

<br>

Adjust the position and size of the `PanelContainer` to your liking.

Select the `Stage` node, and reference the `Label` & `DialogueLabel` node to display your Dialogue. Adjust and configure your `Stage` via the inspector. Alternatively, you can also set them in script:

<table align="center">
<tr align="center">
<td>
    <b> Inspector </b>
</td>
<td>
    <b> GDScript </b>
</td>
</tr>

<tr>
<td>

<img src="https://github.com/nndda/Theatre/assets/96333146/69d7b946-2444-4247-8cdf-394332466c99" width="260">

</td>
<td>

```gdscript
@onready var my_stage : Stage = $Stage

func _ready():
    my_stage.actor_label = $PanelContainer/VBoxContainer/Label
    my_stage.dialogue_label = $PanelContainer/VBoxContainer/DialogueLabel

    my_stage.allow_skip = true
    my_stage.allow_cancel = true
    my_stage.allow_func = true
    my_stage.speed_scale = 1.0
```

</td>
</tr>

</table>

Reference the `Stage` node in the script, and set up a way to progress your Dialogue with `Stage.progress()`.

```gdscript
func _input(event):
    if event.is_action_pressed("ui_accept"):
        my_stage.progress()
```

And finally, start the `Stage` with your `epic_dialogue`.

```gdscript
func _ready():
    my_stage.start(epic_dialogue)
```

<p align="center">
<a href="https://nndda.github.io/Theatre/quickstart/" target="_blank">More detailed quick start tutorial here</a>
</p>

## License

- Theatre is licensed under [MIT](LICENSE).
- [Theatre logo](/addons/Theatre/assets/icons/Theatre.svg), created by [nnda](https://github.com/nndda), is licensed under [CC-BY 4.0](https://creativecommons.org/licenses/by/4.0/).
- [Class icons](addons/Theatre/assets/icons/classes), from [@fontawesome](https://fontawesome.com), are licensed under [CC-BY 4.0](https://creativecommons.org/licenses/by/4.0/).
