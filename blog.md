---
layout: default
title: Blog
---

<section class="blog-section">
    <h2>Blog Posts</h2>
    
    {% if site.posts.size > 0 %}
        <div class="posts-list">
            {% for post in site.posts %}
                <article class="post-preview">
                    <header class="post-preview-header">
                        <h3 class="post-preview-title">
                            <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
                        </h3>
                        <time class="post-preview-date" datetime="{{ post.date | date_to_xmlschema }}">
                            {{ post.date | date: "%B %d, %Y" }}
                        </time>
                    </header>
                    
                    <div class="post-preview-content">
                        {% if post.excerpt %}
                            {{ post.excerpt | markdownify | strip_html | truncatewords: 50 }}
                        {% else %}
                            {{ post.content | markdownify | strip_html | truncatewords: 50 }}
                        {% endif %}
                    </div>
                    
                    <footer class="post-preview-footer">
                        {% if post.categories.size > 0 %}
                            <div class="post-preview-categories">
                                {% for category in post.categories %}
                                    <span class="category">{{ category }}</span>
                                {% endfor %}
                            </div>
                        {% endif %}
                        <a href="{{ post.url | relative_url }}" class="read-more">Read more →</a>
                    </footer>
                </article>
            {% endfor %}
        </div>
    {% else %}
        <p class="no-posts">No blog posts yet. Check back soon!</p>
    {% endif %}
</section>