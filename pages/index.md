---
layout: default
title: Grumpy Barrel
permalink: /
---

<section class="hero">
  <video class="hero-video" autoplay muted loop playsinline>
    <source src="{{ '/assets/video/hero-reel.mp4' | relative_url }}" type="video/mp4">
  </video>
  <div class="hero-overlay"></div>
  <div class="container">
    <h1 class="hero-title">Grumpy Barrel</h1>
    <p class="hero-tagline">Small films with grit, heart, and a clean finish.</p>
    <p class="hero-intro">We're a video production studio based in Singapore. We make commercials, brand films, event recaps, and short-form content for brands that care how things look.</p>
    <div class="hero-cta">
      <a href="{{ '/projects/' | relative_url }}" class="btn btn-primary">See Our Work</a>
      <a href="{{ '/contact/' | relative_url }}" class="btn btn-secondary">Get in Touch</a>
    </div>
  </div>
</section>

<section class="clients">
  <div class="container">
    <p class="clients-label">Brands we've worked with</p>
    <div class="clients-list">
      <span>Bvlgari</span>
      <span>Tiffany &amp; Co.</span>
      <span>SK-II</span>
      <span>Harper's Bazaar</span>
      <span>Singtel</span>
      <span>KFC</span>
      <span>Charles &amp; Keith</span>
      <span>Sentosa</span>
      <span>Adidas</span>
    </div>
  </div>
</section>

<section class="featured-work">
  <div class="container">
    <h2 class="section-title">Our Featured Projects</h2>
    <div class="project-grid">
      {% assign featured = site.projects | where: "featured", true %}
      {% for project in featured %}
      <article class="project-card">
        <a href="{{ project.url | relative_url }}" class="project-card-link">
          {% if project.thumbnail %}
          <div class="project-card-thumb">
            <img src="{{ project.thumbnail }}" alt="{{ project.title }}">
          </div>
          {% elsif project.image %}
          <div class="project-card-thumb">
            <img src="{{ project.image | relative_url }}" alt="{{ project.title }}">
          </div>
          {% else %}
          <div class="project-card-thumb project-card-thumb--placeholder">
            <span>{{ project.title }}</span>
          </div>
          {% endif %}
          <div class="project-card-body">
            <h3 class="project-card-title">{{ project.title }}</h3>
            {% if project.client %}<p class="project-card-client">{{ project.client }}</p>{% endif %}
            {% if project.category %}<p class="project-card-category">{{ project.category }}</p>{% endif %}
            {% if project.description %}<p class="project-card-desc">{{ project.description | truncate: 100 }}</p>{% endif %}
          </div>
        </a>
      </article>
      {% endfor %}
    </div>
    <div class="section-cta">
      <a href="{{ '/projects/' | relative_url }}" class="btn btn-secondary">View All Work</a>
    </div>
  </div>
</section>

<section class="services">
  <div class="container">
    <h2 class="section-title">What We Do</h2>
    <div class="services-grid">
      <div class="service-item">
        <h3>Commercials</h3>
        <p>Product and campaign films that hold attention and earn trust.</p>
      </div>
      <div class="service-item">
        <h3>Brand Films</h3>
        <p>Longer-form stories that go beyond the product and build a point of view.</p>
      </div>
      <div class="service-item">
        <h3>Event Recaps</h3>
        <p>Fast, accurate capture of what happened — without looking like everyone else's recap.</p>
      </div>
      <div class="service-item">
        <h3>Fashion &amp; Beauty</h3>
        <p>Clean, considered visuals for brands where aesthetics matter most.</p>
      </div>
      <div class="service-item">
        <h3>Social Video</h3>
        <p>Short-form content that still looks like something, rather than something thrown together.</p>
      </div>
      <div class="service-item">
        <h3>Documentary &amp; Story Work</h3>
        <p>Real people, real places, properly shot. For brands willing to trust the subject.</p>
      </div>
    </div>
  </div>
</section>

<section class="about-teaser">
  <div class="container">
    <div class="about-teaser-inner">
      <h2>The studio</h2>
      <p>Grumpy Barrel is a small production house. Not an agency, not a collective — just a tight crew that takes the work seriously. We're based in Singapore and we keep things honest: no inflated quotes, no over-promising, no filler footage.</p>
      <a href="{{ '/about/' | relative_url }}" class="btn btn-secondary">About Us</a>
    </div>
  </div>
</section>

<section class="contact-cta">
  <div class="container">
    <div class="contact-cta-inner">
      <h2>Got a project in mind?</h2>
      <p>Tell us what you're working on. We'll give you a straight answer on whether we're the right fit.</p>
      <a href="{{ '/contact/' | relative_url }}" class="btn btn-primary">Get in Touch</a>
    </div>
  </div>
</section>
