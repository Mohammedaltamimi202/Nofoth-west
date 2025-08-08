# Nofoth-west
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>نظام متابعة نفوذ - المنطقة الغربية</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.rtl.min.css" rel="stylesheet">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.10.5/font/bootstrap-icons.css" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js"></script>
    <style>
        :root {
            --primary-color: #781f19;
            --secondary-color: #fdf0f1;
            --accent-color: #d4a5a2;
            --text-color: #5a1612;
            --card-hover: #fce4ec;
        }
        
        body {
            font-family: 'Arial', sans-serif;
            background-color: var(--secondary-color);
            padding: 20px;
            transition: all 0.3s ease;
        }
        
        /* Header styles */
        .header-container {
            background-color: white;
            color: var(--primary-color);
            border: 3px solid var(--primary-color);
            border-radius: 20px;
            padding: 15px;
            font-weight: bold;
            text-align: center;
            margin-bottom: 30px;
            box-shadow: 0 4px 12px rgba(120, 31, 25, 0.15);
        }
        
        .main-title {
            font-size: 2.5rem;
            margin-bottom: 5px;
            letter-spacing: 1px;
        }
        
        .sub-title {
            font-size: 1.5rem;
            opacity: 0.9;
            color: var(--text-color);
        }
        
        /* Dashboard cards */
        .dashboard-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 25px;
            margin-bottom: 40px;
        }
        
        .dashboard-card {
            background-color: white;
            color: var(--primary-color);
            border: 2px solid var(--primary-color);
            border-radius: 20px;
            text-align: center;
            padding: 30px 20px;
            font-weight: bold;
            font-size: 20px;
            cursor: pointer;
            position: relative;
            text-decoration: none;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            height: 100%;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
        }
        
        .dashboard-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 25px rgba(120, 31, 25, 0.2);
            background-color: var(--card-hover);
        }
        
        .card-icon {
            font-size: 3.5rem;
            margin-bottom: 20px;
            color: var(--primary-color);
        }
        
        /* Section styles */
        .section-container {
            display: none;
            background-color: white;
            border-radius: 20px;
            padding: 30px;
            margin-top: 20px;
            box-shadow: 0 5px 25px rgba(0, 0, 0, 0.1);
            border: 1px solid #e0c0c0;
            overflow: auto;
        }
        
        .back-btn {
            background: var(--primary-color);
            color: white;
            border: none;
            padding: 10px 25px;
            border-radius: 30px;
            font-size: 1rem;
            cursor: pointer;
            transition: background 0.3s;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            margin-bottom: 20px;
        }
        
        .back-btn:hover {
            background: var(--text-color);
            transform: scale(1.05);
        }
        
        /* Orders Section Styles */
        .icon-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }
        
        .icon-box {
            background-color: #FFE4E1;
            color: #8B0000;
            border: 2px solid #8B0000;
            border-radius: 20px;
            text-align: center;
            padding: 20px;
            font-weight: bold;
            font-size: 18px;
            cursor: pointer;
            position: relative;
            text-decoration: none;
            transition: all 0.3s;
            min-height: 150px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
        }
        
        .icon-box:hover {
            background-color: #fcdede;
            transform: translateY(-3px);
        }
        
        .dropdown-content, .sub-dropdown {
            display: none;
            position: absolute;
            top: 100%;
            right: 0;
            background-color: #fff;
            color: #8B0000;
            border: 1px solid #8B0000;
            min-width: 200px;
            box-shadow: 0px 8px 16px rgba(0,0,0,0.2);
            border-radius: 10px;
            z-index: 3;
            font-weight: bold;
        }
        
        .dropdown-content div, .sub-dropdown div, .sub-dropdown a {
            padding: 12px 16px;
            cursor: pointer;
            border-bottom: 1px solid #eee;
            text-align: right;
            background-color: #fff;
            text-decoration: none;
            color: #8B0000;
            display: block;
        }
        
        .dropdown-content div:last-child, .sub-dropdown div:last-child, .sub-dropdown a:last-child {
            border-bottom: none;
        }
        
        .sub-item {
            position: relative;
        }
        
        .sub-dropdown {
            right: 100%;
            top: 0;
        }
        
        .sub-item .sub-dropdown {
            display: none;
        }
        
        /* Waste Section Styles */
        .waste-dashboard {
            display: flex;
            justify-content: space-around;
            padding: 40px 20px;
            flex-wrap: wrap;
            gap: 30px;
        }
        
        .waste-card {
            background: white;
            border-radius: 15px;
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
            padding: 30px;
            text-align: center;
            width: 350px;
            transition: transform 0.3s, box-shadow 0.3s;
            cursor: pointer;
            border: 3px solid transparent;
        }
        
        .waste-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 12px 25px rgba(0, 0, 0, 0.2);
        }
        
        .waste-card.match-orders {
            border-color: #781f19;
        }
        
        .waste-card.waste-track {
            border-color: #5a1612;
        }
        
        .waste-icon {
            font-size: 5rem;
            margin-bottom: 20px;
            color: #781f19;
        }
        
        /* Products Section Styles */
        .products-header {
            background: linear-gradient(to right, #781f19, #a02a22);
            color: white;
            padding: 25px;
            text-align: center;
            border-radius: 15px;
            margin-bottom: 20px;
        }
        
        .products-form-container {
            padding: 30px;
            background: white;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }
        
        .form-group {
            margin-bottom: 25px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #781f19;
            font-size: 16px;
        }
        
        .upload-area {
            border: 2px dashed #781f19;
            border-radius: 10px;
            padding: 30px;
            text-align: center;
            background: #fdf0f1;
            cursor: pointer;
            transition: all 0.3s ease;
            min-height: 200px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
        }
        
        .upload-area:hover {
            background: #fbe4e6;
            border-color: #5a1712;
        }
        
        .upload-area i {
            font-size: 50px;
            color: #781f19;
            margin-bottom: 15px;
        }
        
        .upload-text h3 {
            color: #781f19;
            margin-bottom: 5px;
        }
        
        .upload-text p {
            color: #a04a45;
            font-size: 14px;
        }
        
        #image-preview {
            margin-top: 15px;
            display: none;
            max-width: 100%;
            max-height: 300px;
            text-align: center;
        }
        
        #image-preview img {
            max-width: 100%;
            max-height: 250px;
            border-radius: 5px;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
            border: 1px solid #e0c0c0;
        }
        
        select, input[type="date"], input[type="text"] {
            width: 100%;
            padding: 14px;
            border: 1px solid #e0c0c0;
            border-radius: 8px;
            background: white;
            font-size: 16px;
            color: #781f19;
            transition: border 0.3s ease;
        }
        
        select:focus, input[type="date"]:focus, input[type="text"]:focus {
            outline: none;
            border-color: #781f19;
            box-shadow: 0 0 0 3px rgba(120, 31, 25, 0.2);
        }
        
        .btn-container {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-top: 20px;
        }
        
        .btn {
            padding: 14px 35px;
            border: none;
            border-radius: 8px;
            font-size: 17px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .btn-primary {
            background: linear-gradient(to right, #781f19, #a02a22);
            color: white;
        }
        
        .btn-primary:hover {
            background: linear-gradient(to right, #a02a22, #781f19);
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(120, 31, 25, 0.4);
        }
        
        .btn-secondary {
            background: #fdf0f1;
            color: #781f19;
            border: 1px solid #e0c0c0;
        }
        
        .btn-secondary:hover {
            background: #fbe4e6;
        }
        
        .success-message {
            background: #dff0d8;
            border: 1px solid #d0e9c6;
            color: #3c763d;
            padding: 15px;
            border-radius: 8px;
            margin-top: 20px;
            text-align: center;
            display: none;
        }
        
        .form-title {
            color: #781f19;
            text-align: center;
            margin-bottom: 25px;
            padding-bottom: 15px;
            border-bottom: 2px solid #fdf0f1;
        }
        
        /* Toast notifications */
        .toast-container {
            position: fixed;
            bottom: 20px;
            left: 20px;
            z-index: 1060;
            min-width: 300px;
        }
        
        .toast {
            background-color: var(--primary-color);
            color: white;
            border-radius: 10px;
            padding: 15px 20px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
            display: flex;
            align-items: center;
            gap: 15px;
            opacity: 0;
            transform: translateY(20px);
            transition: all 0.4s ease;
        }
        
        .toast.show {
            opacity: 1;
            transform: translateY(0);
        }
        
        .toast i {
            font-size: 1.8rem;
        }
        
        /* Footer */
        .footer {
            text-align: center;
            padding: 20px;
            margin-top: 30px;
            color: var(--text-color);
            font-size: 0.9rem;
            border-top: 1px solid #e0c0c0;
        }
        
        /* Animation */
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .fade-in {
            animation: fadeIn 0.5s ease forwards;
        }
        
        /* Responsive design */
        @media (max-width: 768px) {
            .dashboard-grid {
                grid-template-columns: 1fr;
            }
            
            .main-title {
                font-size: 2rem;
            }
            
            .sub-title {
                font-size: 1.2rem;
            }
            
            .waste-dashboard {
                flex-direction: column;
                align-items: center;
            }
            
            .waste-card {
                width: 100%;
            }
        }
    </style>
</head>
<body>
    <!-- Main Dashboard -->
    <div id="dashboard">
        <div class="header-container fade-in">
            <div class="main-title">شركة نفوذ</div>
            <div class="sub-title">المنطقة الغربية</div>
        </div>
        
        <div class="dashboard-grid">
            <div class="dashboard-card fade-in" onclick="showSection('orders-section')" style="animation-delay: 0.1s">
                <i class="bi bi-clipboard-check card-icon"></i>
                <div>متابعة الطلبيات</div>
                <p class="mt-2 mb-0" style="font-size: 16px; font-weight: normal;">متابعة وتنظيم جميع الطلبيات</p>
            </div>
            
            <div class="dashboard-card fade-in" onclick="showSection('waste-section')" style="animation-delay: 0.2s">
                <i class="bi bi-clipboard-x card-icon"></i>
                <div>متابعة الهدر وفروقات الطلبيات</div>
                <p class="mt-2 mb-0" style="font-size: 16px; font-weight: normal;">تتبع الهدر والفروقات في الطلبيات</p>
            </div>
            
            <div class="dashboard-card fade-in" onclick="showSection('products-section')" style="animation-delay: 0.3s">
                <i class="bi bi-box-seam card-icon"></i>
                <div>متابعة المنتجات الجديدة</div>
                <p class="mt-2 mb-0" style="font-size: 16px; font-weight: normal;">إضافة ومتابعة المنتجات الجديدة</p>
            </div>
        </div>
        
        <div class="footer">
            نظام نفوذ - المنطقة الغربية
        </div>
    </div>
    
    <!-- Orders Section -->
    <div id="orders-section" class="section-container">
        <button class="back-btn" onclick="showDashboard()">
            <i class="fas fa-arrow-left"></i> العودة إلى الرئيسية
        </button>
        
        <div class="header-container" style="margin-top: 20px;">
            <div class="main-title">متابعة الطلبيات</div>
            <div class="sub-title">بوابة متابعة الغربية</div>
        </div>

        <div class="icon-grid">
            <!-- الطلبيات -->
            <div class="icon-box" onclick="toggleDropdown('orders-dropdown')">
                <i class="bi bi-bag-check"></i>
                الطلبيات
                <div class="dropdown-content" id="orders-dropdown">
                    <!-- مامولا -->
                    <div class="sub-item" onclick="toggleSubDropdown(event, 'mamoula-sub')">
                        مامولا
                        <div class="sub-dropdown" id="mamoula-sub">
                            <a href="https://docs.google.com/spreadsheets/d/1rOHIOMq3FCdGKzTHi_HTFJNi0g4IdUabWy13iI275Ao/edit?usp=drivesdk" target="_blank">طلبية المنتجات</a>
                            <a href="https://docs.google.com/spreadsheets/d/1EuaG4s3osNqiMhfX68aWPb6rSDjkyC3hgniUuLk8jZ8/edit?usp=drivesdk" target="_blank">طلبية المستودع</a>
                        </div>
                    </div>

                    <!-- كيك من مامولا -->
                    <div class="sub-item" onclick="toggleSubDropdown(event, 'cake-sub')">
                        كيك من مامولا
                        <div class="sub-dropdown" id="cake-sub">
                            <a href="https://docs.google.com/spreadsheets/d/1XtNX0HzQQh0-p8GpvScYtKjFeJpIFExuWClXrFFemkE/edit?usp=drivesdk" target="_blank">طلبية الكيك</a>
                        </div>
                    </div>

                    <!-- عنبة -->
                    <div class="sub-item" onclick="toggleSubDropdown(event, 'anaba-sub')">
                        عنبة
                        <div class="sub-dropdown" id="anaba-sub">
                            <a href="https://docs.google.com/spreadsheets/d/1sK_yo7QcY-fkUeLP7lXD01OcCfV_fQiOy3fyayieQ8M/edit?usp=sharing" target="_blank">الطلبية اليومية</a>
                            <a href="https://docs.google.com/spreadsheets/d/1EuaG4s3osNqiMhfX68aWPb6rSDjkyC3hgniUuLk8jZ8/edit?usp=drivesdk" target="_blank">طلبية المستودع</a>
                        </div>
                    </div>

                    <!-- لقمة وردية -->
                    <div class="sub-item" onclick="toggleSubDropdown(event, 'lokma-sub')">
                        لقمة وردية
                        <div class="sub-dropdown" id="lokma-sub">
                            <a href="https://docs.google.com/spreadsheets/d/1sp3zhuD9PwCZGItAMO385zIGQvgiaoX0PzZXOCF8SjI/edit?usp=sharing" target="_blank">الطلبية الأسبوعية</a>
                        </div>
                    </div>

                    <!-- قشطية -->
                    <div class="sub-item" onclick="toggleSubDropdown(event, 'qashtia-sub')">
                        قشطية
                        <div class="sub-dropdown" id="qashtia-sub">
                            <a href="https://docs.google.com/spreadsheets/d/141KjwMgoPZb6am5UnLCMVbklVNOg2-YgCtYoVlpWd2I/edit?usp=drivesdk" target="_blank">الطلبية</a>
                        </div>
                    </div>
                </div>
            </div>

            <!-- باقي الأيقونات -->
            <a class="icon-box" href="https://docs.google.com/spreadsheets/d/1qPbIlr1C4Zn11Fo6cUMr3B6t87Uc1k1_cDUEuKAefg0/edit?usp=drivesdk" target="_blank">
                <i class="bi bi-tools"></i>
                الصيانات
            </a>
            <a class="icon-box" href="https://docs.google.com/spreadsheets/d/1_Du-iJcIFD4BnJKPFgGFs5r_0kyoXBNxYQk0Q7gexq8/edit?usp=sharing" target="_blank">
                <i class="bi bi-trash"></i>
                الهدر
            </a>
            <a class="icon-box" href="https://forms.gle/gK3GRwnQQWXZb7NT6" target="_blank">
                <i class="bi bi-calendar-check"></i>
                إغلاق نهاية شهر
            </a>
            <a class="icon-box" href="https://docs.google.com/spreadsheets/d/1KHsFsBBwiW8qDFTX7G8tiK8N_Xa9YHqf1hwEqvkEOIo/edit?usp=drivesdk" target="_blank">
                <i class="bi bi-link-45deg"></i>
                ربط التطبيقات
            </a>
            <a class="icon-box" href="https://docs.google.com/spreadsheets/d/1bJzUp9wSy1f22GIXNOW7rK6QEYHV3JBjqN0LCAsLp88/edit?usp=drivesdk" target="_blank">
                <i class="bi bi-house-door"></i>
                عهدة الفروع
            </a>
            <a class="icon-box" href="https://docs.google.com/spreadsheets/d/1kR-1Vr92iiyFNDTq6-wXo5hoeJdt3o4c-qTwGqCQMIU/edit?usp=drivesdk" target="_blank">
                <i class="bi bi-fire"></i>
                صلاحيات طفايات الحريق
            </a>
            <a class="icon-box" href="https://apps.balady.gov.sa/Eservices/health/Inquiries/Search" target="_blank">
                <i class="bi bi-file-earmark-medical"></i>
                الشهادات الصحية
            </a>
            <div class="icon-box" onclick="toggleDropdown('inventory-dropdown')">
                <i class="bi bi-clipboard-data"></i>
                الجرد
                <div class="dropdown-content" id="inventory-dropdown">
                    <div>الجرد اليومي</div>
                    <div>الجرد الشهري</div>
                </div>
            </div>
        </div>

        <!-- خاص بالمدير -->
        <div class="header-container mt-5" onclick="showLoginPrompt()" style="cursor:pointer;">
            <div class="main-title">خاص بالمدير</div>
        </div>

        <!-- واجهة المدير -->
        <div class="icon-grid mt-3" id="manager-panel" style="display: none;">
            <a class="icon-box" href="#">
                <i class="bi bi-camera-video"></i> 
                متابعة الكاميرات
            </a>
            <a class="icon-box" href="#">
                <i class="bi bi-cash-coin"></i> 
                متابعة الترصيد
            </a>
            <a class="icon-box" href="#">
                <i class="bi bi-person-walking"></i> 
                الزيارات
            </a>
            <a class="icon-box" href="#">
                <i class="bi bi-stars"></i> 
                متابعة المنتجات الجديدة
            </a>
        </div>
    </div>
    
    <!-- Waste Section -->
    <div id="waste-section" class="section-container">
        <button class="back-btn" onclick="showDashboard()">
            <i class="fas fa-arrow-left"></i> العودة إلى الرئيسية
        </button>
        
        <div class="header-container">
            <div class="main-title">متابعة الهدر وفروقات الطلبيات</div>
            <div class="sub-title">نفوذ الغربية</div>
        </div>
        
        <div class="waste-dashboard">
            <div class="waste-card match-orders" id="matchOrdersCard">
                <div class="waste-icon">
                    <i class="fas fa-clipboard-check"></i>
                </div>
                <h2>مطابقة الطلبيات</h2>
                <p>الضغط هنا لمطابقة الطلبيات المرسلة مع المستلمة والتحقق من وجود أي نقص</p>
            </div>
            
            <div class="waste-card waste-track" id="wasteTrackCard">
                <div class="waste-icon">
                    <i class="fas fa-chart-line"></i>
                </div>
                <h2>متابعة الهدر</h2>
                <p>الضغط هنا لمتابعة الهدر وتصنيفه حسب النوع (هدر النقل، هدر الفرع)</p>
            </div>
        </div>
        
        <!-- Waste Tracking Panel Content -->
        <div class="mt-5" style="background: white; padding: 25px; border-radius: 15px; box-shadow: 0 5px 15px rgba(0,0,0,0.1);">
            <h3 class="text-center" style="color: #781f19; margin-bottom: 25px;">نظام متابعة الهدر الشامل</h3>
            
            <div class="row">
                <div class="col-md-6 mb-4">
                    <div class="card h-100 border-primary">
                        <div class="card-header bg-primary text-white">
                            <i class="fas fa-truck me-2"></i> هدر النقل
                        </div>
                        <div class="card-body">
                            <p>تتبع وتصنيف الهدر الناتج عن عمليات النقل والتوزيع</p>
                            <ul class="list-group">
                                <li class="list-group-item">تسجيل الأصناف التالفة أثناء النقل</li>
                                <li class="list-group-item">تحديد كميات الهدر لكل شحنة</li>
                                <li class="list-group-item">تحليل أسباب الهدر في النقل</li>
                            </ul>
                        </div>
                    </div>
                </div>
                
                <div class="col-md-6 mb-4">
                    <div class="card h-100 border-danger">
                        <div class="card-header bg-danger text-white">
                            <i class="fas fa-store me-2"></i> هدر الفرع
                        </div>
                        <div class="card-body">
                            <p>تتبع وتصنيف الهدر الناتج داخل فروع المؤسسة</p>
                            <ul class="list-group">
                                <li class="list-group-item">تسجيل الأصناف التالفة داخل الفروع</li>
                                <li class="list-group-item">متابعة هدر الطهي والإنتاج</li>
                                <li class="list-group-item">تحليل أسباب الهدر في الفروع</li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="text-center mt-4">
                <button class="btn btn-lg" style="background: #781f19; color: white;">
                    <i class="fas fa-file-excel me-2"></i> تصدير تقارير الهدر
                </button>
            </div>
        </div>
    </div>
    
    <!-- Products Section -->
    <div id="products-section" class="section-container">
        <button class="back-btn" onclick="showDashboard()">
            <i class="fas fa-arrow-left"></i> العودة إلى الرئيسية
        </button>
        
        <div class="products-header">
            <h1><i class="fas fa-cube"></i> متابعة المنتجات الجديدة</h1>
            <p> نفوذ الغربية</p>
        </div>
        
        <div class="products-form-container">
            <h2 class="form-title"><i class="fas fa-edit"></i> تفاصيل المنتج</h2>
            
            <div class="form-group">
                <label for="product-image">صورة المنتج:</label>
                <div class="upload-area" id="upload-area">
                    <i class="fas fa-cloud-upload-alt"></i>
                    <div class="upload-text">
                        <h3>انقر لرفع صورة المنتج</h3>
                        <p>الحد الأقصى لحجم الصورة: 5MB (PNG, JPG)</p>
                    </div>
                    <input type="file" id="image-upload" accept="image/*" style="display:none">
                </div>
                <div id="image-preview">
                    <img id="preview" src="#" alt="معاينة الصورة">
                </div>
            </div>
            
            <div class="form-group">
                <label for="brand">البراند:</label>
                <select id="brand">
                    <option value="">-- اختر البراند --</option>
                    <option value="mamula">مامولا</option>
                    <option value="aneba">عنبة</option>
                    <option value="lqma">لقمة وردية</option>
                    <option value="qeshtia">قشطية</option>
                    <option value="cake">كيك من مامولا</option>
                </select>
            </div>
            
            <div class="form-group">
                <label for="branch">الفرع:</label>
                <select id="branch">
                    <option value="">-- اختر الفرع --</option>
                    <option value="riyadh">النعيم</option>
                    <option value="riyadh">الحمدانية</option>
                    <option value="riyadh">السامر</option>
                    <option value="riyadh">النسيم</option>
                    <option value="jeddah">ابحر</option>
                    <option value="dammam">الصفاء</option>
                    <option value="dammam">الجال</option>
                    <option value="dammam">الشوقية</option>
                    <option value="madinah">السنابل</option>
                </select>
            </div>
            
            <div class="form-group">
                <label for="product-name">اسم المنتج:</label>
                <input type="text" id="product-name" placeholder="أدخل اسم المنتج يدويًا">
            </div>
            
            <div class="form-group">
                <label for="date">تاريخ المنتج:</label>
                <input type="date" id="date">
            </div>
            
            <div class="btn-container">
                <button class="btn btn-primary" id="submit-btn"><i class="fas fa-plus-circle"></i> إضافة المنتج</button>
                <button class="btn btn-secondary"><i class="fas fa-times"></i> إلغاء</button>
            </div>
            
            <div class="success-message" id="success-message">
                <i class="fas fa-check-circle"></i> تم إضافة المنتج بنجاح! سيتم إرسال البيانات قريبًا.
            </div>
        </div>
        
        <div class="mt-5" style="background: white; padding: 25px; border-radius: 15px; box-shadow: 0 5px 15px rgba(0,0,0,0.1);">
            <h3 class="text-center" style="color: #781f19; margin-bottom: 25px;">أحدث المنتجات المضافة</h3>
            
            <div class="row">
                <div class="col-md-4 mb-4">
                    <div class="card h-100">
                        <img src="https://via.placeholder.com/300x200?text=منتج+جديد+1" class="card-img-top" alt="منتج جديد">
                        <div class="card-body">
                            <h5 class="card-title">كيك الشوكولاتة الفاخر</h5>
                            <p class="card-text">براند: كيك من مامولا</p>
                            <p class="card-text">تم الإضافة: 2025-08-01</p>
                        </div>
                    </div>
                </div>
                
                <div class="col-md-4 mb-4">
                    <div class="card h-100">
                        <img src="https://via.placeholder.com/300x200?text=منتج+جديد+2" class="card-img-top" alt="منتج جديد">
                        <div class="card-body">
                            <h5 class="card-title">معجنات عنبة المميزة</h5>
                            <p class="card-text">براند: عنبة</p>
                            <p class="card-text">تم الإضافة: 2025-07-28</p>
                        </div>
                    </div>
                </div>
                
                <div class="col-md-4 mb-4">
                    <div class="card h-100">
                        <img src="https://via.placeholder.com/300x200?text=منتج+جديد+3" class="card-img-top" alt="منتج جديد">
                        <div class="card-body">
                            <h5 class="card-title">لقمة وردية بالجبنة</h5>
                            <p class="card-text">براند: لقمة وردية</p>
                            <p class="card-text">تم الإضافة: 2025-07-25</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Toast Notification Container -->
    <div class="toast-container">
        <div class="toast" id="notification-toast">
            <i class="fas fa-info-circle"></i>
            <div id="toast-message">مرحبًا بك في نظام نفوذ</div>
        </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
    <script>
        // Navigation functions
        function showDashboard() {
            document.getElementById('dashboard').style.display = 'block';
            document.getElementById('orders-section').style.display = 'none';
            document.getElementById('waste-section').style.display = 'none';
            document.getElementById('products-section').style.display = 'none';
        }
        
        function showSection(sectionId) {
            document.getElementById('dashboard').style.display = 'none';
            document.getElementById('orders-section').style.display = 'none';
            document.getElementById('waste-section').style.display = 'none';
            document.getElementById('products-section').style.display = 'none';
            
            document.getElementById(sectionId).style.display = 'block';
            
            // Show toast notification
            let message = "";
            switch(sectionId) {
                case 'orders-section':
                    message = "تم فتح متابعة الطلبيات";
                    break;
                case 'waste-section':
                    message = "تم فتح متابعة الهدر وفروقات الطلبيات";
                    break;
                case 'products-section':
                    message = "تم فتح متابعة المنتجات الجديدة";
                    break;
            }
            showToast(message);
        }
        
        // Toast notification
        function showToast(message) {
            const toast = document.getElementById('notification-toast');
            const toastMessage = document.getElementById('toast-message');
            
            toastMessage.textContent = message;
            toast.classList.add('show');
            
            setTimeout(() => {
                toast.classList.remove('show');
            }, 3000);
        }
        
        // Show login prompt for manager
        function showLoginPrompt() {
            if (sessionStorage.getItem('managerLoggedIn') === 'true') {
                document.getElementById('manager-panel').style.display = 'grid';
            } else {
                const password = prompt("الرجاء إدخال كلمة مرور المدير:");
                const correctPassword = '1234'; // Replace with your password
                
                if (password === correctPassword) {
                    sessionStorage.setItem('managerLoggedIn', 'true');
                    document.getElementById('manager-panel').style.display = 'grid';
                    showToast("تم تسجيل دخول المدير بنجاح");
                } else if (password !== null) {
                    alert("كلمة المرور غير صحيحة");
                }
            }
        }
        
        // Dropdown functions
        function toggleDropdown(id) {
            document.querySelectorAll('.dropdown-content').forEach(el => {
                if (el.id !== id) el.style.display = 'none';
            });
            const dropdown = document.getElementById(id);
            dropdown.style.display = dropdown.style.display === 'block' ? 'none' : 'block';
        }

        function toggleSubDropdown(event, id) {
            event.stopPropagation();
            document.querySelectorAll('.sub-dropdown').forEach(el => {
                if (el.id !== id) el.style.display = 'none';
            });
            const sub = document.getElementById(id);
            sub.style.display = sub.style.display === 'block' ? 'none' : 'block';
        }

        document.addEventListener('click', function (e) {
            if (!e.target.closest('.icon-box')) {
                document.querySelectorAll('.dropdown-content, .sub-dropdown').forEach(el => el.style.display = 'none');
            }
        });
        
        // Product image upload
        document.getElementById('upload-area').addEventListener('click', function() {
            document.getElementById('image-upload').click();
        });
        
        document.getElementById('image-upload').addEventListener('change', function(e) {
            if (e.target.files.length > 0) {
                const file = e.target.files[0];
                const reader = new FileReader();
                
                reader.onload = function(e) {
                    const preview = document.getElementById('preview');
                    preview.src = e.target.result;
                    document.getElementById('image-preview').style.display = 'block';
                    
                    const uploadArea = document.getElementById('upload-area');
                    uploadArea.innerHTML = '';
                    const img = document.createElement('img');
                    img.src = e.target.result;
                    img.style.maxWidth = '100%';
                    img.style.maxHeight = '250px';
                    img.style.borderRadius = '5px';
                    uploadArea.appendChild(img);
                }
                
                reader.readAsDataURL(file);
            }
        });
        
        // Set today as default date for products section
        const today = new Date().toISOString().split('T')[0];
        document.getElementById('date').value = today;
        
        // Form submission handler for products
        document.getElementById('submit-btn').addEventListener('click', function() {
            const brand = document.getElementById('brand').value;
            const branch = document.getElementById('branch').value;
            const productName = document.getElementById('product-name').value;
            const date = document.getElementById('date').value;
            const imageUpload = document.getElementById('image-upload').files[0];
            
            if (!brand || !branch || !productName || !date || !imageUpload) {
                showToast('يرجى ملء جميع الحقول ورفع صورة المنتج');
                return;
            }
            
            showToast(`تم إضافة المنتج "${productName}" بنجاح`);
            
            // Reset form
            setTimeout(() => {
                document.getElementById('upload-area').innerHTML = `
                    <i class="fas fa-cloud-upload-alt"></i>
                    <div class="upload-text">
                        <h3>انقر لرفع صورة المنتج</h3>
                        <p>الحد الأقصى لحجم الصورة: 5MB (PNG, JPG)</p>
                    </div>
                `;
                document.getElementById('image-preview').style.display = 'none';
                document.getElementById('brand').value = '';
                document.getElementById('branch').value = '';
                document.getElementById('product-name').value = '';
                document.getElementById('date').value = today;
                document.getElementById('image-upload').value = '';
            }, 1000);
        });
        
        // Initial toast
        setTimeout(() => {
            showToast("مرحبًا بك في  نفوذ - المنطقة الغربية");
        }, 1000);
    </script>
</body>
</html>
