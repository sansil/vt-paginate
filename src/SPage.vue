

<script>
export default {
  inject: {
    context: {},
  },
  props: {
    as: {
      type: String,
      default: "a",
    },
    page: {
      type: [String, Number],
      required: true,
    },
    href: {
      type: String,
      default: "#",
    },
  },
  render(createElement) {
    return createElement(
      this.as,
      {
        attrs: {
          href: this.as === "a" ? this.href : null,
          "aria-page-label": this.page,
          "aria-current-label": this.context.isActivePage(this.page),
        },
        on: {
          click: this.onSelectPage,
        },
      },
      [this.$scopedSlots.default({})]
    );
  },
  methods: {
    onSelectPage() {
      this.context.onSelectPage(this.page);
    },
  },
};
</script>

