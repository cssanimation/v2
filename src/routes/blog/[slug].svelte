<script context="module">
  export async function preload({ params }) {
    const res = await this.fetch(`blog/${params.slug}.json`)
    return res.ok ? { post: await res.json() } : this.error(404, 'Not found')
  }
</script>

<script>
  export let post
</script>

<style>
  .post-header {
    font-size: 16px;
    background-color: darken(#fff, 20%);
    height: 26em;
    overflow: hidden;
    position: relative;
  }

  .post-header.shorter {
    background: none;
    height: 64px;
  }

  .post-header nav {
    padding: 1em 2em;
  }

  .shorter aside {
    padding-top: 4.5em;
  }

  .logo {
    position: absolute;
    left: 1em;
    top: 1em;
    width: 100px;
    z-index: 10;
  }

  .demo {
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
  }

  h2,
  h3,
  h4,
  h5 {
    margin-top: 4rem;
  }

  /* Right to left overrides */
  .rtl h1,
  .rtl h2,
  .rtl h3,
  .rtl h4,
  .rtl h5,
  .rtl p {
    direction: rtl;
    unicode-bidi: embed;
  }
  .rtl img {
    display: block;
    margin: 0 0 0 0;
  }
  .rtl pre {
    margin: 2em 0;
  }
  .rtl .demo-container {
    margin: 2em 0 2em auto;
  }

  .rtl .post-footer h1,
  .rtl .post-footer h2,
  .rtl .post-footer h3,
  .rtl .post-footer h4,
  .rtl .post-footer h5,
  .rtl .post-footer p {
    direction: ltr;
  }

  .post-aside {
    padding-top: 3em;
  }

  .post-aside h3 {
    margin: 0;
  }

  .demo-link {
    margin: 0 0 1em;
  }

  .demo-link .button {
    background: #333;
    border: none;
    color: #fff;
  }

  .translations p {
    font-size: 0.75em;
  }

  .translations ul {
    list-style: none;
    font-size: 0.8em;
    padding: 0 0.5em 0;
  }

  .translations li::before {
    content: '\21FE  ';
  }

  .translate {
    margin-top: 2rem;
    margin-bottom: 0;
  }

  .translation-message {
    margin-bottom: 1.5rem;
  }

  .powered-by {
    font-size: 0.5em;
    color: #888;
    padding-top: 0;
  }

  .powered-by img {
    width: 67px;
    margin-left: 4px;
  }

  .translator p {
    font-size: 0.8em;
  }

  .post-title {
    margin-top: 1.25em;
  }

  .sidebar-email-signup,
  .sidebox {
    background: #eee;
    border-radius: 4px;
    font-size: 12px;
    padding: 0.5em 1em;
  }

  .sidebox h4 {
    font-size: 1.75em;
    margin: 0 0 0.5em;
  }

  .sidebox input[type='email'] {
    width: 100%;
  }

  .sidebox input[type='submit'] {
    font-size: 9px !important;
  }

  .course-sidebar {
    background: #eee;
    border-radius: 0.5em;
    margin: 1.5em 0;
    padding: 0.25em 0.5em 0.5em;
  }
  .course-sidebar img {
    height: 5em;
    margin: 0 auto;
  }
  .course-sidebar h3,
  .course-sidebar p {
    color: #666;
    font-size: 18px;
    text-align: center;
    margin: 0.5em 0;
    font-size: 14px;
    font-style: italic;
  }

  /* Media queries here for various scales using font-size as a handle */

  @media (max-width: 768px) {
    .container {
      width: 95%;
    }
  }

  @media (max-width: 550px) {
    .post-header {
      font-size: 12px;
    }

    .author-details,
    .demo-link,
    .sidebar-email-signup,
    .course-sidebar {
      display: none;
    }
  }

  @media (max-width: 420px) {
    .post-header {
      font-size: 8px;
    }
  }
</style>

<svelte:head>
  <title>{post.metadata.title}</title>

  <meta name="twitter:title" content={post.metadata.title} />
  <meta name="twitter:description" content={post.metadata.description} />
  <meta name="Description" content={post.metadata.description} />
</svelte:head>

<article class="post listify">
  <h1>{post.metadata.title}</h1>
  <p class="standfirst">{post.metadata.description}</p>

  <p class="byline">
    <a href={post.metadata.authorURL}>{post.metadata.author}</a>
    <time datetime={post.metadata.pubdate}>{post.metadata.dateString}</time>
  </p>

  {@html post.html}
</article>
