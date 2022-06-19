# Trillo
hands-on project from the udemy course by Jonas Schmedtmann.

## Notes

### Header

* 使用 `fill` 屬性，設定 svg 背景色
* `align-self` 屬性，可以個別調整子元素在交錯軸線的位置，屬性與 `align-item` 相同。假如我們已經在父元素上設定 `align-item`，但要其中一個內容物的位置需要調整成其他對齊方式，這時我們就可以針對該元素設定 `align-self` 來覆寫原本 `align-item` 的屬性。

### Hotel Overview

* flex 布局搭配 margin: auto 使用，可以完成 justify content 做不到的配置
```scss
.overview {
  display: flex;

  &__stars {
    margin-right: auto;
  }
}
```

### Detail

* 左右並排的列表 `.description list`

```scss
.list {
  list-style: none;
  margin: 3rem 0;
  padding: 3rem 0;
  border-top: var(--line);
  border-bottom: var(--line);

  display: flex;
  flex-wrap: wrap;

  &__item {
    flex: 0 0 50%;
    margin-bottom: 0.7rem;
  }

  // 使用 masks 給 svg icon 加上顏色
  &__item::before {
    content: '';
    display: inline-block;
    width: 1rem;
    height: 1rem;
    margin-right: 0.7rem;

    background-color: var(--color-primary);
    mask-image: url(../img/chevron-thin-right.svg);
    mask-size: cover;
  }
}
```
> 延伸閱讀: [CSS Masks 圖片遮罩效果](https://w3c.hexschool.com/blog/24db18f8)


* 用戶回饋卡片的 `::before` 圖標

```scss
.review {
  position: relative;
  // 略...

  &::before {
    content: '\201C';
    position: absolute;
    top: -2.75rem;
    left: -1rem;
    line-height: 1;
    font-size: 20rem;
    color: var(--color-grey-light-2);
    font-family: sans-serif;
    z-index: 1;
  }
}
```
> 延伸閱讀: [CSS Tricks](https://css-tricks.com/snippets/html/glyphs/)

### Call to action

* Button 特效

```html
<button class="btn">
  <span class="btn__visible">Book now</span>
  <span class="btn__invisible">Only 4 rooms left</span>
</button>
```

```scss
.btn {
  position: relative;
  color: #fff;
  font-size: 1.5rem;
  font-weight: 300;
  text-transform: uppercase;
  border-radius: 100px;
  border: none;
  background-image: linear-gradient(
    to right,
    var(--color-primary-light),
    var(--color-primary-dark)
  );
  overflow: hidden;
  cursor: pointer;

  & > * {
    display: inline-block;
    height: 100%;
    width: 100%;
    transition: all 0.2s;
  }

  &__visible {
    padding: 2rem 7.5rem;
  }

  &__invisible {
    position: absolute;
    left: 0;
    top: -100%;
    padding: 2rem 0;
  }

  &:hover {
    background-image: linear-gradient(
      to left,
      var(--color-primary-light),
      var(--color-primary-dark)
    );
  }

  &:hover &__visible {
    transform: translateY(100%);
  }

  &:hover &__invisible {
    top: 0;
  }

  &:focus {
    outline: none;
    animation: pulsate 1s infinite;
  }
}
```
