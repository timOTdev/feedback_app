<script>
  import { fade, scale } from 'svelte/transition';

  // Using a different to make each card.
  import FeedbackItem from './FeedbackItem.svelte';

  // Will import from our stores file.
  import { FeedbackStore } from '../stores.js';

  /// ===LONG WAY
  // import { onMount, onDestroy } from 'svelte';

  // let feedback = [];

  // // You can subscribe to the store to grab its data.
  // // The subscribe() returns an unsubscribe() function
  // // by default that we can use for onDestroy().
  // const unsubscribe = FeedbackStore.subscribe((data) => (feedback = data));

  // // Before the component is mounted. We are not going to use here.
  // onMount(() => {
  //   console.log('mounted');
  // });

  // // We need to unsubscribe from the store after we are done.
  // onDestroy(() => {
  //   unsubscribe();
  // });

  // ===SHORT WAY
  // Seen below with $FeedbackStore.
  // Will also unsubscribe by default.
</script>

{#each $FeedbackStore as fb (fb.id)}
  <div in:scale out:fade={{ duration: 500 }}>
    <FeedbackItem item={fb} />
  </div>
{/each}
