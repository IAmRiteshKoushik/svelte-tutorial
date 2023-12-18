<script>
  // There are the default values of the props
    export let message = "default value";
    export let showModal = false; 
    export let isPromo = false;
</script>

{#if showModal}
<!-- Adding an additional class to the div by evaluating an expression-->
<!-- or a function -->
  <!-- Attach a click event and not defining it directly but inside App.svelte-->
    <div class="backdrop" class:promo={isPromo} on:click|self>
    <!-- One problem with having a toggling element is that we do not want the toggle  -->
    <!-- to happen when we are hovering over the below div, and only on the backdrop. -->
    <!-- For that we need to stop the event propagation to the child elements. Hence,  -->
    <!-- we add the "self" key word after on:click which limits the event propagation -->
        <div class="modal">
      <!-- EVENT MODIFIER -->
      <!-- The event attachment can be done to any element and if left without  -->
      <!-- a value then it would bubble up and take the event from the parent event -->
      <!-- For example, <p on:click></p> would have led to the on:click from the parent  -->
      <!-- to be inherited by this element  -->

      <!-- Slot tag looks for any child context inside a component. While components are usually  -->
      <!-- declared as single closing tags but there is the possibility that some HTML is embedded-->
      <!-- inside the tags and it is made to behave like non-self closing tag then things can be  -->
      <!--   slotted inside -->
        <slot></slot>
        </div>
    </div>
{/if}

<style>
    .backdrop {
        width: 100%;
        height: 100%;
        position: fixed;
        background: rgba(0,0,0,0.8)
    }

    .modal {
        padding: 10px;
        border-radius: 10px;
        max-width: 400px;
        margin: 10% auto;
        text-align: center;
        background: white;
    }

    .promo .modal {
        background: crimson;
        color: white;
    }

</style>

