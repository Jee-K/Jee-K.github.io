---
layout: page
permalink: /repositories/
title: repositories
description: Selected GitHub profiles and repositories.
nav: true
nav_order: 4
---

<style>
  .github-card-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 1rem;
    margin: 1rem 0 2rem;
  }

  .github-card {
    display: flex;
    align-items: center;
    gap: 1rem;
    min-height: 120px;
    padding: 1.25rem;
    color: var(--global-text-color);
    background: var(--global-card-bg-color, var(--global-bg-color));
    border: 1px solid var(--global-divider-color);
    border-radius: 0.5rem;
    transition:
      border-color 0.2s ease,
      transform 0.2s ease,
      box-shadow 0.2s ease;
  }

  .github-card:hover {
    color: var(--global-text-color);
    text-decoration: none;
    border-color: var(--global-theme-color);
    box-shadow: 0 0.25rem 0.75rem rgba(0, 0, 0, 0.1);
    transform: translateY(-2px);
  }

  .github-card-icon {
    flex: 0 0 auto;
    color: var(--global-theme-color);
    font-size: 2rem;
  }

  .github-card-content {
    min-width: 0;
  }

  .github-card-label {
    display: block;
    margin-bottom: 0.25rem;
    color: var(--global-text-color-light, var(--global-text-color));
    font-size: 0.8rem;
    text-transform: uppercase;
    letter-spacing: 0.04em;
  }

  .github-card-name {
    display: block;
    overflow-wrap: anywhere;
    color: var(--global-theme-color);
    font-size: 1.1rem;
    font-weight: 700;
  }

  .github-card-action {
    display: block;
    margin-top: 0.4rem;
    color: var(--global-text-color-light, var(--global-text-color));
    font-size: 0.9rem;
  }
</style>

{% if site.data.repositories.github_users %}

## GitHub Profile

<div class="github-card-grid">
  {% for user in site.data.repositories.github_users %}
    <a
      class="github-card"
      href="https://github.com/{{ user }}"
      target="_blank"
      rel="noopener noreferrer"
      aria-label="View {{ user }} on GitHub"
    >
      <i class="fa-brands fa-github github-card-icon" aria-hidden="true"></i>
      <span class="github-card-content">
        <span class="github-card-label">GitHub profile</span>
        <span class="github-card-name">@{{ user }}</span>
        <span class="github-card-action">View profile</span>
      </span>
    </a>
  {% endfor %}
</div>
{% endif %}

{% if site.data.repositories.github_repos %}

## GitHub Repositories

<div class="github-card-grid">
  {% for repo in site.data.repositories.github_repos %}
    {% assign repo_parts = repo | split: "/" %}
    {% assign repo_owner = repo_parts | first %}
    {% assign repo_name = repo_parts | last %}
    <a
      class="github-card"
      href="https://github.com/{{ repo }}"
      target="_blank"
      rel="noopener noreferrer"
      aria-label="View the {{ repo_name }} repository on GitHub"
    >
      <i class="fa-brands fa-github github-card-icon" aria-hidden="true"></i>
      <span class="github-card-content">
        <span class="github-card-label">{{ repo_owner }}</span>
        <span class="github-card-name">{{ repo_name }}</span>
        <span class="github-card-action">View repository</span>
      </span>
    </a>
  {% endfor %}
</div>
{% endif %}
