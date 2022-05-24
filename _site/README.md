
## What is this?

A digital garden using a custom version of `simply-jekyll`, notenote.link's template, meewgumi's greenweb template, and optimised for integration with [Obsidian](https://obsidian.md). It is more oriented on note-taking and aims to help myself build a nice knowledge base (or ramdom things) that can scale with time. Another inspiration that I applied from is Johngrib's wiki (https://github.com/johngrib/johngrib-jekyll-skeleton) 

**Demo is here: [kimbariri.github.io](https://kimbariri.github.io)**

For the reference that I got from notenote.link' template, look at [arboretum.link](https://www.arboretum.link/). Build time is approx. 15 seconds, FYI.


![screenshot](/assets/img/screenshot.png)

## What is different?

- Markdown is fully-compatible with Obsidian (including Latex delimiters!)
- There are now only notes (no blog posts).
- There are cosmetic changes (ADHD-friendly code highlighting, larger font, larger page)
- Code is now correctly indented
- Wikilinks, but also alt-text wikilinks (with transclusion!) are usable.

## How do I use this?

Another inspiration from Meewgumi's template is here (https://megu.space/) For further explanation, refer to Meewgumi's guide here (https://garden.megu.space/)

Follow the [How to setup this site](https://notenote.link/notes/how-to-setup-this-site) guide, written by [raghuveerdotnet](https://github.com/raghuveerdotnet) and then adapted for this fork.

If you want to use it with Github Pages, it is possible, [please read this](https://github.com/Maxence-L/notenote.link/issues/5#issuecomment-762508069).

## How can I participate?

Open an issue to share feedback or propose features. Star the repo if you like it! 🌟

## How do I customize this for my needs?

Things to modify to make it yours:

- Meta content in [\_layouts/post.html](_layouts/post.html):
    ```html
    <meta content="My linked notebook" property="og:site_name"/>
    ```
- The favicon and profile are here: [assets/img/](assets/img/)
    ```
- You may want to change the copyright in [\_includes/footer.html](_includes/footer.html):
   ```html
   <p id="copyright-notice">Licence MIT</p>
   ```

## How do I remove the "seasons" feature for the notes?

Delete what's inside [\_includes/feed.html](_includes/feed.html) and replace it with:

```liquid
{%- if page.permalink == "/" -%}
    {%- for item in site.notes -%}
        <div class="feed-title-excerpt-block disable-select" data-url="{{site.url}}{{item.url}}">
            <a href="{{ item.url }}" style="text-decoration: none; color: #555555;">
            {%- if item.status == "Ongoing" or item.status == "ongoing" -%}
                <ul style="padding-left: 20px; margin-top: 20px;" class="tags">
                    <li style="padding: 0 5px; border-radius: 10px;" class="tag"><b>Status: </b>{{item.status | capitalize }}</li>
                </ul>
                <p style="margin-top: 0px;" class="feed-title">{{ item.title }}</p>
            {%- else -%}
                <p class="feed-title">{{ item.title }}</p>
            {%- endif -%}
                <p class="feed-excerpt">{{ item.content | strip_html | strip | escape | truncate: 200}}</p>
            </a>
        </div>
    {%- endfor -%}
{%- endif -%}
````

On command-line, you can run `bundle exec jekyll serve` then go to `localhost:4000` to check the result.