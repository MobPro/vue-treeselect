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
        const shrinkClass = this.shouldShrink ? 'vue-treeselect--label-shrink--shrink' : ''
        const label = this.shouldShrink ? instance.label : ''
        return (
                <label class={`vue-treeselect--label-shrink ${shrinkClass}`}>
                    {label}
                </label>
            )
      },
    },

    render() {
      return (
        <div>
            {this.renderLabel()}
        </div>
      )
    },
  }
</script>
