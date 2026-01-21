<script>
    let posts = [
        {
            title: "XMRig Dashboard",
            date: "2026-01-21",
            summary:
                "A web-based dashboard for monitoring and controlling XMRig cryptocurrency miner, featuring real-time hashrate monitoring and live CPU control.",
            slug: "xmrig-dashboard",
        },
        {
            title: "PiFan - Raspberry Pi 5 Fan Controller",
            date: "2026-01-21",
            summary:
                "A modern GUI application to take full control of your Raspberry Pi 5's active cooler fan speed using hardware PWM.",
            slug: "pifan",
        },
        {
            title: "Bad Apple on RP2350 (RISC-V)",
            date: "2026-01-21",
            summary:
                "Playing the iconic 'Bad Apple' video on a Raspberry Pi Pico 2 (RP2350) using the RISC-V hazard3 cores and SSD1306.",
            slug: "pico2-riscv-badapple",
        },
        {
            title: "fastfetchus",
            date: "2026-01-21",
            summary:
                "A custom system information fetching tool inspired by fastfetch/neofetch, designed for efficiency and aesthetics.",
            slug: "fastfetchus",
        },
        {
            title: "ESP32 Bad Apple",
            date: "2026-01-21",
            summary:
                "Bad Apple video player for ESP32 with SSD1306 OLED, utilising Heatshrink compression for efficient video storage.",
            slug: "deneyap-badapple",
        },
        {
            title: "wthmdif (Why The Hell My Disk Is Full?)",
            date: "2026-01-21",
            summary:
                "A terminal-based disk usage analyzer written in Rust. It helps identify storage consumption with a clear and intuitive interface.",
            slug: "wthmdif",
        },
        {
            title: "NixOS Configuration: Complete Desktop Environment with Hyprland",
            date: "2025-09-30",
            summary:
                "A comprehensive NixOS configuration flake featuring Hyprland window manager, development tools, gaming support, and reproducible system management.",
            slug: "nixos",
        },
        {
            title: "NeuralRust: A Neural Network Implementation in Rust",
            date: "2025-09-05",
            summary:
                "A neural network implementation written in Rust, designed for learning and experimentation with machine learning concepts.",
            slug: "NeuralRust",
        },
        {
            title: "Introducing rust-p2p-chat: A Minimal Peer-to-Peer CLI Chat App in Rust",
            date: "2025-08-22",
            summary:
                "A simple, open-source command-line chat application in Rust for peer-to-peer, encrypted messaging with no central server.",
            slug: "rust-p2p-chat",
        },
    ];

    function navigateToPost(slug) {
        window.location.href = `/blog/tech/${slug}`;
    }
</script>

<div class="w-full min-h-screen p-8">
    <div class="max-w-3xl mx-auto">
        <div class="relative text-center mb-16">
            <div
                class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-32 h-32 bg-pink-500/20 rounded-full blur-3xl"
            ></div>
            <h1 class="text-4xl md:text-5xl relative">
                <span class="text-pink-400 anime-text-glow font-medium"
                    >Tech</span
                >
                <span class="text-purple-300 font-medium relative inline-block">
                    Blog
                    <span
                        class="absolute -top-1 -right-1 w-2 h-2 bg-pink-400 rounded-full animate-ping"
                    ></span>
                </span>
            </h1>
            <div
                class="w-48 h-1 mx-auto mt-4 bg-gradient-to-r from-transparent via-pink-400 to-transparent"
            ></div>
        </div>

        <div class="space-y-6">
            {#each posts as post}
                <button
                    on:click={() => navigateToPost(post.slug)}
                    class="w-full text-left block p-6 rounded-lg bg-slate-800/60 border border-pink-400/10 hover:border-pink-400/40 transition-all duration-200 cursor-pointer hover:transform hover:scale-105"
                >
                    <div class="flex flex-col gap-1">
                        <span class="text-pink-300 text-xl font-semibold"
                            >{post.title}</span
                        >
                        <span class="text-xs text-purple-200/60"
                            >{post.date}</span
                        >
                        <span class="text-purple-100/80 text-base"
                            >{post.summary}</span
                        >
                    </div>
                </button>
            {/each}
        </div>
    </div>
</div>
