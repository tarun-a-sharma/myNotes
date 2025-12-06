
# LoFi vs HiFi

## Lo-Fi (Low-Fidelity) Designs

Simple, rough representations of a user interface — often black-and-white, with basic shapes and placeholders.

### Common forms
- Paper sketches
- Wireframes (hand-drawn or simple digital ones)
- Basic layout diagrams

### Characteristics
- Minimal styling
- Focus on structure and layout
- No detailed interactions
- Quick and inexpensive to produce
- Used early in the design process

### Purpose
- Brainstorming ideas
- Establishing information architecture
- Aligning on layout and flows
- Quickly iterating concepts
- Getting early feedback without over-investing time

## Hi-Fi (High-Fidelity) Designs

Realistic, detailed, and interactive representations of the final UI.

### Common forms
- Pixel-perfect mockups
- Interactive prototypes (in Figma, Adobe XD, Sketch, etc.)
- Designs including brand style, color, typography, and animations

### Characteristics
- Full visuals and theming
- Real or near-real content and data
- Interactive flows and transitions
- Suitable for usability testing
- Very close to the final product

### Purpose
- Validate detailed interactions
- Conduct realistic user testing
- Present to stakeholders
- Prepare handoff to developers
- Finalize the look and feel

## Key Points

- Lo-Fi = Wireframe; Hi-Fi = High fidelity.
- Common mobile frame size: 375 x 667 (recommended).
- Hold Alt and move an item to duplicate it.
- Press `I` to open the color picker.
- Hold Alt while changing width or height to scale both sides.
- `Shift + 1`: Zoom to fit.
- `Shift + 0`: Zoom to 100%.

## Hotkeys

- `V` — Selection cursor.
- Press and hold Space to pan/move the canvas.
- `R` — Rectangle.
- `L` — Line.
- `Shift + L` — Arrow.
- `O` — Ellipse.
- `T` — Text.
- `Ctrl + [ / ]` — Send backward / bring forward (layer position).
- `Ctrl + Shift + [ / ]` — Send to back / bring to front.
- Hold Shift and drag to create a shape with equal width and height.
- `Ctrl + D` — Duplicate.
- Shift + drag to move while preserving alignment.
- Alt + drag duplicates from the center.
- After duplicating once, `Ctrl + D` repeats the last duplicate with the same spacing.
- Select multiple items and moving them will show pink spacing guides to maintain consistent spacing.
- `Ctrl + Shift + H` — Hide/Show selection.
- `Ctrl + Shift + L` — Lock.
- `Shift + R` — Toggle rulers.
- `Ctrl + Alt + K` — Create component.
- `Ctrl + Alt + B` — Detach instance.
- `0`–`9` — Set opacity of the selected element.
- `Ctrl + G` — Group selected items.
- `Shift + A` — Create Auto Layout.

## Frame vs Group

- Items inside frames maintain their individual identity.
- Frames have `Clip content` to show or hide content that extends outside the frame.
- Groups bind items together; resizing the group affects the contained items accordingly.
- Within a group, items can have different widths and heights, but changing the group's properties affects all contained items.

## Layers

- To rename layers, press `Ctrl + R`. Use `Tab` and `Shift + Tab` to navigate layers.
- Select multiple layers and press `Ctrl + R` to rename them in sequence.

## Masking

- Use the `Clip content` checkbox in frames to clip overflowing content.
- `Ctrl + Alt + M` — Use a shape as a mask.
    - Place a shape above the item you want to mask.
    - Move the shape to the top of the layer stack.
    - Press `Ctrl + Alt + M` to create the mask.
    - Masking with a shape allows you to use the shape's properties (fills, strokes, corner radius, etc.).

## Layer Styles

- Layer styles help keep properties consistent and efficient in Figma.
- Save a master style (fills, effects, typography) and apply it to other layers.
- Updates made to the master style automatically update all instances.

## Design Systems

- Define a finite set of colors, typography, and component styles for reuse.
- Ensures consistency across designs and speeds up work.
- Makes iteration faster and reduces cognitive load.

- Add color as a variable.
![alt text](image.png)
- To break the link to a shared style, click the broken chain icon.
![alt text](image-3.png)

- To save a text style, save the full text properties (note: alignment is not saved with text styles).
![alt text](image-4.png)

## Constraints

- Constraints ensure designs adapt to different screen sizes and aspect ratios.
- They allow you to design once and have layouts respond reliably.
- By default, at least two constraints are selected.
- Hold Shift and click edges to remove or toggle multiple constraints.

![alt text](image-5.png)

## Guides

- Guides help align layers and objects precisely across your project.
- Guides do not appear on exported assets.
- `Shift + R` — Toggle rulers.
- Drag from the left or top rulers to create guides.
- Hold Alt while dragging to show distance measurements between items.
![alt text](image-6.png)
- Grid
![alt text](image-7.png)

## Components

- Components are reusable UI elements (buttons, icons, complex elements).
- Similar to text and fill styles, components promote consistency.
![alt text](image-8.png)
- Changes made to a master component (including constraints) propagate to its instances.
- `Ctrl + Alt + K` — Create component.
![alt text](image-9.png)
- You can override individual properties on instances without affecting the master.
- To reset an instance to the master, use the `Reset` option.
![alt text](image-10.png)
- `Ctrl + Alt + B` — Detach instance.
![alt text](image-11.png)
- Edit instance properties from the right-hand panel.
![alt text](image-12.png)
- For better accessibility, use a naming convention like `component-style/component-name`, e.g., `btn/Primary`, `btn/Secondary`.
![alt text](image-13.png)
- Keep master components on a separate page for organization.
![alt text](image-14.png)

## Prototyping (Interaction Design)

- Prototyping replicates how users will interact with designs.
![alt text](image-15.png)

![alt text](image-16.png)
- Select an element, open the `Prototype` tab in the right panel, and a node will appear on the element.
- Drag the node to the destination frame to create an interaction.
![alt text](image-17.png)
- Configure interaction type, animation, and navigation options in the Prototype panel.
![alt text](image-18.png)
- Use the play icon to preview the prototype.
![alt text](image-20.png)

## Export

- Select an item to export, open the `Export` panel in the right-hand corner, and click `+` to add export settings.
![alt text](image-21.png)
- Configure file format, scale, and suffix, then click `Export`.
![alt text](image-22.png)

![alt text](image-23.png)

## Libraries

![alt text](image-24.png)

![alt text](image-25.png)

## Advanced Figma

### Auto Layout

- Auto Layout creates frames that resize dynamically based on their contents.
- Group items (`Ctrl + G`), then right-click and choose `Create Auto Layout` or press `Shift + A`.
![alt text](image-26.png)
- Ensure parent and child dimensions are set to `Hug` when appropriate.
![alt text](image-27.png)

## Scrolling

- Add content inside a frame and set the frame's overflow behavior in the Prototype panel to enable horizontal or vertical scrolling.
![alt text](image-28.png)

## Smart Animate

![alt text](image-29.png)

## Boolean Operations

- Boolean operations let you combine shape layers in various ways (Union, Subtract, Intersect, Exclude).
![alt text](image-30.png)

## Other Tips

- Use the link icon next to width and height to toggle uniform scaling.
- Click and drag on width/height values to adjust them interactively.

## Set Default Properties for an Element

![set-default](./images/default-property.png)

## Copy Properties

![copy-property](./images/copy-property.png)

## Paste Properties

![paste-property](./images/paste-property.png)

## Difference Between Frame and Group

Both are similar, but frames offer additional features:
- `Clip content`.
- Constraints and layout behaviors relative to the frame.

## Smart Animate & Delays

- Use Smart Animate between similar frames to animate shared layers.
- Matching layer names across frames helps Smart Animate identify elements.

## Ideas

- [Dribbble](https://dribbble.com/)
- [Behance](https://www.behance.net/)
- [Envato Elements](https://elements.envato.com/)
- [Adobe Stock](https://stock.adobe.com/in)
- [Pttrns](https://www.pttrns.com/)
- [Awwwards](https://www.awwwards.com/)
- [CSS Design Awards](https://cssdesignawards.com/)
- [One Page Love](https://onepagelove.com/)

## Color Resources

- [Material Color System](https://m3.material.io/styles/color/system/overview)
- [Color Hunt](https://colorhunt.com)
- [Adobe Color](https://color.adobe.com/)
- [Grabient](https://www.grabient.com/)
- [Dribbble color ideas](https://dribbble.com/)
- [CSS Gradient](https://cssgradient.io/)

