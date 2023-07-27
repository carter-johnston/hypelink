<script lang="ts">

    interface HypeLink {
        protocol: string;
        domain: string;
        pathnames: string[];
        searchParams: IterableIterator<[string, string]> | [];
    }
    let urlToDisplay : HypeLink;

    function generateUrl(this : HTMLInputElement) {
        if(!this.value) {
            return;
        }
        try {
            const url = new URL(this.value);

            urlToDisplay = {
                protocol: url.protocol,
                domain: url.host,
                pathnames: url.pathname.split('/'),
                searchParams: url.searchParams.entries() ?? []
            }
            urlToDisplay = urlToDisplay;
        }
        catch(err) {

        }
    }
</script>

<input type="text" on:change={generateUrl}>

<p>{urlToDisplay?.domain ?? "-"}</p>





  
<style lang="postcss">
    :global(html) {
        background-color: theme(colors.gray.100);
    }
</style>