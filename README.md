<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>عرض ResQ-Eye النهائي</title>
    <style>
        /* Base Styling - Arabic Optimized */
        @import url('https://fonts.googleapis.com/css2?family=Tajawal:wght@400;700&display=swap');
        
        body { margin: 0; font-family: 'Tajawal', 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background-color: #0d1117; color: white; overflow: hidden; direction: rtl; text-align: right; }
        .slide { display: none; height: 100vh; width: 100vw; padding: 40px; box-sizing: border-box; flex-direction: column; justify-content: center; align-items: center; text-align: center; }
        .active { display: flex; animation: fadeIn 0.5s ease-in-out; }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
        
        /* Typography */
        h1 { font-size: 3.5rem; margin-bottom: 0.5rem; color: #4facfe; text-transform: uppercase; letter-spacing: 0px; text-shadow: 0 0 10px rgba(79, 172, 254, 0.5); }
        h2 { font-size: 2rem; color: #a1c4fd; margin-top: 0; }
        p { font-size: 1.5rem; line-height: 1.6; max-width: 800px; color: #e0e0e0; }
        ul { text-align: right; font-size: 1.5rem; max-width: 800px; margin-right: auto; margin-left: auto; }
        li { margin-bottom: 15px; }
        .highlight { color: #ff6b6b; font-weight: bold; }

        /* Navigation */
        .controls { position: absolute; bottom: 20px; left: 20px; z-index: 100; direction: ltr; }
        button { background: #4facfe; border: none; padding: 15px 30px; color: white; font-size: 1.2rem; cursor: pointer; border-radius: 5px; transition: 0.3s; font-family: 'Tajawal', sans-serif; box-shadow: 0 0 15px rgba(79, 172, 254, 0.3); }
        button:hover { background: #00f2fe; box-shadow: 0 0 25px rgba(0, 242, 254, 0.6); }

        /* BRANDING ELEMENTS */
        .project-logo-main {
            max-width: 400px;
            margin-bottom: 20px;
            filter: drop-shadow(0 0 20px rgba(79, 172, 254, 0.4));
            animation: floatLogo 6s ease-in-out infinite;
        }
        
        .project-stamp {
            position: absolute;
            top: 20px;
            left: 20px;
            width: 120px;
            opacity: 0.8;
            z-index: 1000;
            filter: drop-shadow(0 0 5px rgba(0,0,0,0.5));
        }

        @keyframes floatLogo {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
            100% { transform: translateY(0px); }
        }

        /* Slide Specifics */
        .dashboard-container { display: flex; width: 90%; height: 60%; background: #161b22; border-radius: 10px; overflow: hidden; box-shadow: 0 10px 30px rgba(0,0,0,0.5); border: 2px solid #4facfe; }
        .feed-panel { flex: 1; background: #000; position: relative; display: flex; justify-content: center; align-items: center; border-left: 2px solid #30363d; flex-direction: column; overflow: hidden; } 
        .data-panel { flex: 1; padding: 20px; text-align: right; background: #0d1117; overflow-y: auto; }
        
        /* Dashboard UI Elements */
        .bounding-box { border: 3px solid #ff4757; width: 150px; height: 80px; position: absolute; z-index: 10; }
        .drone-overlay { position: absolute; top: 10px; right: 10px; color: #2ed573; font-family: monospace; font-size: 1rem; text-align: right; direction: ltr; z-index: 10; background: rgba(0,0,0,0.5); padding: 5px; border-radius: 4px; }
        .isbar-box { background: #161b22; padding: 15px; margin-bottom: 10px; border-radius: 5px; border-right: 5px solid #4facfe; box-shadow: 0 4px 6px rgba(0,0,0,0.1); }
        .isbar-label { font-size: 0.9rem; color: #8b949e; text-transform: uppercase; font-weight: bold; letter-spacing: 1px; }
        .isbar-value { font-size: 1.2rem; color: #e6edf3; font-family: monospace; margin-top: 5px; }
        .critical { border-right: 5px solid #ff4757; background: #3c1518; }
        .critical .isbar-value { color: #ff6b6b; font-weight: bold; animation: pulse 2s infinite; }
        
        @keyframes pulse { 0% { opacity: 1; } 50% { opacity: 0.7; } 100% { opacity: 1; } }

        /* Scanning Animation for Slide 2 */
        .scanner-container {
            width: 80%;
            height: 50vh;
            background: #161b22;
            border: 2px solid #30363d;
            position: relative;
            margin-top: 20px;
            overflow: hidden;
            border-radius: 10px;
            box-shadow: inset 0 0 50px #000;
        }
        
        /* The "Hidden" Victim */
        .victim-dot {
            position: absolute;
            top: 55%;
            left: 30%;
            width: 15px;
            height: 15px;
            background: #30363d;
            border-radius: 50%;
            box-shadow: 0 0 5px #000;
        }

        /* The Failed Scanner */
        .crosshair {
            position: absolute;
            width: 100px;
            height: 100px;
            border: 2px dashed #4facfe;
            border-radius: 10px;
            animation: searchPattern 6s infinite linear;
            box-shadow: 0 0 15px #4facfe;
        }
        
        .searching-text {
            position: absolute;
            top: 20px;
            left: 20px;
            color: #ff4757;
            font-family: monospace;
            font-size: 1.5rem;
            font-weight: bold;
            animation: textPulse 1s infinite;
            direction: ltr;
        }

        @keyframes searchPattern {
            0% { top: 10%; left: 10%; }
            25% { top: 20%; left: 70%; }
            50% { top: 70%; left: 80%; }
            75% { top: 80%; left: 20%; }
            100% { top: 10%; left: 10%; }
        }

        @keyframes textPulse { 0% { opacity: 0.5; } 100% { opacity: 1; } }

        /* NEW STYLES FOR SLIDE 3 (Split Screen) */
        .split-screen-container {
            display: flex;
            width: 90%;
            height: 60vh;
            margin-top: 20px;
            border: 2px solid #4facfe;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 0 30px rgba(79, 172, 254, 0.1);
        }
        
        .screen-half {
            flex: 1;
            position: relative;
            overflow: hidden;
        }
        
        .raw-feed {
            background-color: #000;
            border-left: 2px solid #4facfe;
            filter: grayscale(100%) contrast(1.2);
        }
        
        .ar-feed {
            background-color: #051e3e;
            position: relative;
        }
        
        .overlay-label {
            position: absolute;
            top: 10px;
            right: 10px;
            background: rgba(0,0,0,0.7);
            color: white;
            padding: 5px 10px;
            border-radius: 4px;
            font-size: 0.9rem;
            z-index: 20;
            border: 1px solid #30363d;
        }
        
        .bg-video {
            width: 100%;
            height: 100%;
            object-fit: cover;
            position: absolute;
            top: 0;
            left: 0;
            z-index: 0;
        }

        .raw-feed .bg-video {
            filter: blur(2px) grayscale(100%);
        }
        
        /* AR Elements */
        .red-alert {
            position: absolute;
            border: 3px solid #ff4757;
            box-shadow: 0 0 20px #ff4757, inset 0 0 10px #ff4757;
            width: 50px;
            height: 30px;
            animation: alertPulse 0.5s infinite alternate;
            z-index: 10;
        }
        
        .person-icon {
            font-size: 1.5rem;
            position: absolute;
            top: -5px;
            right: 5px;
            transform: rotate(90deg);
        }
        
        @keyframes alertPulse {
            from { border-color: #ff4757; box-shadow: 0 0 10px #ff4757; }
            to { border-color: white; box-shadow: 0 0 30px #ff4757; }
        }
        
        /* Data Tag Styling */
        .data-tag {
            position: absolute;
            top: 35%;
            left: 55%; 
            background: rgba(13, 17, 23, 0.95);
            border: 1px solid #4facfe;
            border-right: 4px solid #ff4757;
            padding: 15px;
            width: 250px;
            text-align: right;
            box-shadow: 0 10px 30px rgba(0,0,0,0.8);
            z-index: 20;
            border-radius: 4px;
        }
        
        .tag-row {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
            border-bottom: 1px solid rgba(79, 172, 254, 0.3);
            padding-bottom: 4px;
        }
        
        .tag-label {
            font-size: 0.8rem;
            color: #4facfe;
            text-transform: uppercase;
        }
        
        .tag-val {
            font-size: 1rem;
            font-weight: bold;
            color: white;
            font-family: monospace;
        }
        
        .critical-text { color: #ff4757; text-shadow: 0 0 5px red; animation: textPulse 1s infinite; }
        .warning-text { color: #ffa502; }

        /* Logic Flow Diagram */
        .flow-container { display: flex; gap: 20px; margin-top: 30px; flex-wrap: wrap; justify-content: center; flex-direction: row; } 
        .step { background: #161b22; padding: 20px; border-radius: 8px; width: 200px; border-top: 4px solid #4facfe; box-shadow: 0 4px 10px rgba(0,0,0,0.2); transition: transform 0.3s; }
        .step:hover { transform: translateY(-5px); }
        .step-icon { font-size: 2rem; margin-bottom: 10px; }
        .arrow { font-size: 2rem; color: #4facfe; align-self: center; } 

    </style>
</head>
<body>

    <!-- Project Stamp (Visible on all slides) -->
    <img src="Gemini_Generated_Image_3eb0hm3eb0hm3eb0_pixian_ai.png" alt="ResQ-Eye Stamp" class="project-stamp">

    <!-- Navigation -->
    <div class="controls">
        <button onclick="nextSlide()">❮ التالي</button>
        <button onclick="prevSlide()">السابق ❯</button>
    </div>

    <!-- Slide 1: Title -->
    <div class="slide active" id="slide1">
        <!-- Logo Replaces Text Header -->
        <img src="Gemini_Generated_Image_3eb0hm3eb0hm3eb0_pixian_ai.png" alt="ResQ-Eye Logo" class="project-logo-main">
        <h2>تأمين "الساعة الذهبية" في الحشود</h2>
        <p>نظام استجابة ذكية للحوادث وإرسال تقارير ISBAR</p>
        <p style="margin-top: 20px; font-style: italic; color: #8b949e;">"عندما تكون 30 ثانية مدة طويلة جداً للانتظار."</p>
    </div>

    <!-- Slide 2: The Problem (Animated) -->
    <div class="slide" id="slide2">
        <h1>المشكلة: "الفجوة الصامتة"</h1>
        <p>في الحشود الكثيفة، الاكتشاف البشري يشبه البحث عن إبرة في كومة قش.</p>
        
        <div class="scanner-container">
            <!-- Simulated Background (Crowd) -->
            <div style="width:100%; height:100%; opacity:0.1; background-image: radial-gradient(#fff 1px, transparent 1px); background-size: 10px 10px;"></div>
            
            <!-- The Hidden Victim -->
            <div class="victim-dot"></div>
            
            <!-- The Scanning Animation -->
            <div class="crosshair"></div>
            <div class="searching-text">SEARCHING...</div>
            <div style="position: absolute; bottom: 10px; right: 10px; color: #777; font-size: 0.8rem;">محاكاة فشل الاكتشاف البشري</div>
        </div>

        <div style="display: flex; gap: 40px; justify-content: center; margin-top: 20px;">
            <div style="background: #161b22; padding: 15px; border-radius: 10px; width: 40%; box-shadow: 0 4px 6px rgba(0,0,0,0.1);">
                <h3>تأخر الاكتشاف</h3>
                <p style="font-size: 0.9rem; color: #8b949e;">المريض غير مرئي للعين المجردة.</p>
            </div>
            <div style="background: #161b22; padding: 15px; border-radius: 10px; width: 40%; box-shadow: 0 4px 6px rgba(0,0,0,0.1);">
                <h3>فشل النظام الحالي</h3>
                <p style="font-size: 0.9rem; color: #8b949e;">المسح العشوائي لا يجد الهدف بسرعة.</p>
            </div>
        </div>
    </div>

    <!-- Slide 3: The Logic Flow -->
    <div class="slide" id="slide3">
        <h1>آلية عمل ResQ-Eye</h1>
        <p>كيف نقوم بتصفية الضوضاء للعثور على الحالة الطارئة.</p>
        <div class="flow-container"> 
            <div class="step">
                <div class="step-icon">🎥</div>
                <h3>1. المدخلات</h3>
                <p style="font-size: 0.9rem; color: #8b949e;">بث الدرون / CCTV</p>
            </div>
            <div class="arrow">←</div>
            <div class="step">
                <div class="step-icon">📉</div>
                <h3>2. المحفز</h3>
                <p style="font-size: 0.9rem; color: #8b949e;">تغير الوضعية (من رأسي لأفقي)</p>
            </div>
            <div class="arrow">←</div>
            <div class="step">
                <div class="step-icon">⏱️</div>
                <h3>3. الفلتر</h3>
                <p style="font-size: 0.9rem; color: #8b949e;">سكون > 12 ثانية<br><span style="color:#4facfe">(عتبة جاك)</span></p>
            </div>
            <div class="arrow">←</div>
            <div class="step">
                <div class="step-icon">📡</div>
                <h3>4. المخرجات</h3>
                <p style="font-size: 0.9rem; color: #8b949e;">تقرير ISBAR رقمي</p>
            </div>
        </div>
    </div>

    <!-- Slide 3.5: The Comparison (New Slide with Video) -->
    <div class="slide" id="slide3_5">
        <h1>الحل: الذكاء في مواجهة الفوضى</h1>
        <p>مقارنة: اللقطات الخام مقابل رؤية ResQ-Eye</p>
        
        <div class="split-screen-container">
            <!-- Right (in RTL): Raw Chaos -->
            <div class="screen-half raw-feed">
                <div class="overlay-label">اللقطات الخام (CCTV)</div>
                <!-- Video Background -->
                <video class="bg-video" autoplay loop muted playsinline>
                    <source src="videoplaybeweweack (12).mp4" type="video/mp4">
                </video>
            </div>
            
            <!-- Left (in RTL): ResQ-Eye Clarity -->
            <div class="screen-half ar-feed">
                <div class="overlay-label">تحليل ResQ-Eye (AR)</div>
                <!-- Video Background (Clean) -->
                <video class="bg-video" autoplay loop muted playsinline>
                    <source src="videoplaybeweweack (12).mp4" type="video/mp4">
                </video>
                
                <!-- Overlay Elements -->
                <div class="bbox red-alert" style="top:45%; right:45%;"></div>
                
                <!-- Data Tag -->
                <div class="data-tag">
                    <div class="tag-row"><span class="tag-label">الحالة:</span> <span class="tag-val critical-text">غير مستجيب</span></div>
                    <div class="tag-row"><span class="tag-label">الحركة:</span> <span class="tag-val">0.0 م/ث (15ث)</span></div>
                    <div class="tag-row"><span class="tag-label">قبل الحدث:</span> <span class="tag-val warning-text">رصد ترنح</span></div>
                    <div class="tag-row"><span class="tag-label">الدقة:</span> <span class="tag-val">99.8%</span></div>
                </div>
            </div>
        </div>
    </div>

    <!-- Slide 4: The Dashboard Demo -->
    <div class="slide" id="slide4">
        <h2 style="margin-bottom: 20px;">واجهة المرسل (بروتوكول ISBAR)</h2>
        <div class="dashboard-container">
            <!-- Right Panel (in RTL): Simulated Drone Feed -->
            <div class="feed-panel">
                <div class="drone-overlay">
                    CAM: DRONE-04<br>
                    LOC: ZONE D<br>
                    TEMP: 42°C
                </div>
                <!-- Video Background -->
                <video class="bg-video" autoplay loop muted playsinline style="z-index: 0;">
                    <source src="videoplaybeweweack (12).mp4" type="video/mp4">
                </video>
                
                <!-- Targeted Red Box (Static Overlay) -->
                <div class="bounding-box" style="top: 55%; right: 52%; border-color: red; animation: pulse 1s infinite;"></div>
                <div style="position: absolute; top: 55%; right: 52%; background: red; color: white; padding: 2px 5px; font-size: 0.8rem; font-weight: bold; direction: ltr; z-index: 10;">
                    ⚠ UNRESPONSIVE (12s)
                </div>
            </div>

            <!-- Left Panel (in RTL): Corrected ISBAR Data -->
            <div class="data-panel">
                <div class="isbar-box">
                    <div class="isbar-label">I - الهوية (بصرية)</div>
                    <div class="isbar-value">ذكر مجهول، في الأربعينيات تقريباً. رداء أبيض.</div>
                </div>
                <div class="isbar-box">
                    <div class="isbar-label">S - الوضع</div>
                    <div class="isbar-value">تم رصد سقوط. غير مستجيب > 12 ثانية.</div>
                </div>
                <div class="isbar-box">
                    <div class="isbar-label">B - الخلفية (البيئة)</div>
                    <div class="isbar-value">المنطقة D (مزدحمة). الحرارة المحيطة 42°C.</div>
                </div>
                <div class="isbar-box">
                    <div class="isbar-label">A - التقييم (الذكاء الاصطناعي)</div>
                    <div class="isbar-value">احتمالية عالية: ضربة شمس إجهادية.</div>
                </div>
                <div class="isbar-box critical">
                    <div class="isbar-label">R - التوصية</div>
                    <div class="isbar-value">حرج: ابدأ التبريد السريع فوراً. لا تنقل المريض قبل التبريد.</div>
                </div>
            </div>
        </div>
        <p style="font-size: 1rem; margin-top: 10px; color: #8b949e;">*البيانات تقتصر على الملاحظات البصرية وأجهزة استشعار البيئة.</p>
    </div>

    <!-- Slide 5: Scenario -->
    <div class="slide" id="slide5">
        <h1>سيناريو: ضربة شمس في المنطقة D</h1>
        <ul style="list-style: none;">
            <li><strong>T + 0s:</strong> تعثر الهدف (رصد الترنح بواسطة تقدير الوضعية).</li>
            <li><strong>T + 3s:</strong> سقوط الهدف (من رأسي إلى أفقي).</li>
            <li><strong>T + 12s:</strong> <span class="highlight">تحقق عتبة جاك.</span> لا توجد حركة.</li>
            <li><strong>T + 15s:</strong> الذكاء الاصطناعي يربط السقوط + مؤشر حرارة 42°C.</li>
            <li><strong>الإجراء:</strong> يتلقى المرسل أمر: <strong>"أولوية التبريد على النقل"</strong>.</li>
        </ul>
        <div style="margin-top: 30px; border: 2px solid #2ed573; padding: 20px; border-radius: 10px; display: inline-block;">
            <h3 style="margin:0; color: #2ed573;">النتيجة</h3>
            <p style="margin:5px 0 0 0; font-size: 1.2rem;">يصل المسعف ومعه <strong>كمادات ثلج</strong>، وليس فقط نقالة.</p>
        </div>
    </div>

    <!-- Slide 6: Conclusion -->
    <div class="slide" id="slide6">
        <img src="Gemini_Generated_Image_3eb0hm3eb0hm3eb0_pixian_ai.png" alt="ResQ-Eye Logo" style="width: 200px; margin-bottom: 20px;">
        <p style="font-size: 1.8rem; font-weight: bold;">نحفظ الدقائق. ننقذ الأرواح.</p>
        <div style="display: flex; gap: 40px; justify-content: center; margin-top: 50px;">
            <div style="text-align: center;">
                <div style="font-size: 2.5rem;">👨‍💻</div>
                <h3 style="color: #4facfe;">Tom</h3>
                <p style="font-size: 1.2rem; color: #8b949e;">قائد تقني</p>
            </div>
            <div style="text-align: center;">
                <div style="font-size: 2.5rem;">👨‍⚕️</div>
                <h3 style="color: #4facfe;">Dr. Jack</h3>
                <p style="font-size: 1.2rem; color: #8b949e;">قائد طبي</p>
            </div>
        </div>
    </div>

    <script>
        let currentSlide = 0;
        const slides = document.querySelectorAll('.slide');

        function showSlide(index) {
            slides.forEach(slide => slide.classList.remove('active'));
            if (index >= slides.length) currentSlide = 0;
            if (index < 0) currentSlide = slides.length - 1;
            slides[currentSlide].classList.add('active');
        }

        function nextSlide() {
            currentSlide++;
            showSlide(currentSlide);
        }

        function prevSlide() {
            currentSlide--;
            showSlide(currentSlide);
        }
        
        // Keyboard navigation
        document.addEventListener('keydown', function(event) {
            if (event.key === "ArrowLeft") nextSlide(); // Reversed for logical RTL feel
            if (event.key === "ArrowRight") prevSlide();
        });
    </script>
</body>
</html>
