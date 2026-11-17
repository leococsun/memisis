<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Memisis - 專案知識庫</title>
    <!-- 引入 Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="./assets/css/style.css">
</head>
<body class="bg-slate-50 text-slate-800 min-h-screen flex flex-col">
    <!-- 頂部導覽列 (Sticky Navbar) -->
    <header class="sticky top-0 z-50 bg-white/80 backdrop-blur-md border-b border-slate-200">
        <div class="max-w-5xl mx-auto px-6 h-16 flex items-center justify-between">
            <a href="./index.html" class="font-bold text-xl text-indigo-600 flex items-center gap-2">
                <span>🧠</span> Memisis
            </a>
            <nav class="flex items-center gap-6 text-sm font-medium text-slate-600">
                <a href="./index.html" class="hover:text-indigo-600 transition">首頁</a>
                <a href="https://github.com/leococsun/memisis/blob/main/agents.md" target="_blank" class="hover:text-indigo-600 transition">AGENTS.md</a>
                <a href="https://github.com/leococsun/memisis" target="_blank" class="hover:text-indigo-600 transition">GitHub</a>
            </nav>
        </div>
    </header>

    <!-- 主視覺區 (Hero Section) -->
    <section class="bg-gradient-to-b from-indigo-50/50 to-slate-50 py-16 px-6 border-b border-slate-100">
        <div class="max-w-3xl mx-auto text-center">
            <h1 class="text-4xl font-extrabold text-slate-900 tracking-tight mb-4">
                Memisis 專案知識與實驗室
            </h1>
            <p class="text-lg text-slate-600 mb-8">
                本網站透過結構化規範與 AI 代理協作建立，記錄各項學習筆記與專案成果。
            </p>
            <div class="flex justify-center gap-4">
                <a href="#content-grid" class="bg-indigo-600 hover:bg-indigo-700 text-white font-medium px-6 py-3 rounded-lg shadow-sm transition">
                    瀏覽文章列表
                </a>
                <a href="https://github.com/leococsun/memisis" target="_blank" class="bg-white hover:bg-slate-100 border border-slate-300 text-slate-700 font-medium px-6 py-3 rounded-lg shadow-sm transition">
                    查看原始碼
                </a>
            </div>
        </div>
    </section>

    <!-- 內容卡片列表區 (Content Grid) -->
    <main class="flex-grow max-w-5xl mx-auto px-6 py-12 w-full">
        <div class="flex items-center justify-between mb-8">
            <h2 class="text-2xl font-bold text-slate-900">專案內容與筆記</h2>
            <span class="text-xs font-semibold bg-indigo-100 text-indigo-700 px-3 py-1 rounded-full">SOP 驅動開發</span>
        </div>

        <div id="content-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
            
            <!-- 示範卡片 1 -->
            <article class="bg-white rounded-xl border border-slate-200 overflow-hidden shadow-sm hover:shadow-md transition flex flex-col">
                <div class="p-6 flex-grow">
                    <div class="flex items-center justify-between mb-3">
                        <span class="text-xs font-semibold text-indigo-600 bg-indigo-50 px-2.5 py-1 rounded">重大更新</span>
                        <span class="text-xs text-slate-400">2026-10-26</span>
                    </div>
                    <h3 class="text-lg font-bold text-slate-900 mb-2">2026-10-26更新</h3>
                    <p class="text-slate-600 text-sm line-clamp-3">
                        這是 Memisis 10/26更新說明。
                    </p>
                </div>
                <div class="px-6 py-4 bg-slate-50 border-t border-slate-100 flex justify-between items-center">
                    <a href="https://github.com/leococsun/memisis/blob/main/raw/2026-10-26_Update_Notice_Off_the_Rails.md" class="text-indigo-600 hover:text-indigo-700 text-sm font-semibold inline-flex items-center gap-1">
                        閱讀文章 &rarr;
                    </a>
                </div>
            </article>

            <!-- 預留未來新增卡片的位置 -->
            <article class="bg-slate-50 rounded-xl border-2 border-dashed border-slate-300 p-6 flex flex-col items-center justify-center text-center">
                <div class="text-3xl mb-2">➕</div>
                <h3 class="text-md font-bold text-slate-700 mb-1">準備新增下一篇</h3>
                <p class="text-slate-500 text-xs mb-4">依照 AGENTS.md 規則快速擴充新內容</p>
                <span class="text-xs text-indigo-600 font-medium">Coming Soon...</span>
            </article>

        </div>
    </main>

    <!-- 頁尾 -->
    <footer class="bg-white border-t border-slate-200 py-6 text-center text-sm text-slate-500">
        <p>&copy; 2026 Memisis. Powered by GitHub Pages & AGENTS.md workflow.</p>
    </footer>

    <script src="./assets/js/main.js"></script>
</body>
</html>
