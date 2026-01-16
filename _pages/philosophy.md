---
layout: single
title: "Lab Philosophy and Culture"
permalink: /philosophy/
---

The Greene Research Lab cultivates a collaborative and supportive atmosphere where trainees are encouraged to grow as scientists, leaders, and individuals. The lab prioritizes both physical and intellectual safety, ensuring that all members feel comfortable asking questions, experimenting, and learning from mistakes. Diversity and inclusivity are central values, welcoming individuals from all backgrounds and recognizing the importance of different perspectives in scientific research. Integrity and transparency are also key, with a strong emphasis on ethical research practices, open data-sharing, and meticulous documentation.

Trainees are given the opportunity to take initiative in their projects while benefiting from a structured mentorship system, where experienced lab members guide and support newer students. This peer-mentor model fosters a sense of responsibility and community, helping students develop technical expertise, time management skills, and effective scientific communication. Regular meetings, open communication through Slack, and digital collaboration tools ensure research stays on track. While independence is encouraged, the lab also prioritizes student well-being, supporting a healthy balance between academic and personal commitments. This blend of structured mentorship and intellectual freedom allows students to develop confidence in their scientific abilities and thrive in their research. 

For more information please read our [lab compact](https://www.egreenelab.org/philosophy/#our-lab-compact).

<script>
  function toggleFullScreen(button) {
    var embedDiv = button.parentElement;
    if (!embedDiv.classList.contains('expanded')) {
      // OPENING
      var placeholder = document.createElement('div');
      placeholder.id = 'placeholder-temp';
      placeholder.style.display = 'none';
      embedDiv.parentNode.insertBefore(placeholder, embedDiv);
      embedDiv.setAttribute('data-placeholder-id', 'placeholder-temp');

      document.body.appendChild(embedDiv);

      setTimeout(function() {
        embedDiv.classList.add('expanded');
        document.body.style.overflow = 'hidden'; 
        button.innerText = '❌ Close Fullscreen';
      }, 10);
    } else {
      // CLOSING
      embedDiv.classList.remove('expanded');
      document.body.style.overflow = ''; 
      button.innerText = '🔍 Expand / Zoom';

      var placeholderId = embedDiv.getAttribute('data-placeholder-id');
      var placeholder = document.getElementById(placeholderId);
      if (placeholder) {
        placeholder.parentNode.insertBefore(embedDiv, placeholder);
        placeholder.remove(); 
        embedDiv.removeAttribute('data-placeholder-id');
      }
    }
  }
</script>

<style>
  .philosophy-entry {
    clear: both; 
    margin-bottom: 50px; 
    overflow: hidden;
  }

  /* This ensures that when you link to the ID, it doesn't get hidden behind a fixed header */
  h2[id] {
    scroll-margin-top: 60px;
  }

  /* Embed / Zoom Styles */
  .lab-compact-embed { transition: all 0.3s ease; position: relative; background: #f8f9fa; }
  .lab-compact-embed.expanded {
    position: fixed !important; top: 0 !important; left: 0 !important;
    width: 100vw !important; height: 100vh !important;
    z-index: 2147483647 !important; margin: 0 !important; padding: 20px !important;
    background: #ffffff !important; display: flex; flex-direction: column;
    box-sizing: border-box; overflow-y: auto; 
  }
  .lab-compact-embed.expanded iframe, 
  .lab-compact-embed.expanded object, 
  .lab-compact-embed.expanded embed { width: 100%; flex-grow: 1; min-height: 80vh; }
</style>

{% assign interests = site.philosophy | sort: "index" %}

{% for interest in interests %}

<div class="philosophy-entry">

  <h2 id="{{ interest.name | slugify }}" style="margin-top: 0;">
    {{ interest.name }}
  </h2>

  {% assign parity = interest.index | modulo:2 %}
  {% if parity == 0 %}{% assign alignment = "right" %}{% else %}{% assign alignment = "left" %}{% endif %}

  {% if interest.image %}
  <img src="{{ interest.image }}" 
       alt="{{ interest.image_alt }}" 
       style="float: {{ alignment }}; 
              width: 100%; 
              max-height: 500px; 
              object-fit: cover; 
              margin: 0 {% if alignment == 'left' %}1.5em 1em 0{% else %}0 1em 1.5em{% endif %}; 
              border-radius: 8px; 
              box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
  {% endif %}

  <div class="content">
    {{ interest.content | markdownify }}
  </div>

  {% if interest.type == "compact" %}
  <div class="lab-compact-embed" style="clear: both; width: 100%; margin-top: 20px; padding: 20px; background: #f8f9fa; border: 1px solid #dee2e6; border-radius: 8px;">
    
    <button onclick="toggleFullScreen(this)" 
            style="display: block; margin-bottom: 10px; padding: 8px 15px; cursor: pointer; border: 1px solid #ccc; background: white; border-radius: 4px; font-weight: bold;">
      🔍 Expand / Zoom
    </button>

    {{ interest.embed_code }}
    
  </div>
  {% endif %}

</div>
{% endfor %}
