<script>
  import { fade, scale } from 'svelte/transition';

  // Using a different to make each card.
  import FeedbackItem from './FeedbackItem.svelte';

  // Will import from top level store.
  // But setting as [] as default here.
  export let feedback = [];

  // Run here: console.log(feedback)
</script>

{#each feedback as fb (fb.id)}
  <div in:scale out:fade={{ duration: 500 }}>
    <FeedbackItem item={fb} on:delete-feedback />
  </div>
{/each}
