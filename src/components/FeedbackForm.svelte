<script>
  import { v4 as uuidv4 } from 'uuid';
  import Card from './Card.svelte';
  import Button from './Button.svelte';
  import RatingSelect from './RatingSelect.svelte';

  let message;
  let text = '';
  let btnDisabled = true;
  let minText = 10;
  let rating = 10;

  // Validate text length.
  const handleInput = () => {
    if (text.trim().length <= minText) {
      message = `Text must be at least ${minText} characters`;
      btnDisabled = true;
    } else {
      message = null;
      btnDisabled = false;
    }
  };

  // Sets the selected rating.
  const handleSelect = (e) => (rating = e.detail);

  // Submits the user's text and rating.
  const handleSubmit = () => {
    if (text.trim().length > minText) {
      const newFeedback = {
        id: uuidv4(),
        text,
        rating: +rating,
      };

      console.log(newFeedback);
    }
  };
</script>

<Card>
  <header>
    <h2>How do you rate your service?</h2>
  </header>
  <form on:submit|preventDefault={handleSubmit}>
    <RatingSelect on:rating-select={handleSelect} />
    <div class="input-group">
      <input type="text" placeholder="What did you like?" on:input={handleInput} bind:value={text} />
      <Button type="submit" disabled={btnDisabled}>Send</Button>
    </div>
    {#if message}
      <div class="message">
        {message}
      </div>
    {/if}
  </form>
</Card>

<style>
  header {
    max-width: 400px;
    margin: auto;
  }
  header h2 {
    font-size: 22px;
    font-weight: 600;
    text-align: center;
  }
  .input-group {
    display: flex;
    flex-direction: row;
    border: 1px solid #ccc;
    padding: 8px 10px;
    border-radius: 8px;
    margin-top: 15px;
  }
  input {
    flex-grow: 2;
    border: none;
    font-size: 16px;
  }
  input:focus {
    outline: none;
  }
  .message {
    padding-top: 10px;
    text-align: center;
    color: rebeccapurple;
  }
</style>
