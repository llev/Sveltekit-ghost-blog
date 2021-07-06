<script context="module">
  import GhostContentAPI from '@tryghost/content-api'

    export async function load(ctx) {
      const api = new GhostContentAPI({
        url: 'https://dfeb.ghost.io',
        key: '2b5a226412a68c38dadee0dc32',
        version: 'v4'
    })
    let slug = ctx.page.params.slug
      try {
        const post = await api.posts.read({slug}, {formats: ['html']})
        return {props: {"post": post}}
      } catch(err) {
        console.log(err)
      }
  }
</script>
<script>
  export let post
</script>

<h1>{post.title}</h1>
{@html post.html}