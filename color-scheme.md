[Color scheme docs](https://developer.mozilla.org/en-US/docs/Web/CSS/color-scheme)
[Can I use](https://caniuse.com/?search=Color-scheme)
[Codepen](https://codepen.io/lazarus2019/pen/abMzXoL) | [More Infomation](https://css-tricks.com/almanac/properties/c/color-scheme/)
- color-scheme cho phép elemtent chọn mã màu phù hợp với hệ điều hành khi render ra interface. Thường sẽ tác động vào elements của [form controls](https://developer.mozilla.org/en-US/docs/Learn/Forms), [scrollbars](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_scrollbars_styling) và những elements sử dụng [hệ thống màu của CSS](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_colors) (default).
- color-scheme sẽ thông báo browser thay đổi mã màu với bộ stylesheet có sẵn trong browser.
- **khác với prefers-color-scheme:** là bộ mã màu tự khai báo và sử dụng trong stylesheet.
[Forms elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Element#forms)
## Syntax
```css
color-scheme: normal; // sử dụng mã màu mặc định của browser
color-scheme: light; // sử dụng mã màu light của hệ thống
color-scheme: dark; // sử dụng mã màu dark của hệ thống
color-scheme: light dark;
color-scheme: only light; // không cho phép người dùng override mã màu

/* Global values */
color-scheme: inherit;
color-scheme: initial;
color-scheme: revert;
color-scheme: revert-layer;
color-scheme: unset;
```
## Example
### Khai báo mã màu
```css
:root{
	color-scheme: light dark;
}

header {
  color-scheme: only light;
}

main {
  color-scheme: light dark;
}

footer {
  color-scheme: only dark;
}
```
### Khai báo mã màu dựa trên OS theme - Kết hợp với prefers-color-scheme
- Sử dụng prefers-color-scheme để custom dark-mode cho giao diện
- Sử dụng color-scheme để tự động apply mãu màu cho những element hỗ trơ browser stylesheet.
```css
:root {
  color-scheme: light dark;
}

@media (prefers-color-scheme: light) {
  .element {
    color: black;
    background-color: white;
  }
}

@media (prefers-color-scheme: dark) {
  .element {
    color: white;
    background-color: black;
  }
}
```