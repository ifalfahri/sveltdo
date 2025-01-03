<script>
  export let content, listName;
</script>

<div class="card mb-3 has-background-primary-light">
  <div class="card-content">
    <div class="columns">
      <div class="column is-narrow">
        {#if listName !== "Tasks"}
        <span class="icon has-text-primary">
          <i class="fa fa-chevron-left"></i>
        </span>
        {/if}
      </div>
      <div class="column">
        <p class="has-text-primary-dark">{content}</p>
      </div>
      <div class="column is-narrow">
        <span class="icon has-text-danger">
          <i class="fa fa-trash"></i>
        </span>
      </div>
      <div class="column is-narrow">
        {#if listName !== "Done"}
        <span class="icon has-text-primary">
          <i class="fa fa-chevron-right"></i>
        </span>
        {/if}
      </div>
    </div>
  </div>
</div>
