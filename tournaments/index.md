---
title: Tournois
layout: tournament
permalink: /tournois/
---

# Tournois

Bienvenue sur la page des tournois ! Ici, vous trouverez toutes les informations concernant les tournois organisés par le club.

## Classements

{% for ranking in site.data.db.tournament_ranking.entries %}
<div class="ranking-section">
  <h2>Classement Poule {{ forloop.index }}</h2>
  <table class="ranking-table">
    <thead>
      <tr>
        <th>Équipe</th>
        <th>Points</th>
        <th>Victoires</th>
      </tr>
    </thead>
    <tbody>
      {% for team in ranking %}
      <tr>
        <td>{{ team.teamName }}</td>
        <td>{{ team.points }}</td>
        <td>{{ team.wins }}</td>
      </tr>
      {% endfor %}
    </tbody>
  </table>
</div>
{% endfor %}

## Matchs à venir

{% for match in site.data.db.tournament_matches.entries %}
{% if match.matchDate > site.time %}
<div class="match-card">
  <h3>{{ match.team1 }} vs {{ match.team2 }}</h3>
  <p>Date : {{ match.matchDate }}</p>
  <p>Tour : {{ match.round }}</p>
</div>
{% endif %}
{% endfor %}

## Résultats

{% for result in site.data.db.tournament_results.entries %}
<div class="result-card">
  <h3>{{ result.team1 }} vs {{ result.team2 }}</h3>
  <p>Date : {{ result.matchDate }}</p>
  <p>Score : {{ result.score1 }} - {{ result.score2 }}</p>
</div>
{% endfor %}
