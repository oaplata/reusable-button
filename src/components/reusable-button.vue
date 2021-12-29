<template>
  <button :class="classes" :style="style"><slot /></button>
</template>

<script>
const validateProp = (prop) => {
  return prop !== undefined && prop !== null && prop !== false
}

function hexToRgb(hex, alpha = 1) {
  // Expand shorthand form (e.g. "03F") to full form (e.g. "0033FF")
  var shorthandRegex = /^#?([a-f\d])([a-f\d])([a-f\d])$/i;
  hex = hex.replace(shorthandRegex, function(m, r, g, b) {
    return r + r + g + g + b + b;
  });

  var result = /^#?([a-f\d]{2})([a-f\d]{2})([a-f\d]{2})$/i.exec(hex);
  return result ?
  `rgba(${parseInt(result[1], 16)}, ${parseInt(result[2], 16)}, ${parseInt(result[3], 16)}, ${alpha})`
  : null;
}

export default {
  name: 'ReusableButton',
  props: ['color', 'focus', 'outlined', 'text', 'noShadow', 'textColor', 'disabled'],
  computed: {
    classes () {
      const classes = ['btn']
      if (validateProp(this.focus)) {
        classes.push('focus')
      }
      if (validateProp(this.outlined)) {
        classes.push('outlined')
      }
      if (validateProp(this.text)) {
        classes.push('text')
      }
      if (validateProp(this.noShadow)) {
        classes.push('no-shadow')
      }
      if (validateProp(this.disabled)) {
        classes.push('disabled')
      }
      return classes
    },
    style () {
      const color = !validateProp(this.disabled) ? this.color || '#cccccc' : '#888888'
      const style = {
        '--color': color,
        '--hover-color': 0.85,
        '--shadow-color': hexToRgb(color, 0.3),
        '--text-color': this.textColor || '#442233'
      }

      if (validateProp(this.outlined)) {
        style['--outlined-color-bg-hover'] = hexToRgb(style['--color'], 0.2)
      }

      if (validateProp(this.text)) {
        style['--text-color-bg-hover'] = hexToRgb(style['--color'], 0.2)
        style['--text-color'] = style['--color']
      }

      return style
    }
  }
}
</script>

<style>
.btn {
  border: none;
  background: none;
  box-shadow: 2px 2px 5px 0px var(--shadow-color);
  text-transform: capitalize;
  padding: 15px 30px;
  border-radius: 5px;
  background-color: var(--color);
  transition: 0.2s;
  font-size: 25px;
  width: fit-content;
  color: var(--text-color);
  cursor: pointer;
}

.btn:hover, .btn:focus, .btn.focus {
  filter: brightness(var(--hover-color));
}

.btn.outlined {
  background-color: transparent;
  border: solid 2px var(--color);
  /* box-shadow: none; */
}

.btn.outlined:hover, .btn.outlined:focus, .btn.outlined.focus {
  background-color: var(--outlined-color-bg-hover);
}

.btn.text {
  background-color: transparent;
  color: var(--text-color);
  box-shadow: none;
  font-weight: 600;
}

.btn.text:hover, .btn.text:focus, .btn.text.focus {
  background-color: var(--text-color-bg-hover);
}
.btn.disabled:hover, .btn.disabled:focus, .btn.disabled.focus {
  background-color: var(--color);
  filter: none;
}

.btn.no-shadow {
  box-shadow: none;
}

</style>