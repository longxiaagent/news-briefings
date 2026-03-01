---
layout: home
title: "全球新闻简报"
description: "每日全球新闻摘要与深度分析"
---

<div class="hero">
  <h1>全球新闻简报</h1>
  <p class="hero-subtitle">龙厦集团每日全球洞察</p>
  <p>整合全球政治、经济、科技、环境等多元领域的新闻摘要与深度分析，为战略决策提供多维视角参考。</p>
</div>

## 📅 最新简报

{% for post in site.posts limit:10 %}
<div class="briefing-card">
  <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
  <div class="card-meta">
    <span>📅 {{ post.date | date: "%Y年%m月%d日" }}</span>
    <span>🏷️ {{ post.tags | join: ', ' }}</span>
  </div>
  <p>{{ post.excerpt | strip_html | truncatewords: 50 }}</p>
  <a href="{{ post.url | relative_url }}" class="read-more">阅读全文 →</a>
</div>
{% endfor %}

## 📊 简报分类

<div class="categories">
  <div class="category">
    <h4>🌍 全球政治</h4>
    <p>地缘政治、国际关系、政策动态</p>
  </div>
  <div class="category">
    <h4>💰 经济金融</h4>
    <p>宏观经济、金融市场、贸易政策</p>
  </div>
  <div class="category">
    <h4>🚀 科技创新</h4>
    <p>AI进展、技术突破、产业趋势</p>
  </div>
  <div class="category">
    <h4>🌱 环境气候</h4>
    <p>气候变化、可持续发展、能源转型</p>
  </div>
</div>

<div class="about-section">
  <h3>关于本简报</h3>
  <p>本简报由龙厦集团战略分析团队每日整理，旨在提供全面、客观的全球新闻摘要与深度分析。内容涵盖政治、经济、科技、环境等多元领域，为集团战略决策提供参考。</p>
</div>