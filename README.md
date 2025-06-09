<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>インタラクティブ・マニュアル: 2.5Dドット絵ビルダー</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        html {
            scroll-behavior: smooth;
        }
        body {
            background-color: #f8f7f5;
            color: #3d3d3d;
            font-family: 'Hiragino Kaku Gothic ProN', 'Meiryo', sans-serif;
        }
        .highlight {
            animation: highlight-animation 1.5s ease-out;
        }
        @keyframes highlight-animation {
            0% { box-shadow: 0 0 0 4px rgba(66, 153, 225, 0.6); }
            100% { box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06); }
        }
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #f1f1f1;
        }
        ::-webkit-scrollbar-thumb {
            background: #c4c4c4;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #a1a1a1;
        }
        .nav-item.active {
            background-color: #e2e8f0;
            color: #2c5282;
            font-weight: 600;
        }
    </style>
</head>
<body class="antialiased">

    <div class="container mx-auto px-4 py-8">
        
        <header class="text-center mb-10">
            <h1 class="text-4xl font-bold text-gray-800">2.5Dドット絵ビルダー</h1>
            <p class="text-xl text-gray-600 mt-2">インタラクティブ・クイックリファレンス</p>
        </header>

        <div class="p-6 bg-white rounded-xl shadow-md mb-8 border border-gray-200">
            <h2 class="text-xl font-semibold text-gray-700 mb-2 flex items-center"><i data-lucide="info" class="w-5 h-5 mr-2"></i>このガイドの使い方</h2>
            <p class="text-gray-600">このガイドは、「2.5Dドット絵ビルダー」の機能を素早く見つけるための対話的なマニュアルです。左のナビゲーションメニューをクリックするか、下の検索ボックスにキーワードを入力して、知りたい機能を探してください。</p>
        </div>


        <div class="flex flex-col md:flex-row gap-8">
            <aside class="w-full md:w-1/4 top-8 self-start md:sticky">
                <div class="p-4 bg-white rounded-lg shadow-sm border border-gray-200">
                    <div class="mb-4">
                        <input type="search" id="search-box" placeholder="キーワードで検索..." class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 transition">
                    </div>
                    <nav id="navigation"></nav>
                </div>
            </aside>

            <main id="main-content" class="w-full md:w-3/4">
                
            </main>
        </div>
    </div>

    <script>
        const manualData = [
            {
                category: '基本的な使い方',
                items: [
                    { id: 'basic-click', title: 'ブロックを置く/積む (左クリック)', icon: 'mouse-pointer-click', content: '<ul><li class="mb-2"><b>何もないマス:</b> 選択中の色のブロックが1段置かれます。</li><li class="mb-2"><b>同じ色のブロックがあるマス:</b> ブロックが1段ずつ積み上がります（最大5段）。</li><li class="mb-2"><b>最大（5段）のブロック:</b> もう一度クリックすると、1段に戻ります。</li><li><b>違う色のブロックがあるマス:</b> その色で1段のブロックに置き換わります。</li></ul>' },
                    { id: 'basic-right-click', title: 'ブロックを減らす (右クリック)', icon: 'eraser', content: '<p>ブロックがあるマスを右クリックすると、ブロックの段数が1段ずつ減っていきます。</p>' },
                    { id: 'basic-view', title: '視点の変更', icon: 'move-3d', content: '<ul><li class="mb-2"><b>回転:</b> キャンバス上をドラッグすると、視点を360度回転できます。</li><li><b>拡大・縮小:</b> マウスホイールをスクロールします。</li></ul>' }
                ]
            },
            {
                category: '画面の構成',
                items: [
                     { id: 'layout', title: 'キャンバスとコントロールパネル', icon: 'layout-panel-left', content: '<p>画面は、作品を制作する左側の「キャンバス」と、各種設定を行う右側の「コントロールパネル」で構成されています。「コントロールパネル」は「描画」「設定」「ファイル」のタブで機能を切り替えます。</p>' }
                ]
            },
            {
                category: '「描画」タブ',
                items: [
                    { id: 'tool-pen', title: 'ペンツール', icon: 'pen-tool', content: '<p>ブロックを1マスずつ置いたり、積んだり、色を変えたりする基本的なツールです。</p>' },
                    { id: 'tool-bucket', title: 'バケツツール', icon: 'paint-bucket', content: '<p>クリックしたマスと同じ色で、隣接している全てのブロックを選択中の色で一気に塗りつぶします。</p>' },
                    { id: 'tool-eyedropper', title: 'スポイトツール', icon: 'eyedropper', content: '<p>キャンバス上のブロックをクリックして、その色を抽出します。抽出した色は「カスタムカラー」に設定され、すぐに使用できます。</p>' },
                    { id: 'palette-custom', title: 'カスタムカラー & パレット', icon: 'palette', content: '<ul><li class="mb-2"><b>作成:</b> カラーピッカーで好きな色を作成します。</li><li class="mb-2"><b>追加/更新:</b> 「パレットに追加/更新」ボタンでパレットに色を追加・更新します。</li><li class="mb-2"><b>削除:</b> 「選択色を削除」ボタンで不要なカスタムカラーを削除します（デフォルト色は削除不可）。</li><li class="mb-2"><b>並べ替え:</b> パレットの色をドラッグ＆ドロップして、好きな順番に並べ替えられます。</li><li class="mb-2"><b>名前の変更:</b> パレットの色をダブルクリックすると、名前を自由に変更できます。</li><li class="mb-2"><b>リセット:</b> 「リセット」ボタンで、追加したカスタムカラーを全て削除し、初期状態に戻します。</li></ul>' },
                    { id: 'canvas-actions', title: 'キャンバス操作', icon: 'undo-2', content: '<p><b>元に戻す(Undo):</b> 操作を一つ前に戻します。<br><b>やり直す(Redo):</b> 元に戻した操作をやり直します。<br><b>キャンバスをクリア:</b> キャンバス上の全てのブロックを一括で削除します。</p>' }
                ]
            },
            {
                category: '「設定」タブ',
                items: [
                     { id: 'settings-grid', title: 'グリッド設定', icon: 'grid-2x2', content: '<p>キャンバスのマス目の数（幅・高さ）や、サイズ変更時の基準位置（9方向から選択）を調整できます。「設定を更新」で反映されます。</p>' },
                     { id: 'settings-display', title: '表示設定', icon: 'settings-2', content: '<ul><li class="mb-2"><b>背景色:</b> キャンバスの背景色を変更します。</li><li class="mb-2"><b>2Dモード:</b> 視点を真上からの平面表示に切り替えます。</li><li class="mb-2"><b>グリッド線:</b> ガイド線の表示/非表示を切り替えます。</li><li class="mb-2"><b>段数表示:</b> ブロックの段数を数字で表示/非表示します。</li><li class="mb-2"><b>回転ロック:</b> 視点の回転を一時的に無効にします。</li><li class="mb-2"><b>真上から見る:</b> 視点を真上からのビューにリセットします。</li></ul>' }
                ]
            },
            {
                category: '「ファイル」タブ',
                items: [
                     { id: 'file-saveload', title: '保存 & 読込 (.json)', icon: 'save', content: '<p>現在の作品の状態（ブロック配置、パレット情報など）を<code>.json</code>ファイルとしてPCに保存したり、保存したファイルを読み込んで作業を再開したりできます。</p>' },
                     { id: 'file-export', title: 'エクスポート', icon: 'download', content: '<p>作成した作品を様々な形式で書き出せます。</p><ul><li class="mb-2"><b>PNG:</b> 現在の視点から見た画像として保存します。</li><li class="mb-2"><b>STL:</b> 3Dプリンター向けの形式で保存します（色なし）。</li><li class="mb-2"><b>PLY:</b> 色情報を含む3Dモデルとして保存します。</li><li class="mb-2"><b>OBJ:</b> 色情報とセットになった汎用的な3Dモデルとして保存します。</li></ul>' },
                     { id: 'file-canvas-size', title: 'キャンバスサイズ変更', icon: 'maximize', content: '<p>キャンバスの表示領域の幅と高さをピクセル単位で変更できます。</p>' }
                ]
            }
        ];

        const mainContent = document.getElementById('main-content');
        const navigation = document.getElementById('navigation');
        const searchBox = document.getElementById('search-box');

        const renderContent = (filterText = '') => {
            mainContent.innerHTML = '';
            const lowerFilterText = filterText.toLowerCase();

            manualData.forEach(categoryData => {
                const filteredItems = categoryData.items.filter(item => 
                    item.title.toLowerCase().includes(lowerFilterText) || 
                    item.content.toLowerCase().includes(lowerFilterText) ||
                    categoryData.category.toLowerCase().includes(lowerFilterText)
                );

                if (filteredItems.length > 0) {
                    const categorySection = document.createElement('section');
                    categorySection.id = `category-${categoryData.category.replace(/\s+/g, '-')}`;
                    categorySection.className = 'mb-10';

                    const categoryTitle = document.createElement('h2');
                    categoryTitle.className = 'text-2xl font-bold text-gray-700 mb-6 border-b-2 border-blue-200 pb-2';
                    categoryTitle.textContent = categoryData.category;
                    categorySection.appendChild(categoryTitle);

                    const itemsGrid = document.createElement('div');
                    itemsGrid.className = 'grid grid-cols-1 lg:grid-cols-2 gap-6';

                    filteredItems.forEach(item => {
                        const card = document.createElement('div');
                        card.id = `card-${item.id}`;
                        card.className = 'bg-white p-6 rounded-xl shadow-md border border-gray-200 hover:shadow-lg transition-shadow duration-300';
                        card.innerHTML = `
                            <div class="flex items-center text-blue-600 mb-4">
                                <i data-lucide="${item.icon}" class="w-6 h-6 mr-3"></i>
                                <h3 class="text-xl font-semibold text-gray-800">${item.title}</h3>
                            </div>
                            <div class="text-gray-600 leading-relaxed">${item.content}</div>
                        `;
                        itemsGrid.appendChild(card);
                    });

                    categorySection.appendChild(itemsGrid);
                    mainContent.appendChild(categorySection);
                }
            });
            
            lucide.createIcons();
            renderNavigation(filterText);
        };
        
        const renderNavigation = (filterText = '') => {
            navigation.innerHTML = '';
            const lowerFilterText = filterText.toLowerCase();

            manualData.forEach(categoryData => {
                const hasVisibleItems = categoryData.items.some(item => 
                    item.title.toLowerCase().includes(lowerFilterText) || 
                    item.content.toLowerCase().includes(lowerFilterText) ||
                    categoryData.category.toLowerCase().includes(lowerFilterText)
                );

                if(hasVisibleItems) {
                    const categoryWrapper = document.createElement('div');
                    categoryWrapper.className = 'mb-4';
                    
                    const categoryTitle = document.createElement('h3');
                    categoryTitle.className = 'px-3 py-2 text-sm font-bold text-gray-500 uppercase tracking-wider';
                    categoryTitle.textContent = categoryData.category;
                    categoryWrapper.appendChild(categoryTitle);
                    
                    const list = document.createElement('ul');
                    categoryData.items.forEach(item => {
                         if (item.title.toLowerCase().includes(lowerFilterText) || 
                             item.content.toLowerCase().includes(lowerFilterText) ||
                             categoryData.category.toLowerCase().includes(lowerFilterText))
                         {
                            const listItem = document.createElement('li');
                            const link = document.createElement('a');
                            link.href = `#card-${item.id}`;
                            link.textContent = item.title;
                            link.dataset.targetId = item.id;
                            link.className = 'nav-item block px-3 py-2 text-gray-700 rounded-md hover:bg-gray-100 transition-colors text-sm';
                            link.addEventListener('click', (e) => {
                                e.preventDefault();
                                document.querySelectorAll('.nav-item').forEach(el => el.classList.remove('active'));
                                e.target.classList.add('active');
                                const targetCard = document.getElementById(`card-${item.id}`);
                                if (targetCard) {
                                    const yOffset = -80; 
                                    const y = targetCard.getBoundingClientRect().top + window.pageYOffset + yOffset;
                                    window.scrollTo({top: y, behavior: 'smooth'});

                                    targetCard.classList.add('highlight');
                                    setTimeout(() => targetCard.classList.remove('highlight'), 1500);
                                }
                            });
                            listItem.appendChild(link);
                            list.appendChild(listItem);
                        }
                    });
                    categoryWrapper.appendChild(list);
                    navigation.appendChild(categoryWrapper);
                }
            });
        };

        searchBox.addEventListener('input', (e) => {
            renderContent(e.target.value);
        });

        document.addEventListener('DOMContentLoaded', () => {
            renderContent();
        });
    </script>
</body>
</html>
