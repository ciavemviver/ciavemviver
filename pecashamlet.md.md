---
layout: default
title: Hamlet
peca_id: hamlet
---

{% assign peca = site.data.pecas | where: "id", page.peca_id | first %}

<div class="peca-detalhes">
  <div>
    <img src="/assets/images/{{ peca.imagem }}" alt="{{ peca.titulo }}">
  </div>
  
  <div>
    <h1>{{ peca.titulo }}</h1>
    <p class="meta">{{ peca.autor }} | {{ peca.ano }} | {{ peca.categoria }}</p>
    
    <h2>Sinopse</h2>
    <p>{{ peca.resumo }}</p>
    
    <h2>Detalhes</h2>
    <ul>
      <li><strong>Duração:</strong> {{ peca.duracao }}</li>
      <li><strong>Personagens:</strong></li>
      <ul>
        {% for personagem in peca.personagens %}
          <li>{{ personagem }}</li>
        {% endfor %}
      </ul>
    </ul>
    
    <h2>Resenhas Relacionadas</h2>
    <ul>
      {% for post in site.posts %}
        {% if post.peca == page.peca_id %}
          <li>
            <a href="{{ post.url }}">{{ post.title }}</a>
            <span>({{ post.date | date: "%d/%m/%Y" }})</span>
          </li>
        {% endif %}
      {% endfor %}
    </ul>
  </div>
</div>