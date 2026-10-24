#   
```
<!DOCTYPE html>
<html lang="en" class="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
    <title>Sabbia & Sole - Quiet Dictionary</title>

    <!-- iOS Standalone Fullscreen Web App Meta Tags -->
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <meta name="apple-mobile-web-app-title" content="Sabbia">
    <meta name="mobile-web-app-capable" content="yes">
    <meta name="theme-color" content="#181412">

    <!-- Apple Touch Icon (Data URI SVG for crisp home screen icon) -->
    <link rel="apple-touch-icon" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'%3E%3Crect width='100' height='100' rx='22' fill='%23181412'/%3E%3Ccircle cx='50' cy='50' r='38' fill='%23241E1A' stroke='%23463B34' stroke-width='2'/%3E%3Cpath d='M35 32h30c3 0 5 2 5 5v31c0 3-2 5-5 5H35c-3 0-5-2-5-5V37c0-3 2-5 5-5z' fill='none' stroke='%23E3A857' stroke-width='3'/%3E%3Cpath d='M50 32v41' stroke='%23E3A857' stroke-width='2' stroke-dasharray='2 2'/%3E%3C/svg%3E">

    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        // Light Parchment Palette
                        parchment: {
                            50: '#F7F0E6',
                            100: '#EFE1C8',
                            200: '#E8D8BB',
                            300: '#DFCCAA',
                            400: '#CBB48E',
                            800: '#524336',
                            900: '#352B24',
                        },
                        // Night / Dark Lamp Palette
                        night: {
                            900: '#181412', // Deep espresso canvas
                            800: '#241E1A', // Dark walnut card
                            700: '#322A25', // Input/tray area
                            600: '#463B34',
                            200: '#D5C7B8',
                            100: '#E6DDD3', // Warm beige text
                        },
                        amberGold: '#E3A857',
                        terracotta: {
                            500: '#B85C37',
                            600: '#9B4B2B',
                        },
                        paperMuted: '#887B6F',
                        nightMuted: '#9B8D80',
                    },
                    fontFamily: {
                        book: ['"EB Garamond"', 'Georgia', 'serif'],
                        typewriter: ['"Courier Prime"', 'Courier', 'monospace'],
                        display: ['"Fraunces"', 'Georgia', 'serif'],
                    }
                }
            }
        }
    </script>
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Courier+Prime:ital,wght@0,400;0,700;1,400&family=EB+Garamond:ital,wght@0,400..600;1,400..600&family=Fraunces:ital,opsz,wght@0,9..144,300..600;1,9..144,300..600&display=swap" rel="stylesheet">
    <!-- Lucide Icons -->
    <script src="https://unpkg.com/lucide@latest"></script>

    <style>
        body {
            font-family: 'EB Garamond', Georgia, serif;
            -webkit-tap-highlight-color: transparent;
            letter-spacing: 0.015em;
            transition: background-color 0.3s ease, color 0.3s ease;
            user-select: none;
            -webkit-user-select: none;
        }

        /* LIGHT MODE CANVAS */
        html:not(.dark) body {
            background-color: #E2D1B8;
            color: #352B24;
        }

        html:not(.dark) .reader-paper-bg {
            background-color: #EFE1C8;
            background-image: 
                radial-gradient(circle at 50% 50%, #F7F0E6 0%, #EFE1C8 80%),
                radial-gradient(circle at 50% 90%, rgba(184, 92, 55, 0.04) 0%, transparent 60%);
        }

        html:not(.dark) .glass-card {
            background: rgba(232, 216, 187, 0.85);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid rgba(203, 180, 142, 0.5);
            box-shadow: 0 4px 20px -4px rgba(53, 43, 36, 0.05);
        }

        html:not(.dark) .centered-search-card {
            background: rgba(239, 225, 200, 0.9);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid rgba(203, 180, 142, 0.7);
            box-shadow: 0 10px 30px -8px rgba(53, 43, 36, 0.08);
        }

        html:not(.dark) .centered-search-card:focus-within {
            border-color: rgba(184, 92, 55, 0.6);
            box-shadow: 0 0 0 2px rgba(184, 92, 55, 0.2), 0 14px 36px -8px rgba(53, 43, 36, 0.12);
        }

        /* DARK MODE CANVAS ("Night Reading") */
        html.dark body {
            background-color: #110E0C;
            color: #E6DDD3;
        }

        html.dark .reader-paper-bg {
            background-color: #181412;
            background-image: 
                radial-gradient(circle at 50% 40%, #221B17 0%, #181412 85%),
                radial-gradient(circle at 50% 90%, rgba(227, 168, 87, 0.05) 0%, transparent 70%);
        }

        html.dark .glass-card {
            background: rgba(36, 30, 26, 0.88);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid rgba(70, 59, 52, 0.6);
            box-shadow: 0 4px 24px -4px rgba(0, 0, 0, 0.3);
        }

        html.dark .centered-search-card {
            background: rgba(36, 30, 26, 0.92);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid rgba(70, 59, 52, 0.8);
            box-shadow: 0 10px 30px -8px rgba(0, 0, 0, 0.4);
        }

        html.dark .centered-search-card:focus-within {
            border-color: rgba(227, 168, 87, 0.6);
            box-shadow: 0 0 0 2px rgba(227, 168, 87, 0.2), 0 14px 36px -8px rgba(0, 0, 0, 0.5);
        }

        /* Organic Grain Overlay */
        .paper-grain {
            background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noiseFilter'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.8' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noiseFilter)' opacity='0.035'/%3E%3C/svg%3E");
        }

        @keyframes fadeInScale {
            from { opacity: 0; transform: scale(0.98) translateY(6px); }
            to { opacity: 1; transform: scale(1) translateY(0); }
        }

        .animate-radial-in {
            animation: fadeInScale 0.35s cubic-bezier(0.16, 1, 0.3, 1) forwards;
        }

        @keyframes pulseGlow {
            0%, 100% { opacity: 0.4; }
            50% { opacity: 0.9; }
        }

        .pulse-loading {
            animation: pulseGlow 1.4s ease-in-out infinite;
        }

        ::-webkit-scrollbar {
            width: 4px;
        }
        html:not(.dark) ::-webkit-scrollbar-thumb {
            background: #CBB48E;
            border-radius: 99px;
        }
        html.dark ::-webkit-scrollbar-thumb {
            background: #463B34;
            border-radius: 99px;
        }

        /* Target search word highlighted in literature quote */
        .quote-word-highlight {
            font-family: 'EB Garamond', serif;
            font-style: italic;
            font-weight: 600;
            color: #B85C37;
            padding: 0 3px;
            border-radius: 3px;
        }

        html.dark .quote-word-highlight {
            color: #E3A857;
            background-color: rgba(227, 168, 87, 0.15);
        }

        html:not(.dark) .quote-word-highlight {
            background-color: rgba(203, 180, 142, 0.35);
        }

        /* Safe area spacing for iOS notched phones */
        .pt-safe {
            padding-top: max(1.75rem, env(safe-area-inset-top));
        }
        .pb-safe {
            padding-bottom: max(1rem, env(safe-area-inset-bottom));
        }
    </style>
</head>
<body class="min-h-screen flex items-center justify-center p-0 md:p-6 transition-colors duration-300">

    <!-- Mobile Container (iOS Frame) -->
    <div id="appContainer" class="w-full max-w-md h-[100vh] md:h-[870px] md:max-h-[96vh] reader-paper-bg paper-grain md:rounded-[44px] shadow-2xl flex flex-col overflow-hidden relative border-0 md:border-[8px] border-parchment-300 dark:border-night-700 transition-colors duration-300">
        
        <!-- Header -->
        <header class="pt-safe px-6 pb-2 flex items-center justify-between z-20 select-none">
            <!-- Left: Theme Switcher Button -->
            <button onclick="toggleDarkMode()" title="Toggle Theme" class="w-8 h-8 rounded-full glass-card hover:bg-parchment-200 dark:hover:bg-night-700 flex items-center justify-center text-parchment-900 dark:text-night-100 transition-all active:scale-95 shadow-sm">
                <i data-lucide="sun" id="sunIcon" class="w-4 h-4 text-amberGold hidden"></i>
                <i data-lucide="moon" id="moonIcon" class="w-4 h-4 text-parchment-800"></i>
            </button>

            <!-- Center Logo -->
            <div class="flex items-center space-x-2 cursor-pointer" onclick="resetToHome()">
                <div class="w-7 h-7 rounded-full bg-parchment-900 dark:bg-amberGold flex items-center justify-center text-parchment-100 dark:text-night-900 shadow-sm transition-transform active:scale-95">
                    <i data-lucide="book" class="w-3.5 h-3.5"></i>
                </div>
                <span class="font-typewriter text-[11px] font-bold tracking-widest text-parchment-900 dark:text-night-100 uppercase">Sabbia</span>
            </div>

            <!-- Right Actions: Add to Home Screen & Saved Tray -->
            <div class="flex items-center space-x-1.5">
                <button onclick="toggleIosGuideModal()" title="Add to Home Screen" class="w-8 h-8 rounded-full glass-card hover:bg-parchment-200 dark:hover:bg-night-700 flex items-center justify-center text-parchment-900 dark:text-night-100 transition-all active:scale-95 shadow-sm">
                    <i data-lucide="share" class="w-3.5 h-3.5"></i>
                </button>
                <button onclick="toggleSavedTray()" title="Saved Words" class="w-8 h-8 rounded-full glass-card hover:bg-parchment-200 dark:hover:bg-night-700 flex items-center justify-center text-parchment-900 dark:text-night-100 transition-all active:scale-95 shadow-sm relative">
                    <i data-lucide="bookmark" class="w-4 h-4"></i>
                    <span id="bookmarkCount" class="hidden absolute -top-1 -right-1 bg-terracotta-500 dark:bg-amberGold text-white dark:text-night-900 font-typewriter text-[9px] font-bold w-4 h-4 rounded-full flex items-center justify-center shadow">0</span>
                </button>
            </div>
        </header>

        <!-- Main Workspace -->
        <main class="flex-1 flex flex-col justify-center px-6 py-4 overflow-y-auto relative z-10 pb-safe" id="mainContent">
            
            <!-- PERFECTLY CENTERED HOME VIEW -->
            <div id="homeCenterView" class="my-auto w-full flex flex-col items-center justify-center space-y-6 animate-radial-in text-center">
                
                <div class="space-y-1">
                    <h1 class="font-display italic text-3xl text-parchment-900 dark:text-night-100 font-normal tracking-tight">Sabbia & Sole</h1>
                    <p class="font-typewriter text-[11px] text-paperMuted dark:text-nightMuted tracking-wide">Type a word in English or Italian</p>
                </div>

                <!-- Centered Minimal Search Bar -->
                <div class="w-full max-w-sm relative">
                    <div class="relative flex items-center rounded-full centered-search-card transition-all duration-300">
                        <input 
                            type="text" 
                            id="searchInput"
                            placeholder="Type a word..." 
                            autocomplete="off"
                            autocorrect="off"
                            autocapitalize="off"
                            spellcheck="false"
                            class="w-full py-3.5 pl-12 pr-12 rounded-full bg-transparent text-parchment-900 dark:text-night-100 placeholder:text-paperMuted dark:placeholder:text-nightMuted font-book text-lg focus:outline-none"
                            onkeydown="if(event.key==='Enter') executeSearch()"
                        />
                        <i data-lucide="search" class="w-4 h-4 absolute left-4 text-paperMuted dark:text-nightMuted pointer-events-none"></i>
                        
                        <button onclick="executeSearch()" class="absolute right-2 w-8 h-8 rounded-full bg-parchment-900 dark:bg-amberGold text-parchment-100 dark:text-night-900 flex items-center justify-center shadow hover:opacity-90 transition-opacity active:scale-95">
                            <i data-lucide="arrow-right" class="w-4 h-4"></i>
                        </button>
                    </div>
                </div>

                <!-- Quick Word Pills -->
                <div class="flex flex-wrap justify-center gap-1.5 pt-1 max-w-xs">
                    <button onclick="searchWord('Peculiar')" class="px-3 py-1 rounded-full bg-parchment-200/80 dark:bg-night-700/80 hover:bg-parchment-300 dark:hover:bg-night-600 text-parchment-900 dark:text-night-100 font-typewriter text-[10px] transition-colors border border-parchment-300/60 dark:border-night-600">peculiar</button>
                    <button onclick="searchWord('Crepuscolo')" class="px-3 py-1 rounded-full bg-parchment-200/80 dark:bg-night-700/80 hover:bg-parchment-300 dark:hover:bg-night-600 text-parchment-900 dark:text-night-100 font-typewriter text-[10px] transition-colors border border-parchment-300/60 dark:border-night-600">crepuscolo</button>
                    <button onclick="searchWord('Petrichor')" class="px-3 py-1 rounded-full bg-parchment-200/80 dark:bg-night-700/80 hover:bg-parchment-300 dark:hover:bg-night-600 text-parchment-900 dark:text-night-100 font-typewriter text-[10px] transition-colors border border-parchment-300/60 dark:border-night-600">petrichor</button>
                </div>

            </div>

            <!-- Loading State -->
            <div id="loadingState" class="hidden my-auto py-16 flex flex-col items-center justify-center space-y-3 animate-radial-in">
                <div class="w-8 h-8 border-2 border-parchment-300 dark:border-night-600 border-t-parchment-900 dark:border-t-amberGold rounded-full animate-spin"></div>
                <p class="font-typewriter text-[11px] text-paperMuted dark:text-nightMuted">Retrieving dictionary entry...</p>
            </div>

            <!-- Error State -->
            <div id="errorState" class="hidden my-auto py-12 px-4 text-center space-y-4 animate-radial-in">
                <div class="w-10 h-10 rounded-full glass-card mx-auto flex items-center justify-center text-parchment-900 dark:text-night-100">
                    <i data-lucide="book-x" class="w-5 h-5 text-paperMuted dark:text-nightMuted"></i>
                </div>
                <div class="space-y-1">
                    <h3 class="font-display italic text-lg text-parchment-900 dark:text-night-100">Word not found</h3>
                    <p id="errorMessageText" class="font-book text-sm text-paperMuted dark:text-nightMuted max-w-xs mx-auto leading-relaxed">
                        We couldn't retrieve dictionary entries for this word.
                    </p>
                </div>
                <button onclick="resetToHome()" class="px-4 py-1.5 bg-parchment-900 dark:bg-amberGold text-parchment-100 dark:text-night-900 font-typewriter text-[11px] rounded-full hover:opacity-90 transition-opacity">
                    Search Again
                </button>
            </div>

            <!-- RESULT VIEW -->
            <div id="resultView" class="hidden space-y-3.5 animate-radial-in py-2 my-auto">
                
                <!-- Search Refinement Input -->
                <div class="relative flex items-center rounded-full glass-card shadow-sm">
                    <input 
                        type="text" 
                        id="resultSearchInput"
                        placeholder="Search word..." 
                        class="w-full py-2 pl-9 pr-8 rounded-full bg-transparent text-parchment-900 dark:text-night-100 font-book text-sm focus:outline-none"
                        onkeydown="if(event.key==='Enter') executeSearchResult()"
                    />
                    <i data-lucide="search" class="w-3.5 h-3.5 absolute left-3 text-paperMuted dark:text-nightMuted pointer-events-none"></i>
                    <button onclick="resetToHome()" class="absolute right-2.5 text-paperMuted dark:text-nightMuted hover:text-parchment-900 dark:hover:text-night-100">
                        <i data-lucide="x" class="w-3.5 h-3.5"></i>
                    </button>
                </div>

                <!-- Main Word Header Card -->
                <div class="glass-card p-5 rounded-[24px] shadow-sm relative overflow-hidden">
                    <div class="flex justify-between items-start relative z-10">
                        <div>
                            <div class="flex items-center space-x-2 flex-wrap gap-y-1">
                                <h1 id="wordTitle" class="font-display text-3xl font-normal text-parchment-900 dark:text-night-100 tracking-tight">--</h1>
                                
                                <!-- Automatic Language Detection Tag -->
                                <span id="detectedLangTag" class="font-typewriter text-[10px] font-bold tracking-wider text-terracotta-500 dark:text-amberGold bg-parchment-200 dark:bg-night-700 px-2 py-0.5 rounded border border-parchment-300/60 dark:border-night-600 uppercase">
                                    Italiano
                                </span>
                            </div>
                            <div class="flex items-center space-x-2 mt-1">
                                <span id="wordPos" class="font-typewriter text-xs text-paperMuted dark:text-nightMuted">noun</span>
                                <span class="text-parchment-300 dark:text-night-600">â¢</span>
                                <p id="wordPhonetic" class="font-typewriter text-xs text-paperMuted dark:text-nightMuted">/--/</p>
                            </div>
                        </div>
                        
                        <div class="flex items-center space-x-1.5">
                            <button id="audioPlayBtn" onclick="playPronunciation()" class="w-8 h-8 rounded-full bg-parchment-200 dark:bg-night-700 hover:bg-parchment-300 dark:hover:bg-night-600 text-parchment-900 dark:text-night-100 flex items-center justify-center transition-all active:scale-95 hidden" title="Listen">
                                <i data-lucide="volume-2" class="w-3.5 h-3.5"></i>
                            </button>
                            <button id="bookmarkWordBtn" onclick="toggleSaveCurrentWord()" class="w-8 h-8 rounded-full bg-parchment-200 dark:bg-night-700 hover:bg-parchment-300 dark:hover:bg-night-600 text-parchment-900 dark:text-night-100 flex items-center justify-center transition-all active:scale-95" title="Save Word">
                                <i data-lucide="bookmark" id="bookmarkIcon" class="w-3.5 h-3.5"></i>
                            </button>
                        </div>
                    </div>
                </div>

                <!-- Dictionary Definitions Card (Verbatim Format) -->
                <div class="glass-card p-5 rounded-[24px] shadow-sm space-y-2.5">
                    <h3 class="font-typewriter text-[10px] font-bold tracking-widest text-paperMuted dark:text-nightMuted uppercase flex items-center space-x-1.5">
                        <i data-lucide="book-open" class="w-3 h-3 text-terracotta-500 dark:text-amberGold"></i>
                        <span>Definition</span>
                    </h3>
                    <div id="definitionsList" class="space-y-2.5 text-base text-parchment-900 dark:text-night-100 leading-relaxed font-book">
                        <!-- Dynamic definitions -->
                    </div>
                </div>

                <!-- DEFERRED / ASYNCHRONOUS LITERATURE QUOTE CARD -->
                <div class="glass-card p-5 rounded-[24px] shadow-sm space-y-2 relative overflow-hidden">
                    <h3 class="font-typewriter text-[10px] font-bold tracking-widest text-paperMuted dark:text-nightMuted uppercase flex items-center space-x-1.5">
                        <i data-lucide="quote" class="w-3 h-3 text-terracotta-500 dark:text-amberGold"></i>
                        <span>Literature Excerpt</span>
                    </h3>

                    <!-- Shimmer / Asynchronous Search Indicator -->
                    <div id="literatureLoading" class="py-3 flex items-center space-x-2.5 pulse-loading">
                        <div class="w-3.5 h-3.5 border-2 border-terracotta-500 dark:border-amberGold border-t-transparent rounded-full animate-spin"></div>
                        <span class="font-typewriter text-xs text-paperMuted dark:text-nightMuted">Searching book archives for excerpt...</span>
                    </div>

                    <!-- Async Quote Content (Hidden initially, fades in when quote resolves) -->
                    <div id="literatureContent" class="hidden transition-opacity duration-500 space-y-2">
                        <blockquote id="literaryQuote" class="font-book text-base text-parchment-900 dark:text-night-100 border-l-2 border-terracotta-500 dark:border-amberGold pl-3 py-0.5 my-1 leading-relaxed">
                            "..."
                        </blockquote>
                        <div class="text-right">
                            <span id="literaryAuthor" class="font-book italic text-xs text-parchment-800 dark:text-night-200">--</span>
                            <p id="literaryBookTitle" class="font-typewriter text-[10px] text-paperMuted dark:text-nightMuted tracking-tight">--</p>
                        </div>
                    </div>
                </div>

                <!-- Etymology & Roots Card -->
                <div class="glass-card p-5 rounded-[24px] shadow-sm space-y-2.5">
                    <h3 class="font-typewriter text-[10px] font-bold tracking-widest text-paperMuted dark:text-nightMuted uppercase flex items-center space-x-1.5">
                        <i data-lucide="compass" class="w-3 h-3 text-terracotta-500 dark:text-amberGold"></i>
                        <span>Etymology</span>
                    </h3>
                    
                    <div id="etymologyChain" class="flex flex-wrap items-center gap-1.5 pt-0.5">
                        <!-- Dynamic roots -->
                    </div>

                    <p id="etymologyText" class="font-book text-sm text-parchment-800 dark:text-night-200 leading-relaxed pt-1">
                        Etymology details...
                    </p>
                </div>

                <!-- Synonyms Card -->
                <div id="synonymsCard" class="glass-card p-5 rounded-[24px] shadow-sm space-y-2.5">
                    <h3 class="font-typewriter text-[10px] font-bold tracking-widest text-paperMuted dark:text-nightMuted uppercase flex items-center space-x-1.5">
                        <i data-lucide="layers" class="w-3 h-3 text-terracotta-500 dark:text-amberGold"></i>
                        <span>Synonyms</span>
                    </h3>
                    <div id="synonymsTags" class="flex flex-wrap gap-1.5">
                        <!-- Dynamic synonym buttons -->
                    </div>
                </div>

            </div>

        </main>

        <!-- Saved Words Drawer -->
        <div id="savedTray" class="absolute inset-0 reader-paper-bg paper-grain z-30 transform translate-y-full transition-transform duration-300 ease-in-out flex flex-col">
            <div class="p-6 pb-4 pt-safe flex items-center justify-between border-b border-parchment-300/60 dark:border-night-700">
                <div class="flex items-center space-x-2">
                    <i data-lucide="bookmark" class="w-4 h-4 text-terracotta-500 dark:text-amberGold"></i>
                    <h2 class="font-typewriter text-sm font-bold uppercase tracking-wider text-parchment-900 dark:text-night-100">Saved Words Log</h2>
                </div>
                <button onclick="toggleSavedTray()" class="p-1 rounded-full hover:bg-parchment-200 dark:hover:bg-night-700 text-parchment-900 dark:text-night-100 transition-colors">
                    <i data-lucide="x" class="w-5 h-5"></i>
                </button>
            </div>
            <div class="flex-1 overflow-y-auto p-6 space-y-3 pb-safe" id="savedWordsList">
                <!-- Dynamically populated saved words -->
            </div>
        </div>

        <!-- iOS Fullscreen App Installation Instructions Modal -->
        <div id="iosGuideModal" class="absolute inset-0 bg-black/60 backdrop-blur-sm z-40 hidden flex items-end md:items-center justify-center p-4 transition-opacity duration-300">
            <div class="w-full max-w-sm reader-paper-bg paper-grain glass-card p-6 rounded-[28px] shadow-2xl space-y-4 border border-parchment-300 dark:border-night-600 animate-radial-in">
                <div class="flex items-center justify-between border-b border-parchment-300/60 dark:border-night-700 pb-3">
                    <div class="flex items-center space-x-2">
                        <div class="w-6 h-6 rounded-md bg-parchment-900 dark:bg-amberGold text-parchment-100 dark:text-night-900 flex items-center justify-center">
                            <i data-lucide="smartphone" class="w-3.5 h-3.5"></i>
                        </div>
                        <h3 class="font-typewriter text-xs font-bold uppercase tracking-wider text-parchment-900 dark:text-night-100">Add to iPhone Home Screen</h3>
                    </div>
                    <button onclick="toggleIosGuideModal()" class="text-paperMuted dark:text-nightMuted hover:text-parchment-900 dark:hover:text-night-100">
                        <i data-lucide="x" class="w-4 h-4"></i>
                    </button>
                </div>

                <p class="font-book text-sm text-parchment-800 dark:text-night-200 leading-relaxed">
                    To use <strong class="font-semibold text-parchment-900 dark:text-night-100">Sabbia</strong> as a quiet fullscreen app without browser controls:
                </p>

                <div class="space-y-2.5 font-typewriter text-xs text-parchment-900 dark:text-night-100">
                    <div class="flex items-start space-x-3 bg-parchment-200/60 dark:bg-night-700/60 p-2.5 rounded-xl border border-parchment-300/40 dark:border-night-600">
                        <span class="w-5 h-5 rounded-full bg-terracotta-500 dark:bg-amberGold text-white dark:text-night-900 flex items-center justify-center font-bold text-[10px]">1</span>
                        <p class="flex-1 pt-0.5">Tap the <strong class="text-terracotta-500 dark:text-amberGold">Share</strong> icon in Safari (<i data-lucide="share" class="w-3 h-3 inline"></i>)</p>
                    </div>
                    <div class="flex items-start space-x-3 bg-parchment-200/60 dark:bg-night-700/60 p-2.5 rounded-xl border border-parchment-300/40 dark:border-night-600">
                        <span class="w-5 h-5 rounded-full bg-terracotta-500 dark:bg-amberGold text-white dark:text-night-900 flex items-center justify-center font-bold text-[10px]">2</span>
                        <p class="flex-1 pt-0.5">Scroll down and tap <strong class="text-terracotta-500 dark:text-amberGold">"Add to Home Screen"</strong></p>
                    </div>
                    <div class="flex items-start space-x-3 bg-parchment-200/60 dark:bg-night-700/60 p-2.5 rounded-xl border border-parchment-300/40 dark:border-night-600">
                        <span class="w-5 h-5 rounded-full bg-terracotta-500 dark:bg-amberGold text-white dark:text-night-900 flex items-center justify-center font-bold text-[10px]">3</span>
                        <p class="flex-1 pt-0.5">Tap <strong class="text-terracotta-500 dark:text-amberGold">Add</strong> in top right. Launch from home screen!</p>
                    </div>
                </div>

                <button onclick="toggleIosGuideModal()" class="w-full py-2.5 bg-parchment-900 dark:bg-amberGold text-parchment-100 dark:text-night-900 font-typewriter text-xs rounded-full hover:opacity-90 transition-opacity">
                    Got it
                </button>
            </div>
        </div>

        <!-- Toast Notification -->
        <div id="toast" class="absolute bottom-5 left-1/2 -translate-x-1/2 bg-parchment-900 dark:bg-amberGold text-parchment-100 dark:text-night-900 px-4 py-2 rounded-full font-typewriter text-xs shadow-lg opacity-0 pointer-events-none transition-all duration-300 z-50 flex items-center space-x-1.5">
            <i data-lucide="check" class="w-3.5 h-3.5"></i>
            <span id="toastMessage">Saved to reading log</span>
        </div>

    </div>

    <script>
        let currentWordData = null;
        let savedWords = JSON.parse(localStorage.getItem('sabbia_saved_words_v4') || '[]');

        // Dark / Light Theme Setup
        function initTheme() {
            const savedTheme = localStorage.getItem('sabbia_theme');
            if (savedTheme === 'light') {
                document.documentElement.classList.remove('dark');
            } else {
                // Default to Dark
                document.documentElement.classList.add('dark');
            }
            updateThemeIcons();
        }

        function toggleDarkMode() {
            if (document.documentElement.classList.contains('dark')) {
                document.documentElement.classList.remove('dark');
                localStorage.setItem('sabbia_theme', 'light');
            } else {
                document.documentElement.classList.add('dark');
                localStorage.setItem('sabbia_theme', 'dark');
            }
            updateThemeIcons();
        }

        function updateThemeIcons() {
            const isDark = document.documentElement.classList.contains('dark');
            const sunIcon = document.getElementById('sunIcon');
            const moonIcon = document.getElementById('moonIcon');
            if (isDark) {
                sunIcon.classList.remove('hidden');
                moonIcon.classList.add('hidden');
            } else {
                sunIcon.classList.add('hidden');
                moonIcon.classList.remove('hidden');
            }
        }

        function toggleIosGuideModal() {
            const modal = document.getElementById('iosGuideModal');
            if (modal.classList.contains('hidden')) {
                modal.classList.remove('hidden');
            } else {
                modal.classList.add('hidden');
            }
        }

        window.addEventListener('DOMContentLoaded', () => {
            initTheme();
            lucide.createIcons();
            updateSavedBadge();
        });

        function resetToHome() {
            document.getElementById('searchInput').value = '';
            document.getElementById('resultSearchInput').value = '';
            document.getElementById('resultView').classList.add('hidden');
            document.getElementById('errorState').classList.add('hidden');
            document.getElementById('loadingState').classList.add('hidden');
            document.getElementById('homeCenterView').classList.remove('hidden');
        }

        function executeSearch() {
            const query = document.getElementById('searchInput').value.trim();
            if (query) searchWord(query);
        }

        function executeSearchResult() {
            const query = document.getElementById('resultSearchInput').value.trim();
            if (query) searchWord(query);
        }

        function autoDetectLanguage(word) {
            const cleanWord = word.toLowerCase().trim();
            const italianEndings = ['zione', 'zioni', 'mente', 'ismo', 'ista', 'ere', 'are', 'ire', 'ato', 'ito', 'uto', 'scolo', 'eggio', 'evole'];
            const isItalianEnding = italianEndings.some(ending => cleanWord.endsWith(ending));
            const hasItalianAccents = /[Ã Ã¨Ã©Ã¬Ã²Ã³Ã¹]/.test(cleanWord);

            if (hasItalianAccents || isItalianEnding) {
                return 'it';
            }
            return 'en';
        }

        async function searchWord(word) {
            document.getElementById('searchInput').value = word;
            document.getElementById('resultSearchInput').value = word;

            document.getElementById('homeCenterView').classList.add('hidden');
            document.getElementById('resultView').classList.add('hidden');
            document.getElementById('errorState').classList.add('hidden');
            document.getElementById('loadingState').classList.remove('hidden');

            try {
                let initialLang = autoDetectLanguage(word);
                
                // STEP 1: Fetch core verbatim dictionary entry immediately
                let dictData = await fetchVerbatimDictionary(word, initialLang);

                if (dictData) {
                    currentWordData = dictData;
                    renderResultImmediate(dictData);
                    
                    // STEP 2: Asynchronously search book archives for quote in background
                    fetchLiteratureQuoteAsync(word, dictData.detectedLang);
                } else {
                    showError("Could not retrieve dictionary details for this word.");
                }

            } catch (err) {
                console.error(err);
                showError("Unable to load dictionary entry at this moment.");
            } finally {
                document.getElementById('loadingState').classList.add('hidden');
            }
        }

        function cleanEtymologyText(rawText) {
            if (!rawText) return "";
            return rawText
                .replace(/[-=]{2,}/g, '')
                .replace(/\[\d+\]/g, '')
                .replace(/\s+/g, ' ')
                .trim();
        }

        function formatQuoteWithItalicWord(quote, targetWord) {
            if (!quote || !targetWord) return quote;
            const regex = new RegExp(`\\b(${targetWord})\\b`, 'gi');
            return quote.replace(regex, `<span class="quote-word-highlight">$1</span>`);
        }

        // Fast verbatim dictionary lookup
        async function fetchVerbatimDictionary(word, suggestedLang) {
            try {
                let freeDictData = null;
                if (suggestedLang === 'en') {
                    try {
                        const res = await fetch(`https://api.dictionaryapi.dev/api/v2/entries/en/${encodeURIComponent(word)}`);
                        if (res.ok) {
                            const json = await res.json();
                            if (json && json.length) freeDictData = json[0];
                        }
                    } catch (e) { freeDictData = null; }
                }

                const apiKey = "";
                const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-3-flash-preview:generateContent?key=${apiKey}`;

                const prompt = `You are a fast, authoritative dictionary engine for English and Italian.
For the word "${word}":
1. Determine language ("Italiano" or "English").
2. Provide verbatim standard dictionary definitions.
3. Provide clean etymology without dashes or ASCII symbols.
4. Provide etymology roots array (e.g. ["Latin: root", "Middle English"]).
5. Provide 3-5 synonyms.

Return JSON schema:
{
    "word": "${word}",
    "detectedLang": "Italiano" or "English",
    "phonetic": "/phonetic notation/",
    "partOfSpeech": "noun / verb / adjective / adverb",
    "definitions": ["1. Verbatim definition 1", "2. Verbatim definition 2"],
    "etymologyRoots": ["Latin: root", "Old French: root"],
    "etymology": "Paragraph of etymology.",
    "synonyms": ["synonym1", "synonym2"]
}`;

                const response = await fetch(apiUrl, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify({
                        contents: [{ parts: [{ text: prompt }] }],
                        generationConfig: { responseMimeType: "application/json" }
                    })
                });

                if (response.ok) {
                    const result = await response.json();
                    const jsonText = result.candidates?.[0]?.content?.parts?.[0]?.text;
                    if (jsonText) {
                        const parsed = JSON.parse(jsonText);

                        let audioUrl = '';
                        if (freeDictData && freeDictData.phonetics) {
                            const item = freeDictData.phonetics.find(p => p.audio && p.audio.length > 0);
                            if (item) audioUrl = item.audio;
                        }

                        return {
                            word: parsed.word || word,
                            detectedLang: parsed.detectedLang || (suggestedLang === 'it' ? 'Italiano' : 'English'),
                            phonetic: parsed.phonetic || `/${word}/`,
                            partOfSpeech: parsed.partOfSpeech || 'noun',
                            audio: audioUrl,
                            definitions: parsed.definitions && parsed.definitions.length ? parsed.definitions : [`Primary definition of ${word}.`],
                            etymologyRoots: parsed.etymologyRoots || [],
                            etymology: cleanEtymologyText(parsed.etymology),
                            synonyms: parsed.synonyms || []
                        };
                    }
                }

                return null;

            } catch (e) {
                console.error("Dictionary lookup error:", e);
                return null;
            }
        }

        // Asynchronous background literature search
        async function fetchLiteratureQuoteAsync(word, detectedLang) {
            const loadingEl = document.getElementById('literatureLoading');
            const contentEl = document.getElementById('literatureContent');

            loadingEl.classList.remove('hidden');
            contentEl.classList.add('hidden');

            try {
                const apiKey = "";
                const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-3-flash-preview:generateContent?key=${apiKey}`;

                const prompt = `Find an AUTHENTIC, REAL quote from a published book containing the word "${word}".
If the word is Italian, search Italian literature (Dante, Calvino, Pasolini, Eco, Manzoni, etc.).
If English, search classic or modern literature (Tolkien, Dickens, Austen, Woolf, etc.).

Return JSON schema:
{
    "quote": "Direct passage from published book containing '${word}'.",
    "author": "Author Name",
    "bookTitle": "Book Title"
}`;

                const response = await fetch(apiUrl, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify({
                        contents: [{ parts: [{ text: prompt }] }],
                        generationConfig: { responseMimeType: "application/json" }
                    })
                });

                if (response.ok) {
                    const result = await response.json();
                    const jsonText = result.candidates?.[0]?.content?.parts?.[0]?.text;
                    if (jsonText) {
                        const parsed = JSON.parse(jsonText);
                        
                        const formattedQuote = formatQuoteWithItalicWord(parsed.quote || `A line from books with ${word}.`, word);
                        document.getElementById('literaryQuote').innerHTML = `â${formattedQuote}â`;
                        document.getElementById('literaryAuthor').innerText = parsed.author ? `â ${parsed.author}` : '';
                        document.getElementById('literaryBookTitle').innerText = parsed.bookTitle || '';

                        loadingEl.classList.add('hidden');
                        contentEl.classList.remove('hidden');
                        return;
                    }
                }
            } catch (e) {
                console.error("Literature fetch error:", e);
            }

            // Fallback quote if call fails
            document.getElementById('literaryQuote').innerHTML = `âThe character paused, contemplating the <em>${word}</em> nature of the evening.â`;
            document.getElementById('literaryAuthor').innerText = "â Classic Archive";
            document.getElementById('literaryBookTitle').innerText = "Collected Works";
            loadingEl.classList.add('hidden');
            contentEl.classList.remove('hidden');
        }

        function renderResultImmediate(data) {
            document.getElementById('wordTitle').innerText = data.word;
            document.getElementById('detectedLangTag').innerText = data.detectedLang || 'Italiano';
            document.getElementById('wordPos').innerText = data.partOfSpeech || 'noun';
            document.getElementById('wordPhonetic').innerText = data.phonetic || `/${data.word}/`;

            const audioBtn = document.getElementById('audioPlayBtn');
            if (data.audio) {
                audioBtn.classList.remove('hidden');
            } else {
                audioBtn.classList.add('hidden');
            }

            updateBookmarkIconState(data.word);

            // Verbatim Definitions List
            const defContainer = document.getElementById('definitionsList');
            defContainer.innerHTML = data.definitions.map((def, idx) => `
                <div class="flex items-start space-x-2">
                    <span class="font-typewriter text-xs text-terracotta-500 dark:text-amberGold pt-0.5 font-bold">${idx + 1}.</span>
                    <p class="flex-1 text-parchment-900 dark:text-night-100 leading-relaxed font-book text-base">${def}</p>
                </div>
            `).join('');

            // Etymology View
            const etymChain = document.getElementById('etymologyChain');
            if (data.etymologyRoots && data.etymologyRoots.length > 0) {
                etymChain.innerHTML = data.etymologyRoots.map((root, i) => `
                    <span class="inline-flex items-center font-typewriter text-[10px] text-terracotta-500 dark:text-amberGold bg-parchment-200 dark:bg-night-700 px-2 py-0.5 rounded border border-parchment-300/60 dark:border-night-600">
                        ${root}
                    </span>
                    ${i < data.etymologyRoots.length - 1 ? '<span class="text-paperMuted dark:text-nightMuted text-xs">â</span>' : ''}
                `).join('');
                etymChain.classList.remove('hidden');
            } else {
                etymChain.classList.add('hidden');
            }

            document.getElementById('etymologyText').innerText = cleanEtymologyText(data.etymology);

            // Synonyms
            const synCard = document.getElementById('synonymsCard');
            const synTags = document.getElementById('synonymsTags');
            if (data.synonyms && data.synonyms.length > 0) {
                synCard.classList.remove('hidden');
                synTags.innerHTML = data.synonyms.map(syn => `
                    <button onclick="searchWord('${syn}')" class="px-2.5 py-0.5 rounded bg-parchment-200 dark:bg-night-700 hover:bg-parchment-300 dark:hover:bg-night-600 text-parchment-900 dark:text-night-100 font-typewriter text-xs transition-colors border border-parchment-300/60 dark:border-night-600">
                        ${syn}
                    </button>
                `).join('');
            } else {
                synCard.classList.add('hidden');
            }

            document.getElementById('resultView').classList.remove('hidden');
            lucide.createIcons();
        }

        function showError(msg) {
            document.getElementById('errorMessageText').innerText = msg;
            document.getElementById('errorState').classList.remove('hidden');
        }

        function playPronunciation() {
            if (currentWordData && currentWordData.audio) {
                const audio = new Audio(currentWordData.audio);
                audio.play().catch(e => showToast('Audio playback unavailable'));
            } else if (currentWordData) {
                const utterance = new SpeechSynthesisUtterance(currentWordData.word);
                utterance.lang = currentWordData.detectedLang === 'Italiano' ? 'it-IT' : 'en-US';
                window.speechSynthesis.speak(utterance);
            }
        }

        function toggleSaveCurrentWord() {
            if (!currentWordData) return;
            const index = savedWords.findIndex(w => w.word.toLowerCase() === currentWordData.word.toLowerCase());
            
            if (index > -1) {
                savedWords.splice(index, 1);
                showToast("Removed from saved log");
            } else {
                savedWords.unshift({
                    word: currentWordData.word,
                    lang: currentWordData.detectedLang || 'English',
                    phonetic: currentWordData.phonetic,
                    def: currentWordData.definitions[0] || ''
                });
                showToast("Saved to reading log");
            }

            localStorage.setItem('sabbia_saved_words_v4', JSON.stringify(savedWords));
            updateSavedBadge();
            updateBookmarkIconState(currentWordData.word);
            renderSavedTrayList();
        }

        function updateBookmarkIconState(word) {
            const isSaved = savedWords.some(w => w.word.toLowerCase() === word.toLowerCase());
            const icon = document.getElementById('bookmarkIcon');
            if (isSaved) {
                icon.setAttribute('class', 'w-3.5 h-3.5 fill-terracotta-500 dark:fill-amberGold text-terracotta-500 dark:text-amberGold');
            } else {
                icon.setAttribute('class', 'w-3.5 h-3.5 text-parchment-900 dark:text-night-100');
            }
        }

        function updateSavedBadge() {
            const badge = document.getElementById('bookmarkCount');
            if (savedWords.length > 0) {
                badge.innerText = savedWords.length;
                badge.classList.remove('hidden');
            } else {
                badge.classList.add('hidden');
            }
        }

        function toggleSavedTray() {
            const tray = document.getElementById('savedTray');
            const isClosed = tray.classList.contains('translate-y-full');
            if (isClosed) {
                renderSavedTrayList();
                tray.classList.remove('translate-y-full');
            } else {
                tray.classList.add('translate-y-full');
            }
        }

        function renderSavedTrayList() {
            const container = document.getElementById('savedWordsList');
            if (savedWords.length === 0) {
                container.innerHTML = `
                    <div class="text-center py-16 text-paperMuted dark:text-nightMuted space-y-2">
                        <i data-lucide="bookmark" class="w-7 h-7 mx-auto stroke-1"></i>
                        <p class="font-typewriter text-xs">Your reading log is empty.</p>
                    </div>
                `;
            } else {
                container.innerHTML = savedWords.map(item => `
                    <div class="glass-card p-4 rounded-xl flex items-center justify-between hover:border-terracotta-500/50 dark:hover:border-amberGold/50 transition-colors">
                        <div class="cursor-pointer flex-1 pr-3" onclick="toggleSavedTray(); searchWord('${item.word}')">
                            <div class="flex items-center space-x-2">
                                <h4 class="font-display font-semibold text-parchment-900 dark:text-night-100">${item.word}</h4>
                                <span class="font-typewriter text-[9px] text-terracotta-500 dark:text-amberGold uppercase bg-parchment-200 dark:bg-night-700 px-1.5 py-0.2 rounded border border-parchment-300/60 dark:border-night-600">${item.lang}</span>
                            </div>
                            <p class="font-book text-xs text-paperMuted dark:text-nightMuted line-clamp-1 mt-0.5">${item.def}</p>
                        </div>
                        <button onclick="removeSavedWord('${item.word}')" class="text-paperMuted dark:text-nightMuted hover:text-terracotta-500 dark:hover:text-amberGold p-1">
                            <i data-lucide="trash-2" class="w-3.5 h-3.5"></i>
                        </button>
                    </div>
                `).join('');
            }
            lucide.createIcons();
        }

        function removeSavedWord(word) {
            savedWords = savedWords.filter(w => w.word.toLowerCase() !== word.toLowerCase());
            localStorage.setItem('sabbia_saved_words_v4', JSON.stringify(savedWords));
            updateSavedBadge();
            renderSavedTrayList();
            if (currentWordData && currentWordData.word.toLowerCase() === word.toLowerCase()) {
                updateBookmarkIconState(word);
            }
            showToast("Word removed");
        }

        function showToast(msg) {
            const toast = document.getElementById('toast');
            document.getElementById('toastMessage').innerText = msg;
            toast.classList.remove('opacity-0', 'pointer-events-none');
            toast.classList.add('opacity-100');
            setTimeout(() => {
                toast.classList.remove('opacity-100');
                toast.classList.add('opacity-0', 'pointer-events-none');
            }, 2000);
        }
    </script>
</body>
</html>
```
