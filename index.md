---
intro: Hello and welcome. We've had this little patch of the internet for a while now, and it seemed about time to tidy it up. Pull up a chair.
cards:
  - icon: '&#9788;'
    title: About Us
    body: A little about who we are, where we've been, and what we get up to. Updated sporadically, as is traditional.
    link: /about.html
    link_text: Read more
  - icon: '&#9724;'
    title: Photos
    body: Albums from over the years - skiing, celebrations, travels, and the odd gathering that got slightly out of hand.
    link: /photos.html
    link_text: Browse the albums
  - icon: '&#9993;'
    title: Get in Touch
    body: If you've found your way here, you probably already know how to reach us. But just in case.
    link: /contact.html
    link_text: Contact us
  - icon: '&#9993;'
    title: This is a test card
    body: This is a test
    link: /test.html
    link_text: This is a test
home: true
layout: default
---

<section class="intro">
  <p>{{ page.intro }}</p>
</section>

<div class="cards">
{% for card in page.cards %}
  <article class="card">
    <div class="card-icon">{{ card.icon }}</div>
    <h2 class="card-title">{{ card.title }}</h2>
    <p class="card-body">{{ card.body }}</p>
    <a href="{{ card.link | relative_url }}" class="card-link">{{ card.link_text }}</a>
  </article>
{% endfor %}
</div>
