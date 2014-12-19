---
layout: default
---

What if you could augment HTML5's current set of elements with your own? Well, as it turns out, you can. **mdoml** is an experiment in creating custom HTML elements based on today's most common interface design components.

Is this a bad idea? Maybe, but that depends on how you look at it. Sure, it doesn't validate, but it does create a more approachable component-based design system. No more rules around writing classes a certain way—just create the components.

Learn more, suggest changes, or report bugs via [the GitHub repo](https://github.com/mdo/mdoml).

---

## Contents

* Will be replaced with the ToC, excluding the "Contents" header
{:toc}

---

## Things to know

* This isn't about Web Components. This is specifically about writing non-compliant, custom HTML tags as a shorthand.
* This is for all modern browsers, and IE9+. **IE8 and below need help initializing custom HTML elements.** [Consider using the HTML5 shiv.](https://github.com/aFarkas/html5shiv)
* By design, custom HTML elements have no assumed semantics. For example, you gain obvious browser-backed advantages by using a `<form>` over a `<custom-form>` element. **Don't replace semantic elements.**
* Because of that lack of browser-assumed semantics, theoretically there's no disadvantage with custom elements for many components. Instead of a `<div>` for dropdowns, `<dropdown>`s could be used with no discernible impact to accessibility.
* **Custom elements are inline by default.** If you need a block-level element, you'll need to specify that in the CSS.
* This aims to use HTML elements and attributes wherever possible. Classes, IDs, and more are purposefully avoided.
* Accessibility-wise, you'll still need to include ARIA roles where appropriate. I've attempted to do so in a few of the examples below.

---

## Form groups

The custom `<formgroup>` element automatically aligns immediate `<label>`s and their `<input>`s to create hanging checkboxes or radios. Text wrapping, stacking of inputs (without adding `display: block`), and alignment comes automatically.

<formgroup>
  <label for="radio1">
    <input type="radio" id="radio1" name="radios" checked>
    Radio input
  </label>
  <label for="radio2">
    <input type="radio" id="radio2" name="radios">
    Another radio input
  </label>
</formgroup>

{% highlight html %}
<formgroup>
  <label for="radio1">
    <input type="radio" id="radio1" name="radios" checked>
    Radio input
  </label>
  <label for="radio2">
    <input type="radio" id="radio2" name="radios">
    Another radio input
  </label>
</formgroup>
{% endhighlight %}

<formgroup>
  <label for="checkbox1">
    <input type="checkbox" id="checkbox1" checked>
    Checkbox input
  </label>
  <label for="checkbox2">
    <input type="checkbox" id="checkbox2">
    Checkbox input with a super long string of text that can wrap to a second line to show the hanging input.
  </label>
</formgroup>

{% highlight html %}
<formgroup>
  <label for="checkbox1">
    <input type="checkbox" id="checkbox1" checked>
    Checkbox input
  </label>
  <label for="checkbox2">
    <input type="checkbox" id="checkbox2">
    Checkbox input with a super long string of text that can wrap to a second line to show the hanging input.
  </label>
</formgroup>
{% endhighlight %}

---

## Grids

Uses custom `<row>`s and `<column>`s to create a basic grid layout. Columns are then sized with a `cols` attribute.

<row>
  <column cols="1">1</column>
  <column cols="1">1</column>
  <column cols="1">1</column>
  <column cols="1">1</column>
  <column cols="1">1</column>
  <column cols="1">1</column>
  <column cols="1">1</column>
  <column cols="1">1</column>
  <column cols="1">1</column>
  <column cols="1">1</column>
  <column cols="1">1</column>
  <column cols="1">1</column>
</row>

<row>
  <column cols="2">2</column>
  <column cols="2">2</column>
  <column cols="2">2</column>
  <column cols="2">2</column>
  <column cols="2">2</column>
  <column cols="2">2</column>
</row>

<row>
  <column cols="3">3</column>
  <column cols="3">3</column>
  <column cols="3">3</column>
  <column cols="3">3</column>
</row>

<row>
  <column cols="4">4</column>
  <column cols="4">4</column>
  <column cols="4">4</column>
</row>

<row>
  <column cols="5">5</column>
  <column cols="5">5</column>
  <column cols="2">2</column>
</row>

<row>
  <column cols="6">6</column>
  <column cols="6">6</column>
</row>

<row>
  <column cols="7">7</column>
  <column cols="5">5</column>
</row>

<row>
  <column cols="8">8</column>
  <column cols="4">4</column>
</row>

<row>
  <column cols="9">9</column>
  <column cols="3">3</column>
</row>

<row>
  <column cols="10">10</column>
  <column cols="2">2</column>
</row>

<row>
  <column cols="11">11</column>
  <column cols="1">1</column>
</row>

{% highlight html %}
<row>
  <column cols="4">4</column>
  <column cols="4">4</column>
  <column cols="4">4</column>
</row>
{% endhighlight %}

---

## Alerts

Use custom `<alert>`s as messages for warnings, errors, status confirmation, and the like.

<alert role="alert">
  <p>This is an alert with some text in it.</p>
</alert>

<alert is="info" role="alert">
  <p>This is an alert with some text in it.</p>
</alert>

<alert is="warning" role="alert">
  <p>This is an alert with some text in it.</p>
</alert>

<alert is="danger" role="alert">
  <p>This is an alert with some text in it.</p>
</alert>

{% highlight html %}
<alert role="alert">...</alert>
<alert is="info" role="alert">...</alert>
<alert is="warning" role="alert">...</alert>
<alert is="danger" role="alert">...</alert>
{% endhighlight %}

---

## Dropdowns

Contextual menus for buttons and more. Built with a custom `<dropdown>` element and several `<button>` elements as the dropdown actions. Using `<button>`s gives us incredibly ease of use for disabled, hover, and active states.

<div>
<button type="button" id="dropdown-toggle1" active>
  Dropdown button
</button>
<dropdown role="menu" aria-labelledby="dropdown-toggle1">
  <button type="button" disabled>Cut</button>
  <button type="button" disabled>Copy</button>
  <button type="button">Paste</button>
  <hr>
  <button type="button">Spelling and Grammar...</button>
  <hr>
  <button type="button">Inspect Element</button>
</dropdown>
</div>

{% highlight html %}
<button type="button" id="dropdown-toggle" active>
  Dropdown button
</button>
<dropdown role="menu" aria-labelledby="dropdown-toggle">
  <button type="button" disabled>Cut</button>
  <button type="button" disabled>Copy</button>
  <button type="button">Paste</button>
  <hr>
  <button type="button">Spelling and Grammar...</button>
  <hr>
  <button type="button">Inspect Element</button>
</dropdown>
{% endhighlight %}

The contents of a `<dropdown>` could also be customized to include things other than pure `<button>` actions:

<div>
<button type="button" id="dropdown-toggle2" active>
  Dropdown button
</button>
<dropdown role="menu" aria-labelledby="dropdown-toggle2">
  <form>
    <input type="text" placeholder="Search">
  </form>
  <hr>
  <button type="button">United States of America</button>
  <button type="button">United Kingdom</button>
  <hr>
  <button type="button">Canada</button>
  <button type="button">France</button>
  <button type="button">India</button>
  <button type="button">Mexico</button>
</dropdown>
</div>

{% highlight html %}
<dropdown role="menu" aria-labelledby="dropdown-toggle">
  <form>
    <input type="text" placeholder="Search">
  </form>
  <hr>
  <button type="button">United States of America</button>
  <button type="button">United Kingdom</button>
  <hr>
  <button type="button">Canada</button>
  <button type="button">France</button>
  <button type="button">India</button>
  <button type="button">Mexico</button>
</dropdown>
{% endhighlight %}

---

## Combo buttons

Use a custom `<combo-button>` to tether a series of related buttons. This relies on us resetting nearly all the default `<button>` styles, but the controls afforded via disabled, hover, and active states is quite compelling—and easy to style.

<combo-button role="group" aria-label="Combo button">
  <button type="button">Button</button>
  <button type="button">Button</button>
</combo-button>

{% highlight html %}
<combo-button role="group" aria-label="Combo button">
  <button type="button">Button</button>
  <button type="button">Button</button>
</combo-button>
{% endhighlight %}

<combo-button role="group" aria-label="Combo button with disabled button">
  <button type="button" disabled>Disabled</button>
  <button type="button">Button</button>
  <button type="button" active>Active</button>
</combo-button>

{% highlight html %}
<combo-button role="group" aria-label="Combo button with disabled button">
  <button type="button" disabled>Disabled</button>
  <button type="button">Button</button>
  <button type="button" active>Active</button>
</combo-button>
{% endhighlight %}

---

## Breadcrumb

Use the custom `<breadcrumb>` element to show the current path to a particular page. Structurally, it's quite familiar to `<nav>` elements. Theoretically, its contents could be generated based on the page's URL structure or something similar.

<breadcrumb>
  <a href="#">Home</a>
  <a href="#">Subfolder</a>
  <a href="#">Subfolder</a>
  <a>Page</a>
</breadcrumb>

{% highlight html %}
<breadcrumb>
  <a href="#">Home</a>
  <a href="#">Subfolder</a>
  <a href="#">Subfolder</a>
  <a>Page</a>
</breadcrumb>
{% endhighlight %}

---

## Does it work?

Yes, but beyond that I'm not sure where to take something like this. I'm super intrigued and I could totally see myself building things this way in the future. Something about it feels right. Performance is probably a concern though, at least compared to a pure class-driven system (e.g., `.dropdown` over `<dropdown>`).

My ultimate goal for things like this—and popular front-end frameworks—is that these kind of ideas could influence the future changes to the HTML and CSS specs. That sounds a bit lofty, but one never knows.
