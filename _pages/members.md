---
permalink: /members/
title: "Team Members"
author_profile: true
layout: archive
---

Welcome to the ViVi Team Members page!

## Team Members

### Founder
<div class="team-group">
  {% assign leaders = site.data.authors | where: "role", "founder" %}
  {% for member in leaders %}
    <div class="team-member" style="display:inline-block;text-align:center;margin:16px;">
      <img src="/images/members/{{ member.avatar }}" alt="{{ member.name }}" style="width:120px;height:120px;border-radius:50%;object-fit:cover;box-shadow:0 2px 8px #ccc;" />
      <div style="margin-top:8px;font-weight:bold;">{{ member.name }}</div>
      {% if member.position %}<div style="font-size:0.95em;color:#666;">{{ member.position }}</div>{% endif %}
    </div>
  {% endfor %}
</div>

### Advisory Board
<div class="team-group">
  {% assign advisors = site.data.authors | where: "role", "advisory board" %}
  {% for member in advisors %}
    <div class="team-member" style="display:inline-block;text-align:center;margin:16px;">
      <img src="/images/{{ member.avatar }}" alt="{{ member.name }}" style="width:120px;height:120px;border-radius:50%;object-fit:cover;box-shadow:0 2px 8px #ccc;" />
      <div style="margin-top:8px;font-weight:bold;">{{ member.name }}</div>
      {% if member.position %}<div style="font-size:0.95em;color:#666;">{{ member.position }}</div>{% endif %}
    </div>
  {% endfor %}
</div>

### Research Leader
<div class="team-group">
  {% assign leaders = site.data.authors | where: "role", "research leader" %}
  {% for member in leaders %}
    <div class="team-member" style="display:inline-block;text-align:center;margin:16px;">
      <img src="/images/{{ member.avatar }}" alt="{{ member.name }}" style="width:120px;height:120px;border-radius:50%;object-fit:cover;box-shadow:0 2px 8px #ccc;" />
      <div style="margin-top:8px;font-weight:bold;">{{ member.name }}</div>
      {% if member.position %}<div style="font-size:0.95em;color:#666;">{{ member.position }}</div>{% endif %}
    </div>
  {% endfor %}
</div>

### Members
<div class="team-group">
  {% assign members = site.data.authors | where: "role", "member" %}
  {% for member in members %}
    <div class="team-member" style="display:inline-block;text-align:center;margin:16px;">
      <img src="/images/{{ member.avatar }}" alt="{{ member.name }}" style="width:120px;height:120px;border-radius:50%;object-fit:cover;box-shadow:0 2px 8px #ccc;" />
      <div style="margin-top:8px;font-weight:bold;">{{ member.name }}</div>
      {% if member.position %}<div style="font-size:0.95em;color:#666;">{{ member.position }}</div>{% endif %}
    </div>
  {% endfor %}
</div>

### Collaborators
<div class="team-group">
  {% assign collaborators = site.data.authors | where: "role", "collaborator" %}
  {% for member in collaborators %}
    <div class="team-member" style="display:inline-block;text-align:center;margin:16px;">
      <img src="/images/{{ member.avatar }}" alt="{{ member.name }}" style="width:120px;height:120px;border-radius:50%;object-fit:cover;box-shadow:0 2px 8px #ccc;" />
      <div style="margin-top:8px;font-weight:bold;">{{ member.name }}</div>
      {% if member.position %}<div style="font-size:0.95em;color:#666;">{{ member.position }}</div>{% endif %}
    </div>
  {% endfor %}
</div>
