# Omnifood 项目总结
https://omnifood-oknos.netlify.app/
## 7 steps to build a website

1. Define

   - **WHO** the website is for
   - **WHAT** the website if for (business goal / user goal)
   - **Target audience** (be more specific if possible)

2. Plan

   - **Website content**
     - images, videos, text, logos, icons
   - **Sections** each page needs
     - Navigation (header)
     - Hero section
     - Featured-in + How it works
     - Meals
     - Testimonials + Features
     - Pricing
     - Call-to-action
   - **Website personalities**
     - Minimalist / Simple
     - Serious / Elegant
     - Neutral / Pain
     - Startup / Upbeat
     - Playful / Fun
     - Calm / Peaceful
     - Bold / Confident

3. Sketch Layouts and Component Ideas

   - Think about **components** and use them in **layout patterns**
   - Sketches
   - Iterative process

4. Design and Build

   - HTML and CSS
   - Visual styles

5. Test and Optimize

   - Make sure websites work well in all major **browsers**
     - caniuse
   - Different mobile **devices**
     - queries.css
   - **Optimize all images**
     - squoosh
     - change the size of the image
   - Run the **Lighthouse** performance
   - SEO

6. Launch

   - Upload website files to hosting platform
     - Netlify
   - Choose and buy a domain name

7. Maintain and update

## HTML and CSS details

1. 记录各个属性以协调网页

--- 01 **Typography**

- Font sizes (px)

  10 / 12 / 14 / 16 / 18 / 20 / 24 / 30 / 36 / 44 / 52 / 62 / 74 / 86 / 98

- Font weights

  - Default: 400
  - Medium: 500
  - Semi-bold: 600
  - Bold: 700

- Line heights

  - Default: 1
  - Small: 1.05
  - Medium: 1.2
  - Paragraph default: 1.6
  - Large: 1.8

- Letter spacing
  - 0.5px
  - 0.75px

--- 02 **COLORS**

- Primary: #e67e22
- Tints:

  - #fdf2e9
  - #fae5d3
  - #eb984e

- Shades:

  - #cf711f
  - #45260a

- Accents:
- Greys

  - #888
  - #767676 (lightest grey allowed on - #fff)
  - #6f6f6f (lightest grey allowed on - #fdf2e9)
  - #555
  - #333

--- 05 **SHADOWS**

0 2.4rem 4.8rem rgba(0, 0, 0, 0.075);

--- 06 BORDER-RADIUS

- Default: 9px
- Medium: 11px

--- 07 **WHITESPACE**

- Spacing system (px)

  2 / 4 / 8 / 12 / 16 / 24 / 32 / 48 / 64 / 80 / 96 / 128 px

2. 新建 general.css 确定总体默认基本特征

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  font-size: 62.5%;
}

body {
  font-family: sans-serif;
  color: #333;
  font-weight: 400;
  line-height: 1.8;
  font-size: 1.8rem;
}

h1 {
  font-size: 5rem;
  letter-spacing: -0.1rem;
  line-height: 1.1;
  margin-bottom: 3.6rem;
  font-weight: bold;
}

h2 {
  font-size: 4.4rem;
  letter-spacing: -0.1rem;
  font-weight: bold;
  margin-bottom: 8rem;
}

h3 {
  font-size: 2.8rem;
  font-weight: bold;
  margin-bottom: 3rem;
}
```

3. 减少代码重复，在 general.css 里可加入

```css
container {
  max-width: 120rem;
  margin: 0 auto;
  padding: 9.6rem 4.8rem;
}

.grid {
  display: grid;
}

.grid--2--cols {
  grid-template-columns: repeat(2, 1fr);
}

.grid--3--cols {
  grid-template-columns: repeat(3, 1fr);
}

.grid--4--cols {
  grid-template-columns: 18rem 1fr 1fr 1fr;
  gap: 3.2rem;
}
```

4. 在手机的图片后加两个 ⚪

```css
.step-img-box::before,
.step-img-box::after {
  content: "";
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.step-img-box::before {
  width: 60%;
  padding-bottom: 60%;
  border-radius: 50%;
  background-color: #fdf2e9;
  z-index: -2;
}

.step-img-box::after {
  width: 45%;
  padding-bottom: 45%;
  border-radius: 50%;
  background-color: #fae5d3;
  z-index: -1;
}
```

5. Meal 卡片碰到上移效果

```css
.meal-box {
  box-shadow: 0 2.4rem 4.8rem rgba(0, 0, 0, 0.075);
  border-radius: 1rem;
  transition: all 0.35s;
}

.meal-box:hover {
  transform: translate(0, -1.2rem);
  box-shadow: 0 3.2rem 6.4rem rgba(0, 0, 0, 0.05);
}
```

6. 图片碰到放大效果

```css
.gallery-img {
  display: block;
  transition: all 0.5s;
  width: 100%;
}

.gallery-img-box {
  overflow: hidden;
}

.gallery-img:hover {
  transform: scale(1.1);
}
```

7. Call-to-action 的输入信息收集

```html
<form class="grid grid--2--cols cat-input-grid" name="sign-up" netlify>
  <div class="cat-input-box">
    <label for="full-name">Full Name</label>
    <input
      id="full-name"
      type="text"
      placeholder="Lana Del Rey"
      name="full-name"
      required
    />
  </div>
  <div class="cat-input-box">
    <label for="email">Email</label>
    <input
      id="email"
      type="email"
      placeholder="me@example.com"
      name="email"
      required
    />
  </div>
  <div class="cat-input-box">
    <label for="where">Where did you hear from us? </label>
    <select id="where" name="where">
      <option value="">Please choose one option:</option>
      <option value="youtube">YouTube video</option>
      <option value="friends">Friends and family</option>
      <option value="facebook">Facebook ad</option>
      <option value="podcast">Podcast</option>
      <option value="others">Others</option>
    </select>
  </div>
</form>
```

8. Mobile Navigation

```css
.mobile-icon[name="close-outline"] {
  display: none;
}

header {
  position: relative;
}

nav {
  background-color: rgba(255, 255, 255, 0.8);
  backdrop-filter: blur(5px);
  position: absolute;
  height: 100vh;
  width: 100%;
  left: 0;
  top: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  transform: translateX(100%);
  transition: all 0.5s ease-in;

  /* Hide navigation */
  /* Allows NO transitions at all */
  /* display: none; */

  /* 1) Hide it visually */
  opacity: 0;

  /* 2) Make it unaccessible to mouse and keyboard */
  pointer-events: none;

  /* 3) Hide it from screen readers */
  visibility: hidden;
}

nav ul {
  display: flex;
  font-size: 2.4rem;
  flex-direction: column;
  gap: 3.2rem;
}

nav .btn {
  font-size: 2.4rem !important;
}

.nav-open nav {
  opacity: 1;
  pointer-events: auto;
  visibility: visible;
  transform: translateX(0);
}

.nav-open .mobile-icon[name="close-outline"] {
  display: block;
}

.nav-open .mobile-icon[name="menu-outline"] {
  display: none;
}
```

9. JavaScript 部分

```javascript
///////////////////////////////////////////////////////////
// Set current year
const yearEl = document.querySelector(".year");
const currentYear = new Date().getFullYear();
yearEl.textContent = currentYear;

///////////////////////////////////////////////////////////
// Make mobile navigation work

const btnNavEl = document.querySelector(".mobile-btn");
const headerEl = document.querySelector("header");

btnNavEl.addEventListener("click", function () {
  headerEl.classList.toggle("nav-open");
});

///////////////////////////////////////////////////////////
// Smooth scrolling animation

const allLinks = document.querySelectorAll("a:link");

allLinks.forEach(function (link) {
  link.addEventListener("click", function (e) {
    e.preventDefault();
    const href = link.getAttribute("href");

    // Scroll back to top
    if (href === "#")
      window.scrollTo({
        top: 0,
        behavior: "smooth",
      });

    // Scroll to other links
    if (href !== "#" && href.startsWith("#")) {
      const sectionEl = document.querySelector(href);
      sectionEl.scrollIntoView({ behavior: "smooth" });
    }

    // Close mobile naviagtion
    if (link.classList.contains("main-nav-link"))
      headerEl.classList.toggle("nav-open");
  });
});

///////////////////////////////////////////////////////////
Sticky navigation

const sectionHeroEl = document.querySelector(".section-hero");

const obs = new IntersectionObserver(
  function (entries) {
    const ent = entries[0];
    console.log(ent);

    if (ent.isIntersecting === false) {
      document.body.classList.add("sticky");
    }

    if (ent.isIntersecting === true) {
      document.body.classList.remove("sticky");
    }
  },
  {
    // In the viewport
    root: null,
    threshold: 0,
    rootMargin: "-80px",
  }
);
obs.observe(sectionHeroEl);

///////////////////////////////////////////////////////////
// Fixing flexbox gap property missing in some Safari versions
function checkFlexGap() {
  var flex = document.createElement("div");
  flex.style.display = "flex";
  flex.style.flexDirection = "column";
  flex.style.rowGap = "1px";

  flex.appendChild(document.createElement("div"));
  flex.appendChild(document.createElement("div"));

  document.body.appendChild(flex);
  var isSupported = flex.scrollHeight === 1;
  flex.parentNode.removeChild(flex);
  console.log(isSupported);

  if (!isSupported) document.body.classList.add("no-flexbox-gap");
}
checkFlexGap();

// https://unpkg.com/smoothscroll-polyfill@0.4.4/dist/smoothscroll.min.js

/*
.no-flexbox-gap .main-nav-list li:not(:last-child) {
  margin-right: 4.8rem;
}

```
