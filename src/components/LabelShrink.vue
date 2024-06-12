<script>
  export default {
    name: 'vue-treeselect--label-shrink',
    inject: [ 'instance' ],

    computed: {
        shouldShrink() {
            const { instance } = this
            return instance.hasValue || instance.trigger.isFocused || instance.menu.isOpen
        },
    },

    methods: {
        renderLabel() {
            const { instance } = this
            const { placeholder } = instance
            const shrinkClass = this.shouldShrink ? 'vue-treeselect__label-shrink--shrink' : ''
            const shrinkStyle = this.shouldShrink ? `padding-left: ${instance.triggerWidth}px;` : ''
            const shrinkText = this.shouldShrink ? instance.getPlaceholder() : ''
            const label = instance.selectedNodesStates.length ? shrinkText : placeholder
            return (
                <label class={`vue-treeselect__label-shrink ${shrinkClass}`} style={shrinkStyle}>
                    {label}
                </label>
            )
        },
    },

    render() {
      const { instance } = this

      return (
        <div class="vue-treeselect__label-container">
            {this.renderLabel()}
        </div>
      )
    },
  }
</script>
