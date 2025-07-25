<script type="text/javascript">
        var gk_isXlsx = false;
        var gk_xlsxFileLookup = {};
        var gk_fileData = {};
        function filledCell(cell) {
          return cell !== '' && cell != null;
        }
        function loadFileData(filename) {
        if (gk_isXlsx && gk_xlsxFileLookup[filename]) {
            try {
                var workbook = XLSX.read(gk_fileData[filename], { type: 'base64' });
                var firstSheetName = workbook.SheetNames[0];
                var worksheet = workbook.Sheets[firstSheetName];

                // Convert sheet to JSON to filter blank rows
                var jsonData = XLSX.utils.sheet_to_json(worksheet, { header: 1, blankrows: false, defval: '' });
                // Filter out blank rows (rows where all cells are empty, null, or undefined)
                var filteredData = jsonData.filter(row => row.some(filledCell));

                // Heuristic to find the header row by ignoring rows with fewer filled cells than the next row
                var headerRowIndex = filteredData.findIndex((row, index) =>
                  row.filter(filledCell).length >= filteredData[index + 1]?.filter(filledCell).length
                );
                // Fallback
                if (headerRowIndex === -1 || headerRowIndex > 25) {
                  headerRowIndex = 0;
                }

                // Convert filtered JSON back to CSV
                var csv = XLSX.utils.aoa_to_sheet(filteredData.slice(headerRowIndex)); // Create a new sheet from filtered array of arrays
                csv = XLSX.utils.sheet_to_csv(csv, { header: 1 });
                return csv;
            } catch (e) {
                console.error(e);
                return "";
            }
        }
        return gk_fileData[filename] || "";
        }
        </script><!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>STRANGE FRAME 展 : 수상한 틀 - 노매드 그라운드</title>
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@fortawesome/fontawesome-free@6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@300;400;500;700;900&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Noto Sans KR', sans-serif;
            background: linear-gradient(135deg, #1a1a1a 0%, #2d1b1b 50%, #1a1a1a 100%);
            min-height: 100vh;
        }
        .glass-effect {
            background: rgba(255, 255, 255, 0.03);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        .text-shadow {
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.8);
        }
        .poster-shadow {
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.6), 0 0 20px rgba(220, 38, 38, 0.2);
        }
        .red-glow {
            box-shadow: 0 0 20px rgba(220, 38, 38, 0.3);
        }
        .quote-style {
            border-left: 4px solid #dc2626;
            padding-left: 1rem;
            margin: 1.5rem 0;
            background: rgba(220, 38, 38, 0.1);
            border-radius: 0 8px 8px 0;
        }
    </style>
</head>
<body class="text-gray-100">
    <!-- Header -->
    <header class="relative overflow-hidden py-8">
        <div class="absolute inset-0 bg-gradient-to-r from-red-900/20 to-gray-900/20"></div>
        <div class="container mx-auto px-4 relative z-10">
            <div class="text-center">
                <h1 class="text-4xl md:text-6xl font-black text-red-500 mb-2 text-shadow tracking-tight">
                    STRANGE FRAME
                </h1>
                <h2 class="text-2xl md:text-3xl font-bold text-white mb-4 text-shadow">
                    수상한 틀
                </h2>
                <p class="text-lg text-red-400 font-medium">
                    노매드 그라운드 × 청년범아티스트연합회
                </p>
            </div>
        </div>
    </header>

    <!-- Main Content -->
    <main class="container mx-auto px-4 pb-8">
        <!-- Poster and Basic Info Section -->
        <section class="grid lg:grid-cols-2 gap-8 mb-12">
            <!-- Poster -->
            <div class="flex justify-center">
                <div class="poster-shadow rounded-lg overflow-hidden max-w-md w-full">
                    <img src="https://page.gensparksite.com/v1/base64_upload/c1db25c832c20bb9afd25f5b68ad1d8b" 
                         alt="STRANGE FRAME 展 : 수상한 틀 포스터" 
                         class="w-full h-auto object-cover">
                </div>
            </div>

            <!-- Exhibition Info -->
            <div class="space-y-6">
                <div class="glass-effect rounded-lg p-6">
                    <h3 class="text-2xl font-bold text-red-400 mb-4 flex items-center">
                        <i class="fas fa-calendar-alt mr-3"></i>전시 정보
                    </h3>
                    <div class="space-y-3 text-lg">
                        <div class="flex items-start">
                            <span class="font-semibold text-red-300 w-20">일시</span>
                            <span>2025.07.28 ~ 08.03</span>
                        </div>
                        <div class="flex items-start">
                            <span class="font-semibold text-red-300 w03">장소</span>
                            <span>향담갤러리<br><span class="text-gray-400 text-sm">광주 동구 예술길2-1</span></span>
                        </div>
                        <div class="flex items-start">
                            <span class="font-semibold text-red-300 w-20">주최</span>
                            <span>노매드 그라운드<br>청년범아티스트연합회</span>
                        </div>
                    </div>
                </div>

                <div class="glass-effect rounded-lg p-6">
                    <h3 class="text-2xl font-bold text-red-400 mb-4 flex items-center">
                        <i class="fas fa-link mr-3"></i>관련 링크
                    </h3>
                    <div class="space-y-3">
                        <a href="https://whattime.co.kr/nomadground" 
                           class="flex items-center bg-red-600 hover:bg-red-700 text-white px-4 py-3 rounded-lg transition duration-300 red-glow">
                            <i class="fas fa-ticket-alt mr-3"></i>
                            <span class="font-semibold">전시 예약하기</span>
                        </a>
                        <a href="https://instagram.com/wenomadground" 
                           class="flex items-center text-gray-300 hover:text-white transition duration-300">
                            <i class="fab fa-instagram mr-3 text-red-400"></i>
                            @wenomadground
                        </a>
                        <a href="https://www.newssunday.co.kr/bbs/board.php?bo_table=news&wr_id=234893" 
                           class="flex items-center text-gray-300 hover:text-white transition duration-300">
                            <i class="fas fa-newspaper mr-3 text-red-400"></i>
                            관련 기사 보기
                        </a>
                    </div>
                </div>
            </div>
        </section>

        <!-- About Nomad Ground -->
        <section class="glass-effect rounded-lg p-8 mb-12">
            <h3 class="text-3xl font-bold text-red-400 mb-6 text-center">
                노매드 그라운드 소개
            </h3>
            <div class="max-w-4xl mx-auto text-lg leading-relaxed space-y-4">
                <p class="text-center text-xl text-red-300 font-medium mb-6">
                    Nomad Ground × 청년범아티스트연합회
                </p>
                <p>
                    노매드그라운드(Nomad Ground)는 <strong class="text-red-300">'경계 없이 이동하며 머무르지 않는 자'</strong>를 뜻하는 "노매드(Nomad)"와, <strong class="text-red-300">'근거지이자 활동의 무대'</strong>를 뜻하는 "그라운드(Ground)"의 결합어입니다.
                </p>
                <p>
                    우리는 고정된 틀을 벗어나, 경계 없는 사유와 실행을 통해 새로운 문화예술의 현장을 만들어갑니다. 각자의 감각과 철학으로 어디서든 뿌리내리고 연결하는, 살아 있는 창작의 활동지입니다.
                </p>
                <p>
                    이번 전시는 그 움직임의 첫 시도이자, 지역 청년 창작자들이 스스로 사유하고 표현하며 연결되는, 작고도 깊은 문화 실험의 시작점입니다.
                </p>
            </div>
        </section>

        <!-- Exhibition Prologue -->
        <section class="glass-effect rounded-lg p-8">
            <h3 class="text-3xl font-bold text-red-400 mb-6 text-center">
                전시 프롤로그
            </h3>
            <div class="max-w-4xl mx-auto text-lg leading-relaxed space-y-6">
                <h4 class="text-2xl font-bold text-center text-red-300 mb-8">
                    〈STRANGE FRAME 展 : 수상한 틀〉
                </h4>
                
                <p class="text-xl text-center text-red-200 font-medium">
                    우리는 언제부터<br>
                    진실을 외면하고,<br>
                    낯선 불안을 '틀'에 가둔 채 살아왔을까요?
                </p>
                
                <div class="quote-style">
                    <p class="text-gray-200 italic">
                        조지 오웰의 『동물농장』은 말합니다.<br>
                        "진실은 반복되는 거짓 속에서 사라지며, 눈앞의 사실보다 귀에 익은 거짓이 더 쉽게 받아들여진다."<br>
                        "공포는 최고의 복종을 이끌어내며, 질문하지 않는 자만이 살아남는다."
                    </p>
                </div>
                
                <p class="text-center text-xl font-medium text-red-200">
                    그러나 진실은, 여전히 그 자리에 있습니다.<br>
                    다만, 감춰져 있을 뿐입니다.
                </p>
                
                <p>
                    단순화된 프레임, 생각 없이 소비되는 언어들. 편리한 사고는 삶을 간편하게 만들지만, 그것이 과연 인간으로서의 진정한 자유와 행복을 가능하게 할까요?
                </p>
                
                <div class="quote-style">
                    <p class="text-red-200 font-semibold text-center">
                        "자유란 남들이 듣기 싫어하는 말을 할 수 있는 권리다."<br>
                        <span class="text-gray-400">— 조지 오웰</span>
                    </p>
                </div>
                
                <p>
                    오늘날에도 나와 다른 생각을 쉽게 혐오하고, 자유를 가진 자들을 사냥하는 문화는 여전히 만연합니다.
                </p>
                
                <p>
                    이번 전시는 <strong class="text-red-300">공포라는 감각</strong>과 <strong class="text-red-300">심리라는 구조</strong>를 통해, 우리가 무의식적으로 받아들여온 사회적 틀, 언어의 틀, 감정의 틀을 낯설고 생생하게 다시 들여다보는 실험입니다.
                </p>
                
                <p>
                    누군가는 조용히 침묵하고, 누군가는 기꺼이 의심하며, 누군가는 끝내 스스로의 손으로 그 '틀'을 해체하게 될 것입니다.
                </p>
                
                <p class="text-center">
                    이 전시는 두려움으로 시작되지만, 스스로 질문하는 자만이 그 안에서 <strong class="text-red-300 text-xl">진짜 '나'</strong>를 다시 마주할 수 있도록 설계되어 있습니다.
                </p>
                
                <div class="bg-gray-900/50 rounded-lg p-6 mt-8">
                    <p class="text-center text-lg">
                        광주 청년들이 기획하고, 청년들이 직접 만든<br>
                        이 작은 전시의 세계 안에서,<br>
                        <span class="text-red-300 font-semibold">당신은 무엇을 보고, 무엇을 믿으며, 무엇을 깨닫게 될까요?</span>
                    </p>
                    <p class="text-center text-gray-400 mt-4 italic">
                        어쩌면, 이 체험을 통해 내가 몰랐던 '나의 틀'을 발견하게 될지도 모릅니다.
                    </p>
                </div>
            </div>
        </section>
    </main>

    <!-- Footer -->
    <footer class="bg-black/30 py-8 mt-12">
        <div class="container mx-auto px-4 text-center">
            <p class="text-gray-400 mb-2">© 2025 노매드 그라운드 (Nomad Ground)</p>
            <p class="text-gray-500 text-sm">× 청년범아티스트연합회</p>
        </div>
    </footer>
</body>
</html>
