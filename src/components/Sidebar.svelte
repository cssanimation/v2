<script>
  export let metadata
</script>

<style>
  .shorter aside {
    padding-top: 4.5em;
  }
</style>

<aside class="post-aside three columns">
  {#if metadata.demo_url}
    <section class="demo-link">
      <a href={metadata.demo_url} class="button primary-button">Demo</a>
    </section>
  {/if}
  <section class="sidebar-email-signup">
    <h4>CSS Animation Weekly</h4>
    <form
      action="//hop.us7.list-manage.com/subscribe/post?u=07ab661c8a6f6b3ec4c98c791&id=169820d65d"
      method="post"
      class="validate"
      target="_blank"
      novalidate>
      <input
        type="email"
        value=""
        placeholder="Your email"
        name="EMAIL"
        class="email" />
      <div style="position: absolute; left: -5000px;">
        <input
          type="text"
          name="b_07ab661c8a6f6b3ec4c98c791_7daf5f7db7"
          value="" />
      </div>
      <input type="submit" value="Subscribe" name="subscribe" class="button" />
      <p>
        Weekly tutorials and inspiration in your inbox. Sign up now to get your
        FREE book, CSS Animation 101!
      </p>
    </form>
  </section>
  <!--{#if metadata.translator}
        <section class="translator">
          <h3>Translation Info</h3>
          <p>This article translated by <a href="{post.translator_link}">{{ post.translator }}</a>. (<a href="/{{ post.url | split: '/' | last }}/">See original</a>)</p>
        </section>

      {% elsif post.translators}
          <section class="translator">
            <h3>Translation Info</h3>
            <p>This article translated by:
              <ul>
                {% for translator in post.translators}
                  <li><a href="{{ translator.url }}">{{ translator.name }}</a></li>
                {% endfor}
              </ul>
            (<a href="{{ post.english_version }}">See original</a>)</p>
          </section>
      {:else}

        {#if post.source}
          <section class="translations" style="padding-top: 2em">
            <h3>Translations</h3>
            <p class="translation-message">CSS Animation articles are translated by our community - and you can too!</p>
            {% for article in site.data.translations}
              {#if post.url == article.url}
                <ul>
                {% for translation in article.translations}
                  {#if translation.language}

                    <li><a href="/{{ translation.iso }}{{post.url}}" hreflang="{{ translation.iso }}">{{ translation.language }}</a></li>
                  {/if}
                {% endfor}
                </ul>
              {/if}
            {% endfor}
              <p class="translate"><a class="button" href="https://getnative.me/?ref=cssanimation&amp;lang=en&amp;url={{site.url}}{{post.url}}&amp;sourceURL={{post.source}}&amp;title={{ post.title | cgi_escape }}&amp;format=markdown-yaml-frontmatter">Translate this article</a></p>
              <p class="powered-by">Powered by <img src="/images/getnative.png" alt="native - Community powered translations"></p>
          </section>
        {/if}

      {/if}
      -->
</aside>
