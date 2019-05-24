<script context="module">
  export async function preload({ params }) {
    const res = await this.fetch(`${params.slug}.json`)
    return res.ok ? { post: await res.json() } : this.error(404, 'Not found')
  }
</script>

<script>
  export let post
  import PostHeader from '../components/PostHeader.svelte'
  import PostFooter from '../components/PostFooter.svelte'
  import Sidebar from '../components/Sidebar.svelte'
</script>

<style>

</style>

<svelte:head>
  <title>{post.metadata.title}</title>

  <meta name="twitter:title" content={post.metadata.title} />
  <meta name="twitter:description" content={post.metadata.description} />
  <meta name="Description" content={post.metadata.description} />
</svelte:head>

<PostHeader shorter={!!post.metadata.custom_header} />
<article class={`post-content %{post.metadata.rtl ? 'rtl' : 'ltr'}`}>
  <h1 class="post-title">{post.metadata.title}</h1>
  <time datetime={post.metadata.pubdate}>{post.metadata.dateString}</time>
  {@html post.html}
  <PostFooter />
</article>
<Sidebar metadata={post.metadata} />
