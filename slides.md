---
theme: ./themes/rikkei
colorSchema: dark
highlighter: prism
aspectRatio: '16/9'
canvasWidth: 980
monaco: dev
lineNumbers: true
download: false
titleTemplate: '%s - Rikkei Corp'
layout: intro
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: hnq90
introImage: >-
  https://uilogos.co/img/logomark/earth.png
info: |
  ## Rikkei - Slidev template
  Template for Rikkei's presentations
title: Presentation Title
---

# CSS at Scale

Problems with CSS, introduce tailwindCSS framework

<!--
Write notes here
-->

---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: hnq90
layout: table-contents
gradientColors: ['#b70000', '#dc2626']
---

# Table of Contents

- 📝 **Section 1** - Common ways to style React components
- 🎨 **Section 2** - Problems with ancient CSS (CSS-in-CSS)
- 🧑‍💻 **Section 3** - Introduce tailwindCSS

---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: hnq90
layout: new-section
sectionImage: https://uilogos.co/img/logomark/muszica.png
---

# Common ways to style React component

Summarize some common ways to use CSS in React application briefly

---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: hnq90
---

# Inline-style

```ts {all}
import React from 'react'

const Button = () => {
	return (
		<button style={{
			color: 'red',
			padding: '10px 20px',
		}}>
			Simple button
		</button>
	)
}

export default Button

```
<!-- 
### H3

|     |     |
| --- | --- |
| ABC | DEF |
| ABC | DEF |
| ABC | DEF |
| ABC | DEF | -->

---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: hnq90
layout: cover
---

# CSS-in-CSS

```css {all}
// style.css
.button {
	color: 'red';
	padding: '10px, 20px';
	...
}
```

```ts {all|2|1-6|9|all}
// Button.tsx
import React from 'react'
import './style.css'


const Button = () => {
	return (
		<button className="button">Simple button</button>
	)
}

export default Button
```

---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: hnq90
---

# CSS-in-JS

```ts 
import React from "react"
import styled from "styled-components"

const ButtonStyled = styled.button`
      color: 'red';
      padding: '10px 20px';
    `
const Button = (props) => (
	<ButtonStyled {...props}>Simple button</ButtonStyled>
```

---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: hnq90
layout: cover
---


# CSS Module

```ts 
import React from 'react'
import styles from './styles.css'

const Button = () => {
	return (
		<button className={styles.button}>Simple button</button>
	)
}

export default Button
```

---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: hnq90
layout: cover
---

# Questions

### 1. How CSS module works differently with CSS-in-CSS
### 2. What CSS-in-JS does under the hood?

---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: hnq90
layout: center
---

## Why we need so much approaches for only style components?

---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: hnq90
layout: new-section
sectionImage: https://uilogos.co/img/logomark/muszica.png
---

# Problem with CSS-in-CSS


---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: hnq90
layout: cover
---


# DEMO

Let's look at a simple demo first.
https://codesandbox.io/s/css-seminar-hkv96?file=/src/index.tsx

<!-- Trước tiên cùng xem qua một demo đơn giản để chứng minh cho các câu hỏi đã trả lơì ở phía trên và một vài vấn đề với CSS-in-CSS
mà chúng ta sẽ trình bày phía sau -->

---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: hnq90
layout: cover
---


# Global namespace
1. All selectors are global
2. We tend to create new style instead of trying to re-used


<!-- 1. Trong một dự án có cả chục, trăm developers. Việc nghĩ ra tên có ý nghĩa cho một selectors là khó khăn và không cẩn thận có thể dẫ đến trùng tên
2. Khi bắt đầu style theo một design mới hoặc code một màn mới, ta có xu hướng là tạo style mới để sử dụng cho nhanh. Đỡ mất công kiếm xem là chỗ khác đã có nhưng style tương tự chưa -> Dẫn đến file style sheet nhanh chóng phình to ra -->


---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: hnq90
layout: cover
---


# Non-deterministic resolution
1. All selectors can be applied to any components despite the location's of component and CSS file.


<!-- 
  Bất cứ selectors nào cũng có thể được sử dụng mà không cần import một cách rõ ràng vào component -> Xảy ra trường hợp vô ý sử dụng sai selectors
 -->


---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: hnq90
layout: cover
---


# Dead code elimination
1. Cannot make sure whether a selectors only affects on only one component.


<!-- 
  Khi design thay đổi hoặc một component không cần sử dụng nữa -> Cần remove các selectors không cần dùng nữa
  Nhưng không đảm bảo được là selectors này chỉ ảnh hưởng tới style của 1 component -> Không xóa bậy được 
  Muốn chắc chắn thì phải kiểm tra -> mất thời gian
 -->



---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: hnq90
layout: cover
---


# Minification
1. Because it's hard to remove unused selectors. Which leads to harding reduce the CSS file's size.


<!-- 
  Không giảm được size của file CSS thì tốc độ tải trang sẽ giảm
-->


---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: hnq90
layout: cover
---


# Sharing styling
1. Hard to reused predefined styling


<!-- 
  Vì style của các member trong team viết hoàn toàn không có tính hệ thống. Để có thể biết được style như design yêu cầu này đã có sẵn chưa 
  để tìm mà sử dụng lại. Nếu có tìm thì cũng mất thời gian
 -->



---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: hnq90
layout: new-section
sectionImage: https://uilogos.co/img/logomark/muszica.png
---

# Introduce TailwindCSS

Introduce CSS framework CSS and let's see how many problems it solves


<!-- [Documentations](https://sli.dev) / [GitHub Repo](https://github.com/slidevjs/slidev) -->
