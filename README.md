# Trillo

advanced css course project #2

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
