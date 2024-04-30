<script>
  let comment = "";

  /** @type {import('./$types').Snapshot<string>} */
  export const snapshot = {
    capture: () => comment,
    restore: (value) => (comment = value),
  };
</script>

<form method="POST">
  <label for="comment">Comment</label>
  <textarea id="comment" bind:value={comment} />
  <button>Post comment</button>
</form>
