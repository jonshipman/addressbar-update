Code is in src/routes/+page.svelte

```
    <script lang="ts">
        import { browser } from '$app/environment';
        import { goto } from '$app/navigation';

        let searchTerm = '';
        let input: HTMLInputElement;

        $: browser && updateAddressBar(searchTerm);

        function updateAddressBar(s: string) {
            setTimeout(() => {
                goto(`?q=${s}`).then(handleFocus);
            });
        }

        function handleFocus() {
            setTimeout(() => {
                input.focus();
                input.setSelectionRange(1000, 1000);
            });
        }
    </script>

    <input bind:value={searchTerm} bind:this={input} />
```
