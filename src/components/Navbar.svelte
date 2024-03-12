<script lang="ts">
  import { onMount } from "svelte";

  let currentPathname = "/";
  
  const links = [
    ["/basics", "Basics"],
    ["/anywhere/1", "Anywhere #1"],
    ["/anywhere/2", "Anywhere #2"],
    ["/previous", "Previous"],
    ["/target-layouts", "Target Layouts"],
    ["/form-validation", "Form Validation"],
    ["/all-siblings", "Siblings"],
    ["/quantity-queries", "Quantity Queries"],
    ["/empty-children", "Empty Children"],
    ["/nested-dropdown", "Nested Dropdown"],
    ["/attribute-matching", "Attribute Matching"],
  ];
  
  function setActive() {
    currentPathname = window.location.pathname;
  }
  onMount(() => {
    setActive();
    document.addEventListener("astro:before-swap", setActive);
  });
</script>
<nav>
  <ul class="nav-list">
    <li>
      <a class={currentPathname === "/" ? "active" : ""} href="/">
        Home
      </a>
    </li>
    {#each links as [path, label] }  
      <li>
        <a class={currentPathname.startsWith(path) ? "active" : ""} href="{path}">
          {label}
        </a>
      </li>
    {/each}
  </ul>
</nav>
