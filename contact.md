---
layout: default
title: Contact
permalink: /contact/
---

## Get in Touch

Have a question, a suggestion, or a FOSS project you think deserves coverage? Fill out the form below and it will go straight to the Fossil Project inbox.

<style>
  .contact-form {
    margin-top: 2rem;
  }

  .form-group {
    margin-bottom: 1.5rem;
  }

  .form-group label {
    display: block;
    font-size: 0.85rem;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    color: #7a7060;
    margin-bottom: 0.5rem;
  }

  .form-group input,
  .form-group textarea {
    width: 100%;
    background: #161410;
    border: 1px solid #2a2620;
    border-radius: 3px;
    padding: 0.75rem 1rem;
    color: #c8c0b0;
    font-family: 'Source Serif 4', Georgia, serif;
    font-size: 1rem;
    transition: border-color 0.2s;
  }

  .form-group input:focus,
  .form-group textarea:focus {
    outline: none;
    border-color: #e8821a;
  }

  .form-group textarea {
    height: 150px;
    resize: vertical;
  }

  .submit-btn {
    background: transparent;
    border: 1px solid #e8821a;
    color: #e8821a;
    padding: 0.75rem 2rem;
    font-family: 'Source Serif 4', Georgia, serif;
    font-size: 0.9rem;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    cursor: pointer;
    transition: all 0.2s;
    border-radius: 3px;
  }

  .submit-btn:hover {
    background: #e8821a;
    color: #0e0d0b;
  }
</style>

<form class="contact-form" action="https://formspree.io/f/xyknlbyg" method="POST">
  <div class="form-group">
    <label for="name">Name</label>
    <input type="text" id="name" name="name" placeholder="Your name" required>
  </div>
  <div class="form-group">
    <label for="email">Email</label>
    <input type="email" id="email" name="email" placeholder="your@email.com" required>
  </div>
  <div class="form-group">
    <label for="subject">Subject</label>
    <input type="text" id="subject" name="subject" placeholder="What is this about?">
  </div>
  <div class="form-group">
    <label for="message">Message</label>
    <textarea id="message" name="message" placeholder="Your message here..." required></textarea>
  </div>
  <button type="submit" class="submit-btn">Send Message</button>
</form>
