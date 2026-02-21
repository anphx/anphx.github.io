---
layout: post
title: "Developing a Gallery Page with Pure CSS Masonry and Jekyll"
date: 2025-02-09 18:45:00 +0200
categories: jekyll css gallery
image: "/images/pure-css-masonry-layout-with-flexbo.png"
tags: [techno]
featured: yes
---

Creating a visually appealing gallery page can enhance the user experience on your website. In this tutorial, we'll walk through the steps to develop a gallery page using pure CSS masonry and Jekyll, head to [Captures](/captures/) for inspiration.

#### Prerequisites

Before we start, ensure you have the following:

- A Jekyll project set up.
- Basic knowledge of HTML, CSS, and Liquid templating.

#### 1. Create the Gallery Page

First, create a new file named `captures.html` in the `_pages` directory of your Jekyll project. Add the following front matter and HTML structure:

```liquid
---
layout: gallery
title: Photo Captures
permalink: /captures/
---
<div class="row" data-masonry='{"percentPosition": true }'>
  {% assign galleryImages = site.static_files | where: "layout", "gallery" %}
  {% for image in galleryImages limit:4 %}
    <div class="col-sm-6 col-lg-3 p-2">
      <div class="card m-0 p-0 border-0">
        <img
          src="{{ image.path }}"
          alt="{{ image.name }}"
          class="card-img-top" />
      </div>
    </div>
  {% endfor %}
</div>

```

This code sets up a gallery page with a masonry layout. The data-masonry attribute is used to enable the masonry layout with percentage-based positioning.

#### 2. Add custom CSS for your Masonry Layout

For example, pen your main CSS file (e.g., main.css) and add the following styles:

```css
/_ Masonry CSS _/ .row {
  display: flex;
  flex-wrap: wrap;
  margin-left: -10px;
  margin-right: -10px;
}

.col-sm-6,
.col-lg-3 {
  padding-left: 10px;
  padding-right: 10px;
}

.card {
  margin-bottom: 20px;
}

.card-img-top {
  width: 100%;
  height: auto;
  display: block;
}
```

These styles ensure that the images are displayed in a masonry layout with proper spacing and alignment.

#### 3. Add Images to the Gallery

To add images to your gallery, place them in the assets/images directory (or any other directory you prefer). To help with filtering images in a specific folder, you can add extra information for the front matter in `_config.yml`

For example, create an image file example.jpg with the layout front matter:

```yml
default:
  - scope:
      path: "images/gallery"
    values:
      layout: "gallery"
```

#### 4. Build and Serve Your Jekyll Site

Finally, build and serve your Jekyll site to see the gallery in action. Run the following command in your terminal:

```bash

jekyll serve

```

Navigate to _http://localhost:4000/captures/_ to view your gallery page.

In this tutorial, we've created a gallery page with a pure CSS masonry layout. By following these steps, you can easily set up a visually appealing gallery page for your website. Feel free to customize the styles and layout to match your design preferences.

> Happy coding!

References:

- [Work with Static Files in Jekyll](https://jekyllrb.com/docs/static-files/)
- [Bootstrap and Masonry](https://getbootstrap.com/docs/5.0/examples/masonry/)
