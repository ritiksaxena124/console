<script lang="ts" context="module">
    export type Breadcrumb = {
        title: string;
        href?: string;
    };
</script>

<script lang="ts">
    import { trackEvent } from '$lib/actions/analytics';

    export let breadcrumbs: Breadcrumb[];

    function track() {
        trackEvent('click_breadcrumb');
    }
</script>

<nav class="breadcrumbs is-only-desktop" aria-label="breadcrumb">
    <ol class="breadcrumbs-list">
        {#each breadcrumbs as breadcrumb}
            <li class="breadcrumbs-item">
                {#if breadcrumb.href}
                    <a href={breadcrumb.href} title={breadcrumb.title} on:click={track}>
                        {breadcrumb.title}
                    </a>
                {:else}
                    <span>{breadcrumb.title}</span>
                {/if}
            </li>
        {/each}
    </ol>
</nav>
