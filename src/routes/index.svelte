<script context="module">
  import GhostContentAPI from '@tryghost/content-api'

    export async function load(ctx) {
      const api = new GhostContentAPI({
        url: 'https://dfeb.ghost.io',
        key: '2b5a226412a68c38dadee0dc32',
        version: 'v4'
    })
      try {
        const jsonPosts = await api.posts.browse({limit: 5, include: 'tags, authors'})
        return {props: {"posts": jsonPosts}}
      } catch(err) {
        console.log(err)
      }
  }
</script>
<script>
    export let posts
</script>

  <h1>Welcome to SvelteKit</h1>
  <p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>

  <ul>
    {#each posts as post}
    <li><a href="/posts/{post.slug}">{post.title}</a></li>
    {/each}
  </ul>
