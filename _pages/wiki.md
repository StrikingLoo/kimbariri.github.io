---
layout: page
title: Kimba.RiRi's Tremendous Repository of Knowledge, Opinions and Trivia
favicon: 
---
	<h1>{{ page.title }}</h1>

   <p>
   "Your machine is a library, not a publication device. You have copies of documents in there that you control directly, that you can annotate, change, add links to, summarize, and this is because the memex is a tool to think with, not a tool to publish with." -- <a href="https://hapgood.us/2015/10/17/the-garden-and-the-stream-a-technopastoral/">Mike Caulfield</a>
</p><p>
   I encourage you to make a Pull Request to this website's GitHub project and add your own bit of trivia, interesting links or notes you keep coming back to. 
   </p>

<p>Below is a cloud with every article in this wiki. If you don't know where to start or what you're looking for, or want to know more about these notes' contents, see the garden's <a href="/wiki-articles/navigation-guide">navigation guide</a>.</p>

<div style = 'text-align:center;'>
<!-- Html Elements for Search -->
<input type="text" id="search-input" placeholder="Search my personal wiki..." style='font-size: 1.05em;text-align:center;min-width:500px;'>

<div id="search-container">
<ul id="results-container" style='list-style-type:none;'></ul>
</div>

      <h2> All Notes</h2>

	<ul class="posts">
{% assign _notes_ = site.pages | where_exp: "item" , "item.path contains 'wiki-articles' " | sort:"path" %}
{% for item in _notes_ %}
{% if item.path contains 'index' %}
{% else %}
<a href="{{ item.url }}" class="wiki-item" title="{{ item.description }}">{{item.path | split: "/" | last | remove_first: ".md" }}</a>
{% endif %}
{% endfor %}
   </ul>
   
</div>
<br/>

<p>Idea and a bit of the code were taken from <a href='https://tomcritchlow.com/wiki/'>Tom Critchlow's Digital Garden</a>. </p>

<!-- Script pointing to search-script.js -->
<script src="/assets/js/simple-jekyll-search.min.js" type="text/javascript"></script>

<!-- Configuration -->
<script>
SimpleJekyllSearch({
  searchInput: document.getElementById('search-input'),
  resultsContainer: document.getElementById('results-container'),
  json: '/search.json'
})
</script>