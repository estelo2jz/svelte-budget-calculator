<script>
  import SectionTitle from './Title.svelte';
  import Expense from './Expense.svelte';
  import { fly } from 'svelte/transition';
  import { flip } from 'svelte/animate';
  export let expenses = [];
  
</script>

<style> 
  h2 {
    text-transform: capitalize;
  }
</style>

<section>
  <SectionTitle title="expense list" />
  <ul>
    {#each expenses as expense, index (expense.id)}
    <div in:fly={{x:200, delay: index*700 }} out:fly={{ x:-200}} animate:flip>  
      <Expense {...expense}  />
    </div>
    {:else}
      <h2>No Expenses Added To The List!</h2>
    {/each}
  </ul>
</section>