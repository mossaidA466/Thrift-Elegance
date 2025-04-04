# Thrift-Elegance
Thrift Elegance
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>أناقة التوفير - منصة الملابس المستعملة</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css">
    <style>
        /* CSS Reset & Fonts */
        @import url('https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Tajawal', sans-serif;
            background: #f8f9fa;
            color: #333;
        }

        /* نظام الألوان */
        :root {
            --primary: #2A9D8F;
            --primary-light: #40b5a7;
            --primary-dark: #1e7268;
            --secondary: #264653;
            --accent: #E76F51;
            --light: #F4A261;
            --light-gray: #f1f1f1;
            --gray: #6c757d;
            --error: #dc3545;
            --success: #28a745;
        }

        /* تنسيق الصفحة الرئيسية */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 1.5rem;
        }

        /* الهيدر المحسن */
        .header {
            background: white;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        .header-content {
            max-width: 1200px;
            margin: 0 auto;
            padding: 1rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--primary);
            display: flex;
            align-items: center;
            gap: 0.5rem;
            text-decoration: none;
        }

        .logo i {
            font-size: 1.8rem;
        }

        /* نظام البحث المحسن */
        .search-bar {
            flex: 0 1 500px;
            position: relative;
        }

        .search-input {
            width: 100%;
            padding: 0.8rem 3rem 0.8rem 1.2rem;
            border: 2px solid #ddd;
            border-radius: 25px;
            font-size: 1rem;
            transition: all 0.3s;
        }

        .search-input:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 8px rgba(42,157,143,0.3);
        }

        .search-icon {
            position: absolute;
            left: 1rem;
            top: 50%;
            transform: translateY(-50%);
            color: var(--gray);
        }

        /* أزرار المستخدم */
        .user-nav {
            display: flex;
            gap: 1rem;
            align-items: center;
        }

        .user-menu {
            position: relative;
        }

        .user-avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: var(--light-gray);
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--gray);
            transition: all 0.2s;
        }

        .user-avatar:hover {
            background: var(--light);
            color: white;
        }

        .dropdown-menu {
            position: absolute;
            top: 100%;
            left: 0;
            background: white;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            border-radius: 8px;
            width: 200px;
            z-index: 10;
            overflow: hidden;
            display: none;
        }

        .dropdown-menu.active {
            display: block;
            animation: fadeIn 0.3s;
        }

        .dropdown-item {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            padding: 0.8rem 1rem;
            color: var(--secondary);
            text-decoration: none;
            transition: all 0.2s;
        }

        .dropdown-item:hover {
            background: var(--light-gray);
        }

        /* الأزرار */
        .btn {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
            padding: 0.8rem 1.5rem;
            border-radius: 25px;
            border: none;
            cursor: pointer;
            font-weight: 500;
            font-size: 0.95rem;
            transition: all 0.3s;
            text-decoration: none;
        }

        .btn-primary {
            background: var(--primary);
            color: white;
        }

        .btn-primary:hover {
            background: var(--primary-dark);
        }

        .btn-outline {
            background: transparent;
            border: 2px solid var(--primary);
            color: var(--primary);
        }

        .btn-outline:hover {
            background: var(--primary);
            color: white;
        }

        .btn-accent {
            background: var(--accent);
            color: white;
        }

        .btn-accent:hover {
            background: #d15a45;
        }

        /* فلترات البحث المحسنة */
        .filters-container {
            background: white;
            padding: 1.2rem;
            border-radius: 10px;
            margin: 1.5rem 0;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
        }

        .filters {
            display: flex;
            gap: 0.8rem;
            flex-wrap: wrap;
        }

        .filter-btn {
            background: var(--light-gray);
            border: none;
            padding: 0.6rem 1.2rem;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.2s;
            font-size: 0.9rem;
        }

        .filter-btn.active {
            background: var(--primary);
            color: white;
        }

        .advanced-filters {
            margin-top: 1.2rem;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1rem;
        }

        .filter-group {
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
        }

        .filter-group label {
            font-weight: 500;
            color: var(--secondary);
            font-size: 0.9rem;
        }

        .filter-select, .filter-input {
            padding: 0.6rem;
            border: 1px solid #ddd;
            border-radius: 6px;
            font-size: 0.9rem;
            transition: all 0.2s;
        }

        .filter-select:focus, .filter-input:focus {
            outline: none;
            border-color: var(--primary);
        }

        .price-range {
            display: flex;
            gap: 0.5rem;
            align-items: center;
        }

        .price-range input {
            flex: 1;
        }

        /* بطاقات المنتجات المحسنة */
        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 1.5rem;
            padding: 1.5rem 0;
        }

        .product-card {
            background: white;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
            transition: all 0.3s;
            position: relative;
        }

        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 20px rgba(0,0,0,0.15);
        }

        .wishlist-btn {
            position: absolute;
            top: 1rem;
            right: 1rem;
            background: rgba(255,255,255,0.8);
            border: none;
            width: 35px;
            height: 35px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            z-index: 5;
            transition: all 0.2s;
        }

        .wishlist-btn i {
            color: var(--gray);
            transition: all 0.2s;
        }

        .wishlist-btn:hover {
            background: white;
        }

        .wishlist-btn:hover i, .wishlist-btn.active i {
            color: var(--accent);
        }

        .product-image {
            height: 250px;
            position: relative;
            overflow: hidden;
        }

        .product-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: all 0.5s;
        }

        .product-card:hover .product-image img {
            transform: scale(1.05);
        }

        .product-badge {
            position: absolute;
            top: 1rem;
            left: 1rem;
            background: var(--accent);
            color: white;
            padding: 0.3rem 0.8rem;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 500;
            z-index: 5;
        }

        .product-badge.new {
            background: var(--primary);
        }

        .product-badge.discount {
            background: var(--accent);
        }

        /* تفاصيل المنتج */
        .product-details {
            padding: 1.2rem;
        }

        .product-title {
            font-size: 1.1rem;
            margin-bottom: 0.5rem;
            font-weight: 500;
            color: var(--secondary);
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        .product-meta {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 0.8rem;
        }

        .product-seller {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            font-size: 0.85rem;
            color: var(--gray);
        }

        .seller-avatar {
            width: 25px;
            height: 25px;
            border-radius: 50%;
            background: var(--light-gray);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.7rem;
        }

        .product-rating {
            display: flex;
            align-items: center;
            gap: 0.3rem;
            color: var(--gray);
            font-size: 0.85rem;
        }

        .rating-stars {
            color: #FFD700;
        }

        .product-pricing {
            display: flex;
            align-items: baseline;
            gap: 0.5rem;
            margin-bottom: 1rem;
        }

        .product-price {
            color: var(--primary);
            font-size: 1.3rem;
            font-weight: 700;
        }

        .product-price.original {
            color: var(--gray);
            font-size: 1rem;
            font-weight: 400;
            text-decoration: line-through;
        }

        .product-actions {
            display: flex;
            gap: 0.8rem;
        }

        .action-btn {
            flex: 1;
            padding: 0.6rem;
            border-radius: 6px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
            transition: all 0.2s;
            cursor: pointer;
            font-size: 0.9rem;
        }

        .buy-btn {
            background: var(--primary);
            color: white;
            border: none;
        }

        .buy-btn:hover {
            background: var(--primary-dark);
        }

        .chat-btn {
            background: transparent;
            border: 1px solid var(--primary);
            color: var(--primary);
        }

        .chat-btn:hover {
            background: var(--primary-light);
            color: white;
        }

        /* نظام الأمان */
        .security-badge {
            display: inline-flex;
            align-items: center;
            gap: 0.3rem;
            background: var(--success);
            color: white;
            padding: 0.3rem 0.8rem;
            border-radius: 15px;
            font-size: 0.75rem;
            margin-top: 0.8rem;
        }

        /* التصنيفات المميزة */
        .featured-categories {
            padding: 2rem 0;
        }

        .section-title {
            font-size: 1.5rem;
            color: var(--secondary);
            margin-bottom: 1.5rem;
            font-weight: 700;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .section-title i {
            color: var(--primary);
        }

        .categories-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
            gap: 1.2rem;
        }

        .category-card {
            position: relative;
            border-radius: 10px;
            overflow: hidden;
            aspect-ratio: 1;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
            transition: all 0.3s;
        }

        .category-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 15px rgba(0,0,0,0.15);
        }

        .category-image {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .category-overlay {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: linear-gradient(transparent, rgba(0,0,0,0.7));
            padding: 1rem;
            color: white;
        }

        .category-title {
            font-size: 1.1rem;
            font-weight: 600;
            margin-bottom: 0.3rem;
        }

        .category-count {
            font-size: 0.8rem;
            opacity: 0.9;
        }

        /* نظام العضويات */
        .membership-banner {
            background: linear-gradient(45deg, var(--primary), var(--secondary));
            border-radius: 15px;
            padding: 2rem;
            color: white;
            margin: 2rem 0;
            display: flex;
            align-items: center;
            gap: 2rem;
            box-shadow: 0 5px 15px rgba(38, 70, 83, 0.2);
        }

        .banner-content {
            flex: 1;
        }

        .banner-title {
            font-size: 1.8rem;
            margin-bottom: 1rem;
            font-weight: 700;
        }

        .banner-text {
            margin-bottom: 1.5rem;
            line-height: 1.5;
            opacity: 0.9;
        }

        .membership-badges {
            display: flex;
            gap: 1rem;
            margin-bottom: 1.5rem;
        }

        .badge {
            background: rgba(255,255,255,0.2);
            padding: 0.5rem 1rem;
            border-radius: 20px;
            font-size: 0.9rem;
            display: flex;
            align-items: center;
            gap: 0.3rem;
        }

        .banner-image {
            flex: 0 0 200px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .banner-image img {
            max-width: 100%;
            border-radius: 10px;
        }

        /* نظام التعليقات والمراجعات */
        .reviews-section {
            padding: 2rem 0;
        }

        .reviews-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
            gap: 1.5rem;
        }

        .review-card {
            background: white;
            border-radius: 10px;
            padding: 1.5rem;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
        }

        .review-header {
            display: flex;
            align-items: center;
            gap: 1rem;
            margin-bottom: 1rem;
        }

        .reviewer-avatar {
            width: 45px;
            height: 45px;
            border-radius: 50%;
            background: var(--light-gray);
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .reviewer-details {
            flex: 1;
        }

        .reviewer-name {
            font-weight: 500;
            color: var(--secondary);
            margin-bottom: 0.2rem;
        }

        .review-date {
            font-size: 0.8rem;
            color: var(--gray);
        }

        .review-rating {
            display: flex;
            gap: 0.1rem;
            font-size: 0.9rem;
            color: #FFD700;
            margin-bottom: 0.8rem;
        }

        .review-text {
            color: var(--gray);
            line-height: 1.5;
            margin-bottom: 1rem;
        }

        .review-product {
            display: flex;
            align-items: center;
            gap: 0.8rem;
            background: var(--light-gray);
            padding: 0.8rem;
            border-radius: 8px;
        }

        .review-product-image {
            width: 50px;
            height: 50px;
            border-radius: 6px;
            background: white;
            overflow: hidden;
        }

        .review-product-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .review-product-details {
            flex: 1;
        }

        .review-product-title {
            font-size: 0.9rem;
            color: var(--secondary);
            font-weight: 500;
            margin-bottom: 0.2rem;
        }

        .review-product-price {
            font-size: 0.85rem;
            color: var(--primary);
            font-weight: 500;
        }

        /* الفوتر المحسن */
        .footer {
            background: var(--secondary);
            color: white;
            padding: 3rem 0 1.5rem;
            margin-top: 2rem;
        }

        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 2rem;
            margin-bottom: 2rem;
        }

        .footer-column h3 {
            font-size: 1.2rem;
            margin-bottom: 1.2rem;
            font-weight: 600;
        }

        .footer-links {
            display: flex;
            flex-direction: column;
            gap: 0.8rem;
        }

        .footer-link {
            color: rgba(255,255,255,0.8);
            text-decoration: none;
            transition: all 0.2s;
        }

        .footer-link:hover {
            color: white;
            transform: translateX(-5px);
        }

        .newsletter {
            margin-top: 1rem;
        }

        .newsletter-form {
            display: flex;
            gap: 0.5rem;
            margin-top: 0.8rem;
        }

        .newsletter-input {
            flex: 1;
            padding: 0.8rem;
            border-radius: 6px;
            border: none;
            font-size: 0.9rem;
        }

        .newsletter-btn {
            background: var(--accent);
            color: white;
            border: none;
            border-radius: 6px;
            padding: 0 1rem;
            cursor: pointer;
            transition: all 0.2s;
        }

        .newsletter-btn:hover {
            background: #d15a45;
        }

        .social-icons {
            display: flex;
            gap: 1rem;
            margin-top: 1.2rem;
        }

        .social-icon {
            width: 35px;
            height: 35px;
            border-radius: 50%;
            background: rgba(255,255,255,0.1);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            transition: all 0.2s;
        }

        .social-icon:hover {
            background: var(--primary);
            transform: translateY(-3px);
        }

        .footer-bottom {
            border-top: 1px solid rgba(255,255,255,0.1);
            padding-top: 1.5rem;
            text-align: center;
            color: rgba(255,255,255,0.7);
            font-size: 0.9rem;
        }

        /* النافذة المنبثقة للتسجيل */
        .modal {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0,0,0,0.5);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 2000;
            opacity: 0;
            visibility: hidden;
            transition: all 0.3s;
        }

        .modal.active {
            opacity: 1;
            visibility: visible;
        }

        .modal-content {
            background: white;
            border-radius: 15px;
            width: 400px;
            max-width: 90%;
            overflow: hidden;
            box-shadow: 0 5px 25px rgba(0,0,0,0.2);
            transform: translateY(-20px);
            transition: all 0.3s;
        }

        .modal.active .modal-content {
            transform: translateY(0);
        }

        .modal-header {
            padding: 1.5rem;
            background: var(--primary);
            color: white;
            position: relative;
        }

        .modal-title {
            font-size: 1.3rem;
            font-weight: 600;
            margin-bottom: 0.3rem;
        }

        .modal-subtitle {
            opacity: 0.9;
            font-size: 0.9rem;
        }

        .close-modal {
            position: absolute;
            top: 1rem;
            left: 1rem;
            background: none;
            border: none;
            color: white;
            font-size: 1.2rem;
            cursor: pointer;
            opacity: 0.8;
            transition: all 0.2s;
        }

        .close-modal:hover {
            opacity: 1;
        }

        .modal-body {
            padding: 1.5rem;
        }

        .form-group {
            margin-bottom: 1.2rem;
        }

        .form-label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 500;
            color: var(--secondary);
        }

        .form-input {
            width: 100%;
            padding: 0.8rem;
            border: 1px solid #ddd;
            border-radius: 6px;
            transition: all 0.3s;
        }

        .form-input:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 5px rgba(42,157,143,0.2);
        }

        .form-footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 0.9rem;
        }

        .remember-me {
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .forgot-password {
            color: var(--primary);
            text-decoration: none;
        }

        .social-login {
            margin-top: 1.5rem;
            text-align: center;
        }

        .social-login-title {
            display: flex;
            align-items: center;
            gap: 1rem;
            margin-bottom: 1rem;
            color: var(--gray);
            font-size: 0.9rem;
        }

        .social-login-title::before,
        .social-login-title::after {
            content: "";
            flex: 1;
            height: 1px;
            background: #ddd;
        }

        .social-login-buttons {
            display: flex;
            gap: 1rem;
        }

        .social-btn {
            flex: 1;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
            padding: 0.8rem;
            border-radius: 6px;
            background: white;
            border: 1px solid #ddd;
            color: var(--gray);
            cursor: pointer;
            transition: all 0.2s;
        }

        .social-btn:hover {
            background: var(--light-gray);
        }

        .modal-footer {
            padding: 1rem 1.5rem;
            background: var(--light-gray);
            text-align: center;
            font-size: 0.9rem;
        }

        .modal-footer a {
            color: var(--primary);
            text-decoration: none;
            font-weight: 500;
        }

        /* زر بيع المنتج العائم */
        .sell-button {
            position: fixed;
            bottom: 20px;
            left: 20px;
            background-color: var(--primary);
            color: white;
            border: none;
            border-radius: 50%;
            width: 60px;
            height: 60px;
            font-size: 24px;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
            cursor: pointer;
            z-index: 50;
            transition: all 0.3s;
        }

        .sell-button:hover {
            transform: scale(1.1);
            background-color: var(--primary-dark);
        }

        /* خيارات الفرز */
        .sorting-options {
            margin: 1rem 0;
            display: flex;
            justify-content: flex-end;
        }

        .sorting-options select {
            padding: 0.5rem;
            border: 1px solid #ddd;
            border-radius: 6px;
            font-size: 0.9rem;
        }

        /* تأثير التكبير على الصور */
        .product-image {
            position: relative;
            overflow: hidden;
        }

        .product-image:hover .zoom-overlay {
            opacity: 1;
        }

        .zoom-overlay {
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0,0,0,0.5);
            opacity: 0;
            transition: opacity 0.3s;
            cursor: zoom-in;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
        }

        /* قواعد تجاوبية */
        @media (max-width: 768px) {
            .header-content {
                flex-wrap: wrap;
                gap: 1rem;
            }
            
            .search-bar {
                order: 3;
                flex: 0 0 100%;
            }
            
            .user-nav {
                order: 2;
            }
            
            .membership-banner {
                flex-direction: column;
                padding: 1.5rem;
                gap: 1rem;
            }
            
            .banner-image {
                flex: 0 0 auto;
            }
            
            .advanced-filters {
                grid-template-columns: 1fr;
            }

            .products-grid {
                grid-template-columns: repeat(2, 1fr);
            }

            .reviews-grid {
                grid-template-columns: 1fr;
            }
        }

        @media (max-width: 480px) {
            .products-grid {
                grid-template-columns: 1fr;
            }

            .product-actions {
                opacity: 1 !important;
            }
        }

        /* الرسوم المتحركة */
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .animate-fadeIn {
            animation: fadeIn 0.3s ease-in-out;
        }
    </style>
</head>
<body>
    <!-- الهيدر المحسن -->
    <header class="header">
        <div class="header-content">
            <a href="#" class="logo">
                <i class="fas fa-tshirt"></i>
                أناقة التوفير
            </a>
            
            <div class="search-bar">
                <input type="text" class="search-input" placeholder="ما الذي تبحث عنه؟">
                <i class="fas fa-search search-icon"></i>
            </div>

            <nav class="user-nav">
                <button class="btn btn-outline" id="login-btn">
                    <i class="fas fa-user"></i>
                    تسجيل الدخول
                </button>
                <button class="btn btn-primary">
                    <i class="fas fa-plus-circle"></i>
                    بيع الآن
                </button>
                <div class="user-menu">
                    <div class="user-avatar">
                        <i class="fas fa-user"></i>
                    </div>
                    <div class="dropdown-menu" id="user-dropdown">
                        <a href="#profile" class="dropdown-item">
                            <i class="fas fa-user-circle"></i>
                            حسابي
                        </a>
                        <a href="#orders" class="dropdown-item">
                            <i class="fas fa-shopping-bag"></i>
                            طلباتي
                        </a>
                        <a href="#favorites" class="dropdown-item">
                            <i class="fas fa-heart"></i>
                            المفضلة
                        </a>
                        <a href="#messages" class="dropdown-item">
                            <i class="fas fa-comments"></i>
                            الرسائل
                        </a>
                        <a href="#settings" class="dropdown-item">
                            <i class="fas fa-cog"></i>
                            الإعدادات
                        </a>
                        <a href="#logout" class="dropdown-item">
                            <i class="fas fa-sign-out-alt"></i>
                            تسجيل الخروج
                        </a>
                    </div>
                </div>
            </nav>
        </div>
    </header>

    <main class="container">
        <!-- فلترات البحث -->
        <div class="filters-container">
            <div class="filters">
                <button class="filter-btn active">الكل</button>
                <button class="filter-btn">نسائية</button>
                <button class="filter-btn">رجالية</button>
                <button class="filter-btn">أطفال</button>
                <button class="filter-btn">أحذية</button>
                <button class="filter-btn">حقائب</button>
                <button class="filter-btn">إكسسوارات</button>
                <button class="filter-btn">ماركات عالمية</button>
                <button class="filter-btn">خصومات</button>
            </div>

            <div class="advanced-filters">
                <div class="filter-group">
                    <label for="category">التصنيف</label>
                    <select id="category" class="filter-select">
                        <option value="">جميع التصنيفات</option>
                        <option value="clothing">ملابس</option>
                        <option value="shoes">أحذية</option>
                        <option value="accessories">إكسسوارات</option>
                    </select>
                </div>
                <div class="filter-group">
                    <label for="size">المقاس</label>
                    <select id="size" class="filter-select">
                        <option value="">جميع المقاسات</option>
                        <option value="s">S</option>
                        <option value="m">M</option>
                        <option value="l">L</option>
                        <option value="xl">XL</option>
                    </select>
                </div>
                <div class="filter-group">
                    <label for="condition">الحالة</label>
                    <select id="condition" class="filter-select">
                        <option value="">جميع الحالات</option>
                        <option value="new">جديد</option>
                        <option value="like-new">كالجديد</option>
                        <option value="good">جيد</option>
                    </select>
                </div>
                <div class="filter-group">
                    <label for="price-range">نطاق السعر</label>
                    <div class="price-range">
                        <input type="range" id="price-range" min="0" max="1000" step="50" class="filter-input">
                        <span id="price-value">0 - 1000 ريال</span>
                    </div>
                </div>
            </div>
        </div>

        <!-- خيارات الفرز -->
        <div class="sorting-options">
            <select id="sortBy">
                <option value="newest">الأحدث</option>
                <option value="price_asc">السعر من الأقل للأعلى</option>
                <option value="price_desc">السعر من الأعلى للأقل</option>
                <option value="rating">الأعلى تقييماً</option>
            </select>
        </div>

        <!-- المنتجات المميزة -->
        <section class="featured-products">
            <h2 class="section-title">
                <i class="fas fa-star"></i>
                منتجات مميزة
            </h2>
            
            <div class="products-grid">
                <!-- منتج 1 -->
                <div class="product-card">
                    <div class="product-image">
                        <img src="https://via.placeholder.com/300x300" alt="قميص رجالي">
                        <div class="zoom-overlay">
                            <i class="fas fa-search-plus fa-2x"></i>
                        </div>
                        <button class="wishlist-btn">
                            <i class="far fa-heart"></i>
                        </button>
                        <span class="product-badge new">جديد</span>
                    </div>
                    <div class="product-details">
                        <h3 class="product-title">قميص جينز رجالي ماركة زارا</h3>
                        <div class="product-meta">
                            <div class="product-seller">
                                <div class="seller-avatar">س</div>
                                <span>سارة</span>
                            </div>
                            <div class="product-rating">
                                <span class="rating-stars">★★★★☆</span>
                                <span>(4.5)</span>
                            </div>
                        </div>
                        <div class="product-pricing">
                            <span class="product-price">85 ريال</span>
                            <span class="product-price original">120 ريال</span>
                        </div>
                        <div class="product-actions">
                            <button class="action-btn buy-btn">
                                <i class="fas fa-shopping-cart"></i>
                                شراء
                            </button>
                            <button class="action-btn chat-btn">
                                <i class="fas fa-comment"></i>
                                دردشة
                            </button>
                        </div>
                        <div class="security-badge">
                            <i class="fas fa-shield-alt"></i>
                            شراء آمن
                        </div>
                    </div>
                </div>

                <!-- منتج 2 -->
                <div class="product-card">
                    <div class="product-image">
                        <img src="https://via.placeholder.com/300x300" alt="حذاء رياضي">
                        <div class="zoom-overlay">
                            <i class="fas fa-search-plus fa-2x"></i>
                        </div>
                        <button class="wishlist-btn">
                            <i class="far fa-heart"></i>
                        </button>
                        <span class="product-badge discount">خصم 30%</span>
                    </div>
                    <div class="product-details">
                        <h3 class="product-title">حذاء رياضي ماركة أديداس</h3>
                        <div class="product-meta">
                            <div class="product-seller">
                                <div class="seller-avatar">أ</div>
                                <span>أحمد</span>
                            </div>
                            <div class="product-rating">
                                <span class="rating-stars">★★★★★</span>
                                <span>(5.0)</span>
                            </div>
                        </div>
                        <div class="product-pricing">
                            <span class="product-price">120 ريال</span>
                            <span class="product-price original">170 ريال</span>
                        </div>
                        <div class="product-actions">
                            <button class="action-btn buy-btn">
                                <i class="fas fa-shopping-cart"></i>
                                شراء
                            </button>
                            <button class="action-btn chat-btn">
                                <i class="fas fa-comment"></i>
                                دردشة
                            </button>
                        </div>
                        <div class="security-badge">
                            <i class="fas fa-shield-alt"></i>
                            شراء آمن
                        </div>
                    </div>
                </div>

                <!-- منتج 3 -->
                <div class="product-card">
                    <div class="product-image">
                        <img src="https://via.placeholder.com/300x300" alt="فستان نسائي">
                        <div class="zoom-overlay">
                            <i class="fas fa-search-plus fa-2x"></i>
                        </div>
                        <button class="wishlist-btn">
                            <i class="far fa-heart"></i>
                        </button>
                    </div>
                    <div class="product-details">
                        <h3 class="product-title">فستان صيفي طويل ماركة H&M</h3>
                        <div class="product-meta">
                            <div class="product-seller">
                                <div class="seller-avatar">ن</div>
                                <span>نورة</span>
                            </div>
                            <div class="product-rating">
                                <span class="rating-stars">★★★☆☆</span>
                                <span>(3.2)</span>
                            </div>
                        </div>
                        <div class="product-pricing">
                            <span class="product-price">65 ريال</span>
                        </div>
                        <div class="product-actions">
                            <button class="action-btn buy-btn">
                                <i class="fas fa-shopping-cart"></i>
                                شراء
                            </button>
                            <button class="action-btn chat-btn">
                                <i class="fas fa-comment"></i>
                                دردشة
                            </button>
                        </div>
                        <div class="security-badge">
                            <i class="fas fa-shield-alt"></i>
                            شراء آمن
                        </div>
                    </div>
                </div>

                <!-- منتج 4 -->
                <div class="product-card">
                    <div class="product-image">
                        <img src="https://via.placeholder.com/300x300" alt="جاكيت رياضي">
                        <div class="zoom-overlay">
                            <i class="fas fa-search-plus fa-2x"></i>
                        </div>
                        <button class="wishlist-btn">
                            <i class="far fa-heart"></i>
                        </button>
                    </div>
                    <div class="product-details">
                        <h3 class="product-title">جاكيت رياضي ماركة نايك</h3>
                        <div class="product-meta">
                            <div class="product-seller">
                                <div class="seller-avatar">م</div>
                                <span>محمد</span>
                            </div>
                            <div class="product-rating">
                                <span class="rating-stars">★★★★☆</span>
                                <span>(4.7)</span>
                            </div>
                        </div>
                        <div class="product-pricing">
                            <span class="product-price">200 ريال</span>
                        </div>
                        <div class="product-actions">
                            <button class="action-btn buy-btn">
                                <i class="fas fa-shopping-cart"></i>
                                شراء
                            </button>
                            <button class="action-btn chat-btn">
                                <i class="fas fa-comment"></i>
                                دردشة
                            </button>
                        </div>
                        <div class="security-badge">
                            <i class="fas fa-shield-alt"></i>
                            شراء آمن
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- التصنيفات المميزة -->
        <section class="featured-categories">
            <h2 class="section-title">
                <i class="fas fa-tags"></i>
                تصفح حسب التصنيف
            </h2>
            
            <div class="categories-grid">
                <div class="category-card">
                    <img src="https://via.placeholder.com/300x300" alt="ملابس نسائية" class="category-image">
                    <div class="category-overlay">
                        <h3 class="category-title">ملابس نسائية</h3>
                        <p class="category-count">1,245 منتج</p>
                    </div>
                </div>
                <div class="category-card">
                    <img src="https://via.placeholder.com/300x300" alt="ملابس رجالية" class="category-image">
                    <div class="category-overlay">
                        <h3 class="category-title">ملابس رجالية</h3>
                        <p class="category-count">856 منتج</p>
                    </div>
                </div>
                <div class="category-card">
                    <img src="https://via.placeholder.com/300x300" alt="أحذية" class="category-image">
                    <div class="category-overlay">
                        <h3 class="category-title">أحذية</h3>
                        <p class="category-count">432 منتج</p>
                    </div>
                </div>
                <div class="category-card">
                    <img src="https://via.placeholder.com/300x300" alt="إكسسوارات" class="category-image">
                    <div class="category-overlay">
                        <h3 class="category-title">إكسسوارات</h3>
                        <p class="category-count">321 منتج</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- نظام العضويات -->
        <div class="membership-banner">
            <div class="banner-content">
                <h2 class="banner-title">انضم إلى عضويتنا المميزة</h2>
                <p class="banner-text">احصل على خصومات حصرية، شحن مجاني، وإمكانية إرجاع المنتجات لمدة 30 يومًا مع عضوية أناقة التوفير المميزة.</p>
                
                <div class="membership-badges">
                    <div class="badge">
                        <i class="fas fa-tag"></i>
                        خصومات حصرية
                    </div>
                    <div class="badge">
                        <i class="fas fa-truck"></i>
                        شحن مجاني
                    </div>
                    <div class="badge">
                        <i class="fas fa-undo"></i>
                        إرجاع سهل
                    </div>
                </div>
                
                <button class="btn btn-accent">اشترك الآن</button>
            </div>
            
            <div class="banner-image">
                <img src="https://via.placeholder.com/200x200" alt="عضوية مميزة">
            </div>
        </div>

        <!-- الأكثر مبيعاً -->
        <section class="best-sellers">
            <h2 class="section-title">
                <i class="fas fa-fire"></i>
                الأكثر مبيعاً
            </h2>
            
            <div class="products-grid">
                <!-- منتج 5 -->
                <div class="product-card">
                    <div class="product-image">
                        <img src="https://via.placeholder.com/300x300" alt="حذاء بوما">
                        <div class="zoom-overlay">
                            <i class="fas fa-search-plus fa-2x"></i>
                        </div>
                        <button class="wishlist-btn">
                            <i class="far fa-heart"></i>
                        </button>
                    </div>
                    <div class="product-details">
                        <h3 class="product-title">حذاء رياضي ماركة بوما</h3>
                        <div class="product-meta">
                            <div class="product-seller">
                                <div class="seller-avatar">ل</div>
                                <span>لينا</span>
                            </div>
                            <div class="product-rating">
                                <span class="rating-stars">★★★★☆</span>
                                <span>(4.3)</span>
                            </div>
                        </div>
                        <div class="product-pricing">
                            <span class="product-price">150 ريال</span>
                        </div>
                        <div class="product-actions">
                            <button class="action-btn buy-btn">
                                <i class="fas fa-shopping-cart"></i>
                                شراء
                            </button>
                            <button class="action-btn chat-btn">
                                <i class="fas fa-comment"></i>
                                دردشة
                            </button>
                        </div>
                        <div class="security-badge">
                            <i class="fas fa-shield-alt"></i>
                            شراء آمن
                        </div>
                    </div>
                </div>

                <!-- منتج 6 -->
                <div class="product-card">
                    <div class="product-image">
                        <img src="https://via.placeholder.com/300x300" alt="بلوزة نسائية">
                        <div class="zoom-overlay">
                            <i class="fas fa-search-plus fa-2x"></i>
                        </div>
                        <button class="wishlist-btn">
                            <i class="far fa-heart"></i>
                        </button>
                        <span class="product-badge new">جديد</span>
                    </div>
                    <div class="product-details">
                        <h3 class="product-title">بلوزة نسائية ماركة مانجو</h3>
                        <div class="product-meta">
                            <div class="product-seller">
                                <div class="seller-avatar">ع</div>
                                <span>عمر</span>
                            </div>
                            <div class="product-rating">
                                <span class="rating-stars">★★★★★</span>
                                <span>(4.9)</span>
                            </div>
                        </div>
                        <div class="product-pricing">
                            <span class="product-price">95 ريال</span>
                            <span class="product-price original">130 ريال</span>
                        </div>
                        <div class="product-actions">
                            <button class="action-btn buy-btn">
                                <i class="fas fa-shopping-cart"></i>
                                شراء
                            </button>
                            <button class="action-btn chat-btn">
                                <i class="fas fa-comment"></i>
                                دردشة
                            </button>
                        </div>
                        <div class="security-badge">
                            <i class="fas fa-shield-alt"></i>
                            شراء آمن
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- التقييمات والمراجعات -->
        <section class="reviews-section">
            <h2 class="section-title">
                <i class="fas fa-comment-alt"></i>
                آراء العملاء
            </h2>
            
            <div class="reviews-grid">
                <div class="review-card">
                    <div class="review-header">
                        <div class="reviewer-avatar">ن</div>
                        <div class="reviewer-details">
                            <h3 class="reviewer-name">نورا</h3>
                            <p class="review-date">منذ 3 أيام</p>
                        </div>
                    </div>
                    <div class="review-rating">
                        ★★★★★
                    </div>
                    <p class="review-text">
                        المنتج كان أفضل مما توقعت! الحالة ممتازة والتوصيل كان سريعاً. شكراً لأناقة التوفير على هذه الخدمة الرائعة.
                    </p>
                    <div class="review-product">
                        <div class="review-product-image">
                            <img src="https://via.placeholder.com/50x50" alt="قميص جينز">
                        </div>
                        <div class="review-product-details">
                            <h4 class="review-product-title">قميص جينز رجالي</h4>
                            <p class="review-product-price">85 ريال</p>
                        </div>
                    </div>
                </div>
                
                <div class="review-card">
                    <div class="review-header">
                        <div class="reviewer-avatar">خ</div>
                        <div class="reviewer-details">
                            <h3 class="reviewer-name">خالد</h3>
                            <p class="review-date">منذ أسبوع</p>
                        </div>
                    </div>
                    <div class="review-rating">
                        ★★★★☆
                    </div>
                    <p class="review-text">
                        تجربة جيدة بشكل عام، المنتج كما هو موصوف ولكن الشحن استغرق وقتاً أطول قليلاً من المتوقع.
                    </p>
                    <div class="review-product">
                        <div class="review-product-image">
                            <img src="https://via.placeholder.com/50x50" alt="حذاء رياضي">
                        </div>
                        <div class="review-product-details">
                            <h4 class="review-product-title">حذاء رياضي أديداس</h4>
                            <p class="review-product-price">120 ريال</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <!-- الفوتر -->
    <footer class="footer">
        <div class="container">
            <div class="footer-content">
                <div class="footer-column">
                    <h3>أناقة التوفير</h3>
                    <p>منصة رائدة لبيع وشراء الملابس المستعملة بجودة عالية وأسعار مناسبة.</p>
                    <div class="social-icons">
                        <a href="#" class="social-icon">
                            <i class="fab fa-twitter"></i>
                        </a>
                        <a href="#" class="social-icon">
                            <i class="fab fa-instagram"></i>
                        </a>
                        <a href="#" class="social-icon">
                            <i class="fab fa-snapchat"></i>
                        </a>
                        <a href="#" class="social-icon">
                            <i class="fab fa-tiktok"></i>
                        </a>
                    </div>
                </div>
                
                <div class="footer-column">
                    <h3>روابط سريعة</h3>
                    <div class="footer-links">
                        <a href="#" class="footer-link">الصفحة الرئيسية</a>
                        <a href="#" class="footer-link">تصفح المنتجات</a>
                        <a href="#" class="footer-link">كيفية البيع</a>
                        <a href="#" class="footer-link">الأسئلة الشائعة</a>
                    </div>
                </div>
                
                <div class="footer-column">
                    <h3>خدمة العملاء</h3>
                    <div class="footer-links">
                        <a href="#" class="footer-link">تواصل معنا</a>
                        <a href="#" class="footer-link">سياسة الإرجاع</a>
                        <a href="#" class="footer-link">شروط الاستخدام</a>
                        <a href="#" class="footer-link">سياسة الخصوصية</a>
                    </div>
                </div>
                
                <div class="footer-column">
                    <h3>النشرة البريدية</h3>
                    <p>اشترك ليصلك كل جديد عن العروض والمنتجات.</p>
                    <div class="newsletter">
                        <form class="newsletter-form">
                            <input type="email" class="newsletter-input" placeholder="بريدك الإلكتروني">
                            <button type="submit" class="newsletter-btn">
                                <i class="fas fa-paper-plane"></i>
                            </button>
                        </form>
                    </div>
                </div>
            </div>
            
            <div class="footer-bottom">
                <p>&copy; 2025 أناقة التوفير. جميع الحقوق محفوظة.</p>
            </div>
        </div>
    </footer>

    <!-- زر بيع المنتج العائم -->
    <button class="sell-button">
        <i class="fas fa-plus"></i>
    </button>

    <!-- نافذة تسجيل الدخول -->
    <div class="modal" id="login-modal">
        <div class="modal-content">
            <div class="modal-header">
                <button class="close-modal" id="close-login">
                    <i class="fas fa-times"></i>
                </button>
                <h3 class="modal-title">مرحباً بعودتك!</h3>
                <p class="modal-subtitle">سجل الدخول للوصول إلى حسابك</p>
            </div>
            <div class="modal-body">
                <form id="login-form">
                    <div class="form-group">
                        <label for="email" class="form-label">البريد الإلكتروني</label>
                        <input type="email" id="email" class="form-input" required>
                    </div>
                    <div class="form-group">
                        <label for="password" class="form-label">كلمة المرور</label>
                        <input type="password" id="password" class="form-input" required>
                    </div>
                    <div class="form-footer">
                        <div class="remember-me">
                            <input type="checkbox" id="remember">
                            <label for="remember">تذكرني</label>
                        </div>
                        <a href="#" class="forgot-password">نسيت كلمة المرور؟</a>
                    </div>
                    <button type="submit" class="btn btn-primary" style="width: 100%; margin-top: 1rem;">تسجيل الدخول</button>
                </form>
                
                <div class="social-login">
                    <div class="social-login-title">
                        أو سجل الدخول باستخدام
                    </div>
                    <div class="social-login-buttons">
                        <button class="social-btn">
                            <i class="fab fa-google"></i>
                            جوجل
                        </button>
                        <button class="social-btn">
                            <i class="fab fa-apple"></i>
                            أبل
                        </button>
                    </div>
                </div>
            </div>
            <div class="modal-footer">
                <p>ليس لديك حساب؟ <a href="#" id="show-register">سجل الآن</a></p>
            </div>
        </div>
    </div>

    <script>
        // تفعيل القائمة المنسدلة للمستخدم
        const userAvatar = document.querySelector('.user-avatar');
        const userDropdown = document.getElementById('user-dropdown');
        
        userAvatar.addEventListener('click', function() {
            userDropdown.classList.toggle('active');
        });

        // إغلاق القائمة عند النقر خارجها
        document.addEventListener('click', function(e) {
            if (!e.target.closest('.user-menu')) {
                userDropdown.classList.remove('active');
            }
        });

        // تفعيل نافذة تسجيل الدخول
        const loginBtn = document.getElementById('login-btn');
        const loginModal = document.getElementById('login-modal');
        const closeLogin = document.getElementById('close-login');
        
        loginBtn.addEventListener('click', function() {
            loginModal.classList.add('active');
        });
        
        closeLogin.addEventListener('click', function() {
            loginModal.classList.remove('active');
        });

        // إغلاق النافذة عند النقر خارجها
        loginModal.addEventListener('click', function(e) {
            if (e.target === loginModal) {
                loginModal.classList.remove('active');
            }
        });

        // تفعيل زر المفضلة
        document.querySelectorAll('.wishlist-btn').forEach(btn => {
            btn.addEventListener('click', function() {
                const icon = this.querySelector('i');
                icon.classList.toggle('far');
                icon.classList.toggle('fas');
                icon.classList.toggle('active');
                
                if (icon.classList.contains('active')) {
                    this.classList.add('animate__animated', 'animate__pulse');
                    setTimeout(() => {
                        this.classList.remove('animate__animated', 'animate__pulse');
                    }, 1000);
                }
            });
        });

        // تفعيل خيارات الفرز
        document.getElementById('sortBy').addEventListener('change', async function() {
            // هنا يمكنك إضافة كود لفرز المنتجات حسب الخيار المحدد
            console.log('تم اختيار:', this.value);
            // يمكنك إضافة AJAX لتحميل المنتجات مرتبة أو فرزها على العميل
        });

        // تفعيل فلتر نطاق السعر
        const priceRange = document.getElementById('price-range');
        const priceValue = document.getElementById('price-value');
        
        priceRange.addEventListener('input', function() {
            priceValue.textContent = `0 - ${this.value} ريال`;
        });

        // تفعيل زر بيع المنتج العائم
        const sellButton = document.querySelector('.sell-button');
        sellButton.addEventListener('click', function() {
            alert('سيتم فتح نموذج إضافة منتج جديد');
            // يمكنك فتح نافذة منبثقة أو توجيه المستخدم إلى صفحة البيع
        });

        // نظام الأمان: منع حقن XSS
        function sanitizeHTML(text) {
            const div = document.createElement('div');
            div.textContent = text;
            return div.innerHTML;
        }

        // نظام التقييمات
        class RatingSystem {
            constructor(container) {
                this.stars = Array.from(container.querySelectorAll('.star'));
                this.init();
            }

            init() {
                this.stars.forEach((star, index) => {
                    star.addEventListener('click', () => this.setRating(index + 1));
                });
            }

            setRating(rating) {
                this.stars.forEach((star, idx) => {
                    star.classList.toggle('active', idx < rating);
                });
            }
        }

        // تهيئة النظام
        document.addEventListener('DOMContentLoaded', () => {
            document.querySelectorAll('.rating-container').forEach(container => {
                new RatingSystem(container);
            });
        });
    </script>
</body>
</html>
