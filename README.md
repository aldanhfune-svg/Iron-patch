<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>تطبيق حديدك - IronPatch</title>
    <!-- Chart.js للرسم البياني -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <!-- FontAwesome للأيقونات -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #10b981;
            --primary-dark: #059669;
            --bg-light: #f3f4f6;
            --card-bg: #ffffff;
            --text-main: #1f2937;
            --text-sub: #4b5563;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--bg-light);
            color: var(--text-main);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 15px;
        }

        .mobile-container {
            width: 100%;
            max-width: 400px;
            background-color: var(--card-bg);
            border-radius: 30px;
            box-shadow: 0 15px 35px rgba(0,0,0,0.1);
            overflow: hidden;
            border: 8px solid #ffffff;
        }

        /* Header */
        .app-header {
            background: linear-gradient(135deg, #10b981, #047857);
            color: white;
            padding: 25px 20px;
            text-align: center;
            position: relative;
        }

        .app-header h1 {
            font-size: 1.5rem;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .status-badge {
            display: inline-block;
            background: rgba(255, 255, 255, 0.2);
            padding: 4px 12px;
            border-radius: 15px;
            font-size: 0.8rem;
            margin-top: 8px;
        }

        /* Main Content */
        .app-body {
            padding: 20px;
        }

        .card {
            background: #f9fafb;
            border-radius: 16px;
            padding: 18px;
            margin-bottom: 15px;
            border: 1px solid #e5e7eb;
        }

        .card-title {
            font-size: 0.95rem;
            color: var(--text-sub);
            margin-bottom: 10px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        /* Gauge / Current Reading */
        .value-display {
            text-align: center;
            padding: 10px 0;
        }

        .reading-number {
            font-size: 3rem;
            font-weight: bold;
            color: var(--primary-dark);
            line-height: 1;
        }

        .unit {
            font-size: 0.9rem;
            color: var(--text-sub);
        }

        .health-status {
            display: inline-flex;
            align-items: center;
            gap: 6px;
            background-color: #d1fae5;
            color: #065f46;
            padding: 6px 14px;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: bold;
            margin-top: 10px;
        }

        /* Test Controls */
        .demo-controls {
            display: flex;
            gap: 8px;
            margin-top: 10px;
            justify-content: center;
        }

        .btn-sm {
            padding: 5px 10px;
            font-size: 0.75rem;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            transition: 0.2s;
        }

        .btn-normal { background-color: #d1fae5; color: #065f46; }
        .btn-low { background-color: #fee2e2; color: #991b1b; }
        .btn-high { background-color: #fef3c7; color: #92400e; }

        /* Actions */
        .btn-primary {
            width: 100%;
            background-color: var(--primary);
            color: white;
            border: none;
            padding: 14px;
            border-radius: 12px;
            font-size: 1rem;
            font-weight: bold;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            transition: background 0.3s;
        }

        .btn-primary:hover {
            background-color: var(--primary-dark);
        }

        /* Footer Nav */
        .nav-bar {
            display: flex;
            justify-content: space-around;
            padding: 12px 0;
            background: #ffffff;
            border-top: 1px solid #e5e7eb;
        }

        .nav-item {
            text-align: center;
            color: #9ca3af;
            font-size: 0.75rem;
            text-decoration: none;
        }

        .nav-item.active {
            color: var(--primary);
            font-weight: bold;
        }

        .nav-item i {
            font-size: 1.2rem;
            display: block;
            margin-bottom: 3px;
        }
    </style>
</head>
<body>

<div class="mobile-container">
    <!-- Header -->
    <div class="app-header">
        <h1><i class="fa-solid fa-droplet"></i> حديدك IronPatch</h1>
        <div class="status-badge"><i class="fa-solid fa-wifi"></i> اللاصقة متصلة (سلكياً/لاسلكياً)</div>
    </div>

    <!-- Main Content -->
    <div class="app-body">
        
        <!-- Current Value Card -->
        <div class="card">
            <div class="card-title"><i class="fa-solid fa-heart-pulse"></i> القراءة الحالية</div>
            <div class="value-display">
                <div class="reading-number" id="ironValue">18.5</div>
                <div class="unit">μmol/L</div>
                <div class="health-status" id="statusBadge">
                    <i class="fa-solid fa-circle-check"></i> ضمن النطاق الطبيعي
                </div>
            </div>

            <!-- Demo Simulation Buttons -->
            <div class="demo-controls">
                <button class="btn-sm btn-low" onclick="updateReading(8.2, 'low')">محاكاة انخفاض</button>
                <button class="btn-sm btn-normal" onclick="updateReading(18.5, 'normal')">طبيعي</button>
                <button class="btn-sm btn-high" onclick="updateReading(32.0, 'high')">محاكاة ارتفاع</button>
            </div>
        </div>

        <!-- Weekly Chart Card -->
        <div class="card">
            <div class="card-title"><i class="fa-solid fa-chart-line"></i> تاريخ القراءات (أسبوعي)</div>
            <canvas id="ironChart" height="160"></canvas>
        </div>

        <!-- Recommendation Card -->
        <div class="card">
            <div class="card-title"><i class="fa-solid fa-lightbulb"></i> الإرشادات والتوصيات</div>
            <p id="recommendationText" style="font-size: 0.85rem; color: var(--text-sub); line-height: 1.5;">
                مستويات الحديد ممتازة لديك! احرص على تناول الأغذية الغنية بالفيتمينات واستمر على النمط الغذائي المتوازن.
            </p>
        </div>

        <!-- Action Button -->
        <button class="btn-primary" onclick="exportReport()">
            <i class="fa-solid fa-file-arrow-down"></i> تحميل التقرير الطبي (PDF)
        </button>

    </div>

    <!-- Navigation Bar -->
    <div class="nav-bar">
        <a href="#" class="nav-item active"><i class="fa-solid fa-house"></i>الرئيسية</a>
        <a href="#" class="nav-item"><i class="fa-solid fa-chart-simple"></i>التقارير</a>
        <a href="#" class="nav-item"><i class="fa-solid fa-apple-whole"></i>النصائح</a>
        <a href="#" class="nav-item"><i class="fa-solid fa-gear"></i>الإعدادات</a>
    </div>
</div>

<script>
    // Initialize Chart
    const ctx = document.getElementById('ironChart').getContext('2d');
    const ironChart = new Chart(ctx, {
        type: 'line',
        data: {
            labels: ['1 سبتمبر', '5 سبتمبر', '10 سبتمبر', '15 سبتمبر', '20 سبتمبر'],
            datasets: [{
                label: 'مستوى الحديد (μmol/L)',
                data: [12, 14, 11, 16, 18.5],
                borderColor: '#10b981',
                backgroundColor: 'rgba(16, 185, 129, 0.1)',
                fill: true,
                tension: 0.4,
                pointRadius: 4
            }]
        },
        options: {
            responsive: true,
            plugins: { legend: { display: false } },
            scales: {
                y: { min: 0, max: 35 }
            }
        }
    });

    // Update Reading Function
    function updateReading(val, type) {
        document.getElementById('ironValue').innerText = val;
        const badge = document.getElementById('statusBadge');
        const text = document.getElementById('recommendationText');

        if(type === 'low') {
            badge.style.backgroundColor = '#fee2e2';
            badge.style.color = '#991b1b';
            badge.innerHTML = '<i class="fa-solid fa-triangle-exclamation"></i> انخفاض في مستوى الحديد';
            text.innerText = 'تنبيه: تم رصد انخفاض في الحديد. يوصى بتناول الأطعمة الغنية بالحديد (مثل السبانخ واللحوم الحمراء) ومراجعة الطبيب.';
        } else if(type === 'high') {
            badge.style.backgroundColor = '#fef3c7';
            badge.style.color = '#92400e';
            badge.innerHTML = '<i class="fa-solid fa-circle-exclamation"></i> ارتـفـاع في المستوى';
            text.innerText = 'ملاحظة: نسبة الحديد أعلى من المعتاد. يرجى الاستشارة قبل تناول أي مكملات إضافية.';
        } else {
            badge.style.backgroundColor = '#d1fae5';
            badge.style.color = '#065f46';
            badge.innerHTML = '<i class="fa-solid fa-circle-check"></i> ضمن النطاق الطبيعي';
            text.innerText = 'مستويات الحديد ممتازة لديك! احرص على تناول الأغذية الغنية بالفيتمينات واستمر على النمط الغذائي المتوازن.';
        }
    }

    // Export PDF Report Simulation
    function exportReport() {
        alert('جاري توليد التقرير الطبي لـ IronPatch بصيغة PDF لمشاركته مع الطبيب المتابع...');
    }
</script>

</body>
</html>


