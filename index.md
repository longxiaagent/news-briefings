---
layout: home
title: "全球新闻简报"
description: "龙厦集团每日全球新闻摘要与深度分析"
---

<div class="hero-banner" style="background: linear-gradient(135deg, #1a237e 0%, #283593 100%); color: white; padding: 4rem 2rem; text-align: center; border-radius: 12px; margin-bottom: 3rem;">
  <h1 style="font-size: 3rem; font-weight: 700; margin-bottom: 1rem;">全球新闻简报</h1>
  <p style="font-size: 1.25rem; opacity: 0.9; margin-bottom: 2rem;">龙厦集团每日全球洞察 · 为战略决策提供多维视角</p>
  <div style="display: flex; justify-content: center; gap: 1rem; flex-wrap: wrap;">
    <span style="background: rgba(255, 255, 255, 0.2); padding: 0.5rem 1rem; border-radius: 20px;">🌍 全球宏观</span>
    <span style="background: rgba(255, 255, 255, 0.2); padding: 0.5rem 1rem; border-radius: 20px;">🚀 科技产业</span>
    <span style="background: rgba(255, 255, 255, 0.2); padding: 0.5rem 1rem; border-radius: 20px;">🤖 人工智能</span>
    <span style="background: rgba(255, 255, 255, 0.2); padding: 0.5rem 1rem; border-radius: 20px;">💰 市场商业</span>
  </div>
</div>

<div class="stats" style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 1rem; margin-bottom: 3rem;">
  <div class="stat-card" style="background: white; padding: 1.5rem; border-radius: 12px; box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08); text-align: center;">
    <div style="font-size: 2rem; color: #1a237e; font-weight: 700;">{{ site.posts.size }}</div>
    <div style="color: #666;">累计简报</div>
  </div>
  <div class="stat-card" style="background: white; padding: 1.5rem; border-radius: 12px; box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08); text-align: center;">
    <div style="font-size: 2rem; color: #1a237e; font-weight: 700;">6</div>
    <div style="color: #666;">分析维度</div>
  </div>
  <div class="stat-card" style="background: white; padding: 1.5rem; border-radius: 12px; box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08); text-align: center;">
    <div style="font-size: 2rem; color: #1a237e; font-weight: 700;">每日</div>
    <div style="color: #666;">更新频率</div>
  </div>
  <div class="stat-card" style="background: white; padding: 1.5rem; border-radius: 12px; box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08); text-align: center;">
    <div style="font-size: 2rem; color: #1a237e; font-weight: 700;">09:00</div>
    <div style="color: #666;">GMT+1 发布</div>
  </div>
</div>

<h2 style="color: #1a237e; font-size: 2rem; margin-bottom: 2rem; border-bottom: 3px solid #5c6bc0; padding-bottom: 0.5rem;">📅 最新简报</h2>

{% for post in site.posts limit:5 %}
<div class="briefing-card" style="background: white; border-radius: 12px; padding: 2rem; margin-bottom: 2rem; box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08); border: 1px solid #e0e0e0; transition: all 0.3s ease;">
  <h3 style="color: #1a237e; font-size: 1.5rem; margin-bottom: 1rem;">
    <a href="{{ post.url | relative_url }}" style="color: inherit; text-decoration: none;">{{ post.title }}</a>
  </h3>
  <div style="display: flex; gap: 1rem; color: #666; font-size: 0.9rem; margin-bottom: 1rem; flex-wrap: wrap;">
    <span>📅 {{ post.date | date: "%Y年%m月%d日" }}</span>
    <span>👤 {{ post.author }}</span>
    {% for tag in post.tags limit:3 %}
    <span style="background: #f5f7fa; color: #283593; padding: 0.25rem 0.75rem; border-radius: 20px; font-size: 0.85rem;">{{ tag }}</span>
    {% endfor %}
  </div>
  <p style="color: #555; line-height: 1.6; margin-bottom: 1.5rem;">{{ post.excerpt | strip_html | truncatewords: 60 }}</p>
  <a href="{{ post.url | relative_url }}" style="display: inline-block; background: linear-gradient(135deg, #1a237e 0%, #283593 100%); color: white; padding: 0.5rem 1.5rem; border-radius: 6px; text-decoration: none; font-weight: 500; transition: all 0.3s ease;">
    阅读全文 →
  </a>
</div>
{% endfor %}

{% if site.posts.size > 5 %}
<div style="text-align: center; margin: 3rem 0;">
  <a href="/archive/" style="color: #5c6bc0; text-decoration: none; font-weight: 500; font-size: 1.1rem;">
    查看所有简报（共{{ site.posts.size }}篇） →
  </a>
</div>
{% endif %}

<div class="info-grid" style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 2rem; margin-top: 4rem;">
  <div class="info-card" style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); padding: 2rem; border-radius: 12px;">
    <h3 style="color: #1565c0; margin-bottom: 1rem; display: flex; align-items: center; gap: 0.5rem;">
      <span>🎯</span> 分析框架
    </h3>
    <ul style="color: #333; line-height: 1.6;">
      <li><strong>信息筛选</strong>：主流媒体与权威来源</li>
      <li><strong>交叉验证</strong>：多源验证确保准确性</li>
      <li><strong>结构分析</strong>：关注长期趋势与结构变化</li>
      <li><strong>意义判断</strong>：每段分析包含"为什么重要"</li>
    </ul>
  </div>
  
  <div class="info-card" style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); padding: 2rem; border-radius: 12px;">
    <h3 style="color: #7b1fa2; margin-bottom: 1rem; display: flex; align-items: center; gap: 0.5rem;">
      <span>📊</span> 覆盖领域
    </h3>
    <ul style="color: #333; line-height: 1.6;">
      <li><strong>全球宏观</strong>：地缘政治、经济政策、贸易动态</li>
      <li><strong>科技产业</strong>：技术创新、产业发展、竞争格局</li>
      <li><strong>人工智能</strong>：模型进展、应用落地、伦理监管</li>
      <li><strong>市场商业</strong>：资本流向、企业动态、市场趋势</li>
    </ul>
  </div>
  
  <div class="info-card" style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); padding: 2rem; border-radius: 12px;">
    <h3 style="color: #2e7d32; margin-bottom: 1rem; display: flex; align-items: center; gap: 0.5rem;">
      <span>⚡</span> 生成流程
    </h3>
    <ul style="color: #333; line-height: 1.6;">
      <li><strong>09:00 GMT+1</strong>：自动生成当日简报</li>
      <li><strong>多渠道分发</strong>：Telegram + GitHub网站</li>
      <li><strong>质量审查</strong>：自动化+人工双重检查</li>
      <li><strong>持续优化</strong>：基于反馈迭代改进</li>
    </ul>
  </div>
</div>

<div style="background: #f5f7fa; padding: 2rem; border-radius: 12px; margin-top: 3rem; text-align: center;">
  <h3 style="color: #1a237e; margin-bottom: 1rem;">订阅每日简报</h3>
  <p style="color: #666; margin-bottom: 1.5rem;">通过Telegram接收每日简报，或访问GitHub网站查看完整档案</p>
  <div style="display: flex; justify-content: center; gap: 1rem; flex-wrap: wrap;">
    <a href="https://t.me/your_channel" style="background: #0088cc; color: white; padding: 0.75rem 1.5rem; border-radius: 6px; text-decoration: none; font-weight: 500;">📱 Telegram频道</a>
    <a href="https://github.com/longxiaagent/news-briefings" style="background: #333; color: white; padding: 0.75rem 1.5rem; border-radius: 6px; text-decoration: none; font-weight: 500;">🐙 GitHub仓库</a>
  </div>
</div>