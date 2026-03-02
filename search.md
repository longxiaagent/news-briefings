---
layout: page
title: 搜索简报
permalink: /search/
---

<h1>搜索简报</h1>
<p class="page-subtitle">使用关键词搜索历史简报内容</p>

<div id="search-container" style="max-width: 800px; margin: 2rem auto;">
  <input type="text" id="search-input" placeholder="输入关键词，如：AI、美联储、供应链..." style="width: 100%; padding: 1rem; font-size: 1rem; border: 2px solid #5c6bc0; border-radius: 8px; margin-bottom: 1rem;">
  <div id="results-container"></div>
</div>

<script>
// 获取所有简报数据
{% assign all_posts = site.posts %}
var posts = [
  {% for post in all_posts %}
  {
    title: "{{ post.title | escape }}",
    url: "{{ post.url | relative_url }}",
    date: "{{ post.date | date: '%Y年%m月%d日' }}",
    excerpt: "{{ post.excerpt | strip_html | escape }}",
    tags: [{% for tag in post.tags %}"{{ tag | escape }}"{% unless forloop.last %},{% endunless %}{% endfor %}],
    content: "{{ post.content | strip_html | escape | remove: '"' }}"
  }{% unless forloop.last %},{% endunless %}
  {% endfor %}
];

// 简单搜索功能
function performSearch(query) {
  var results = [];
  var queryLower = query.toLowerCase();
  
  posts.forEach(function(post) {
    var score = 0;
    
    // 标题匹配（最高权重）
    if (post.title.toLowerCase().includes(queryLower)) {
      score += 100;
    }
    
    // 标签匹配（中等权重）
    post.tags.forEach(function(tag) {
      if (tag.toLowerCase().includes(queryLower)) {
        score += 50;
      }
    });
    
    // 内容匹配（较低权重）
    if (post.content.toLowerCase().includes(queryLower)) {
      score += 10;
    }
    
    // 摘要匹配
    if (post.excerpt.toLowerCase().includes(queryLower)) {
      score += 20;
    }
    
    if (score > 0) {
      results.push({
        post: post,
        score: score
      });
    }
  });
  
  // 按分数排序
  results.sort(function(a, b) {
    return b.score - a.score;
  });
  
  return results;
}

// 显示结果
function displayResults(results) {
  var container = document.getElementById('results-container');
  
  if (results.length === 0) {
    container.innerHTML = '<div style="text-align: center; padding: 2rem; color: #666;">没有找到相关简报</div>';
    return;
  }
  
  var html = '<div style="margin-top: 2rem;"><h3 style="color: #1a237e; margin-bottom: 1rem;">找到 ' + results.length + ' 个结果</h3>';
  
  results.forEach(function(result) {
    var post = result.post;
    html += `
      <div class="search-result" style="background: white; border-radius: 8px; padding: 1.5rem; margin-bottom: 1rem; box-shadow: 0 2px 8px rgba(0,0,0,0.08); border: 1px solid #e0e0e0;">
        <h4 style="margin-bottom: 0.5rem;">
          <a href="${post.url}" style="color: #1a237e; text-decoration: none;">${post.title}</a>
        </h4>
        <div style="color: #666; font-size: 0.9rem; margin-bottom: 0.75rem;">
          📅 ${post.date}
          ${post.tags.length > 0 ? ' | 🏷️ ' + post.tags.slice(0, 3).join(', ') : ''}
        </div>
        <p style="color: #555; line-height: 1.5;">${post.excerpt.substring(0, 150)}...</p>
        <a href="${post.url}" style="color: #5c6bc0; text-decoration: none; font-weight: 500;">阅读全文 →</a>
      </div>
    `;
  });
  
  html += '</div>';
  container.innerHTML = html;
}

// 事件监听
document.getElementById('search-input').addEventListener('input', function(e) {
  var query = e.target.value.trim();
  
  if (query.length === 0) {
    document.getElementById('results-container').innerHTML = '';
    return;
  }
  
  if (query.length < 2) {
    document.getElementById('results-container').innerHTML = 
      '<div style="text-align: center; padding: 1rem; color: #666;">请输入至少2个字符</div>';
    return;
  }
  
  var results = performSearch(query);
  displayResults(results);
});

// 搜索示例
var examples = ['AI', '美联储', '供应链', '监管', '芯片'];
var examplesHtml = '<div style="margin-top: 1rem; color: #666; font-size: 0.9rem;">搜索示例: ';
examples.forEach(function(example, index) {
  examplesHtml += '<span style="cursor: pointer; background: #f5f7fa; color: #283593; padding: 0.25rem 0.5rem; border-radius: 4px; margin: 0 0.25rem; font-size: 0.85rem;" onclick="document.getElementById(\'search-input\').value=\'' + example + '\'; document.getElementById(\'search-input\').dispatchEvent(new Event(\'input\'));">' + example + '</span>';
});
examplesHtml += '</div>';

document.getElementById('search-container').innerHTML += examplesHtml;
</script>

<style>
.search-result:hover {
  transform: translateY(-1px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.12);
}

#search-input:focus {
  outline: none;
  box-shadow: 0 0 0 3px rgba(92, 107, 192, 0.2);
}
</style>