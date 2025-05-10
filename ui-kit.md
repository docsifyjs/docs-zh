<!-- markdownlint-disable single-title no-duplicate-heading -->

# UI Kit

<details>
  <summary>查看本页面的 markdown 源代码</summary>
  <div style="max-height: 50vh; overflow: auto;">

[ui-kit.md](https://cdn.jsdelivr.net/gh/docsifyjs/docs-zh@main/ui-kit.md ":include :type=code")

  </div>
</details>

## 块引用 :id=blockquotes

> Cras aliquet nulla quis metus tincidunt, sed placerat enim cursus. Etiam
> turpis nisl, posuere eu condimentum ut, interdum a risus. Sed non luctus mi.
> Quisque malesuada risus sit amet tortor aliquet, a posuere ex iaculis. Vivamus
> ultrices enim dui, eleifend porttitor elit aliquet sed.
>
> _- 引用来源_

#### 嵌套 :id=nested

<!-- prettier-ignore -->

> 第 1 级
>
> > 第 2 级
> >
> > > 第 3 级

## 按钮 :id=buttons

#### 默认按钮 :id=default

<button>按钮</button>

#### 基础按钮 :id=basic

<button type="button">按钮</button> <a href="javascript:void(0);" class="button">链接按钮</a> <input type="button" value="Input Button" class="button">

#### 主按钮 :id=primary

<button type="button" class="primary">按钮</button> <a href="javascript:void(0);" class="button primary">链接按钮</a> <input type="button" value="Input Button" class="primary">

#### 次要按钮 :id=secondary

<button type="button" class="secondary">按钮</button> <a href="javascript:void(0);" class="button secondary">链接按钮</a> <input type="button" value="Input Button" class="secondary">

## 标注 :id=callouts

!> **Important** 使用`内联代码`和额外的占位符文本用于
强制包装内容和换行。

?> **Tip** 使用`内联代码`和额外的占位符文本用于
强制包装内容和换行。

## 代码 :id=code

这是 `内联代码`

```javascript
const add = (num1, num2) => num1 + num2;
const total = add(1, 2);

console.log(total); // 3
```

```html
<body>
  <p>Hello</p>
</body>
```

## 颜色 :id=colors

#### 主题 :id=theme

<div class="ui-kit-color">
  <figure>
    <div style="background: var(--theme-color-1);"></div>

    <figcaption>1<figcaption>
  </figure>
  <figure>
    <div style="background: var(--theme-color-2);"></div>

    <figcaption>2<figcaption>
  </figure>
  <figure>
    <div style="background: var(--theme-color-3);"></div>

    <figcaption>3<figcaption>
  </figure>
  <figure>
    <div style="background: var(--theme-color-4);"></div>

    <figcaption>4<figcaption>
  </figure>
  <figure>
    <div style="background: var(--theme-color);"></div>

    <figcaption>主题颜色<figcaption>
  </figure>
  <figure>
    <div style="background: var(--theme-color-5);"></div>

    <figcaption>5<figcaption>
  </figure>
  <figure>
    <div style="background: var(--theme-color-6);"></div>

    <figcaption>6<figcaption>
  </figure>
  <figure>
    <div style="background: var(--theme-color-7);"></div>

    <figcaption>7<figcaption>
  </figure>
  <figure>
    <div style="background: var(--theme-color-8);"></div>

    <figcaption>8<figcaption>
  </figure>
</div>

#### 单色 :id=monochromatic

<div class="ui-kit-color">
  <figure>
    <div style="background: var(--color-mono-min); border: 1px solid var(--color-mono-2);"></div>

    <figcaption>Min<figcaption>
  </figure>
  <figure>
    <div style="background: var(--color-mono-1);"></div>

    <figcaption>1<figcaption>
  </figure>
  <figure>
    <div style="background: var(--color-mono-2);"></div>

    <figcaption>2<figcaption>
  </figure>
  <figure>
    <div style="background: var(--color-mono-3);"></div>

    <figcaption>3<figcaption>
  </figure>
  <figure>
    <div style="background: var(--color-mono-4);"></div>

    <figcaption>4<figcaption>
  </figure>
  <figure>
    <div style="background: var(--color-mono-5);"></div>

    <figcaption>5<figcaption>
  </figure>
  <figure>
    <div style="background: var(--color-mono-6);"></div>

    <figcaption>6<figcaption>
  </figure>
  <figure>
    <div style="background: var(--color-mono-7);"></div>

    <figcaption>7<figcaption>
  </figure>
  <figure>
    <div style="background: var(--color-mono-8);"></div>

    <figcaption>8<figcaption>
  </figure>
  <figure>
    <div style="background: var(--color-mono-9);"></div>

    <figcaption>9<figcaption>
  </figure>
  <figure>
    <div style="background: var(--color-mono-max);"></div>

    <figcaption>Max<figcaption>
  </figure>
</div>

## 详细信息 :id=details

<details>
  <summary>详细信息（点击打开）</summary>

Suscipit nemo aut ex suscipit voluptatem laboriosam odio velit. Ipsum eveniet labore sequi non optio vel. Ut culpa ad accusantium est aut harum ipsam voluptatum. Velit eum incidunt non sint. Et molestiae veniam natus autem vel assumenda ut numquam esse. Non nisi id qui vero corrupti quos et.

</details>

<details open>
  <summary>详细信息（默认打开）</summary>

Suscipit nemo aut ex suscipit voluptatem laboriosam odio velit. Ipsum eveniet labore sequi non optio vel. Ut culpa ad accusantium est aut harum ipsam voluptatum. Velit eum incidunt non sint. Et molestiae veniam natus autem vel assumenda ut numquam esse. Non nisi id qui vero corrupti quos et.

</details>

## 表格要素 :id=form-elements

### Fieldset

<form>
  <fieldset>
    <legend>Legend</legend>
    <p>
      <label>
        Label<br>
        <input type="text" placeholder="Placeholder">
      </label>
    </p>
  </fieldset>
</form>

### Input

#### Checkbox

<form>
  <label><input type="checkbox" value="HTML" checked> HTML</label><br>
  <label><input type="checkbox" value="CSS"> CSS</label><br>
  <label><input type="checkbox" value="JavaScript"> JavaScript</label>
</form>

#### Datalist

<form>
  <label>
    Label<br>
    <input list="planets">
    <datalist id="planets">
      <option value="Earth">Earth</option>
      <option value="Jupiter">Jupiter</option>
      <option value="Mars">Mars</option>
      <option value="Mercury">Mercury</option>
      <option value="Neptune">Neptune</option>
      <option value="Saturn">Saturn</option>
      <option value="Uranus">Uranus</option>
      <option value="Venus">Venus</option>
    </datalist>
  </label>
</form>

#### Radio

<form>
  <label><input type="radio" name="language" value="HTML" checked> HTML</label><br>
  <label><input type="radio" name="language" value="CSS"> CSS</label><br>
  <label><input type="radio" name="language" value="JavaScript"> JavaScript</label>
</form>

#### Text

<form>
  <label>
    First name<br>
    <input type="text" placeholder="Placeholder">
  </label>
</form>

#### Toggles

<form>
Checkbox (multi-select)

<label><input class="toggle" type="checkbox" checked> HTML</label><br> <label><input class="toggle" type="checkbox"> CSS</label><br> <label><input class="toggle" type="checkbox"> JavaScript</label>

Radio (single-select)

<label><input class="toggle" type="radio" name="toggle" checked> HTML</label><br> <label><input class="toggle" type="radio" name="toggle"> CSS</label><br> <label><input class="toggle" type="radio" name="toggle"> JavaScript</label>

</form>

### Select

<form>
  <label>
    Label<br>
    <select>
      <option value="Earth">Select a planet...</option>
      <option value="Earth">Earth</option>
      <option value="Jupiter">Jupiter</option>
      <option value="Mars">Mars</option>
      <option value="Mercury">Mercury</option>
      <option value="Neptune">Neptune</option>
      <option value="Saturn">Saturn</option>
      <option value="Uranus">Uranus</option>
      <option value="Venus">Venus</option>
    </select>
  </label>
</form>

### Textarea

<textarea rows="5" cols="40">Ipsam totam tempora. Dolorum voluptas error tempore asperiores vitae error laboriosam autem possimus.
</textarea>

## Headings

# Heading 1 {docsify-ignore}

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse luctus nulla eu ex varius, a varius elit tincidunt. Aenean arcu magna, gravida id purus a, interdum convallis turpis. Aenean id ipsum eu tortor sollicitudin scelerisque in quis elit.

## Heading 2 {docsify-ignore}

Vestibulum lobortis laoreet nunc vel vulputate. In et augue non lectus pellentesque molestie et ac justo. Sed sed turpis ut diam gravida sagittis nec at neque. Vivamus id tellus est. Nam ac dignissim mi. Vestibulum nec sem convallis, condimentum augue at, commodo diam.

### Heading 3 {docsify-ignore}

Suspendisse sit amet tincidunt nibh, ac interdum velit. Ut orci diam, dignissim at enim sit amet, placerat rutrum magna. Mauris consectetur nibh eget sem feugiat, sit amet congue quam laoreet. Curabitur sed massa metus.

#### Heading 4 {docsify-ignore}

Donec odio orci, facilisis ac vehicula in, vestibulum ut urna. Ut bibendum ullamcorper risus, ac euismod leo maximus sed. In pulvinar sagittis rutrum. Morbi quis cursus diam. Cras ac laoreet nulla, rhoncus sodales dui.

##### Heading 5 {docsify-ignore}

Commodo sit veniam nulla cillum labore ullamco aliquip quis. Consequat nulla fugiat consequat ex duis proident. Adipisicing excepteur tempor exercitation ad. Consectetur voluptate Lorem sint elit exercitation ullamco dolor.

###### Heading 6 {docsify-ignore}

Ipsum ea amet dolore mollit incididunt fugiat nulla laboris est sint voluptate. Ex culpa id amet ipsum amet pariaturipsum officia sit laborum irure ullamco deserunt. Consequat qui tempor occaecat nostrud proident.

## Horizontal Rule

Text before rule.

---

Text after rule.

## IFrame

[Example](../_media/example.html ":include height=200px")

## Images

#### Inline-style

![Docsify Logo](../_media/icon.svg "This is the Docsify logo!")

#### Reference-style

![Docsify Logo][logo]

[logo]: ../_media/icon.svg "This is the Docsify logo!"

#### Light / Dark Theme

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="_media/moon.svg">
  <source media="(prefers-color-scheme: light)" srcset="_media/sun.svg">
  <img alt="BinaryTree" src="_media/sun.svg" width="122">
</picture>

## Keyboard

#### Default

<kbd>&#8963</kbd><kbd>&#8997</kbd><kbd>&#9003</kbd>

<kbd>Ctrl</kbd><kbd>Alt</kbd><kbd>Del</kbd>

<kbd>&#8963; Control</kbd><kbd>&#8997; Alt</kbd><kbd>&#9003; Delete</kbd>

#### Alternate

<kbd class="alt">&#8963</kbd><kbd class="alt">&#8997</kbd><kbd class="alt">&#9003</kbd>

<kbd class="alt">Ctrl</kbd><kbd class="alt">Alt</kbd><kbd class="alt">Del</kbd>

<kbd class="alt">&#8963; Control</kbd><kbd class="alt">&#8997; Alt</kbd><kbd class="alt">&#9003; Delete</kbd>

#### Entities

<div style="display: grid; grid-template-columns: auto auto 1fr; gap: 1em 0.2em; align-items: end;">
  <div><kbd class="alt">&uarr;</kbd></div>  <div><kbd>&uarr;</kbd></div>  <div>Arrow Up</div>
  <div><kbd class="alt">&darr;</kbd></div>  <div><kbd>&darr;</kbd></div>  <div>Arrow Down</div>
  <div><kbd class="alt">&larr;</kbd></div>  <div><kbd>&larr;</kbd></div>  <div>Arrow Left</div>
  <div><kbd class="alt">&rarr;</kbd></div>  <div><kbd>&rarr;</kbd></div>  <div>Arrow Right</div>
  <div><kbd class="alt">&#8682;</kbd></div> <div><kbd>&#8682;</kbd></div> <div>Caps Lock</div>
  <div><kbd class="alt">&#8984;</kbd></div> <div><kbd>&#8984;</kbd></div> <div>Command</div>
  <div><kbd class="alt">&#8963;</kbd></div> <div><kbd>&#8963;</kbd></div> <div>Control</div>
  <div><kbd class="alt">&#9003;</kbd></div> <div><kbd>&#9003;</kbd></div> <div>Delete</div>
  <div><kbd class="alt">&#8998;</kbd></div> <div><kbd>&#8998;</kbd></div> <div>Delete (Forward)</div>
  <div><kbd class="alt">&#8600;</kbd></div> <div><kbd>&#8600;</kbd></div> <div>End</div>
  <div><kbd class="alt">&#8996;</kbd></div> <div><kbd>&#8996;</kbd></div> <div>Enter</div>
  <div><kbd class="alt">&#9099;</kbd></div> <div><kbd>&#9099;</kbd></div> <div>Escape</div>
  <div><kbd class="alt">&#8598;</kbd></div> <div><kbd>&#8598;</kbd></div> <div>Home</div>
  <div><kbd class="alt">&#8670;</kbd></div> <div><kbd>&#8670;</kbd></div> <div>Page Up</div>
  <div><kbd class="alt">&#8671;</kbd></div> <div><kbd>&#8671;</kbd></div> <div>Page Down</div>
  <div><kbd class="alt">&#8997;</kbd></div> <div><kbd>&#8997;</kbd></div> <div>Option, Alt</div>
  <div><kbd class="alt">&#8629;</kbd></div> <div><kbd>&#8629;</kbd></div> <div>Return</div>
  <div><kbd class="alt">&#8679;</kbd></div> <div><kbd>&#8679;</kbd></div> <div>Shift</div>
  <div><kbd class="alt">&#9251;</kbd></div> <div><kbd>&#9251;</kbd></div> <div>Space</div>
  <div><kbd class="alt">&#8677;</kbd></div> <div><kbd>&#8677;</kbd></div> <div>Tab</div>
  <div><kbd class="alt">&#8676;</kbd></div> <div><kbd>&#8676;</kbd></div> <div>Tab + Shift</div>
 </div>

## 链接 :id=links

[内联链接](https://google.com)

[带标题的内联链接](https://google.com "Google")

[参考链接名称][link1]

[引用链接编号][1]

[Reference link by self]

[link1]: https://google.com
[1]: https://google.com
[Reference link by self]: https://google.com

## 列表 :id=lists

### 有序列表 :id=ordered-list

1. Ordered
2. Ordered
 1. Nested
 2. Nested (Wrapping): Similique tempora et. Voluptatem consequuntur ut. Rerum minus et sed beatae. Consequatur ut nemo laboriosam quo architecto quia qui. Corrupti aut omnis velit.
3. Ordered (Wrapping): Error minima modi rem sequi facere voluptatem. Est nihil veritatis doloribus et corporis ipsam. Pariatur eos ipsam qui odit labore est voluptatem enim. Veritatis est qui ut pariatur inventore.

### 无序列表 :id=unordered-list

- Unordered
- Unordered
 - Nested
 - Nested (Wrapping): Quia consectetur sint vel ut excepturi ipsa voluptatum suscipit hic. Ipsa error qui molestiae harum laboriosam. Rerum non amet illo voluptatem odio pariatur. Ut minus enim.
- Unordered (Wrapping): Fugiat qui tempore ratione amet repellendus repudiandae non. Rerum nisi officia enim. Itaque est alias voluptatibus id molestiae accusantium. Cupiditate sequi qui omnis sed faceere aliquid quia ut.

### 任务清单 :id=task-list

- [x] Task
- [ ] Task
 - [ ] Subtask
 - [ ] Subtask
 - [x] Subtask
- [ ] Task (Wrapping): Earum consequuntur itaque numquam sunt error omnis ipsum repudiandae. Est assumenda neque eum quia quisquam laborum beatae autem ad. Fuga fugiat perspiciatis harum quia dignissimos molestiae. Officia quo eveniet tempore modi voluptates consequatur. Eum odio adipisci labore.
 - [x] Subtask (Wrapping): Vel possimus eaque laborum. Voluptates qui debitis quaerat atque molestiae quia explicabo doloremque. Reprehenderit perspiciatis a aut impedit temporibus aut quasi quia. Incidunt sed recusandae vitae asperiores sit in.

## Output

<output data-lang="output">
  <p>Et cum fugiat nesciunt voluptates. A atque quos doloribus dolorem quo. Et dignissimos omnis nam. Recusandae voluptatem nam. Tenetur veniam et qui consequatur. Aut sequi atque fuga itaque iusto eum nihil quod iure.</p>
  <ol>
    <li>Item</li>
    <li>Item</li>
    <li>Item</li>
  </ol>
</output>

## 表格 :id=tables

### Alignment

| Left Align | Center Align | Right Align | Non&#8209;Breaking&amp;nbsp;Header |
| ---------- | :----------: | ----------: | -------------------------------------------------------------------------- |
| A1         |      A2      |          A3 | A4                                                                         |
| B1         |      B2      |          B3 | B4                                                                         |
| C1         |      C2      |          C3 | C4                                                                         |

### Headerless

|    |    |    |    |
| -- | -- | -- | -- |
| A1 | A2 | A3 | A4 |
| B1 | B2 | B3 | B4 |
| C1 | C2 | C3 | C4 |

### Scrolling

| Header                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Dicta&amp;nbsp;in&amp;nbsp;nobis&amp;nbsp;dolor&amp;nbsp;adipisci&amp;nbsp;qui.&amp;nbsp;Accusantium&amp;nbsp;voluptates&amp;nbsp;est&amp;nbsp;dolor&amp;nbsp;laboriosam&amp;nbsp;qui&amp;nbsp;voluptatibus.&amp;nbsp;Veritatis&amp;nbsp;eos&amp;nbsp;aspernatur&amp;nbsp;iusto&amp;nbsp;et&amp;nbsp;dicta&amp;nbsp;quas.&amp;nbsp;Fugit&amp;nbsp;voluptatem&amp;nbsp;dolorum&amp;nbsp;qui&amp;nbsp;quisquam.&amp;nbsp;nihil |
| Aut&amp;nbsp;praesentium&amp;nbsp;officia&amp;nbsp;aut&amp;nbsp;delectus.&amp;nbsp;Quas&amp;nbsp;atque&amp;nbsp;reprehenderit&amp;nbsp;saepe.&amp;nbsp;Et&amp;nbsp;voluptatibus&amp;nbsp;qui&amp;nbsp;dolores&amp;nbsp;rem&amp;nbsp;facere&amp;nbsp;in&amp;nbsp;dignissimos&amp;nbsp;id&amp;nbsp;aut.&amp;nbsp;Debitis&amp;nbsp;excepturi&amp;nbsp;delectus&amp;nbsp;et&amp;nbsp;quos&amp;nbsp;numquam&amp;nbsp;magnam.      |
| Sed&amp;nbsp;eum&amp;nbsp;atque&amp;nbsp;at&amp;nbsp;laborum&amp;nbsp;aut&amp;nbsp;et&amp;nbsp;repellendus&amp;nbsp;ullam&amp;nbsp;dolor.&amp;nbsp;Cupiditate&amp;nbsp;saepe&amp;nbsp;voluptatibus&amp;nbsp;odit&amp;nbsp;est&amp;nbsp;pariatur&amp;nbsp;qui.&amp;nbsp;Hic&amp;nbsp;sunt&amp;nbsp;nihil&amp;nbsp;optio&amp;nbsp;enim&amp;nbsp;eum&amp;nbsp;laudantium.&amp;nbsp;Repellendus&amp;nbsp;voluptate.              |

## Text Elements

<mark>Marked text</mark>

<pre>Preformatted text</pre>

<samp>Sample Output</samp>

<small>Small Text</small>

This is <sub>subscript</sub>

This is <sup>superscript</sup>

<ins>Underlined Text</ins>

## Text Styles

Body text

**Bold text**

_Italic text_

**_Bold and italic text_**

~~Strikethrough~~
