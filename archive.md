---
layout: page
title: 简报归档
permalink: /archive/
---

<h1>简报归档</h1>
<p class="page-subtitle">浏览所有历史简报，按年份和月份分类</p>

{% assign posts_by_year = site.posts | group_by_exp: "post", "post.date | date: '%Y'" %}

{% for year in posts_by_year %}
<div class="year-section" style="margin-bottom: 3rem;">
  <h2 style="color: #1a237e; border-bottom: 2px solid #5c6bc0; padding-bottom: 0.5rem; margin-bottom: 1.5rem;">{{ year.name }}年</h2>
  
  {% assign posts_by_month = year.items | group_by_exp: "post", "post.date | date: '%m'" %}
  
  {% for month in posts_by_month %}
    {% assign month_name = month.items[0].date | date: "%m月" %}
    <div class="month-section" style="margin-bottom: 2rem;">
      <h3 style="color: #283593; font-size: 1.25rem; margin-bottom: 1rem;">{{ month_name }}</h3>
      
      <div class="posts-grid" style="display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); gap: 1rem;">
        {% for post in month.items %}
        <div class="archive-card" style="background: white; border-radius: 8px; padding: 1.25rem; box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08); border: 1px solid #e0e0e0; transition: all 0.3s ease;">
          <h4 style="margin-bottom: 0.5rem;">
            <a href="{{ post.url | relative_url }}" style="color: #1a237e; text-decoration: none; font-size: 1.1rem;">{{ post.title }}</a>
          </h4>
          <div style="color: #666; font-size: 0.9rem; margin-bottom: 0.75rem;">
            {{ post.date | date: "%Y年%m月%d日" }}
          </div>
          <div style="margin-bottom: 1rem;">
            {% for tag in post.tags limit:2 %}
            <span style="background: #f5f7fa; color: #283593; padding: 0.2rem 0.6rem; border-radius: 12px; font-size: 0.8rem; margin-right: 0.5rem;">{{ tag }}</span>
            {% endfor %}
          </div>
          <a href="{{ post.url | relative_url }}" style="color: #5c6bc0; font-size: 0.9rem; text-decoration: none; font-weight: 500;">阅读 →</a>
        </div>
        {% endfor %}
      </div>
    </div>
  {% endfor %}
</div>
{% endfor %}

<div class="stats" style="background: #f5f7fa; padding: 1.5rem; border-radius: 8px; margin-top: 3rem;">
  <h3 style="color: #1a237e; margin-bottom: 1rem;">统计信息</h3>
  <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); gap: 1rem;">
    <div style="text-align: center;">
      <div style="font-size: 2rem; color: #1a237e; font-weight: 700;">{{ site.posts.size }}</div>
      <div style="color: #666;">总简报数</div>
    </div>
    <div style="text-align: center;">
      <div style="font-size: 2rem; color: #1a237e; font-weight: 700;">
        {% assign years = site.posts | map: "date" | map: "year" | uniq | size %}
        {{ years }}
      </div>
      <div style="color: #666;">覆盖年份</div>
    </div>
    <div style="text-align: center;">
      <div style="font-size: 2rem; color: #1a237e; font-weight: 700;">
        {% assign tags = site.posts | map: "tags" | join: ',' | split: ',' | uniq | size %}
        {{ tags }}
      </div>
      <div style="color: #666;">不同标签</div>
    </div>
    <div style="text-align: center;">
      <div style="font-size: 2rem; color: #1a237e; font-weight: 700;">每日</div>
      <div style="color: #666;">更新频率</div>
    </div>
  </div>
</div>

<style>
.archive-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.12);
}
</style>