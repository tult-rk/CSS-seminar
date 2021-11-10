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
handle: tult
introImage: >-
  /images/funny.png
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
handle: tult
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
handle: tult
layout: new-section
sectionImage: /images/css-in-react.png
---

# Common ways to style React component

Summarize some common ways to use CSS in React application briefly

---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: tult
---

# Inline-style

```ts {all|5-8|all}
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

---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: tult
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

```ts {all|8|all}
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
handle: tult
---

# CSS-in-JS

```ts {all|4-7|9|all}
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
handle: tult
layout: cover
---


# CSS Module

```ts {all|2|6|all}
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
handle: tult
layout: cover
---

# Questions

### 1. How CSS module works differently with CSS-in-CSS
### 2. What CSS-in-JS does under the hood?

---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: tult
layout: center
---

## Why we need so much approaches for only style components?

---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: tult
layout: new-section
sectionImage: /images/css.png
---

# Problem with CSS-in-CSS


---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: tult
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
handle: tult
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
handle: tult
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
handle: tult
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
handle: tult
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
handle: tult
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
handle: tult
layout: new-section
sectionImage: /images/tailwind.png
---

# Introduce TailwindCSS

Introduce CSS framework CSS and let's see how many problems it solves


---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: tult
layout: center
---


# What is tailwindCSS?


---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: tult
layout: cover
---

## TailwindCSS is a utility-first CSS framework. 

- It contains a bunch of predefined classes
- Think about it like boostrap but of course..... with differences.


```ts
<ul class="space-y-4">
  <li>
    <div class="w-64 h-3 bg-gradient-to-br from-fuchsia-500 to-purple-600"></div>
  </li>
  <li>
    <div class="w-56 h-3 bg-gradient-to-br from-fuchsia-500 to-purple-600"></div>
  </li>
  <li>
    <div class="w-48 h-3 bg-gradient-to-br from-fuchsia-500 to-purple-600"></div>
  </li>
  <li>
    <div class="w-40 h-3 bg-gradient-to-br from-fuchsia-500 to-purple-600"></div>
  </li>
</ul>

```

<!-- Bao gồm rất nhiều các predefine classes được chia thành các categories như typography,sizing, border, .... -->


---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: tult
layout: center
---


# Advantages of using tailwindCSS


---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: tult
layout: cover
---

# Free in design 
- Allow you to style components at low level
- Easy to customize
- Re-useability


<!-- 
1. Tailwind không tạo sẵn các component với một đống các props như material ui hoặc ant design mà nó cung cấp các 
predefined classes ở mức low-level. Eg padding-left: 2rem; -> pl-8. Developer cảm giác tự do để customize hơn 
Khi làm việc với tailwind, developers cần phải nghĩ tới việc code làm sao để có thể tái sử dụng component này về sau,
các thẻ HTML này sẽ có những attributes, event  nào thay vì ghi nhớ các props của một component làm sẵn  -->

<!-- 
1. Nhiều người tiếp xúc với các thư viện như material ui, ... trước khi thành thạo HTML, DOM thành ra khi cần phải thao tác trực
tiếp với DOM thì sẽ gặp chút ít khó khăn hơn vì chưa thông thạo -->

---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: tult
layout: cover
---

# System characteristic

- Comes with handy predefined classes 
- Do not increase the CSS file size so much


<!-- 2. Tailwind được tạo bởi các predefined classes, nghĩa là khi ta cần style một component, ta biết được các styling ta cần sử dụng đã 
được định nghĩa trước -> Lấy ra dùng. Không cần viết cái mới như CSS thông thường -> Giảm độ lớn của file CSS.  

GIỐNG BOOSTRAP -> CẦN CHỈ RA ĐIỂM KHÁC BIỆT
 -->




<!-- [Documentations](https://sli.dev) / [GitHub Repo](https://github.com/slidevjs/slidev) -->


---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: tult
layout: cover
---

# Tiny in production 

- Tailwind automatically removes all unusued CSS when building for production (*)
- Most tailwind projects ship less than 10kB of CSS to the client 


<!-- Fun fact: Size của boostrap size sau khi minifize là trên 100kB tùy từng phiên bản  -->


---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: tult
layout: center
---

# Some notices that good to know


---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: tult
layout: cover
---

# Adding base styles for HTML element 
You can adding default style for HTML element

```ts
// style.css
@tailwind base;
@tailwind components;
@tailwind utilities;

@layer base {
  a {
    @apply text-blue-600 hover:underline;
  }
  h1 {
    @apply text-2xl font-semibold;
  }
}
```


---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: tult
layout: cover
---

# Extracting component's style

You can extracting style of component that is used repeatedly

```ts
// style.css
@tailwind base;
@tailwind components;
@tailwind utilities;

@layer components {
  .btn-blue {
    @apply px-4 py-2 rounded-lg bg-blue-500 hover:bg-blue-600;
  }
}
```



---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: tult
layout: cover
---

# Extracting utilities

You also can add new utilities for reuse between many components

```ts
// style.css
@tailwind base;
@tailwind components;
@tailwind utilities;

@layer utilities {
  .center-content {
    @apply absolute top-1/2 left-1/2 translate-x-1/2 -translate-y-1/2
  }
}
```


<!-- Chú ý là cú pháp của component và utilities là tương đối giống nhau nhưng ta nên phân biệt rõ. Component là các style sẽ được áp dụng cụ thể cho một 
component nào đó. Trong khi utilities có thể được sử dụng giữa các component vs mục đích tạo hiệu ứng -->


---
logoHeader: /logo.png
website: https://rikkeisoft.com
handle: tult
layout: cover
---

# Just-in-Time mode 

- Only combine the code that needed

```ts
  // tailwind.config.js

module.exports = {
   mode: 'jit',
    purge: [
      // ...
    ],
    theme: {
      // ...
    }
    // ...
  }

```

<!-- Show the impacts of Just-in-Time mode -->
<!-- Chỉ combine các classes đang sử dụng. Y hệt như khi chạy ở production mode -> Tiết kiệm thời gian combine  -->