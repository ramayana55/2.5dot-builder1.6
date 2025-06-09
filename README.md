<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>2.5dot-builder1.6</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        body {
            font-family: 'Hiragino Kaku Gothic ProN', 'Meiryo', sans-serif;
            background-color: #f9fafb;
            color: #1f2937;
        }
        .prose h1, .prose h2, .prose h3 {
            border-bottom: 1px solid #d1d5db;
            padding-bottom: 0.3em;
        }
        .prose h1 {
            font-size: 2.25rem;
        }
        .prose h2 {
            font-size: 1.875rem;
        }
         .prose h3 {
            font-size: 1.5rem;
        }
        .prose ul {
            list-style-type: disc;
            padding-left: 1.5rem;
        }
        .prose li {
            margin-bottom: 0.5rem;
        }
        .prose a {
            color: #2563eb;
            text-decoration: none;
        }
        .prose a:hover {
            text-decoration: underline;
        }
        .prose code {
            background-color: #e5e7eb;
            padding: 0.2em 0.4em;
            margin: 0;
            font-size: 85%;
            border-radius: 6px;
        }
    </style>
</head>
<body class="p-4 md:p-8 lg:p-12">
    <main class="prose prose-lg max-w-4xl mx-auto bg-white p-8 rounded-xl shadow-md">
        
        <h1>2.5dot-builder1.6</h1>

        <img src="https://placehold.co/800x450/e2e8f0/334155?text=2.5D%E3%83%89%E3%83%83%E3%83%88%E7%B5%B5%E3%83%93%E3%83%AB%E3%83%80%E3%83%BC%20UI" alt="2.5Dドット絵ビルダーの操作画面" class="rounded-lg shadow-lg my-8">

        <p>ドット絵を描くような感覚で、手軽に3Dの立体作品（ボクセルアート）を制作できるWebアプリケーションです。</p>

        <h2><i data-lucide="star" class="inline-block w-6 h-6 mr-2"></i> 主な機能</h2>
        <p>このアプリケーションには、あなたの創造性をサポートするための様々な機能が搭載されています。</p>

        <div class="grid md:grid-cols-2 gap-8">
            <div>
                <h3><i data-lucide="edit-3" class="inline-block w-5 h-5 mr-2"></i> 描画 & 編集</h3>
                <ul>
                    <li><strong>直感的な操作</strong>: マウスのクリックだけでブロックを配置、積層、削除できます。</li>
                    <li><strong>多彩な描画ツール</strong>:
                        <ul>
                            <li><strong>ペン</strong>: 1マスずつ正確に描画します。</li>
                            <li><strong>バケツ</strong>: 同じ色の連結部分を一度に塗りつぶします。</li>
                            <li><strong>スポイト</strong>: キャンバス上の色を簡単に抽出できます。</li>
                        </ul>
                    </li>
                    <li><strong>柔軟なパレット管理</strong>:
                        <ul>
                            <li>カスタムカラーの作成と保存。</li>
                            <li>ドラッグ＆ドロップによるパレットの並べ替え。</li>
                            <li>パレットの名称変更、リセット機能。</li>
                        </ul>
                    </li>
                    <li><strong>アンドゥ/リドゥ</strong>: 操作の取り消し・やり直しが可能です。</li>
                </ul>
            </div>
            <div>
                <h3><i data-lucide="settings-2" class="inline-block w-5 h-5 mr-2"></i> カスタマイズ</h3>
                 <ul>
                    <li><strong>グリッド設定</strong>: キャンバスのサイズを自由に変更できます。</li>
                    <li><strong>表示設定</strong>:
                        <ul>
                            <li>背景色の変更</li>
                            <li>2Dモードと3Dモードの切り替え</li>
                            <li>グリッド線や段数の表示/非表示</li>
                            <li>カメラの回転ロックと視点リセット</li>
                        </ul>
                    </li>
                 </ul>
                <h3><i data-lucide="file-down" class="inline-block w-5 h-5 mr-2"></i> ファイル操作</h3>
                <ul>
                    <li><strong>セーブ & ロード</strong>: 作業中のプロジェクトを<code>JSON</code>形式で保存・読込できます。</li>
                    <li><strong>多様なエクスポート形式</strong>:
                        <ul>
                            <li><strong>PNG</strong>: 作品のスクリーンショットを画像として保存します。</li>
                            <li><strong>STL</strong>: 3Dプリンター用の標準形式で出力します。</li>
                            <li><strong>PLY / OBJ</strong>: 色情報を含む、汎用的な3Dモデル形式で保存します。</li>
                        </ul>
                    </li>
                </ul>
            </div>
        </div>
        
        <h2><i data-lucide="tool" class="inline-block w-6 h-6 mr-2"></i> 使用技術</h2>
        <div class="flex flex-wrap gap-4 my-4">
            <span class="bg-blue-100 text-blue-800 text-sm font-medium mr-2 px-2.5 py-0.5 rounded">HTML</span>
            <span class="bg-blue-100 text-blue-800 text-sm font-medium mr-2 px-2.5 py-0.5 rounded">CSS</span>
            <span class="bg-yellow-100 text-yellow-800 text-sm font-medium mr-2 px-2.5 py-0.5 rounded">JavaScript</span>
            <span class="bg-green-100 text-green-800 text-sm font-medium mr-2 px-2.5 py-0.5 rounded">Three.js</span>
            <span class="bg-purple-100 text-purple-800 text-sm font-medium mr-2 px-2.5 py-0.5 rounded">Tailwind CSS</span>
            <span class="bg-indigo-100 text-indigo-800 text-sm font-medium mr-2 px-2.5 py-0.5 rounded">Lucide Icons</span>
        </div>
        <ul>
            <li><strong>フロントエンド</strong>: HTML, CSS, JavaScript</li>
            <li><strong>3Dレンダリング</strong>: <a href="https://threejs.org/" target="_blank" rel="noopener noreferrer">Three.js</a></li>
            <li><strong>UIフレームワーク</strong>: <a href="https://tailwindcss.com/" target="_blank" rel="noopener noreferrer">Tailwind CSS</a></li>
            <li><strong>アイコン</strong>: <a href="https://lucide.dev/" target="_blank" rel="noopener noreferrer">Lucide Icons</a></li>
        </ul>

        <h2><i data-lucide="rocket" class="inline-block w-6 h-6 mr-2"></i> 使い方</h2>
        <ol class="list-decimal pl-5">
            <li>ブラウザでアプリケーションを開きます。</li>
            <li>右側のコントロールパネルから色やツールを選択します。</li>
            <li>左側のキャンバスにマウスで描画します。</li>
            <li>完成した作品は、様々な形式でエクスポートできます。</li>
        </ol>
        <p class="mt-4">より詳しい操作方法は、以下のインタラクティブマニュアルをご覧ください。</p>
        <div class="my-4 no-prose">
             <a href="https://jovial-panda-bfe044.netlify.app/" target="_blank" rel="noopener noreferrer" class="inline-flex items-center justify-center px-5 py-3 border border-transparent text-base font-medium rounded-md text-white bg-blue-600 hover:bg-blue-700">
                <i data-lucide="book-open" class="inline-block w-5 h-5 mr-3"></i>
                インタラクティブマニュアルを開く
            </a>
        </div>
        <p>ぜひ、あなただけのオリジナル3Dドット絵を作成してみてください！</p>
    </main>

    <script>
        lucide.createIcons();
    </script>
</body>
</html>

