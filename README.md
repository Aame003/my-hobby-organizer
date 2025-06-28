# my-hobby-organizer
username.github.io/my-hobby-organizer
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>منظم الهوايات والأهداف</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
        }
        
        h1 {
            text-align: center;
            color: #4a5568;
            margin-bottom: 30px;
            font-size: 2.5rem;
        }
        
        .tabs {
            display: flex;
            border-bottom: 2px solid #e2e8f0;
            margin-bottom: 30px;
            flex-wrap: wrap;
        }
        
        .tab {
            padding: 15px 25px;
            cursor: pointer;
            border: none;
            background: none;
            font-size: 16px;
            color: #718096;
            border-bottom: 3px solid transparent;
            transition: all 0.3s ease;
        }
        
        .tab.active {
            color: #667eea;
            border-bottom-color: #667eea;
            font-weight: bold;
        }
        
        .tab-content {
            display: none;
            animation: fadeIn 0.5s ease;
        }
        
        .tab-content.active {
            display: block;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .priority-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .priority-box {
            border: 2px solid #e2e8f0;
            border-radius: 15px;
            padding: 20px;
            transition: all 0.3s ease;
        }
        
        .priority-box:hover {
            border-color: #667eea;
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.1);
        }
        
        .priority-high { border-color: #f56565; }
        .priority-medium { border-color: #ed8936; }
        .priority-low { border-color: #48bb78; }
        
        .priority-title {
            font-size: 1.2rem;
            font-weight: bold;
            margin-bottom: 15px;
        }
        
        .priority-high .priority-title { color: #f56565; }
        .priority-medium .priority-title { color: #ed8936; }
        .priority-low .priority-title { color: #48bb78; }
        
        .habit-item {
            display: flex;
            align-items: center;
            padding: 10px;
            margin: 5px 0;
            background: #f7fafc;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .habit-item:hover {
            background: #edf2f7;
        }
        
        .habit-checkbox {
            margin-left: 10px;
            transform: scale(1.2);
        }
        
        .weekly-schedule {
            display: grid;
            grid-template-columns: repeat(7, 1fr);
            gap: 10px;
            margin-top: 20px;
        }
        
        .day-card {
            background: #f7fafc;
            border-radius: 10px;
            padding: 15px;
            text-align: center;
            border: 2px solid transparent;
            transition: all 0.3s ease;
        }
        
        .day-card:hover {
            border-color: #667eea;
            background: #e6fffa;
        }
        
        .day-name {
            font-weight: bold;
            color: #4a5568;
            margin-bottom: 10px;
        }
        
        .time-block {
            background: white;
            padding: 8px;
            margin: 5px 0;
            border-radius: 5px;
            font-size: 12px;
            cursor: pointer;
            border: 1px solid #e2e8f0;
        }
        
        .time-block:hover {
            background: #667eea;
            color: white;
        }
        
        .budget-tracker {
            background: linear-gradient(135deg, #4fd1c7 0%, #81e6d9 100%);
            padding: 20px;
            border-radius: 15px;
            color: white;
            margin-bottom: 20px;
        }
        
        .budget-item {
            display: flex;
            justify-content: space-between;
            margin: 10px 0;
            padding: 10px;
            background: rgba(255,255,255,0.2);
            border-radius: 8px;
        }
        
        .progress-bar {
            width: 100%;
            height: 20px;
            background: #e2e8f0;
            border-radius: 10px;
            overflow: hidden;
            margin: 10px 0;
        }
        
        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, #48bb78, #38a169);
            transition: width 0.5s ease;
        }
        
        .add-btn {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 25px;
            cursor: pointer;
            font-size: 16px;
            transition: all 0.3s ease;
            margin: 10px 5px;
        }
        
        .add-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.3);
        }
        
        input, select, textarea {
            width: 100%;
            padding: 12px;
            border: 2px solid #e2e8f0;
            border-radius: 8px;
            font-size: 16px;
            margin: 5px 0;
            transition: border-color 0.3s ease;
        }
        
        input:focus, select:focus, textarea:focus {
            outline: none;
            border-color: #667eea;
        }
        
        .motivational-quote {
            background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%);
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            font-style: italic;
            color: #744210;
            margin: 20px 0;
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.02); }
        }
        
        .resource-card {
            background: white;
            border: 2px solid #e2e8f0;
            border-radius: 12px;
            padding: 20px;
            margin: 15px 0;
            transition: all 0.3s ease;
        }
        
        .resource-card:hover {
            border-color: #667eea;
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
        }
        
        .free-badge {
            background: #48bb78;
            color: white;
            padding: 5px 10px;
            border-radius: 15px;
            font-size: 12px;
            font-weight: bold;
        }
        
        @media (max-width: 768px) {
            .container {
                padding: 15px;
                margin: 10px;
            }
            
            .weekly-schedule {
                grid-template-columns: 1fr;
            }
            
            .tabs {
                flex-direction: column;
            }
            
            h1 {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>🎯 منظم الهوايات والأهداف الشخصية</h1>
        
        <div class="tabs">
            <button class="tab active" onclick="showTab('priorities')">الأولويات</button>
            <button class="tab" onclick="showTab('schedule')">الجدول الأسبوعي</button>
            <button class="tab" onclick="showTab('budget')">الميزانية المجانية</button>
            <button class="tab" onclick="showTab('progress')">تتبع التقدم</button>
            <button class="tab" onclick="showTab('resources')">مصادر مجانية</button>
        </div>
        
        <!-- الأولويات -->
        <div id="priorities" class="tab-content active">
            <div class="motivational-quote">
                "التركيز على شيء واحد أفضل من محاولة فعل كل شيء في نفس الوقت"
            </div>
            
            <div class="priority-grid">
                <div class="priority-box priority-high">
                    <div class="priority-title">🔴 الأولوية العالية (شهر واحد)</div>
                    <div class="habit-item">
                        <input type="checkbox" class="habit-checkbox">
                        <span>قراءة كتاب واحد فقط من الكتب الموجودة</span>
                    </div>
                    <div class="habit-item">
                        <input type="checkbox" class="habit-checkbox">
                        <span>تعلم الإنجليزية 30 دقيقة يومياً (مجاناً)</span>
                    </div>
                    <div class="habit-item">
                        <input type="checkbox" class="habit-checkbox">
                        <span>ممارسة الرياضة 20 دقيقة يومياً</span>
                    </div>
                </div>
                
                <div class="priority-box priority-medium">
                    <div class="priority-title">🟡 الأولوية المتوسطة (شهرين)</div>
                    <div class="habit-item">
                        <input type="checkbox" class="habit-checkbox">
                        <span>تعلم أساسيات البرمجة (مجاناً)</span>
                    </div>
                    <div class="habit-item">
                        <input type="checkbox" class="habit-checkbox">
                        <span>قراءة كتاب ثاني</span>
                    </div>
                    <div class="habit-item">
                        <input type="checkbox" class="habit-checkbox">
                        <span>تعلم مهارة في إدارة الأعمال</span>
                    </div>
                </div>
                
                <div class="priority-box priority-low">
                    <div class="priority-title">🟢 الأولوية المنخفضة (3 أشهر فما فوق)</div>
                    <div class="habit-item">
                        <input type="checkbox" class="habit-checkbox">
                        <span>توسيع معرفة الحاسوب</span>
                    </div>
                    <div class="habit-item">
                        <input type="checkbox" class="habit-checkbox">
                        <span>قراءة المزيد من الكتب</span>
                    </div>
                    <div class="habit-item">
                        <input type="checkbox" class="habit-checkbox">
                        <span>تطوير مهارات متقدمة</span>
                    </div>
                </div>
            </div>
        </div>
        
        <!-- الجدول الأسبوعي -->
        <div id="schedule" class="tab-content">
            <h2>📅 جدولك الأسبوعي المقترح</h2>
            <p style="margin-bottom: 20px; color: #718096;">اختر الأوقات التي تناسبك واضغط على المربعات لتخصيصها</p>
            
            <div class="weekly-schedule">
                <div class="day-card">
                    <div class="day-name">السبت</div>
                    <div class="time-block" onclick="toggleTime(this)">6:00-6:30 رياضة</div>
                    <div class="time-block" onclick="toggleTime(this)">7:00-7:30 إنجليزية</div>
                    <div class="time-block" onclick="toggleTime(this)">8:00-8:30 قراءة</div>
                </div>
                <div class="day-card">
                    <div class="day-name">الأحد</div>
                    <div class="time-block" onclick="toggleTime(this)">6:00-6:30 رياضة</div>
                    <div class="time-block" onclick="toggleTime(this)">7:00-7:30 برمجة</div>
                    <div class="time-block" onclick="toggleTime(this)">8:00-8:30 قراءة</div>
                </div>
                <div class="day-card">
                    <div class="day-name">الاثنين</div>
                    <div class="time-block" onclick="toggleTime(this)">6:00-6:30 رياضة</div>
                    <div class="time-block" onclick="toggleTime(this)">7:00-7:30 إنجليزية</div>
                    <div class="time-block" onclick="toggleTime(this)">8:00-8:30 قراءة</div>
                </div>
                <div class="day-card">
                    <div class="day-name">الثلاثاء</div>
                    <div class="time-block" onclick="toggleTime(this)">6:00-6:30 رياضة</div>
                    <div class="time-block" onclick="toggleTime(this)">7:00-7:30 برمجة</div>
                    <div class="time-block" onclick="toggleTime(this)">8:00-8:30 قراءة</div>
                </div>
                <div class="day-card">
                    <div class="day-name">الأربعاء</div>
                    <div class="time-block" onclick="toggleTime(this)">6:00-6:30 رياضة</div>
                    <div class="time-block" onclick="toggleTime(this)">7:00-7:30 إنجليزية</div>
                    <div class="time-block" onclick="toggleTime(this)">8:00-8:30 قراءة</div>
                </div>
                <div class="day-card">
                    <div class="day-name">الخميس</div>
                    <div class="time-block" onclick="toggleTime(this)">6:00-6:30 رياضة</div>
                    <div class="time-block" onclick="toggleTime(this)">7:00-7:30 برمجة</div>
                    <div class="time-block" onclick="toggleTime(this)">8:00-8:30 قراءة</div>
                </div>
                <div class="day-card">
                    <div class="day-name">الجمعة</div>
                    <div class="time-block" onclick="toggleTime(this)">راحة أو مراجعة</div>
                    <div class="time-block" onclick="toggleTime(this)">وقت حر</div>
                    <div class="time-block" onclick="toggleTime(this)">تخطيط الأسبوع القادم</div>
                </div>
            </div>
        </div>
        
        <!-- الميزانية المجانية -->
        <div id="budget" class="tab-content">
            <div class="budget-tracker">
                <h2>💰 خطة الميزانية الصفرية</h2>
                <p>تعلم وطور نفسك بدون إنفاق أي أموال!</p>
            </div>
            
            <div class="resource-card">
                <h3>📚 استغلال الكتب الموجودة</h3>
                <p><strong>المشكلة:</strong> 55 كتاب عندك و 10 لم تقرأها</p>
                <p><strong>الحل:</strong> توقف عن شراء كتب جديدة واقرأ كتاب واحد فقط</p>
                <div class="free-badge">مجاني 100%</div>
            </div>
            
            <div class="resource-card">
                <h3>🏃‍♂️ الرياضة المجانية</h3>
                <ul>
                    <li>المشي في الحي أو الحديقة</li>
                    <li>تمارين منزلية (YouTube مجاني)</li>
                    <li>الجري في الصباح الباكر</li>
                    <li>تمارين الوزن الحر (استخدم أشياء منزلية)</li>
                </ul>
                <div class="free-badge">مجاني 100%</div>
            </div>
            
            <div class="resource-card">
                <h3>💡 نصائح توفير المال</h3>
                <ul>
                    <li>احذف تطبيقات التسوق من هاتفك</li>
                    <li>اكتب قائمة بما تحتاجه فعلاً قبل الشراء</li>
                    <li>انتظر 24 ساعة قبل أي عملية شراء غير ضرورية</li>
                    <li>ركز على استخدام ما تملكه بالفعل</li>
                </ul>
                <div class="free-badge">نصائح مجانية</div>
            </div>
        </div>
        
        <!-- تتبع التقدم -->
        <div id="progress" class="tab-content">
            <h2>📈 تتبع تقدمك</h2>
            
            <div class="resource-card">
                <h3>📖 تقدم القراءة</h3>
                <p>الكتاب الحالي: <input type="text" placeholder="اسم الكتاب"></p>
                <p>عدد الصفحات المقروءة: <input type="number" placeholder="0" id="pages-read" oninput="updateProgress('reading', this.value, 200)"></p>
                <div class="progress-bar">
                    <div class="progress-fill" id="reading-progress" style="width: 0%"></div>
                </div>
                <p>النسبة المئوية: <span id="reading-percentage">0%</span></p>
            </div>
            
            <div class="resource-card">
                <h3>🇺🇸 تقدم الإنجليزية</h3>
                <p>عدد الأيام المدروسة هذا الشهر: <input type="number" placeholder="0" id="english-days" oninput="updateProgress('english', this.value, 30)"></p>
                <div class="progress-bar">
                    <div class="progress-fill" id="english-progress" style="width: 0%"></div>
                </div>
                <p>النسبة المئوية: <span id="english-percentage">0%</span></p>
            </div>
            
            <div class="resource-card">
                <h3>💻 تقدم البرمجة</h3>
                <p>عدد الدروس المكتملة: <input type="number" placeholder="0" id="programming-lessons" oninput="updateProgress('programming', this.value, 50)"></p>
                <div class="progress-bar">
                    <div class="progress-fill" id="programming-progress" style="width: 0%"></div>
                </div>
                <p>النسبة المئوية: <span id="programming-percentage">0%</span></p>
            </div>
            
            <div class="resource-card">
                <h3>🏃‍♂️ تقدم الرياضة</h3>
                <p>عدد أيام التمرين هذا الشهر: <input type="number" placeholder="0" id="exercise-days" oninput="updateProgress('exercise', this.value, 25)"></p>
                <div class="progress-bar">
                    <div class="progress-fill" id="exercise-progress" style="width: 0%"></div>
                </div>
                <p>النسبة المئوية: <span id="exercise-percentage">0%</span></p>
            </div>
        </div>
        
        <!-- المصادر المجانية -->
        <div id="resources" class="tab-content">
            <h2>🎓 مصادر التعلم المجانية</h2>
            
            <div class="resource-card">
                <h3>🇺🇸 تعلم الإنجليزية مجاناً</h3>
                <ul>
                    <li><strong>Duolingo:</strong> تطبيق مجاني لتعلم اللغات</li>
                    <li><strong>BBC Learning English:</strong> موقع مجاني من بي بي سي</li>
                    <li><strong>YouTube:</strong> قنوات مثل English with Lucy</li>
                    <li><strong>VOA Learning English:</strong> أخبار بلغة إنجليزية سهلة</li>
                </ul>
                <div class="free-badge">مجاني</div>
            </div>
            
            <div class="resource-card">
                <h3>💻 تعلم البرمجة مجاناً</h3>
                <ul>
                    <li><strong>freeCodeCamp:</strong> دورات برمجة كاملة مجانية</li>
                    <li><strong>Codecademy:</strong> دروس تفاعلية (النسخة المجانية)</li>
                    <li><strong>CS50 Harvard:</strong> دورة جامعة هارفارد المجانية</li>
                    <li><strong>YouTube:</strong> قنوات عربية مثل الزيرو ويب سكول</li>
                </ul>
                <div class="free-badge">مجاني</div>
            </div>
            
            <div class="resource-card">
                <h3>📊 إدارة الأعمال مجاناً</h3>
                <ul>
                    <li><strong>Coursera:</strong> دورات مجانية من جامعات عالمية</li>
                    <li><strong>edX:</strong> دورات من MIT وهارفارد</li>
                    <li><strong>Khan Academy:</strong> دروس في الاقتصاد والمالية</li>
                    <li><strong>YouTube:</strong> قنوات متخصصة في ريادة الأعمال</li>
                </ul>
                <div class="free-badge">مجاني</div>
            </div>
            
            <div class="resource-card">
                <h3>🖥️ الحاسوب والإنترنت</h3>
                <ul>
                    <li><strong>Digital Garage by Google:</strong> مهارات رقمية مجانية</li>
                    <li><strong>Microsoft Learn:</strong> تعلم برامج مايكروسوفت</li>
                    <li><strong>Cybrary:</strong> أمن المعلومات مجاناً</li>
                    <li><strong>CompTIA:</strong> أساسيات تقنية المعلومات</li>
                </ul>
                <div class="free-badge">مجاني</div>
            </div>
            
            <div class="motivational-quote">
                "أفضل استثمار يمكنك القيام به هو في نفسك. كلما تعلمت أكثر، كلما كسبت أكثر" - وارن بافيت
            </div>
        </div>
    </div>
    
    <script>
        function showTab(tabName) {
            // إخفاء جميع المحتويات
            const contents = document.querySelectorAll('.tab-content');
            contents.forEach(content => content.classList.remove('active'));
            
            // إزالة التفعيل من جميع التبويبات
            const tabs = document.querySelectorAll('.tab');
            tabs.forEach(tab => tab.classList.remove('active'));
            
            // إظهار المحتوى المطلوب
            document.getElementById(tabName).classList.add('active');
            
            // تفعيل التبويب المطلوب
            event.target.classList.add('active');
        }
        
        function toggleTime(element) {
            if (element.style.backgroundColor === 'rgb(102, 126, 234)') {
                element.style.backgroundColor = '';
                element.style.color = '';
            } else {
                element.style.backgroundColor = '#667eea';
                element.style.color = 'white';
            }
        }
        
        function updateProgress(type, current, total) {
            const percentage = Math.min((current / total) * 100, 100);
            const progressBar = document.getElementById(type + '-progress');
            const percentageSpan = document.getElementById(type + '-percentage');
            
            progressBar.style.width = percentage + '%';
            percentageSpan.textContent = Math.round(percentage) + '%';
        }
        
        // رسائل تحفيزية تتغير كل 5 ثوان
        const motivationalQuotes = [
            "التركيز على شيء واحد أفضل من محاولة فعل كل شيء في نفس الوقت",
            "النجاح هو مجموع الجهود الصغيرة المتكررة يوماً بعد يوم",
            "لا تؤجل عمل اليوم إلى الغد، ابدأ الآن ولو بخطوة صغيرة",
            "الانضباط هو اختيار ما تريده أكثر على ما تريده الآن",
            "كل خبير كان مبتدئاً في يوم من الأيام"
        ];
        
        let quoteIndex = 0;
        setInterval(() => {
            const quoteElements = document.querySelectorAll('.motivational-quote');
            quoteElements.forEach(element => {
                if (!element.textContent.includes('وارن بافيت')) {
                    element.textContent = motivationalQuotes[quoteIndex];
                }
            });
            quoteIndex = (quoteIndex + 1) % motivationalQuotes.length;
        }, 5000);
        
        // حفظ البيانات محلياً (في الذاكرة فقط)
        let userData = {
            priorities: [],
            schedule: {},
            progress: {
                reading: 0,
                english: 0,
                programming: 0,
                exercise: 0
            }
        };
        
        // دالة لحفظ التقدم
        function saveProgress() {
            // في التطبيق الحقيقي، ستحفظ البيانات في قاعدة البيانات المحلية
            console.log('تم حفظ التقدم:', userData);
        }
        
        // تحديث كل دقيقة
        setInterval(saveProgress, 60000);
    </script>
</body>
</html>
