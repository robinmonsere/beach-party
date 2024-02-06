<script>
    import { injectSpeedInsights } from "@vercel/speed-insights/sveltekit"
    import { dev } from '$app/environment';
    import { inject } from '@vercel/analytics';
    injectSpeedInsights();
    inject({ mode: dev ? 'development' : 'production' });

</script>

<slot/>