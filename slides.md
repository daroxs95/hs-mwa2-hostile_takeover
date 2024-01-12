---
theme: seriph
background: /bg.jpg
class: text-center
highlighter: shiki
lineNumbers: false
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
drawings:
  persist: false
transition: slide-left
title: Hostile Takeover
mdc: true
fonts:
  # basically the text
  sans: 'Hebo'
  # use with `font-serif` css class from windicss
  serif: 'Robot Slab'
  # for code blocks, inline code, etc.
  mono: 'Fira Code'
themeConfig:
  primary: '#ef2964'
download: true
---

# FITCE Hostile takeover

[//]: # (<p class="">Game store for the masses</p>)

<div class="abs-br m-6 flex gap-2">
  <a href="https://github.com/daroxs95/destore" target="_blank" alt="GitHub" title="Open in GitHub"
  class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://github.com/daroxs95/destore)
-->

---

# Routes

<img border="rounded" src="/routes.png" alt="">


---

# Models

<div grid="~ cols-2 gap-4">
<div>

## Users
- id
- name

</div>
<div>

## News
- id
- title
- text
- countryId

</div>
</div>

<br />

<div grid="~ cols-2 gap-4">
<div>

## Seminars
- id
- title
- text

</div>
<div>

## Speakers
- seminarId
- userId

</div>
</div>

---

# Models

<div grid="~ cols-2 gap-4">
<div>

## Countries
- id
- name

</div>
<div>

## Events
- id
- name
- countryId
- date

</div>
</div>

<div grid="~ cols-2 gap-4">
<div>

## Academies
- id
- title
- text

</div>
</div>


---

# Models
<img border="rounded" src="/models.png" alt="">


---
class: px-20
---

# Layout

### Base layout
```tsx
<app-layout showHeadline:boolean>
    <navbar />
    <hero showHeadline={showHeadline} />
    <slot /> // --> Here goes each page/route specifics 
    <partnerships-section />
    <footer />
</app-layout>
```

### Route `/`
<div grid="~ cols-2 gap-4">
<div>

```tsx
<more-information />
<academy-section>
    <online-module-li />
    ...
</academy-section>
<recent-news-section>
    <news-card />
    ...
</recent-news-section>
```

</div>
<div>

```
recentNews: Array<{
    slug: string
    country: string
    title: string
    description: string
    publishedAt: Date
}>
onlineModules: Array<{
    slug: string
    title: string
    subtitle: string
}>
```

</div>
</div>

---
class: px-20
---

# Layout

### Route `/news`
<div grid="~ cols-2 gap-4">
<div>

```tsx
<news-section>
  <pagination-section />
  <news-card />
  <news-card />
  ...
</news-section>
```

</div>
<div>

```
news: Array<{
    slug: string
    country: string
    title: string
    description: string
    publishedAt: string
}>
```

</div>
</div>

### Route `/academy`
<div grid="~ cols-2 gap-4">
<div>

```tsx
<main-content>
  <online-module-card />
  ...
</main-content>
<instructors-aside>
  <instructor-card />
  ...
</instructors-aside>
```

</div>
<div>

```
instructors: Array<{
    name: string
    description: string
    contactLink: string
    image: string
}>
onlineModules: Array<{
    slug: string
    title: string
    subtitle: string
    headline: string
}>
```

</div>
</div>

---
class: px-20
---

# Layout


### Route `/academy/seminar/:slug`
<div grid="~ cols-2 gap-4">
<div>

```tsx
<main-content>
  <seminar-card />
  <speakers-list>
    <speaker-card />
    <speaker-card />
    ...
  </speakers-list>
</main-content>
<aside />
```

</div>
<div>

```
module: {
    title: string
    subtitle: string
    headline: string
    description: string
    publishedAt: string
}
instructors: Array<{
    name: string
    description: string
    contactLink: string
    image: string
}>
```

</div>
</div>

---
class: px-20
---

# Layout

### Route `/events`
<div grid="~ cols-2 gap-4">
<div>

```tsx
<upcoming-events>
  <event-card />
  <event-card />
  ...
</upcoming-events>
<past-events>
  <event-card />
  <event-card />
  ...
</past-events>
```

</div>
<div>

```
upcomingEvents: Array<{
    date: Date
    country: string
    title: string
}>
pastEvents: Array<{
    date: Date
    country: string
    title: string
}>
```

</div>
</div>

### Route `/contact-us`
<div grid="~ cols-2 gap-4">
<div>

```tsx
<main-content>
    ...
</main-content>
<countries-aside />

```

</div>
<div>

```
countries: Array<{
    name: string
    slug: string
}>
```

</div>
</div>

---
class: px-20
---

# Layout

### Route `/member-countries`
<div grid="~ cols-2 gap-4">
<div>

```tsx
<main-content>
    ...
</main-content>
<countries-aside />
```

</div>
<div>

```
countries: Array<{
    name: string
    slug: string
}>
```

</div>
</div>

---
class: px-20
---

# Layout

### Route `/countries/:slug`
<div grid="~ cols-2 gap-4">
<div>

```tsx
<main-content>
    <country-card />
    <upcoming-events>
        <event-card />
        <event-card />
        ...
    </upcoming-events>
    <upcoming-news>
        <news-card />
        <news-card />
        ...
    </upcoming-news>
</main-content>
<countries-info-aside />
```

</div>
<div>

```
country: {
    name: string
    headline: string
    flagImage: string
    description: string
}
upcomingEventsInCountry: Array<{
    date: Date
    title: string
}>
upcomingNewsInCountry: Array<{
    title: string
    slug: string
    description: string
    publishedAt: Date
}>
```

</div>
</div>

---
class: px-20
---

# Layout

<div grid="~ cols-2 gap-4">
<div>

### Route `/about`

```tsx
<index-aside />
<main-content>
    ...
</main-content>
```

</div>
<div>

### Route `/structure`

```tsx
<index-aside />
<main-content>
    ...
</main-content>
```

</div>
</div>

<div grid="~ cols-2 gap-4">
<div>

### Route `/history`

```tsx
<index-aside />
<main-content>
    ...
</main-content>
```

</div>
</div>

---
layout: center
class: text-center
---
# Thanks 👋

