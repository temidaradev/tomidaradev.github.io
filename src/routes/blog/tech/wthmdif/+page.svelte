<script>
    import Wthmdif from "../../../../components/blog/Wthmdif.svelte";
    import Sakura from "../../../../components/Sakura.svelte";
</script>

<div class="blog-container">
    <div class="sakura-overlay">
        <Sakura />
    </div>

    <div class="max-w-4xl mx-auto px-4 py-8">
        <div class="blog-content">
            <Wthmdif />
        </div>

        <div class="mt-8 text-center">
            <a href="/blog/tech" class="back-link"> ← Back to Tech Blog </a>
        </div>
    </div>
</div>

<style>
    .blog-container {
        position: relative;
        min-height: 100vh;
        background: linear-gradient(
            135deg,
            rgba(13, 12, 33, 0.95) 0%,
            rgba(45, 41, 87, 0.8) 100%
        );
        overflow: hidden;
    }

    .sakura-overlay {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        pointer-events: none;
        z-index: 1;
        opacity: 0.15;
    }

    .blog-content {
        position: relative;
        z-index: 2;
        background: rgba(40, 42, 54, 0.95);
        border-radius: 12px;
        border: 1px solid rgba(255, 121, 198, 0.2);
        backdrop-filter: blur(10px);
        padding: 2rem;
        margin: 2rem 0;
        box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
    }

    .blog-content :global(.markdown-content) {
        color: #f8f8f2;
    }

    .blog-content :global(h1) {
        color: #ff79c6;
        margin-top: 1.5rem;
        margin-bottom: 1rem;
    }

    .blog-content :global(h2) {
        color: #ff79c6;
        margin-top: 1.5rem;
        margin-bottom: 1rem;
    }

    .blog-content :global(h3) {
        color: #ff79c6;
        margin-top: 1.5rem;
        margin-bottom: 1rem;
    }

    .blog-content :global(h4) {
        color: #ff79c6;
        margin-top: 1.5rem;
        margin-bottom: 1rem;
    }

    .blog-content :global(h5) {
        color: #ff79c6;
        margin-top: 1.5rem;
        margin-bottom: 1rem;
    }

    .blog-content :global(h6) {
        color: #ff79c6;
        margin-top: 1.5rem;
        margin-bottom: 1rem;
    }

    .blog-content :global(p) {
        margin-bottom: 1rem;
        line-height: 1.6;
    }

    .blog-content :global(code) {
        background: rgba(68, 71, 90, 0.8);
        padding: 0.2rem 0.4rem;
        border-radius: 4px;
        font-family: "Fira Code", monospace;
    }

    .blog-content :global(pre) {
        background: rgba(68, 71, 90, 0.9);
        padding: 1rem;
        border-radius: 8px;
        overflow-x: auto;
        margin: 1rem 0;
    }

    .back-link {
        display: inline-flex;
        align-items: center;
        gap: 0.5rem;
        color: #ff79c6;
        text-decoration: none;
        font-weight: 500;
        transition: all 0.3s ease;
        position: relative;
        z-index: 2;
        padding: 0.75rem 1.5rem;
        border: 1px solid rgba(255, 121, 198, 0.3);
        border-radius: 8px;
        background: rgba(255, 121, 198, 0.1);
        backdrop-filter: blur(10px);
    }

    .back-link:hover {
        color: #ff92d0;
        border-color: rgba(255, 121, 198, 0.6);
        background: rgba(255, 121, 198, 0.2);
        transform: translateY(-2px);
        box-shadow: 0 4px 15px rgba(255, 121, 198, 0.3);
    }
</style>
