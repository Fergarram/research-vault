
## Quick Overview

This week I finally focused on the command/action system. I don't know how to call it yet. But I do have defined the way that it works. You can look at the diagram below.

![[control-tree-diagram-notes.png]]

The idea is that all interactions can be understood as a tree starting from the cursor's location.

Here is a text representation of the diagram:

1. Cursor hovers on top of elements
2. Determine which type of element is being hovered: floor, static thing or controllable thing.
3. Actions can be configured at this point of the tree, but they can go further down depending on the modifier keys such as `shift` or `ctrl`.

![[controls.gif]]

This above GIF is actually incorrect because it doesn't show the available actions once the controllable thing is in focus. But it illustrates how the tree is used to show the available interactions and modifiers using the floating cursor guide.

## Modifier-Action Trees

My goal is to make it easy for thing creators to define action trees. This is what I'm kinda aiming for:

```js
const global_actions = {
	// Controllable things
	// Like the notebook-paper, most interactable things in the room.
	"controllable": {

		// When a thing is focused the tree narrows down from here.
		"notebook-paper": {
			// Contents are pulled from the notebook-paper module but shown here for illustration.
			"LMB": {
				text: "",
			}
		},

		// Modifiers available when hovering ANY controllable thing.
		"mods": {
			"Ctrl": {
				// Actions for ANY controllable thing for the "ctrl" modifier
				"LMB": {
					text: "Lift thing"
				},
				"RMB": {
					text: "Resize thing"
				}
			},
			"Shift": {
				"LMB": {
					text: "Multi-select"
				},
				"RMB": {
					text: "Native menu"
				}
			},
		},

		// Actions available just by hovering on ANY controllable thing
		"actions": {
			"LMB": {
				text: "Focus"
			},
		},
	},
	// Static things:
	// Things that are decorative or have no defined interactions.
	"static": {
		// Same structure as for controllable things. Except that there is no further drilling into specific things because that would make it a controllable thing.
	},

	// Floor or room actions
	// Actions like lasso tool to select many things or pulling out a context menu about the wallpaper.
	"floor": 
		"mods": {
			"Shift": {
				"LMB": {
					text: "Lasso select"
				},
				"RMB": {
					text: "Native menu"
				}
			}
		},
		"actions": {
			"Tab": {
				text: "Tools"
			},
			"RMB": {
				text: "Options menu"
			}
		}
	}
};
```

With a setup like this, based on the currently pressed keys and mouse hovering state, and focus state, we can narrow down the options to the available actions.

## Action Management

The way I see it is there will be actions defined "globally" like the actions for all controllable or static things and actions for the room floor.

But when a thing has keyboard or mouse interactions it can define those interactions by creating an object tree like that.

### Action implementation reference

At the end, when the user runs an action, which will be determined by the action manager module, it will notify the thing module so that it is the thing module that is in charge of running whatever thing is needed. This way the scope is limited to that thing module.

For global actions it would be the same as thing modules but without the thing definition. For example, a pen that allows you to draw anywhere on the floor or at a transparent layer on top of things.

I still need to see how the implementation looks like at the end, but I think that these are good steps towards my goals.