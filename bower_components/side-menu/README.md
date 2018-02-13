


##&lt;side-menu&gt;

Material design: [Menus](https://www.google.com/design/spec/components/menus.html)

`<side-menu>` implements an accessible menu control with Material Design styling. The focused item
is highlighted, and the selected item has bolded text.

```html
<side-menu>
  <paper-item>Item 1</paper-item>
  <paper-item>Item 2</paper-item>
</side-menu>
```

An initial selection can be specified with the `selected` attribute.

```html
<side-menu selected="0">
  <paper-item>Item 1</paper-item>
  <paper-item>Item 2</paper-item>
</side-menu>
```

Make a multi-select menu with the `multi` attribute. Items in a multi-select menu can be deselected,
and multiple items can be selected.

```html
<side-menu multi>
  <paper-item>Item 1</paper-item>
  <paper-item>Item 2</paper-item>
</side-menu>
```

### Styling

The following custom properties and mixins are available for styling:

| Custom property | Description | Default |
| --- | --- | --- |
| `--side-menu-background-color` | Menu background color | `--primary-background-color` |
| `--side-menu-color` | Menu foreground color | `--primary-text-color` |
| `--side-menu-disabled-color` | Foreground color for a disabled item | `--disabled-text-color` |
| `--side-menu` | Mixin applied to the menu | `{}` |
| `--side-menu-selected-item` | Mixin applied to the selected item | `{}` |
| `--side-menu-focused-item` | Mixin applied to the focused item | `{}` |
| `--side-menu-focused-item-after` | Mixin applied to the ::after pseudo-element for the focused item | `{}` |

### Accessibility

`<side-menu>` has `role="menu"` by default. A multi-select menu will also have
`aria-multiselectable` set. It implements key bindings to navigate through the menu with the up and
down arrow keys, esc to exit the menu, and enter to activate a menu item. Typing the first letter
of a menu item will also focus it.



##&lt;side-submenu&gt;

`<side-submenu>` is a nested menu inside of a parent `<side-menu>`. It
consists of a trigger that expands or collapses another `<side-menu>`:

```html
<side-menu>
  <side-submenu>
    <paper-item class="menu-trigger">Topics</paper-item>
    <side-menu class="menu-content">
      <paper-item>Topic 1</paper-item>
      <paper-item>Topic 2</paper-item>
      <paper-item>Topic 3</paper-item>
    </side-menu>
  </side-submenu>
  <side-submenu>
    <paper-item class="menu-trigger">Faves</paper-item>
    <side-menu class="menu-content">
      <paper-item>Fave 1</paper-item>
      <paper-item>Fave 2</paper-item>
    </side-menu>
  </side-submenu>
  <side-submenu disabled>
    <paper-item class="menu-trigger">Unavailable</paper-item>
    <side-menu class="menu-content">
      <paper-item>Disabled 1</paper-item>
      <paper-item>Disabled 2</paper-item>
    </side-menu>
  </side-submenu>
</side-menu>
```

Just like in `<side-menu>`, the focused item is highlighted, and the selected
item has bolded text. Please see the `<side-menu>` docs for which attributes
(such as `multi` and `selected`), and styling options are available for the
`menu-content` menu.


