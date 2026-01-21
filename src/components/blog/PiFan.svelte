<script>
    import { marked } from "marked";
    import "../../styles/markdown.css";
    import { onMount } from "svelte";
    import { fade, fly } from "svelte/transition";

    const url =
        "https://raw.githubusercontent.com/temidaradev/PiFan/master/README.md";

    const fallbackContent = `\n# PiFan\n\nA modern GUI application designed specifically for the Raspberry Pi 5. It allows you to take full control of your active cooler's fan speed using hardware PWM.\n`;

    let content = "";
    let error = null;
    let isLoading = true;

    async function fetchContent() {
        try {
            const controller = new AbortController();
            const timeoutId = setTimeout(() => controller.abort(), 10000);

            const response = await fetch(url, {
                signal: controller.signal,
                cache: "no-cache",
            });

            clearTimeout(timeoutId);

            if (!response.ok) {
                console.warn(
                    "Failed to fetch README from GitHub, using fallback content",
                );
                return marked(fallbackContent);
            }

            const text = await response.text();
            if (!text || text.trim().length < 10) {
                console.warn(
                    "Received empty or invalid content from GitHub, using fallback content",
                );
                return marked(fallbackContent);
            }

            const htmlContent = marked(text);

            const filteredContent = htmlContent
                .replace(/<video[^>]*>.*?<\/video>/gis, "")
                .replace(/<iframe[^>]*>.*?<\/iframe>/gis, "")
                .replace(/<embed[^>]*\/?>/gis, "")
                .replace(/<object[^>]*>.*?<\/object>/gis, "")
                .replace(/<source[^>]*\/?>/gis, "")
                .replace(
                    /https:\/\/github\.com\/user-attachments\/assets\/[^\s<>"]*/gi,
                    "",
                )
                .replace(
                    /!\[.*?\]\(https:\/\/github\.com\/user-attachments\/assets\/[^)]*\)/gi,
                    "",
                );

            return filteredContent;
        } catch (e) {
            console.error("Error fetching content:", e);
            return marked(fallbackContent);
        } finally {
            isLoading = false;
            error = null;
        }
    }

    onMount(() => {
        fetchContent().then((result) => {
            content = result;
        });
    });
</script>

<div class="relative py-6">
    {#if isLoading}
        <div class="flex justify-center items-center h-40" in:fade>
            <div class="loading-container">
                <span class="text-pink-400 text-xl">Loading PiFan...</span>
                <div class="loading-animation"></div>
            </div>
        </div>
    {:else if error}
        <div class="error-container" in:fade>
            <p class="text-red-400 text-center text-lg">Error: {error}</p>
            <button
                class="retry-button mt-4"
                on:click={() => {
                    isLoading = true;
                    error = null;
                    fetchContent().then((result) => {
                        content = result;
                    });
                }}
            >
                Try Again
            </button>
        </div>
    {:else}
        <div class="markdown-wrapper" in:fly={{ y: 20, duration: 600 }}>
            <div class="markdown-content">
                {@html content}
            </div>
        </div>
    {/if}
</div>

<style>
    .markdown-wrapper {
        position: relative;
        max-width: 900px;
        margin: 0 auto;
    }
    .loading-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 16px;
    }
    .loading-animation {
        position: relative;
        width: 60px;
        height: 4px;
        background: rgba(255, 121, 198, 0.2);
        border-radius: 4px;
        overflow: hidden;
    }
    .loading-animation::after {
        content: "";
        position: absolute;
        top: 0;
        left: 0;
        height: 100%;
        width: 30%;
        background: #ff79c6;
        border-radius: 4px;
        animation: loading 1.5s infinite ease;
    }
    @keyframes loading {
        0% {
            left: -30%;
        }
        100% {
            left: 100%;
        }
    }
    .error-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 2rem;
        max-width: 600px;
        margin: 0 auto;
    }
    .retry-button {
        padding: 0.5rem 1.5rem;
        background-color: rgba(255, 121, 198, 0.2);
        border: 1px solid #ff79c6;
        color: #ff79c6;
        border-radius: 4px;
        font-weight: 500;
        transition: all 0.2s ease;
        cursor: pointer;
    }
    .retry-button:hover {
        background-color: rgba(255, 121, 198, 0.3);
        box-shadow: 0 0 10px rgba(255, 121, 198, 0.4);
    }
</style>
