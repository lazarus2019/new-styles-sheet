[Prefers-color-scheme](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-color-scheme)
[Can I use](https://caniuse.com/?search=prefers-color-scheme)
[Codepen](https://codepen.io/lazarus2019/pen/abMzXoL)

- prefers-color-scheme dùng để detect người dùng yêu cầu sử dụng mã màu light/dark. Dựa vào theme của hệ thống hoặc thông tin theme của browser.
- Ngoài ra còn hỗ trợ CSS style cho SVG, iframe hay nhúng elements dựa trên color-scheme của element cha trên webpage.
- Hỗ trợ cross-origin.

## Syntax

```css
@media (prefers-color-scheme: dark) {
  .element {
    background: #000;
    color: #fff;
  }
}
@media (prefers-color-scheme: light) {
  .element {
    background: #fff;
    color: #000;
  }
}
```

### Kết hợp color-scheme thay đổi màu cho svg

**màu mặc định: blue**

- image 1: kế thừa mã màu từ browser và có thay đổi khi đổi theme
- image 2 và 3: kế thừa mã màu của element cha

```html
<div>
  <img />
</div>

<div style="color-scheme: light">
  <img />
</div>
<div style="color-scheme: dark">
  <img />
</div>

<!-- Embed an SVG for all <img> elements -->
<script>
  for (let img of document.querySelectorAll('img')) {
    img.alt = 'circle';
    img.src =
      'data:image/svg+xml;base64,' +
      btoa(`
      <svg width="32" height="32" viewBox="0 0 32 32" xmlns="http://www.w3.org/2000/svg">
        <style>
          :root { color: blue }
          @media (prefers-color-scheme: dark) {
            :root { color: purple }
          }
        </style>
        <circle fill="currentColor" cx="16" cy="16" r="16"/>
      </svg>
    `);
  }
</script>
```

### Detect OS theme bằng JS

```js
const isDarkOSDarkTheme = window.matchMedia(
  '(prefers-color-scheme: dark)'
).matches;

if (prefersDark) {
  root.classList.add('DarkMode');
} else {
  root.classList.remove('DarkMode');
}
```
