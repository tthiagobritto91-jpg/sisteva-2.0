# sisteva-2.0
sistema de escritorio versão 2
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Thiago Britto Advogados Associados</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary: #1e3a5f;
            --secondary: #2d4a6f;
            --accent: #c5a572;
            --gold: #d4af37;
            --text-dark: #1a1a1a;
            --text-light: #ffffff;
            --bg-light: #f8f9fa;
        }

        body {
            font-family: 'Poppins', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
            line-height: 1.7;
            color: var(--text-dark);
            font-weight: 400;
        }

        /* Navigation */
        nav {
            background: linear-gradient(135deg, #1e3a5f 0%, #2d4a6f 100%);
            padding: 1.2rem 0;
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            box-shadow: 0 4px 20px rgba(0,0,0,0.15);
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            color: var(--text-light);
            font-size: 16px;
            font-weight: 700;
            text-decoration: none;
            display: flex;
            flex-direction: column;
            line-height: 1.2;
        }

        .logo-container {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .logo-display {
            width: 45px;
            height: 45px;
            background: rgba(255, 255, 255, 0.1);
            border: 2px solid rgba(255, 255, 255, 0.2);
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
        }

        .logo-display img {
            width: 100%;
            height: 100%;
            object-fit: contain;
        }

        .logo-subtitle {
            font-size: 10px;
            font-weight: 400;
            opacity: 0.9;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .nav-links {
            display: flex;
            gap: 30px;
            list-style: none;
        }

        .nav-links a {
            color: var(--text-light);
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s;
        }

        .nav-links a:hover {
            color: var(--accent);
        }

        .btn-area {
            background: linear-gradient(135deg, var(--accent) 0%, var(--gold) 100%);
            color: var(--text-dark);
            padding: 8px 20px;
            border-radius: 6px;
            text-decoration: none;
            font-weight: 600;
            font-size: 0.9rem;
            transition: all 0.3s;
            box-shadow: 0 4px 15px rgba(197, 165, 114, 0.3);
            letter-spacing: 0.3px;
        }

        .btn-area:hover {
            transform: translateY(-2px);
        }

        /* Menu Hamburguer */
        .menu-toggle {
            display: none;
            flex-direction: column;
            cursor: pointer;
            gap: 5px;
        }

        .menu-toggle span {
            width: 28px;
            height: 3px;
            background: var(--text-light);
            border-radius: 2px;
            transition: all 0.3s;
        }

        .menu-toggle.active span:nth-child(1) {
            transform: rotate(45deg) translate(8px, 8px);
        }

        .menu-toggle.active span:nth-child(2) {
            opacity: 0;
        }

        .menu-toggle.active span:nth-child(3) {
            transform: rotate(-45deg) translate(7px, -7px);
        }

        .nav-menu-wrapper {
            display: flex;
            align-items: center;
            gap: 30px;
        }

        @media (max-width: 968px) {
            .menu-toggle {
                display: flex;
            }

            .nav-menu-wrapper {
                position: fixed;
                top: 70px;
                right: -100%;
                width: 280px;
                height: calc(100vh - 70px);
                background: var(--primary);
                flex-direction: column;
                padding: 30px 20px;
                gap: 0;
                transition: right 0.4s;
                box-shadow: -5px 0 20px rgba(0,0,0,0.3);
            }

            .nav-menu-wrapper.active {
                right: 0;
            }

            .nav-links {
                flex-direction: column;
                width: 100%;
                gap: 0;
            }

            .nav-links li {
                width: 100%;
                border-bottom: 1px solid rgba(255,255,255,0.1);
            }

            .nav-links a {
                display: block;
                padding: 15px 0;
            }

            .btn-area {
                width: 100%;
                text-align: center;
                margin-top: 20px;
            }
        }

        /* Hero Section */
        .hero {
            background: linear-gradient(135deg, rgba(30, 58, 95, 0.95) 0%, rgba(45, 74, 111, 0.95) 100%), 
                        url('https://images.unsplash.com/photo-1589829545856-d10d557cf95f?w=1600&h=900&fit=crop') center/cover;
            color: var(--text-light);
            padding: 140px 20px 90px;
            text-align: center;
            margin-top: 60px;
            position: relative;
        }

        .hero h1 {
            font-size: 3rem;
            margin-bottom: 20px;
            font-weight: 700;
            text-align: center;
        }

        .hero p {
            font-size: 1.3rem;
            max-width: 800px;
            margin: 0 auto 30px;
            opacity: 0.95;
            text-align: center;
        }

        .stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 30px;
            max-width: 900px;
            margin: 50px auto 0;
        }

        .stat-card {
            background: rgba(255,255,255,0.15);
            backdrop-filter: blur(15px);
            padding: 30px;
            border-radius: 15px;
            border: 2px solid rgba(255,255,255,0.25);
            transition: all 0.3s;
        }

        .stat-card:hover {
            background: rgba(255,255,255,0.2);
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }

        .stat-number {
            font-size: 2.5rem;
            font-weight: 700;
            color: var(--accent);
            margin-bottom: 5px;
        }

        .stat-label {
            font-size: 1rem;
            opacity: 0.9;
        }

        /* Sections */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 60px 20px;
        }

        .section-title {
            text-align: center;
            font-size: 2.8rem;
            color: var(--primary);
            margin-bottom: 15px;
            font-weight: 700;
            letter-spacing: -0.5px;
            position: relative;
            display: inline-block;
            width: 100%;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 80px;
            height: 4px;
            background: linear-gradient(90deg, var(--accent) 0%, var(--gold) 100%);
            border-radius: 2px;
        }

        .section-subtitle {
            text-align: center;
            font-size: 1.2rem;
            color: #666;
            max-width: 700px;
            margin: 0 auto 50px;
        }

        /* About Section */
        .about-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 50px;
            align-items: center;
        }

        .about-text h3 {
            color: var(--secondary);
            font-size: 1.8rem;
            margin-bottom: 20px;
        }

        .about-text p {
            color: #555;
            margin-bottom: 15px;
            font-size: 1.05rem;
        }

        .about-image {
            background: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 100%);
            height: 450px;
            border-radius: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 100px;
            box-shadow: 0 15px 50px rgba(30, 58, 95, 0.3);
            position: relative;
            overflow: hidden;
            background-size: cover;
            background-position: center;
            --overlay-opacity: 0.5;
        }

        .about-image::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, rgba(30, 58, 95, 0.5) 0%, rgba(45, 74, 111, 0.5) 100%);
            pointer-events: none;
            opacity: 0;
            transition: all 0.3s;
            z-index: 1;
        }

        .about-image.has-image::after {
            opacity: var(--overlay-opacity, 0.5);
        }



        .about-image::before {
            content: '';
            position: absolute;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.1) 1px, transparent 1px);
            background-size: 20px 20px;
            animation: float 20s infinite linear;
        }

        @keyframes float {
            0% { transform: translate(0, 0); }
            100% { transform: translate(-50%, -50%); }
        }

        /* Areas Section */
        .areas-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 25px;
        }

        .area-card {
            background: linear-gradient(135deg, #ffffff 0%, #f8f9fa 100%);
            border: 1px solid #e8e8e8;
            border-radius: 15px;
            padding: 35px 25px;
            text-align: center;
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            cursor: pointer;
            position: relative;
            overflow: hidden;
        }

        .area-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 4px;
            background: linear-gradient(90deg, var(--accent) 0%, var(--gold) 100%);
            transform: scaleX(0);
            transition: transform 0.4s;
        }

        .area-card:hover::before {
            transform: scaleX(1);
        }

        .area-card:hover {
            border-color: var(--accent);
            box-shadow: 0 15px 40px rgba(197, 165, 114, 0.2);
            transform: translateY(-8px);
        }

        .area-icon {
            width: 60px;
            height: 3px;
            background: linear-gradient(90deg, var(--accent) 0%, var(--gold) 100%);
            margin: 0 auto 20px;
            transition: all 0.3s;
            display: block;
        }

        .area-card:hover .area-icon {
            width: 80px;
        }

        /* Variações de formato do ícone */
        .area-icon.circle {
            width: 50px;
            height: 50px;
            border-radius: 50%;
        }

        .area-icon.square {
            width: 50px;
            height: 50px;
            border-radius: 8px;
        }

        .area-icon.diamond {
            width: 40px;
            height: 40px;
            transform: rotate(45deg);
            margin: 10px auto 30px;
        }

        .area-card:hover .area-icon.diamond {
            transform: rotate(45deg) scale(1.2);
            width: 40px;
        }

        .area-icon.dot {
            width: 15px;
            height: 15px;
            border-radius: 50%;
        }

        .area-card:hover .area-icon.circle,
        .area-card:hover .area-icon.square,
        .area-card:hover .area-icon.dot {
            width: 50px;
            height: 50px;
        }

        .area-card:hover .area-icon.dot {
            width: 20px;
            height: 20px;
        }

        .area-card h3 {
            color: var(--primary);
            font-size: 1.3rem;
            margin-bottom: 10px;
        }

        .area-card p {
            color: #666;
            font-size: 0.95rem;
        }

        /* Botão de Editar Ícone */
        .edit-icon-btn {
            position: absolute;
            top: 10px;
            right: 10px;
            background: var(--accent);
            color: white;
            border: none;
            width: 30px;
            height: 30px;
            border-radius: 50%;
            cursor: pointer;
            font-size: 14px;
            display: flex;
            align-items: center;
            justify-content: center;
            opacity: 0;
            transition: opacity 0.3s;
        }

        .area-card:hover .edit-icon-btn {
            opacity: 1;
        }

        /* Painel de Customização */
        .customize-panel {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: white;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.3);
            z-index: 3000;
            min-width: 400px;
        }

        .customize-panel.active {
            display: block;
        }

        .customize-overlay {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            z-index: 2999;
        }

        .customize-overlay.active {
            display: block;
        }

        .customize-panel h3 {
            color: var(--primary);
            margin-bottom: 20px;
        }

        .customize-section {
            margin-bottom: 20px;
        }

        .customize-section label {
            display: block;
            margin-bottom: 10px;
            font-weight: 600;
            color: var(--text-dark);
        }

        .format-options {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 10px;
        }

        .format-option {
            padding: 10px;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            cursor: pointer;
            text-align: center;
            transition: all 0.3s;
        }

        .format-option:hover {
            border-color: var(--accent);
        }

        .format-option.selected {
            border-color: var(--accent);
            background: rgba(197, 165, 114, 0.1);
        }

        .color-options {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
        }

        .color-option {
            width: 40px;
            height: 40px;
            border-radius: 8px;
            cursor: pointer;
            border: 3px solid transparent;
            transition: all 0.3s;
        }

        .color-option:hover {
            transform: scale(1.1);
        }

        .color-option.selected {
            border-color: var(--text-dark);
        }

        .customize-buttons {
            display: flex;
            gap: 10px;
            margin-top: 20px;
        }

        .customize-buttons button {
            flex: 1;
            padding: 12px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s;
        }

        .btn-apply {
            background: var(--secondary);
            color: white;
        }

        .btn-apply:hover {
            background: var(--primary);
        }

        .btn-cancel {
            background: #e0e0e0;
            color: var(--text-dark);
        }

        .btn-cancel:hover {
            background: #ccc;
        }

        /* Services Section */
        .services {
            background: #f8f9fa;
        }

        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }

        .service-card {
            background: white;
            padding: 40px;
            border-radius: 15px;
            box-shadow: 0 8px 25px rgba(0,0,0,0.1);
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            border: 1px solid #f0f0f0;
        }

        .service-card:hover {
            transform: translateY(-5px);
        }

        .service-icon {
            width: 70px;
            height: 70px;
            background: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 100%);
            border-radius: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 32px;
            margin-bottom: 25px;
            box-shadow: 0 5px 15px rgba(30, 58, 95, 0.3);
        }

        .service-card h3 {
            color: var(--primary);
            margin-bottom: 15px;
            font-size: 1.4rem;
        }

        .service-card p {
            color: #666;
            margin-bottom: 20px;
        }

        .btn-service {
            background: linear-gradient(135deg, var(--secondary) 0%, var(--primary) 100%);
            color: white;
            padding: 12px 28px;
            border-radius: 8px;
            text-decoration: none;
            display: inline-block;
            transition: all 0.3s;
            font-weight: 600;
            box-shadow: 0 4px 15px rgba(30, 58, 95, 0.2);
        }

        .btn-service:hover {
            background: var(--primary);
        }

        /* CTA Section */
        .cta {
            background: linear-gradient(135deg, var(--secondary) 0%, var(--primary) 100%);
            color: white;
            text-align: center;
            padding: 60px 20px;
        }

        .cta h2 {
            font-size: 2.5rem;
            margin-bottom: 20px;
        }

        .btn-whatsapp {
            background: #25D366;
            color: white;
            padding: 15px 40px;
            border-radius: 50px;
            text-decoration: none;
            font-size: 1.2rem;
            font-weight: 600;
            display: inline-block;
            margin-top: 20px;
            transition: transform 0.3s;
        }

        .btn-whatsapp:hover {
            transform: scale(1.05);
        }

        /* Footer */
        footer {
            background: var(--primary);
            color: white;
            padding: 40px 20px 20px;
        }

        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 40px;
            margin-bottom: 30px;
        }

        .footer-section h3 {
            color: var(--accent);
            margin-bottom: 15px;
        }

        .footer-section p,
        .footer-section a {
            color: rgba(255,255,255,0.8);
            text-decoration: none;
            display: block;
            margin-bottom: 8px;
        }

        .footer-section a:hover {
            color: var(--accent);
        }

        .footer-bottom {
            text-align: center;
            padding-top: 20px;
            border-top: 1px solid rgba(255,255,255,0.1);
            color: rgba(255,255,255,0.7);
        }

        /* Modal Login */
        .modal {
            display: none;
            position: fixed;
            z-index: 2000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.7);
            backdrop-filter: blur(5px);
        }

        .modal.active {
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .modal-content {
            background: white;
            padding: 40px;
            border-radius: 15px;
            max-width: 400px;
            width: 90%;
            box-shadow: 0 10px 40px rgba(0,0,0,0.3);
        }

        .modal-content h2 {
            color: var(--primary);
            margin-bottom: 25px;
            text-align: center;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            color: var(--text-dark);
            font-weight: 500;
        }

        .form-group input {
            width: 100%;
            padding: 12px;
            border: 2px solid #e0e0e0;
            border-radius: 5px;
            font-size: 1rem;
            transition: border-color 0.3s;
        }

        .form-group input:focus {
            outline: none;
            border-color: var(--secondary);
        }

        .btn-login-submit {
            width: 100%;
            background: var(--secondary);
            color: white;
            padding: 12px;
            border: none;
            border-radius: 5px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: background 0.3s;
        }

        .btn-login-submit:hover {
            background: var(--primary);
        }

        .close-modal {
            float: right;
            font-size: 28px;
            font-weight: bold;
            color: #999;
            cursor: pointer;
            line-height: 20px;
        }

        .close-modal:hover {
            color: var(--primary);
        }

        /* Admin Dashboard */
        #admin-dashboard {
            display: none;
            padding: 80px 20px 40px;
            background: #f5f5f5;
            min-height: 100vh;
        }

        .dashboard-header {
            background: white;
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 30px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
        }

        .dashboard-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .dashboard-card {
            background: white;
            padding: 25px;
            border-radius: 10px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
            border-left: 4px solid var(--secondary);
        }

        .dashboard-card h3 {
            color: #666;
            font-size: 0.9rem;
            margin-bottom: 10px;
            text-transform: uppercase;
        }

        .dashboard-card .number {
            font-size: 2.5rem;
            font-weight: 700;
            color: var(--primary);
        }

        .dashboard-section {
            background: white;
            padding: 30px;
            border-radius: 10px;
            margin-bottom: 20px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
        }

        .dashboard-section h2 {
            color: var(--primary);
            margin-bottom: 20px;
            border-bottom: 2px solid #e0e0e0;
            padding-bottom: 10px;
        }

        .process-list {
            list-style: none;
        }

        .process-item {
            padding: 15px;
            border-bottom: 1px solid #e0e0e0;
            display: flex;
            justify-content: space-between;
            align-items: center;
            transition: background 0.2s;
        }

        .process-item:hover {
            background: #f8f9fa;
        }

        .process-item:last-child {
            border-bottom: none;
        }

        .badge {
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 600;
        }

        .badge.ativo {
            background: #d4edda;
            color: #155724;
        }

        .badge.pendente {
            background: #fff3cd;
            color: #856404;
        }

        .badge.concluido {
            background: #d1ecf1;
            color: #0c5460;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .hero h1 {
                font-size: 2rem;
            }

            .hero p {
                font-size: 1rem;
            }

            .nav-links {
                display: none;
            }

            .about-content {
                grid-template-columns: 1fr;
            }

            .section-title {
                font-size: 2rem;
            }
        }

        /* WhatsApp Float Button */
        .whatsapp-float {
            position: fixed;
            width: 60px;
            height: 60px;
            bottom: 30px;
            right: 30px;
            background-color: #25D366;
            color: white;
            border-radius: 50%;
            text-align: center;
            font-size: 30px;
            box-shadow: 2px 2px 10px rgba(0,0,0,0.3);
            z-index: 999;
            display: flex;
            align-items: center;
            justify-content: center;
            text-decoration: none;
            transition: transform 0.3s;
        }

        .whatsapp-float:hover {
            transform: scale(1.1);
        }

        /* Botões de Edição de Texto */
        .edit-text-btn {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 28px;
            height: 28px;
            background: rgba(255, 255, 255, 0.2);
            border: 1px solid rgba(255, 255, 255, 0.3);
            border-radius: 50%;
            color: white;
            cursor: pointer;
            font-size: 14px;
            margin-left: 10px;
            opacity: 0;
            transition: all 0.3s;
            vertical-align: middle;
        }

        .edit-text-btn:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: scale(1.1);
        }

        .editable-text:hover .edit-text-btn {
            opacity: 1;
        }

        .editable-text {
            display: inline-block;
            position: relative;
        }

        .hero h1.editable-text,
        .hero p.editable-text {
            display: block;
            text-align: center;
            width: 100%;
        }

        /* User Info Section */
        .user-info {
            display: none;
            align-items: center;
            gap: 15px;
            color: var(--text-light);
        }

        .user-info.active {
            display: flex;
        }

        .user-name {
            font-weight: 600;
            font-size: 0.95rem;
        }

        .btn-logout {
            background: rgba(255, 255, 255, 0.1);
            color: var(--text-light);
            padding: 6px 18px;
            border-radius: 5px;
            text-decoration: none;
            font-weight: 500;
            font-size: 0.9rem;
            transition: all 0.3s;
            border: 1px solid rgba(255, 255, 255, 0.2);
            cursor: pointer;
        }

        .btn-logout:hover {
            background: rgba(255, 255, 255, 0.2);
            border-color: rgba(255, 255, 255, 0.4);
        }

        /* Form Steps */
        .form-steps {
            display: flex;
            justify-content: space-between;
            margin-bottom: 30px;
            position: relative;
        }

        .form-steps::before {
            content: '';
            position: absolute;
            top: 20px;
            left: 0;
            right: 0;
            height: 2px;
            background: #e0e0e0;
            z-index: 0;
        }

        .step {
            flex: 1;
            text-align: center;
            position: relative;
            z-index: 1;
        }

        .step-number {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: #e0e0e0;
            color: #999;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
            margin-bottom: 8px;
            transition: all 0.3s;
        }

        .step.active .step-number {
            background: var(--secondary);
            color: white;
        }

        .step.completed .step-number {
            background: var(--accent);
            color: white;
        }

        .step-label {
            font-size: 0.85rem;
            color: #999;
            font-weight: 500;
        }

        .step.active .step-label {
            color: var(--primary);
            font-weight: 600;
        }

        .form-step-content {
            display: none;
        }

        .form-step-content.active {
            display: block;
        }

        .form-row {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 15px;
        }

        .form-buttons {
            display: flex;
            gap: 10px;
            margin-top: 20px;
            justify-content: space-between;
        }

        .btn-prev, .btn-next {
            flex: 1;
            padding: 12px 30px;
            border: none;
            border-radius: 5px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
        }

        .btn-prev {
            background: #e0e0e0;
            color: var(--text-dark);
        }

        .btn-prev:hover {
            background: #ccc;
        }

        .btn-next {
            background: var(--secondary);
            color: white;
        }

        .btn-next:hover {
            background: var(--primary);
        }

        /* User Level Badges */
        .level-badge {
            padding: 4px 10px;
            border-radius: 12px;
            font-size: 0.75rem;
            font-weight: 600;
            text-transform: uppercase;
        }

        .level-badge.nivel1 {
            background: #d1ecf1;
            color: #0c5460;
        }

        .level-badge.nivel2 {
            background: #fff3cd;
            color: #856404;
        }

        .level-badge.nivel3 {
            background: #d4edda;
            color: #155724;
        }

        /* Action Buttons */
        .action-buttons {
            display: flex;
            gap: 8px;
        }

        .btn-action {
            padding: 6px 12px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 0.85rem;
            font-weight: 600;
            transition: all 0.3s;
        }

        .btn-edit {
            background: #ffc107;
            color: #000;
        }

        .btn-edit:hover {
            background: #e0a800;
        }

        .btn-delete {
            background: #dc3545;
            color: white;
        }

        .btn-delete:hover {
            background: #c82333;
        }

        .hidden {
            display: none !important;
        }

        /* Search Section */
        .search-box {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
        }

        .search-input {
            flex: 1;
            padding: 12px 20px;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            font-size: 1rem;
            transition: border-color 0.3s;
        }

        .search-input:focus {
            outline: none;
            border-color: var(--secondary);
        }

        .btn-search {
            padding: 12px 30px;
            background: var(--secondary);
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s;
        }

        .btn-search:hover {
            background: var(--primary);
        }

        .search-results {
            margin-top: 20px;
        }

        .result-item {
            background: white;
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 15px;
            cursor: pointer;
            transition: all 0.3s;
            border: 2px solid #f0f0f0;
        }

        .result-item:hover {
            border-color: var(--accent);
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            transform: translateY(-2px);
        }

        .result-title {
            font-size: 1.1rem;
            font-weight: 600;
            color: var(--primary);
            margin-bottom: 8px;
        }

        .result-info {
            color: #666;
            font-size: 0.9rem;
        }

        /* Process Details Modal */
        .details-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.7);
            z-index: 3000;
            overflow-y: auto;
        }

        .details-modal.active {
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }

        .details-content {
            background: white;
            border-radius: 15px;
            max-width: 900px;
            width: 100%;
            max-height: 90vh;
            overflow-y: auto;
            position: relative;
        }

        .details-header {
            background: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 100%);
            color: white;
            padding: 25px 30px;
            border-radius: 15px 15px 0 0;
            position: sticky;
            top: 0;
            z-index: 10;
        }

        .details-header h2 {
            margin: 0 0 5px 0;
            font-size: 1.8rem;
        }

        .details-header p {
            margin: 0;
            opacity: 0.9;
        }

        .details-close {
            position: absolute;
            top: 20px;
            right: 20px;
            background: rgba(255,255,255,0.2);
            border: none;
            color: white;
            width: 35px;
            height: 35px;
            border-radius: 50%;
            cursor: pointer;
            font-size: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s;
        }

        .details-close:hover {
            background: rgba(255,255,255,0.3);
            transform: rotate(90deg);
        }

        .details-body {
            padding: 30px;
        }

        .details-section {
            margin-bottom: 30px;
        }

        .details-section h3 {
            color: var(--primary);
            font-size: 1.3rem;
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: 2px solid #e0e0e0;
        }

        .detail-row {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 15px;
            margin-bottom: 15px;
        }

        .detail-item {
            background: #f8f9fa;
            padding: 15px;
            border-radius: 8px;
        }

        .detail-label {
            font-weight: 600;
            color: #666;
            font-size: 0.85rem;
            text-transform: uppercase;
            margin-bottom: 5px;
        }

        .detail-value {
            color: var(--text-dark);
            font-size: 1rem;
        }

        .no-results {
            text-align: center;
            padding: 40px;
            color: #999;
            font-size: 1.1rem;
        }

        /* Financial Section */
        .financial-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .financial-card {
            background: linear-gradient(135deg, #ffffff 0%, #f8f9fa 100%);
            padding: 25px;
            border-radius: 15px;
            border-left: 4px solid;
            box-shadow: 0 4px 15px rgba(0,0,0,0.08);
            transition: all 0.3s;
        }

        .financial-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 25px rgba(0,0,0,0.12);
        }

        .financial-card.income {
            border-left-color: #27ae60;
        }

        .financial-card.expense {
            border-left-color: #e74c3c;
        }

        .financial-card.balance {
            border-left-color: #3498db;
        }

        .financial-card.pending {
            border-left-color: #f39c12;
        }

        .financial-label {
            font-size: 0.9rem;
            color: #666;
            margin-bottom: 10px;
            text-transform: uppercase;
            font-weight: 600;
        }

        .financial-value {
            font-size: 2rem;
            font-weight: 700;
            color: var(--text-dark);
        }

        .financial-value.positive {
            color: #27ae60;
        }

        .financial-value.negative {
            color: #e74c3c;
        }

        .financial-tabs {
            display: flex;
            gap: 10px;
            margin-bottom: 25px;
            border-bottom: 2px solid #e0e0e0;
        }

        .financial-tab {
            padding: 12px 24px;
            background: none;
            border: none;
            cursor: pointer;
            font-size: 1rem;
            font-weight: 600;
            color: #666;
            position: relative;
            transition: all 0.3s;
        }

        .financial-tab.active {
            color: var(--secondary);
        }

        .financial-tab.active::after {
            content: '';
            position: absolute;
            bottom: -2px;
            left: 0;
            width: 100%;
            height: 2px;
            background: var(--secondary);
        }

        .transaction-form {
            background: white;
            padding: 25px;
            border-radius: 15px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.08);
            margin-bottom: 30px;
        }

        .transaction-form h3 {
            margin-top: 0;
            color: var(--primary);
            margin-bottom: 20px;
        }

        .transaction-table {
            width: 100%;
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 4px 15px rgba(0,0,0,0.08);
        }

        .transaction-table table {
            width: 100%;
            border-collapse: collapse;
        }

        .transaction-table th {
            background: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 100%);
            color: white;
            padding: 15px;
            text-align: left;
            font-weight: 600;
        }

        .transaction-table td {
            padding: 15px;
            border-bottom: 1px solid #f0f0f0;
        }

        .transaction-table tr:hover {
            background: #f8f9fa;
        }

        .transaction-table tbody tr:last-child td {
            border-bottom: none;
        }

        .badge.paid {
            background: #27ae60;
        }

        .badge.pending {
            background: #f39c12;
        }

        .badge.overdue {
            background: #e74c3c;
        }

        .badge.canceled {
            background: #95a5a6;
        }

        .financial-filters {
            display: flex;
            gap: 15px;
            margin-bottom: 20px;
            flex-wrap: wrap;
        }

        .financial-filters select,
        .financial-filters input {
            padding: 10px 15px;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            font-size: 0.95rem;
        }

        .btn-action {
            padding: 8px 15px;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-size: 0.9rem;
            transition: all 0.3s;
        }

        .btn-action.view {
            background: #3498db;
            color: white;
        }

        .btn-action.view:hover {
            background: #2980b9;
        }

        .btn-action.delete {
            background: #e74c3c;
            color: white;
        }

        .btn-action.delete:hover {
            background: #c0392b;
        }

        .empty-state {
            text-align: center;
            padding: 60px 20px;
            color: #999;
        }

        .empty-state-icon {
            font-size: 4rem;
            margin-bottom: 15px;
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav>
        <div class="nav-container">
            <div class="logo-container">
                <div class="logo-display" id="logoPreview"></div>
                <a href="#" class="logo">
                    <span>THIAGO BRITTO</span>
                    <span class="logo-subtitle">Escritório de Advocacia</span>
                </a>
            </div>
            <div class="nav-menu-wrapper" id="navMenu">
                <ul class="nav-links" id="mainNavLinks">
                    <li><a href="#home" onclick="closeMenu()">Início</a></li>
                    <li><a href="#sobre" onclick="closeMenu()">Sobre</a></li>
                    <li><a href="#atuacao" onclick="closeMenu()">Áreas de Atuação</a></li>
                    <li><a href="#servicos" onclick="closeMenu()">Serviços</a></li>
                    <li><a href="#contato" onclick="closeMenu()">Contato</a></li>
                </ul>
                <a href="#" class="btn-area" id="loginBtn" onclick="openLoginModal(event); closeMenu();">Login</a>
                <div class="user-info" id="userInfo">
                    <span class="user-name" id="userName">Administrador</span>
                    <a href="#" class="btn-logout" onclick="logout(); return false;">Sair</a>
                </div>
            </div>
            <div class="menu-toggle" id="menuToggle" onclick="toggleMenu()">
                <span></span>
                <span></span>
                <span></span>
            </div>
        </div>
    </nav>

    <!-- Main Website -->
    <div id="main-site">
        <!-- Hero Section -->
        <section class="hero" id="home">
            <h1 class="editable-text" id="heroTitle">Thiago Britto Advogados Associados<button class="edit-text-btn" onclick="editText('heroTitle')">✎</button></h1>
            <p class="editable-text" id="heroSubtitle">Tradição que inspira confiança, inovação que garante resultados<button class="edit-text-btn" onclick="editText('heroSubtitle')">✎</button></p>
            
            <div class="stats">
                <div class="stat-card">
                    <div class="stat-number editable-text" id="statClients">20mil+<button class="edit-text-btn" onclick="editText('statClients')">✎</button></div>
                    <div class="stat-label">Clientes Ativos</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number editable-text" id="statProcesses">31mil+<button class="edit-text-btn" onclick="editText('statProcesses')">✎</button></div>
                    <div class="stat-label">Processos Gerenciados</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number editable-text" id="statYears">30+<button class="edit-text-btn" onclick="editText('statYears')">✎</button></div>
                    <div class="stat-label">Anos de Experiência</div>
                </div>
            </div>
        </section>

        <!-- About Section -->
        <section class="container" id="sobre">
            <h2 class="section-title">SOBRE NÓS</h2>
            <p class="section-subtitle">Tradição que inspira confiança, inovação que garante resultados</p>
            
            <div class="about-content">
                <div class="about-text">
                    <h3>Experiência e Comprometimento</h3>
                    <p>No Thiago Britto Advogados Associados, combinamos mais de 30 anos de experiência com uma visão moderna e tecnológica da advocacia.</p>
                    <p>Atendemos mais de 20 mil clientes ativos e administramos mais de 31 mil processos em diversas áreas do Direito, sempre com ética, seriedade e compromisso com resultados concretos.</p>
                    <p>Nossa missão é clara: fortalecer a sua causa com um atendimento ágil, humano e estratégico, acompanhando de perto cada etapa do seu processo.</p>
                </div>
                <div class="about-image" id="aboutImage">
                    <div style="font-size: 120px; text-shadow: 0 10px 30px rgba(0,0,0,0.3);"></div>
                </div>
            </div>
        </section>

        <!-- Areas de Atuação -->
        <section class="container" id="atuacao">
            <h2 class="section-title">ÁREAS DE ATUAÇÃO</h2>
            <p class="section-subtitle">Nossas Especialidades</p>
            
            <div class="areas-grid">
                <div class="area-card">
                    <button class="edit-icon-btn" onclick="openCustomizePanel(0)">✎</button>
                    <div class="area-icon" data-format="line" data-color="gold"></div>
                    <h3>EMPRESARIAL</h3>
                    <p>Advocacia especializada em Direito Empresarial</p>
                </div>
                <div class="area-card">
                    <button class="edit-icon-btn" onclick="openCustomizePanel(1)">✎</button>
                    <div class="area-icon" data-format="line" data-color="gold"></div>
                    <h3>IMOBILIÁRIO</h3>
                    <p>Advocacia especializada em Direito Imobiliário</p>
                </div>
                <div class="area-card">
                    <button class="edit-icon-btn" onclick="openCustomizePanel(2)">✎</button>
                    <div class="area-icon" data-format="line" data-color="gold"></div>
                    <h3>FAMÍLIA E SUCESSÕES</h3>
                    <p>Assessoria em Direito de Família e Planejamento Patrimonial</p>
                </div>
                <div class="area-card">
                    <button class="edit-icon-btn" onclick="openCustomizePanel(3)">✎</button>
                    <div class="area-icon" data-format="line" data-color="gold"></div>
                    <h3>SERVIDORES PÚBLICOS</h3>
                    <p>Especialistas nos Direitos dos Servidores Públicos</p>
                </div>
                <div class="area-card">
                    <button class="edit-icon-btn" onclick="openCustomizePanel(4)">✎</button>
                    <div class="area-icon" data-format="line" data-color="gold"></div>
                    <h3>BANCÁRIO</h3>
                    <p>Advocacia especializada em Direito Bancário</p>
                </div>
                <div class="area-card">
                    <button class="edit-icon-btn" onclick="openCustomizePanel(5)">✎</button>
                    <div class="area-icon" data-format="line" data-color="gold"></div>
                    <h3>PREVIDENCIÁRIO</h3>
                    <p>Advocacia especializada em Direito Previdenciário</p>
                </div>
                <div class="area-card">
                    <button class="edit-icon-btn" onclick="openCustomizePanel(6)">✎</button>
                    <div class="area-icon" data-format="line" data-color="gold"></div>
                    <h3>ADMINISTRATIVO</h3>
                    <p>Advocacia especializada em Direito Administrativo</p>
                </div>
                <div class="area-card">
                    <button class="edit-icon-btn" onclick="openCustomizePanel(7)">✎</button>
                    <div class="area-icon" data-format="line" data-color="gold"></div>
                    <h3>SAÚDE</h3>
                    <p>Advocacia especializada em Direito da Saúde</p>
                </div>
                <div class="area-card">
                    <button class="edit-icon-btn" onclick="openCustomizePanel(8)">✎</button>
                    <div class="area-icon" data-format="line" data-color="gold"></div>
                    <h3>CONSUMIDOR</h3>
                    <p>Advocacia especializada em Direito do Consumidor</p>
                </div>
                <div class="area-card">
                    <button class="edit-icon-btn" onclick="openCustomizePanel(9)">✎</button>
                    <div class="area-icon" data-format="line" data-color="gold"></div>
                    <h3>TRIBUTÁRIO</h3>
                    <p>Advocacia especializada em Direito Tributário</p>
                </div>
                <div class="area-card">
                    <button class="edit-icon-btn" onclick="openCustomizePanel(10)">✎</button>
                    <div class="area-icon" data-format="line" data-color="gold"></div>
                    <h3>ASSESSORIA JURÍDICA</h3>
                    <p>Serviços de Assessoria para empresas e pessoas físicas</p>
                </div>
            </div>
        </section>

        <!-- Services Section -->
        <section class="services" id="servicos">
            <div class="container">
                <h2 class="section-title">SERVIÇOS</h2>
                <p class="section-subtitle">Soluções jurídicas especializadas</p>
                
                <div class="services-grid">
                    <div class="service-card">
                        <div class="service-icon">
                        </div>
                        <h3>Consultoria Preventiva</h3>
                        <p>Assessoria jurídica contínua para empresas e profissionais que desejam prevenir litígios e manter conformidade legal.</p>
                        <a href="https://wa.me/5598992031747" class="btn-service">Quero saber mais</a>
                    </div>
                    <div class="service-card">
                        <div class="service-icon">
                        </div>
                        <h3>Contencioso Estratégico</h3>
                        <p>Representação em processos judiciais com foco em soluções eficazes e alinhadas aos objetivos dos nossos clientes.</p>
                        <a href="https://wa.me/5598992031747" class="btn-service">Quero saber mais</a>
                    </div>
                    <div class="service-card">
                        <div class="service-icon">
                        </div>
                        <h3>Planejamento Sucessório</h3>
                        <p>Estruturação patrimonial e planejamento sucessório para proteção e continuidade do seu patrimônio familiar.</p>
                        <a href="https://wa.me/5598992031747" class="btn-service">Quero saber mais</a>
                    </div>
                </div>
            </div>
        </section>

        <!-- CTA Section -->
        <section class="cta" id="contato">
            <h2>Estamos prontos para te atender agora!</h2>
            <p>Entre em contato com nossa equipe de especialistas</p>
            <a href="https://wa.me/5598992031747" class="btn-whatsapp">Fale pelo WhatsApp</a>
        </section>

        <!-- Footer -->
        <footer>
            <div class="footer-content">
                <div class="footer-section">
                    <h3>Thiago Britto Advogados</h3>
                    <p>Tradição, ética e resultados há mais de 30 anos.</p>
                </div>
                <div class="footer-section">
                    <h3>Contato</h3>
                    <p>WhatsApp: (98) 99203-1747</p>
                    <p>contato@thiagobritto.adv.br</p>
                    <p>São Luís - MA</p>
                </div>
                <div class="footer-section">
                    <h3>Links Úteis</h3>
                    <a href="#sobre">Sobre Nós</a>
                    <a href="#atuacao">Áreas de Atuação</a>
                    <a href="#servicos">Serviços</a>
                    <a href="#" onclick="openLoginModal(event)">Login</a>
                </div>
            </div>
            <div class="footer-bottom">
                <p>&copy; 2026 Thiago Britto Advogados Associados. Todos os direitos reservados.</p>
            </div>
        </footer>
    </div>

    <!-- Admin Dashboard -->
    <div id="admin-dashboard">
        <div class="container">
            <div class="dashboard-header">
                <h1 style="color: var(--primary); margin-bottom: 10px;">Painel Administrativo</h1>
                <p style="color: #666;">Bem-vindo(a), <span id="user-name">Administrador</span> (<span id="user-level-display">Nível 3</span>) | <a href="#" onclick="logout()" style="color: var(--secondary);">Sair</a></p>
            </div>

            <!-- Gestão de Usuários - Apenas Nível 3 -->
            <div id="user-management-section" class="dashboard-section">
                <h2>Gestão de Usuários</h2>
                
                <div style="margin-bottom: 30px;">
                    <h3 style="color: var(--primary); margin-bottom: 15px;">Usuários Cadastrados</h3>
                    <ul class="process-list" id="users-list">
                        <li class="process-item">
                            <div>
                                <strong>admin</strong>
                                <p style="color: #666; font-size: 0.9rem;">Administrador Principal</p>
                            </div>
                            <div style="display: flex; gap: 10px; align-items: center;">
                                <span class="level-badge nivel3">Nível 3</span>
                                <span style="color: #999; font-size: 0.85rem;">Usuário padrão</span>
                            </div>
                        </li>
                    </ul>
                </div>

                <h3 style="color: var(--primary); margin-bottom: 20px;">Cadastrar Novo Usuário</h3>
                <form id="add-user-form" style="display: grid; gap: 15px;">
                    <div class="form-row">
                        <div class="form-group">
                            <label>Nome Completo: *</label>
                            <input type="text" id="new-user-name" required>
                        </div>
                        <div class="form-group">
                            <label>Usuário (Login): *</label>
                            <input type="text" id="new-username" required>
                        </div>
                    </div>

                    <div class="form-row">
                        <div class="form-group">
                            <label>Senha: *</label>
                            <input type="password" id="new-password" required>
                        </div>
                        <div class="form-group">
                            <label>Nível de Acesso: *</label>
                            <select id="new-user-level" style="width: 100%; padding: 12px; border: 2px solid #e0e0e0; border-radius: 5px;" required>
                                <option value="">Selecione...</option>
                                <option value="1">Nível 1 - Apenas Visualização</option>
                                <option value="2">Nível 2 - Visualização e Cadastro</option>
                                <option value="3">Nível 3 - Acesso Total</option>
                            </select>
                        </div>
                    </div>

                    <div class="form-group">
                        <label>Cargo/Função:</label>
                        <input type="text" id="new-user-role" placeholder="Ex: Advogado, Secretário, Assistente">
                    </div>

                    <div style="background: #f8f9fa; padding: 15px; border-radius: 8px; margin: 10px 0;">
                        <strong style="color: var(--primary);">Permissões por Nível:</strong>
                        <ul style="margin: 10px 0 0 20px; color: #666;">
                            <li><strong>Nível 1:</strong> Visualizar clientes e processos</li>
                            <li><strong>Nível 2:</strong> Visualizar e cadastrar clientes e processos</li>
                            <li><strong>Nível 3:</strong> Visualizar, cadastrar, editar e excluir</li>
                        </ul>
                    </div>

                    <button type="submit" class="btn-login-submit">Cadastrar Usuário</button>
                </form>
            </div>

            <div class="dashboard-grid">
                <div class="dashboard-card">
                    <h3>Clientes Ativos</h3>
                    <div class="number" id="total-clients">20.547</div>
                </div>
                <div class="dashboard-card">
                    <h3>Processos Gerenciados</h3>
                    <div class="number" id="total-processes">31.248</div>
                </div>
                <div class="dashboard-card">
                    <h3>Processos Ativos</h3>
                    <div class="number" id="active-processes">8.421</div>
                </div>
                <div class="dashboard-card">
                    <h3>Taxa de Sucesso</h3>
                    <div class="number">94%</div>
                </div>
            </div>

            <!-- Busca de Processos -->
            <div class="dashboard-section">
                <h2>Buscar Processos</h2>
                <div class="search-box">
                    <input type="text" id="search-input" class="search-input" placeholder="Digite número do processo, nome do cliente ou tipo de ação...">
                    <button class="btn-search" onclick="searchProcesses()">Buscar</button>
                </div>
                <div id="search-results" class="search-results"></div>
            </div>

            <!-- Gestão Financeira (Apenas Nível 3) -->
            <div id="financial-section" class="dashboard-section" style="display: none;">
                <h2>Gestão Financeira</h2>
                
                <!-- Financial Summary Cards -->
                <div class="financial-grid">
                    <div class="financial-card income">
                        <div class="financial-label">Total Receitas</div>
                        <div class="financial-value positive" id="total-income">R$ 0,00</div>
                    </div>
                    <div class="financial-card expense">
                        <div class="financial-label">Total Despesas</div>
                        <div class="financial-value negative" id="total-expenses">R$ 0,00</div>
                    </div>
                    <div class="financial-card balance">
                        <div class="financial-label">Saldo</div>
                        <div class="financial-value" id="balance">R$ 0,00</div>
                    </div>
                    <div class="financial-card pending">
                        <div class="financial-label">Honorários Pendentes</div>
                        <div class="financial-value" id="pending-fees">R$ 0,00</div>
                    </div>
                </div>

                <!-- Tabs -->
                <div class="financial-tabs">
                    <button class="financial-tab active" onclick="showFinancialTab('transactions')">Transações</button>
                    <button class="financial-tab" onclick="showFinancialTab('add')">Adicionar Movimentação</button>
                    <button class="financial-tab" onclick="showFinancialTab('reports')">Relatórios</button>
                </div>

                <!-- Tab: Transações -->
                <div id="tab-transactions" class="financial-tab-content">
                    <div class="financial-filters">
                        <select id="filter-type" onchange="filterTransactions()">
                            <option value="all">Todos os Tipos</option>
                            <option value="income">Receitas</option>
                            <option value="expense">Despesas</option>
                        </select>
                        <select id="filter-status" onchange="filterTransactions()">
                            <option value="all">Todos os Status</option>
                            <option value="paid">Pagos</option>
                            <option value="pending">Pendentes</option>
                            <option value="overdue">Atrasados</option>
                        </select>
                        <input type="month" id="filter-month" onchange="filterTransactions()" value="">
                        <button class="btn-primary" onclick="clearFilters()">Limpar Filtros</button>
                    </div>

                    <div class="transaction-table" id="transactions-container">
                        <!-- Transactions will be loaded here -->
                    </div>
                </div>

                <!-- Tab: Adicionar Movimentação -->
                <div id="tab-add" class="financial-tab-content" style="display: none;">
                    <div class="transaction-form">
                        <h3>Nova Movimentação Financeira</h3>
                        <form id="add-transaction-form">
                            <div class="form-row">
                                <div class="form-group">
                                    <label>Tipo de Movimentação *</label>
                                    <select id="transaction-type" required onchange="updateFormByType()">
                                        <option value="">Selecione...</option>
                                        <option value="income-honorario">Receita - Honorários</option>
                                        <option value="income-consulta">Receita - Consulta</option>
                                        <option value="income-outro">Receita - Outro</option>
                                        <option value="expense-aluguel">Despesa - Aluguel</option>
                                        <option value="expense-salario">Despesa - Salário</option>
                                        <option value="expense-fornecedor">Despesa - Fornecedor</option>
                                        <option value="expense-outro">Despesa - Outro</option>
                                    </select>
                                </div>
                                <div class="form-group">
                                    <label>Valor *</label>
                                    <input type="text" id="transaction-value" placeholder="R$ 0,00" required oninput="formatCurrency(this)">
                                </div>
                            </div>

                            <div class="form-row">
                                <div class="form-group">
                                    <label>Descrição *</label>
                                    <input type="text" id="transaction-description" placeholder="Descrição da movimentação" required>
                                </div>
                                <div class="form-group">
                                    <label>Data *</label>
                                    <input type="date" id="transaction-date" required>
                                </div>
                            </div>

                            <div class="form-row" id="process-field" style="display: none;">
                                <div class="form-group">
                                    <label>Processo Relacionado</label>
                                    <input type="text" id="transaction-process" placeholder="Número do processo">
                                </div>
                                <div class="form-group">
                                    <label>Cliente</label>
                                    <input type="text" id="transaction-client" placeholder="Nome do cliente">
                                </div>
                            </div>

                            <div class="form-row">
                                <div class="form-group">
                                    <label>Forma de Pagamento *</label>
                                    <select id="transaction-payment-method" required>
                                        <option value="">Selecione...</option>
                                        <option value="dinheiro">Dinheiro</option>
                                        <option value="pix">PIX</option>
                                        <option value="cartao">Cartão</option>
                                        <option value="transferencia">Transferência</option>
                                        <option value="boleto">Boleto</option>
                                        <option value="cheque">Cheque</option>
                                    </select>
                                </div>
                                <div class="form-group">
                                    <label>Status *</label>
                                    <select id="transaction-status" required>
                                        <option value="paid">Pago</option>
                                        <option value="pending">Pendente</option>
                                        <option value="overdue">Atrasado</option>
                                    </select>
                                </div>
                            </div>

                            <div class="form-row">
                                <div class="form-group">
                                    <label>Categoria</label>
                                    <input type="text" id="transaction-category" placeholder="Ex: Escritório, Marketing, etc.">
                                </div>
                                <div class="form-group">
                                    <label>Parcelas</label>
                                    <input type="number" id="transaction-installments" min="1" max="120" value="1">
                                </div>
                            </div>

                            <div class="form-group">
                                <label>Observações</label>
                                <textarea id="transaction-notes" rows="3" placeholder="Observações adicionais..."></textarea>
                            </div>

                            <button type="submit" class="btn-primary" style="width: 100%; padding: 15px;">Salvar Movimentação</button>
                        </form>
                    </div>
                </div>

                <!-- Tab: Relatórios -->
                <div id="tab-reports" class="financial-tab-content" style="display: none;">
                    <div class="financial-grid">
                        <div class="financial-card">
                            <div class="financial-label">Receitas Mês Atual</div>
                            <div class="financial-value positive" id="month-income">R$ 0,00</div>
                        </div>
                        <div class="financial-card">
                            <div class="financial-label">Despesas Mês Atual</div>
                            <div class="financial-value negative" id="month-expenses">R$ 0,00</div>
                        </div>
                        <div class="financial-card">
                            <div class="financial-label">Resultado Mês</div>
                            <div class="financial-value" id="month-balance">R$ 0,00</div>
                        </div>
                        <div class="financial-card">
                            <div class="financial-label">Ticket Médio</div>
                            <div class="financial-value" id="avg-ticket">R$ 0,00</div>
                        </div>
                    </div>

                    <div class="transaction-form">
                        <h3>Resumo por Categoria</h3>
                        <div id="category-report"></div>
                    </div>

                    <div class="transaction-form">
                        <h3>Maiores Transações do Mês</h3>
                        <div id="top-transactions"></div>
                    </div>
                </div>
            </div>

            <div class="dashboard-section">
                <h2>Processos Recentes</h2>
                <ul class="process-list" id="process-list">
                    <li class="process-item">
                        <div>
                            <strong>Silva vs. Empresa X</strong>
                            <p style="color: #666; font-size: 0.9rem;">Processo: 2024001 | Cliente: João Silva</p>
                        </div>
                        <span class="badge ativo">ATIVO</span>
                    </li>
                    <li class="process-item">
                        <div>
                            <strong>Ação Previdenciária</strong>
                            <p style="color: #666; font-size: 0.9rem;">Processo: 2024002 | Cliente: Maria Santos</p>
                        </div>
                        <span class="badge pendente">PENDENTE</span>
                    </li>
                    <li class="process-item">
                        <div>
                            <strong>Inventário e Partilha</strong>
                            <p style="color: #666; font-size: 0.9rem;">Processo: 2024003 | Cliente: Carlos Oliveira</p>
                        </div>
                        <span class="badge concluido">CONCLUÍDO</span>
                    </li>
                    <li class="process-item">
                        <div>
                            <strong>Ação Trabalhista</strong>
                            <p style="color: #666; font-size: 0.9rem;">Processo: 2024004 | Cliente: Ana Costa</p>
                        </div>
                        <span class="badge ativo">ATIVO</span>
                    </li>
                    <li class="process-item">
                        <div>
                            <strong>Direito do Consumidor</strong>
                            <p style="color: #666; font-size: 0.9rem;">Processo: 2024005 | Cliente: Pedro Alves</p>
                        </div>
                        <span class="badge pendente">PENDENTE</span>
                    </li>
                </ul>
            </div>

            <div class="dashboard-section" id="add-process-section">
                <h2>Adicionar Novo Processo</h2>
                
                <!-- Indicador de Etapas -->
                <div class="form-steps">
                    <div class="step active" id="step1">
                        <div class="step-number">1</div>
                        <div class="step-label">Dados do Cliente</div>
                    </div>
                    <div class="step" id="step2">
                        <div class="step-number">2</div>
                        <div class="step-label">Informações do Processo</div>
                    </div>
                </div>

                <form id="add-process-form">
                    <!-- Etapa 1: Dados do Cliente -->
                    <div class="form-step-content active" id="step1-content">
                        <h3 style="color: var(--primary); margin-bottom: 20px;">Dados Pessoais do Cliente</h3>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label>Nome Completo: *</label>
                                <input type="text" id="client-name" required>
                            </div>
                            <div class="form-group">
                                <label>CPF/CNPJ: *</label>
                                <input type="text" id="client-document" required>
                            </div>
                        </div>

                        <div class="form-row">
                            <div class="form-group">
                                <label>RG:</label>
                                <input type="text" id="client-rg">
                            </div>
                            <div class="form-group">
                                <label>Data de Nascimento:</label>
                                <input type="date" id="client-birthdate">
                            </div>
                        </div>

                        <div class="form-row">
                            <div class="form-group">
                                <label>Telefone: *</label>
                                <input type="tel" id="client-phone" required>
                            </div>
                            <div class="form-group">
                                <label>E-mail:</label>
                                <input type="email" id="client-email">
                            </div>
                        </div>

                        <div class="form-group">
                            <label>Endereço Completo:</label>
                            <input type="text" id="client-address" placeholder="Rua, Número, Bairro, Cidade - Estado">
                        </div>

                        <div class="form-row">
                            <div class="form-group">
                                <label>CEP:</label>
                                <input type="text" id="client-cep">
                            </div>
                            <div class="form-group">
                                <label>Profissão:</label>
                                <input type="text" id="client-profession">
                            </div>
                        </div>

                        <div class="form-group">
                            <label>Observações:</label>
                            <textarea id="client-notes" rows="3" style="width: 100%; padding: 12px; border: 2px solid #e0e0e0; border-radius: 5px; font-family: inherit; resize: vertical;"></textarea>
                        </div>

                        <div class="form-buttons">
                            <div></div>
                            <button type="button" class="btn-next" onclick="nextStep()">Próximo</button>
                        </div>
                    </div>

                    <!-- Etapa 2: Informações do Processo -->
                    <div class="form-step-content" id="step2-content">
                        <h3 style="color: var(--primary); margin-bottom: 20px;">Informações do Processo</h3>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label>Número do Processo: *</label>
                                <input type="text" id="process-number" required>
                            </div>
                            <div class="form-group">
                                <label>Tipo de Ação: *</label>
                                <select id="process-type" style="width: 100%; padding: 12px; border: 2px solid #e0e0e0; border-radius: 5px;" required>
                                    <option value="">Selecione...</option>
                                    <option value="Empresarial">Empresarial</option>
                                    <option value="Imobiliário">Imobiliário</option>
                                    <option value="Família e Sucessões">Família e Sucessões</option>
                                    <option value="Servidores Públicos">Servidores Públicos</option>
                                    <option value="Bancário">Bancário</option>
                                    <option value="Previdenciário">Previdenciário</option>
                                    <option value="Administrativo">Administrativo</option>
                                    <option value="Saúde">Saúde</option>
                                    <option value="Consumidor">Consumidor</option>
                                    <option value="Tributário">Tributário</option>
                                    <option value="Outros">Outros</option>
                                </select>
                            </div>
                        </div>

                        <div class="form-row">
                            <div class="form-group">
                                <label>Vara/Comarca:</label>
                                <input type="text" id="process-court">
                            </div>
                            <div class="form-group">
                                <label>Data de Distribuição:</label>
                                <input type="date" id="process-date">
                            </div>
                        </div>

                        <div class="form-row">
                            <div class="form-group">
                                <label>Status: *</label>
                                <select id="process-status" style="width: 100%; padding: 12px; border: 2px solid #e0e0e0; border-radius: 5px;" required>
                                    <option value="ativo">Ativo</option>
                                    <option value="pendente">Pendente</option>
                                    <option value="concluido">Concluído</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label>Valor da Causa:</label>
                                <input type="text" id="process-value" placeholder="R$ 0,00">
                            </div>
                        </div>

                        <div class="form-group">
                            <label>Descrição do Processo: *</label>
                            <textarea id="process-description" rows="4" style="width: 100%; padding: 12px; border: 2px solid #e0e0e0; border-radius: 5px; font-family: inherit; resize: vertical;" required></textarea>
                        </div>

                        <div class="form-group">
                            <label>Parte Contrária:</label>
                            <input type="text" id="process-opponent">
                            </div>

                        <div class="form-group">
                            <label>Observações Adicionais:</label>
                            <textarea id="process-notes" rows="3" style="width: 100%; padding: 12px; border: 2px solid #e0e0e0; border-radius: 5px; font-family: inherit; resize: vertical;"></textarea>
                        </div>

                        <div class="form-buttons">
                            <button type="button" class="btn-prev" onclick="prevStep()">Anterior</button>
                            <button type="submit" class="btn-next">Finalizar e Adicionar</button>
                        </div>
                    </div>
                </form>
            </div>
        </div>
    </div>

    <!-- Customize Panel -->
    <div class="customize-overlay" id="customizeOverlay" onclick="closeCustomizePanel()"></div>
    <div class="customize-panel" id="customizePanel">
        <h3>Personalizar Ícone</h3>
        
        <div class="customize-section">
            <label>Formato:</label>
            <div class="format-options">
                <div class="format-option selected" data-format="line" onclick="selectFormat('line')">
                    <div style="width: 40px; height: 3px; background: #ccc; margin: 10px auto;"></div>
                    <small>Linha</small>
                </div>
                <div class="format-option" data-format="circle" onclick="selectFormat('circle')">
                    <div style="width: 30px; height: 30px; background: #ccc; border-radius: 50%; margin: 5px auto;"></div>
                    <small>Círculo</small>
                </div>
                <div class="format-option" data-format="square" onclick="selectFormat('square')">
                    <div style="width: 30px; height: 30px; background: #ccc; border-radius: 5px; margin: 5px auto;"></div>
                    <small>Quadrado</small>
                </div>
                <div class="format-option" data-format="diamond" onclick="selectFormat('diamond')">
                    <div style="width: 25px; height: 25px; background: #ccc; transform: rotate(45deg); margin: 10px auto;"></div>
                    <small>Losango</small>
                </div>
                <div class="format-option" data-format="dot" onclick="selectFormat('dot')">
                    <div style="width: 15px; height: 15px; background: #ccc; border-radius: 50%; margin: 12px auto;"></div>
                    <small>Ponto</small>
                </div>
                <div class="format-option" data-format="none" onclick="selectFormat('none')">
                    <div style="height: 30px; margin: 5px auto; display: flex; align-items: center; justify-content: center;">✕</div>
                    <small>Nenhum</small>
                </div>
            </div>
        </div>

        <div class="customize-section">
            <label>Cor:</label>
            <div class="color-options">
                <div class="color-option selected" data-color="gold" onclick="selectColor('gold')" style="background: linear-gradient(135deg, #c5a572 0%, #d4af37 100%);"></div>
                <div class="color-option" data-color="blue" onclick="selectColor('blue')" style="background: linear-gradient(135deg, #1e3a5f 0%, #2d4a6f 100%);"></div>
                <div class="color-option" data-color="red" onclick="selectColor('red')" style="background: linear-gradient(135deg, #dc3545 0%, #c82333 100%);"></div>
                <div class="color-option" data-color="green" onclick="selectColor('green')" style="background: linear-gradient(135deg, #28a745 0%, #218838 100%);"></div>
                <div class="color-option" data-color="purple" onclick="selectColor('purple')" style="background: linear-gradient(135deg, #6f42c1 0%, #5a32a3 100%);"></div>
                <div class="color-option" data-color="orange" onclick="selectColor('orange')" style="background: linear-gradient(135deg, #fd7e14 0%, #e8590c 100%);"></div>
                <div class="color-option" data-color="teal" onclick="selectColor('teal')" style="background: linear-gradient(135deg, #20c997 0%, #1aa179 100%);"></div>
                <div class="color-option" data-color="pink" onclick="selectColor('pink')" style="background: linear-gradient(135deg, #e83e8c 0%, #d63384 100%);"></div>
            </div>
        </div>

        <div class="customize-buttons">
            <button class="btn-cancel" onclick="closeCustomizePanel()">Cancelar</button>
            <button class="btn-apply" onclick="applyCustomization()">Aplicar</button>
        </div>
    </div>

    <!-- Process Details Modal -->
    <div id="process-details-modal" class="details-modal">
        <div class="details-content">
            <div class="details-header">
                <button class="details-close" onclick="closeProcessDetails()">×</button>
                <h2 id="detail-process-title">Detalhes do Processo</h2>
                <p id="detail-process-number"></p>
            </div>
            <div class="details-body">
                <div class="details-section">
                    <h3>Informações do Processo</h3>
                    <div class="detail-row">
                        <div class="detail-item">
                            <div class="detail-label">Número do Processo</div>
                            <div class="detail-value" id="detail-proc-number">-</div>
                        </div>
                        <div class="detail-item">
                            <div class="detail-label">Tipo de Ação</div>
                            <div class="detail-value" id="detail-proc-type">-</div>
                        </div>
                        <div class="detail-item">
                            <div class="detail-label">Status</div>
                            <div class="detail-value" id="detail-proc-status">-</div>
                        </div>
                    </div>
                    <div class="detail-row">
                        <div class="detail-item">
                            <div class="detail-label">Vara/Comarca</div>
                            <div class="detail-value" id="detail-proc-court">-</div>
                        </div>
                        <div class="detail-item">
                            <div class="detail-label">Data de Distribuição</div>
                            <div class="detail-value" id="detail-proc-date">-</div>
                        </div>
                        <div class="detail-item">
                            <div class="detail-label">Valor da Causa</div>
                            <div class="detail-value" id="detail-proc-value">-</div>
                        </div>
                    </div>
                    <div class="detail-row">
                        <div class="detail-item" style="grid-column: 1 / -1;">
                            <div class="detail-label">Descrição</div>
                            <div class="detail-value" id="detail-proc-description">-</div>
                        </div>
                    </div>
                    <div class="detail-row">
                        <div class="detail-item">
                            <div class="detail-label">Parte Contrária</div>
                            <div class="detail-value" id="detail-proc-opponent">-</div>
                        </div>
                        <div class="detail-item" style="grid-column: 2 / -1;">
                            <div class="detail-label">Observações</div>
                            <div class="detail-value" id="detail-proc-notes">-</div>
                        </div>
                    </div>
                </div>

                <div class="details-section">
                    <h3>Dados do Cliente</h3>
                    <div class="detail-row">
                        <div class="detail-item">
                            <div class="detail-label">Nome Completo</div>
                            <div class="detail-value" id="detail-client-name">-</div>
                        </div>
                        <div class="detail-item">
                            <div class="detail-label">CPF/CNPJ</div>
                            <div class="detail-value" id="detail-client-document">-</div>
                        </div>
                        <div class="detail-item">
                            <div class="detail-label">RG</div>
                            <div class="detail-value" id="detail-client-rg">-</div>
                        </div>
                    </div>
                    <div class="detail-row">
                        <div class="detail-item">
                            <div class="detail-label">Data de Nascimento</div>
                            <div class="detail-value" id="detail-client-birthdate">-</div>
                        </div>
                        <div class="detail-item">
                            <div class="detail-label">Telefone</div>
                            <div class="detail-value" id="detail-client-phone">-</div>
                        </div>
                        <div class="detail-item">
                            <div class="detail-label">E-mail</div>
                            <div class="detail-value" id="detail-client-email">-</div>
                        </div>
                    </div>
                    <div class="detail-row">
                        <div class="detail-item" style="grid-column: 1 / -1;">
                            <div class="detail-label">Endereço</div>
                            <div class="detail-value" id="detail-client-address">-</div>
                        </div>
                    </div>
                    <div class="detail-row">
                        <div class="detail-item">
                            <div class="detail-label">CEP</div>
                            <div class="detail-value" id="detail-client-cep">-</div>
                        </div>
                        <div class="detail-item">
                            <div class="detail-label">Profissão</div>
                            <div class="detail-value" id="detail-client-profession">-</div>
                        </div>
                        <div class="detail-item">
                            <div class="detail-label">Observações</div>
                            <div class="detail-value" id="detail-client-notes">-</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Login Modal -->
    <div id="login-modal" class="modal">
        <div class="modal-content">
            <span class="close-modal" onclick="closeLoginModal()">&times;</span>
            <h2>Login</h2>
            <form id="login-form">
                <div class="form-group">
                    <label>Usuário:</label>
                    <input type="text" id="username" required>
                </div>
                <div class="form-group">
                    <label>Senha:</label>
                    <input type="password" id="password" required>
                </div>
                <button type="submit" class="btn-login-submit">Entrar</button>
            </form>
            <p style="text-align: center; margin-top: 15px; color: #666; font-size: 0.9rem;">
                Usuário padrão: <strong>admin</strong> | Senha: <strong>admin123</strong> (Nível 3)
            </p>
        </div>
    </div>

    <!-- WhatsApp Float Button -->
    <a href="https://wa.me/5598992031747" class="whatsapp-float" target="_blank">
        ☎
    </a>

    <script>


        // Customização de Ícones
        let currentEditingIndex = -1;
        let selectedFormat = 'line';
        let selectedColor = 'gold';

        // Sistema de Usuários e Permissões
        let currentUser = {
            username: '',
            name: '',
            level: 0
        };

        // Inicializar usuário admin padrão
        function initializeDefaultUsers() {
            const users = localStorage.getItem('systemUsers');
            if (!users) {
                const defaultUsers = [
                    {
                        username: 'admin',
                        password: 'admin123',
                        name: 'Administrador Principal',
                        role: 'Administrador',
                        level: 3
                    }
                ];
                localStorage.setItem('systemUsers', JSON.stringify(defaultUsers));
            }
        }

        // Verificar permissão
        function hasPermission(action) {
            // action: 'view', 'create', 'edit', 'delete'
            if (action === 'view') return currentUser.level >= 1;
            if (action === 'create') return currentUser.level >= 2;
            if (action === 'edit' || action === 'delete') return currentUser.level >= 3;
            return false;
        }

        // Aplicar controle de acesso na interface
        function applyAccessControl() {
            // Esconder/mostrar seção de gestão de usuários (apenas nível 3)
            const userManagement = document.getElementById('user-management-section');
            if (currentUser.level < 3) {
                userManagement.classList.add('hidden');
            }

            // Esconder formulário de adicionar processo para nível 1
            const addProcessSection = document.getElementById('add-process-section');
            if (currentUser.level < 2) {
                addProcessSection.classList.add('hidden');
            }
        }

        // Navegação entre etapas do formulário
        let currentStep = 1;

        function nextStep() {
            // Validar campos obrigatórios da etapa 1
            const clientName = document.getElementById('client-name').value;
            const clientDocument = document.getElementById('client-document').value;
            const clientPhone = document.getElementById('client-phone').value;

            if (!clientName || !clientDocument || !clientPhone) {
                alert('Por favor, preencha todos os campos obrigatórios marcados com *');
                return;
            }

            currentStep = 2;
            updateFormSteps();
        }

        function prevStep() {
            currentStep = 1;
            updateFormSteps();
        }

        function updateFormSteps() {
            // Atualizar indicadores de etapa
            document.getElementById('step1').classList.remove('active', 'completed');
            document.getElementById('step2').classList.remove('active', 'completed');
            
            if (currentStep === 1) {
                document.getElementById('step1').classList.add('active');
                document.getElementById('step1-content').classList.add('active');
                document.getElementById('step2-content').classList.remove('active');
            } else if (currentStep === 2) {
                document.getElementById('step1').classList.add('completed');
                document.getElementById('step2').classList.add('active');
                document.getElementById('step1-content').classList.remove('active');
                document.getElementById('step2-content').classList.add('active');
            }
        }

        // Edição de Textos
        function editText(elementId) {
            const element = document.getElementById(elementId);
            if (!element) return;
            
            // Pegar apenas o texto, sem o botão
            const textNode = Array.from(element.childNodes).find(node => node.nodeType === 3);
            const currentText = textNode ? textNode.textContent.trim() : element.textContent.replace('✎', '').trim();
            
            const newText = prompt('Digite o novo texto:', currentText);
            
            if (newText !== null && newText.trim() !== '') {
                // Atualizar apenas o texto, mantendo o botão
                textNode.textContent = newText;
                
                // Salvar no localStorage
                const savedTexts = JSON.parse(localStorage.getItem('editableTexts') || '{}');
                savedTexts[elementId] = newText;
                localStorage.setItem('editableTexts', JSON.stringify(savedTexts));
            }
        }

        const colorMap = {
            'gold': 'linear-gradient(90deg, #c5a572 0%, #d4af37 100%)',
            'blue': 'linear-gradient(90deg, #1e3a5f 0%, #2d4a6f 100%)',
            'red': 'linear-gradient(90deg, #dc3545 0%, #c82333 100%)',
            'green': 'linear-gradient(90deg, #28a745 0%, #218838 100%)',
            'purple': 'linear-gradient(90deg, #6f42c1 0%, #5a32a3 100%)',
            'orange': 'linear-gradient(90deg, #fd7e14 0%, #e8590c 100%)',
            'teal': 'linear-gradient(90deg, #20c997 0%, #1aa179 100%)',
            'pink': 'linear-gradient(90deg, #e83e8c 0%, #d63384 100%)',
        };

        function openCustomizePanel(index) {
            currentEditingIndex = index;
            const icon = document.querySelectorAll('.area-icon')[index];
            selectedFormat = icon.dataset.format || 'line';
            selectedColor = icon.dataset.color || 'gold';
            
            // Atualizar seleções visuais
            document.querySelectorAll('.format-option').forEach(opt => {
                opt.classList.toggle('selected', opt.dataset.format === selectedFormat);
            });
            document.querySelectorAll('.color-option').forEach(opt => {
                opt.classList.toggle('selected', opt.dataset.color === selectedColor);
            });
            
            document.getElementById('customizePanel').classList.add('active');
            document.getElementById('customizeOverlay').classList.add('active');
        }

        function closeCustomizePanel() {
            document.getElementById('customizePanel').classList.remove('active');
            document.getElementById('customizeOverlay').classList.remove('active');
        }

        function selectFormat(format) {
            selectedFormat = format;
            document.querySelectorAll('.format-option').forEach(opt => {
                opt.classList.toggle('selected', opt.dataset.format === format);
            });
        }

        function selectColor(color) {
            selectedColor = color;
            document.querySelectorAll('.color-option').forEach(opt => {
                opt.classList.toggle('selected', opt.dataset.color === color);
            });
        }

        function applyCustomization() {
            if (currentEditingIndex >= 0) {
                const icon = document.querySelectorAll('.area-icon')[currentEditingIndex];
                
                // Remover classes anteriores
                icon.classList.remove('circle', 'square', 'diamond', 'dot', 'line');
                
                // Aplicar novo formato
                if (selectedFormat !== 'none') {
                    icon.classList.add(selectedFormat);
                    icon.style.display = 'block';
                } else {
                    icon.style.display = 'none';
                }
                
                // Aplicar cor
                icon.style.background = colorMap[selectedColor];
                
                // Salvar no dataset
                icon.dataset.format = selectedFormat;
                icon.dataset.color = selectedColor;
                
                // Salvar no localStorage
                saveIconCustomizations();
            }
            
            closeCustomizePanel();
        }

        // Salvar customizações dos ícones
        function saveIconCustomizations() {
            const icons = document.querySelectorAll('.area-icon');
            const customizations = [];
            icons.forEach((icon, index) => {
                customizations.push({
                    format: icon.dataset.format || 'line',
                    color: icon.dataset.color || 'gold'
                });
            });
            localStorage.setItem('iconCustomizations', JSON.stringify(customizations));
        }

        // Carregar customizações salvas
        function loadSavedData() {
            // Carregar logo
            const savedLogo = localStorage.getItem('logoImage');
            if (savedLogo) {
                const logoPreview = document.getElementById('logoPreview');
                logoPreview.innerHTML = `<img src="${savedLogo}" alt="Logo">`;
            }

            // Carregar imagem da seção sobre
            const savedAboutImage = localStorage.getItem('aboutImage');
            if (savedAboutImage) {
                const aboutImage = document.getElementById('aboutImage');
                aboutImage.style.backgroundImage = `url('${savedAboutImage}')`;
                aboutImage.classList.add('has-image');
                const innerDiv = aboutImage.querySelector('div:first-child');
                if (innerDiv) {
                    innerDiv.style.display = 'none';
                }
                
                // Aplicar opacidade salva
                const savedOpacity = localStorage.getItem('aboutImageOpacity');
                if (savedOpacity) {
                    aboutImage.style.setProperty('--overlay-opacity', savedOpacity / 100);
                }
            }

            // Carregar customizações dos ícones
            const savedCustomizations = localStorage.getItem('iconCustomizations');
            if (savedCustomizations) {
                const customizations = JSON.parse(savedCustomizations);
                const icons = document.querySelectorAll('.area-icon');
                icons.forEach((icon, index) => {
                    if (customizations[index]) {
                        const { format, color } = customizations[index];
                        
                        // Remover classes anteriores
                        icon.classList.remove('circle', 'square', 'diamond', 'dot', 'line');
                        
                        // Aplicar formato
                        if (format !== 'none') {
                            icon.classList.add(format);
                            icon.style.display = 'block';
                        } else {
                            icon.style.display = 'none';
                        }
                        
                        // Aplicar cor
                        icon.style.background = colorMap[color];
                        
                        // Salvar no dataset
                        icon.dataset.format = format;
                        icon.dataset.color = color;
                    }
                });
            }

            // Carregar textos editados
            const savedTexts = localStorage.getItem('editableTexts');
            if (savedTexts) {
                const texts = JSON.parse(savedTexts);
                Object.keys(texts).forEach(elementId => {
                    const element = document.getElementById(elementId);
                    if (element) {
                        // Atualizar apenas o texto, mantendo o botão
                        const textNode = Array.from(element.childNodes).find(node => node.nodeType === 3);
                        if (textNode) {
                            textNode.textContent = texts[elementId];
                        }
                    }
                });
            }
        }

        // Menu Hamburguer
        function toggleMenu() {
            const navMenu = document.getElementById('navMenu');
            const menuToggle = document.getElementById('menuToggle');
            navMenu.classList.toggle('active');
            menuToggle.classList.toggle('active');
        }

        function closeMenu() {
            const navMenu = document.getElementById('navMenu');
            const menuToggle = document.getElementById('menuToggle');
            navMenu.classList.remove('active');
            menuToggle.classList.remove('active');
        }

        // Login Modal
        function openLoginModal(e) {
            e.preventDefault();
            document.getElementById('login-modal').classList.add('active');
        }

        function closeLoginModal() {
            document.getElementById('login-modal').classList.remove('active');
        }

        // Login Handler
        document.getElementById('login-form').addEventListener('submit', function(e) {
            e.preventDefault();
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;

            // Carregar usuários
            const users = JSON.parse(localStorage.getItem('systemUsers') || '[]');
            const user = users.find(u => u.username === username && u.password === password);

            if (user) {
                // Salvar usuário atual
                currentUser = {
                    username: user.username,
                    name: user.name,
                    level: user.level
                };

                document.getElementById('main-site').style.display = 'none';
                document.getElementById('admin-dashboard').style.display = 'block';
                document.getElementById('userName').textContent = user.name;
                document.getElementById('user-level-display').textContent = `Nível ${user.level}`;
                
                // Ocultar menu principal e botão de login, mostrar info do usuário
                document.getElementById('mainNavLinks').style.display = 'none';
                document.getElementById('loginBtn').style.display = 'none';
                document.getElementById('userInfo').classList.add('active');
                document.getElementById('menuToggle').style.display = 'none';
                
                // Aplicar controle de acesso
                applyAccessControl();
                
                // Inicializar seção financeira
                initializeFinancialSection();
                
                closeLoginModal();
                
                // Smooth scroll to top
                window.scrollTo({ top: 0, behavior: 'smooth' });
            } else {
                alert('Usuário ou senha incorretos!');
            }
        });

        // Logout
        function logout() {
            document.getElementById('main-site').style.display = 'block';
            document.getElementById('admin-dashboard').style.display = 'none';
            document.getElementById('login-form').reset();
            
            // Restaurar menu principal e ocultar info do usuário
            document.getElementById('mainNavLinks').style.display = 'flex';
            document.getElementById('loginBtn').style.display = 'block';
            document.getElementById('userInfo').classList.remove('active');
            document.getElementById('menuToggle').style.display = 'flex';
            
            // Limpar usuário atual
            currentUser = { username: '', name: '', level: 0 };
            
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        // Delete User
        function deleteUser(username) {
            if (username === 'admin') {
                alert('Não é possível excluir o usuário administrador padrão!');
                return;
            }

            if (!hasPermission('delete')) {
                alert('Você não tem permissão para excluir usuários!');
                return;
            }

            if (!confirm(`Tem certeza que deseja excluir o usuário "${username}"?`)) {
                return;
            }

            // Remover do localStorage
            let users = JSON.parse(localStorage.getItem('systemUsers') || '[]');
            users = users.filter(u => u.username !== username);
            localStorage.setItem('systemUsers', JSON.stringify(users));

            // Recarregar lista
            loadUsersList();
            
            alert('Usuário excluído com sucesso!');
        }

        // Carregar lista de usuários
        function loadUsersList() {
            const users = JSON.parse(localStorage.getItem('systemUsers') || '[]');
            const usersList = document.getElementById('users-list');
            
            usersList.innerHTML = '';
            
            users.forEach(user => {
                const item = document.createElement('li');
                item.className = 'process-item';
                
                const deleteBtn = user.username === 'admin' 
                    ? '<span style="color: #999; font-size: 0.85rem;">Usuário padrão</span>'
                    : `<button class="btn-action btn-delete" onclick="deleteUser('${user.username}')">✕ Excluir</button>`;
                
                item.innerHTML = `
                    <div>
                        <strong>${user.username}</strong>
                        <p style="color: #666; font-size: 0.9rem;">${user.name}${user.role ? ' - ' + user.role : ''}</p>
                    </div>
                    <div style="display: flex; gap: 10px; align-items: center;">
                        <span class="level-badge nivel${user.level}">Nível ${user.level}</span>
                        <div class="action-buttons">
                            ${deleteBtn}
                        </div>
                    </div>
                `;
                
                usersList.appendChild(item);
            });
        }

        // Add User Handler
        document.getElementById('add-user-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            if (!hasPermission('create')) {
                alert('Você não tem permissão para cadastrar usuários!');
                return;
            }

            const name = document.getElementById('new-user-name').value;
            const username = document.getElementById('new-username').value;
            const password = document.getElementById('new-password').value;
            const level = parseInt(document.getElementById('new-user-level').value);
            const role = document.getElementById('new-user-role').value || 'Funcionário';

            // Carregar usuários existentes
            const users = JSON.parse(localStorage.getItem('systemUsers') || '[]');
            
            // Verificar se usuário já existe
            if (users.find(u => u.username === username)) {
                alert('Este nome de usuário já está em uso!');
                return;
            }

            // Adicionar novo usuário
            const newUser = {
                username: username,
                password: password,
                name: name,
                role: role,
                level: level
            };

            users.push(newUser);
            localStorage.setItem('systemUsers', JSON.stringify(users));

            // Recarregar lista
            loadUsersList();
            
            // Reset form
            this.reset();
            
            alert('Usuário cadastrado com sucesso!');
        });

        // ===== FINANCIAL MANAGEMENT =====
        
        // Inicializar seção financeira
        function initializeFinancialSection() {
            if (currentUser && currentUser.level === 3) {
                document.getElementById('financial-section').style.display = 'block';
                loadTransactions();
                updateFinancialSummary();
            } else {
                document.getElementById('financial-section').style.display = 'none';
            }
        }

        // Alternar tabs financeiras
        function showFinancialTab(tabName) {
            // Hide all tabs
            document.querySelectorAll('.financial-tab-content').forEach(tab => {
                tab.style.display = 'none';
            });
            
            // Remove active class from all buttons
            document.querySelectorAll('.financial-tab').forEach(btn => {
                btn.classList.remove('active');
            });
            
            // Show selected tab
            document.getElementById('tab-' + tabName).style.display = 'block';
            event.target.classList.add('active');
            
            if (tabName === 'reports') {
                updateReports();
            }
        }

        // Formatar campo de valor como moeda
        function formatCurrency(input) {
            let value = input.value.replace(/\D/g, '');
            value = (value / 100).toFixed(2);
            input.value = 'R$ ' + value.replace('.', ',').replace(/(\d)(?=(\d{3})+(?!\d))/g, '$1.');
        }

        // Converter valor formatado para número
        function parseCurrency(value) {
            return parseFloat(value.replace('R$ ', '').replace(/\./g, '').replace(',', '.'));
        }

        // Atualizar formulário baseado no tipo
        function updateFormByType() {
            const type = document.getElementById('transaction-type').value;
            const processField = document.getElementById('process-field');
            
            if (type.includes('honorario') || type.includes('consulta')) {
                processField.style.display = 'flex';
            } else {
                processField.style.display = 'none';
            }
        }

        // Adicionar transação
        document.getElementById('add-transaction-form')?.addEventListener('submit', function(e) {
            e.preventDefault();
            
            const transactionData = {
                id: Date.now(),
                type: document.getElementById('transaction-type').value,
                value: parseCurrency(document.getElementById('transaction-value').value),
                description: document.getElementById('transaction-description').value,
                date: document.getElementById('transaction-date').value,
                process: document.getElementById('transaction-process').value,
                client: document.getElementById('transaction-client').value,
                paymentMethod: document.getElementById('transaction-payment-method').value,
                status: document.getElementById('transaction-status').value,
                category: document.getElementById('transaction-category').value,
                installments: parseInt(document.getElementById('transaction-installments').value) || 1,
                notes: document.getElementById('transaction-notes').value,
                createdAt: new Date().toISOString(),
                createdBy: currentUser.username
            };

            // Salvar no localStorage
            const transactions = JSON.parse(localStorage.getItem('systemTransactions') || '[]');
            
            // Se tiver parcelas, criar múltiplas transações
            if (transactionData.installments > 1) {
                const valuePerInstallment = transactionData.value / transactionData.installments;
                const baseDate = new Date(transactionData.date);
                
                for (let i = 0; i < transactionData.installments; i++) {
                    const installmentDate = new Date(baseDate);
                    installmentDate.setMonth(installmentDate.getMonth() + i);
                    
                    const installment = {
                        ...transactionData,
                        id: Date.now() + i,
                        value: valuePerInstallment,
                        date: installmentDate.toISOString().split('T')[0],
                        description: `${transactionData.description} (${i + 1}/${transactionData.installments})`,
                        installment: i + 1,
                        totalInstallments: transactionData.installments
                    };
                    
                    transactions.push(installment);
                }
            } else {
                transactions.push(transactionData);
            }
            
            localStorage.setItem('systemTransactions', JSON.stringify(transactions));
            
            // Reset form
            this.reset();
            
            // Atualizar displays
            loadTransactions();
            updateFinancialSummary();
            
            // Voltar para aba de transações
            showFinancialTab('transactions');
            
            alert('Movimentação adicionada com sucesso!');
        });

        // Carregar transações
        function loadTransactions() {
            const transactions = JSON.parse(localStorage.getItem('systemTransactions') || '[]');
            displayTransactions(transactions);
        }

        // Exibir transações
        function displayTransactions(transactions) {
            const container = document.getElementById('transactions-container');
            
            if (transactions.length === 0) {
                container.innerHTML = `
                    <div class="empty-state">
                        <div class="empty-state-icon">$</div>
                        <p>Nenhuma transação registrada</p>
                    </div>
                `;
                return;
            }

            // Ordenar por data (mais recente primeiro)
            transactions.sort((a, b) => new Date(b.date) - new Date(a.date));

            const html = `
                <table>
                    <thead>
                        <tr>
                            <th>Data</th>
                            <th>Descrição</th>
                            <th>Tipo</th>
                            <th>Categoria</th>
                            <th>Valor</th>
                            <th>Status</th>
                            <th>Ações</th>
                        </tr>
                    </thead>
                    <tbody>
                        ${transactions.map(t => {
                            const isIncome = t.type.includes('income');
                            const typeLabel = t.type.split('-')[1];
                            const date = new Date(t.date).toLocaleDateString('pt-BR');
                            const value = t.value.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' });
                            
                            return `
                                <tr>
                                    <td>${date}</td>
                                    <td>
                                        ${t.description}
                                        ${t.client ? `<br><small style="color: #666;">Cliente: ${t.client}</small>` : ''}
                                    </td>
                                    <td><span class="badge ${isIncome ? 'ativo' : 'arquivado'}">${isIncome ? 'Receita' : 'Despesa'}</span></td>
                                    <td>${t.category || typeLabel}</td>
                                    <td style="font-weight: 600; color: ${isIncome ? '#27ae60' : '#e74c3c'}">${isIncome ? '+' : '-'} ${value}</td>
                                    <td><span class="badge ${t.status}">${getStatusLabel(t.status)}</span></td>
                                    <td>
                                        <button class="btn-action view" onclick="viewTransaction(${t.id})" title="Ver Detalhes">Ver</button>
                                        <button class="btn-action delete" onclick="deleteTransaction(${t.id})" title="Excluir">Excluir</button>
                                    </td>
                                </tr>
                            `;
                        }).join('')}
                    </tbody>
                </table>
            `;
            
            container.innerHTML = html;
        }

        // Obter label de status
        function getStatusLabel(status) {
            const labels = {
                'paid': 'Pago',
                'pending': 'Pendente',
                'overdue': 'Atrasado',
                'canceled': 'Cancelado'
            };
            return labels[status] || status;
        }

        // Filtrar transações
        function filterTransactions() {
            const type = document.getElementById('filter-type').value;
            const status = document.getElementById('filter-status').value;
            const month = document.getElementById('filter-month').value;
            
            let transactions = JSON.parse(localStorage.getItem('systemTransactions') || '[]');
            
            if (type !== 'all') {
                transactions = transactions.filter(t => t.type.includes(type));
            }
            
            if (status !== 'all') {
                transactions = transactions.filter(t => t.status === status);
            }
            
            if (month) {
                transactions = transactions.filter(t => t.date.startsWith(month));
            }
            
            displayTransactions(transactions);
        }

        // Limpar filtros
        function clearFilters() {
            document.getElementById('filter-type').value = 'all';
            document.getElementById('filter-status').value = 'all';
            document.getElementById('filter-month').value = '';
            loadTransactions();
        }

        // Atualizar resumo financeiro
        function updateFinancialSummary() {
            const transactions = JSON.parse(localStorage.getItem('systemTransactions') || '[]');
            
            let totalIncome = 0;
            let totalExpenses = 0;
            let pendingFees = 0;
            
            transactions.forEach(t => {
                if (t.type.includes('income')) {
                    totalIncome += t.value;
                    if (t.status === 'pending' && t.type.includes('honorario')) {
                        pendingFees += t.value;
                    }
                } else {
                    totalExpenses += t.value;
                }
            });
            
            const balance = totalIncome - totalExpenses;
            
            document.getElementById('total-income').textContent = totalIncome.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' });
            document.getElementById('total-expenses').textContent = totalExpenses.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' });
            document.getElementById('pending-fees').textContent = pendingFees.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' });
            
            const balanceElement = document.getElementById('balance');
            balanceElement.textContent = balance.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' });
            balanceElement.className = 'financial-value ' + (balance >= 0 ? 'positive' : 'negative');
        }

        // Atualizar relatórios
        function updateReports() {
            const transactions = JSON.parse(localStorage.getItem('systemTransactions') || '[]');
            const currentMonth = new Date().toISOString().slice(0, 7);
            
            const monthTransactions = transactions.filter(t => t.date.startsWith(currentMonth));
            
            let monthIncome = 0;
            let monthExpenses = 0;
            const categories = {};
            
            monthTransactions.forEach(t => {
                const category = t.category || t.type.split('-')[1];
                
                if (!categories[category]) {
                    categories[category] = { income: 0, expense: 0 };
                }
                
                if (t.type.includes('income')) {
                    monthIncome += t.value;
                    categories[category].income += t.value;
                } else {
                    monthExpenses += t.value;
                    categories[category].expense += t.value;
                }
            });
            
            const monthBalance = monthIncome - monthExpenses;
            const avgTicket = monthTransactions.length > 0 ? monthIncome / monthTransactions.filter(t => t.type.includes('income')).length : 0;
            
            document.getElementById('month-income').textContent = monthIncome.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' });
            document.getElementById('month-expenses').textContent = monthExpenses.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' });
            
            const monthBalanceElement = document.getElementById('month-balance');
            monthBalanceElement.textContent = monthBalance.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' });
            monthBalanceElement.className = 'financial-value ' + (monthBalance >= 0 ? 'positive' : 'negative');
            
            document.getElementById('avg-ticket').textContent = avgTicket.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' });
            
            // Relatório por categoria
            const categoryHtml = Object.entries(categories).map(([cat, values]) => `
                <div style="padding: 15px; background: #f8f9fa; border-radius: 8px; margin-bottom: 10px;">
                    <strong>${cat}</strong><br>
                    <span style="color: #27ae60;">Receitas: ${values.income.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' })}</span> | 
                    <span style="color: #e74c3c;">Despesas: ${values.expense.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' })}</span>
                </div>
            `).join('');
            
            document.getElementById('category-report').innerHTML = categoryHtml || '<p style="color: #999;">Nenhum dado disponível</p>';
            
            // Top transações
            const topTransactions = [...monthTransactions]
                .filter(t => t.type.includes('income'))
                .sort((a, b) => b.value - a.value)
                .slice(0, 5);
            
            const topHtml = topTransactions.map((t, i) => `
                <div style="padding: 15px; background: #f8f9fa; border-radius: 8px; margin-bottom: 10px; display: flex; justify-content: space-between; align-items: center;">
                    <div>
                        <strong>${i + 1}. ${t.description}</strong><br>
                        <small style="color: #666;">${new Date(t.date).toLocaleDateString('pt-BR')}</small>
                    </div>
                    <strong style="color: #27ae60; font-size: 1.2rem;">${t.value.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' })}</strong>
                </div>
            `).join('');
            
            document.getElementById('top-transactions').innerHTML = topHtml || '<p style="color: #999;">Nenhum dado disponível</p>';
        }

        // Ver detalhes da transação
        function viewTransaction(id) {
            const transactions = JSON.parse(localStorage.getItem('systemTransactions') || '[]');
            const transaction = transactions.find(t => t.id === id);
            
            if (!transaction) return;
            
            const details = `
DETALHES DA TRANSAÇÃO
${'='.repeat(50)}

Tipo: ${transaction.type.includes('income') ? 'Receita' : 'Despesa'}
Categoria: ${transaction.type.split('-')[1]}
Descrição: ${transaction.description}
Valor: ${transaction.value.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' })}
Data: ${new Date(transaction.date).toLocaleDateString('pt-BR')}
Status: ${getStatusLabel(transaction.status)}
Forma de Pagamento: ${transaction.paymentMethod}
${transaction.client ? `\nCliente: ${transaction.client}` : ''}
${transaction.process ? `\nProcesso: ${transaction.process}` : ''}
${transaction.category ? `\nCategoria Personalizada: ${transaction.category}` : ''}
${transaction.installment ? `\nParcela: ${transaction.installment}/${transaction.totalInstallments}` : ''}
${transaction.notes ? `\nObservações: ${transaction.notes}` : ''}
            `;
            
            alert(details);
        }

        // Excluir transação
        function deleteTransaction(id) {
            if (!confirm('Tem certeza que deseja excluir esta transação?')) return;
            
            let transactions = JSON.parse(localStorage.getItem('systemTransactions') || '[]');
            transactions = transactions.filter(t => t.id !== id);
            localStorage.setItem('systemTransactions', JSON.stringify(transactions));
            
            loadTransactions();
            updateFinancialSummary();
            
            alert('Transação excluída com sucesso!');
        }

        // Busca de Processos
        function searchProcesses() {
            const searchTerm = document.getElementById('search-input').value.toLowerCase().trim();
            const resultsContainer = document.getElementById('search-results');
            
            if (!searchTerm) {
                resultsContainer.innerHTML = '<p class="no-results">Digite algo para buscar</p>';
                return;
            }

            // Carregar processos salvos
            const processes = JSON.parse(localStorage.getItem('systemProcesses') || '[]');
            
            // Filtrar processos
            const results = processes.filter(proc => {
                return (
                    proc.processNumber.toLowerCase().includes(searchTerm) ||
                    proc.clientName.toLowerCase().includes(searchTerm) ||
                    proc.processType.toLowerCase().includes(searchTerm) ||
                    proc.processDescription.toLowerCase().includes(searchTerm) ||
                    (proc.clientDocument && proc.clientDocument.toLowerCase().includes(searchTerm))
                );
            });

            // Exibir resultados
            if (results.length === 0) {
                resultsContainer.innerHTML = '<p class="no-results">Nenhum processo encontrado</p>';
                return;
            }

            resultsContainer.innerHTML = results.map((proc, index) => `
                <div class="result-item" onclick="showProcessDetails(${proc.id})">
                    <div class="result-title">${proc.processType} - ${proc.processDescription}</div>
                    <div class="result-info">
                        <strong>Processo:</strong> ${proc.processNumber} | 
                        <strong>Cliente:</strong> ${proc.clientName} | 
                        <strong>Status:</strong> <span class="badge ${proc.processStatus}">${proc.processStatus.toUpperCase()}</span>
                    </div>
                </div>
            `).join('');
        }

        // Enter para buscar
        document.getElementById('search-input')?.addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                searchProcesses();
            }
        });

        // Mostrar detalhes do processo
        function showProcessDetails(processId) {
            const processes = JSON.parse(localStorage.getItem('systemProcesses') || '[]');
            const process = processes.find(p => p.id === processId);
            
            if (!process) return;

            // Preencher dados do processo
            document.getElementById('detail-process-title').textContent = process.processType;
            document.getElementById('detail-process-number').textContent = `Processo N° ${process.processNumber}`;
            document.getElementById('detail-proc-number').textContent = process.processNumber;
            document.getElementById('detail-proc-type').textContent = process.processType;
            document.getElementById('detail-proc-status').innerHTML = `<span class="badge ${process.processStatus}">${process.processStatus.toUpperCase()}</span>`;
            document.getElementById('detail-proc-court').textContent = process.processCourt || '-';
            document.getElementById('detail-proc-date').textContent = process.processDate ? new Date(process.processDate).toLocaleDateString('pt-BR') : '-';
            document.getElementById('detail-proc-value').textContent = process.processValue || '-';
            document.getElementById('detail-proc-description').textContent = process.processDescription;
            document.getElementById('detail-proc-opponent').textContent = process.processOpponent || '-';
            document.getElementById('detail-proc-notes').textContent = process.processNotes || '-';

            // Preencher dados do cliente
            document.getElementById('detail-client-name').textContent = process.clientName;
            document.getElementById('detail-client-document').textContent = process.clientDocument;
            document.getElementById('detail-client-rg').textContent = process.clientRg || '-';
            document.getElementById('detail-client-birthdate').textContent = process.clientBirthdate ? new Date(process.clientBirthdate).toLocaleDateString('pt-BR') : '-';
            document.getElementById('detail-client-phone').textContent = process.clientPhone;
            document.getElementById('detail-client-email').textContent = process.clientEmail || '-';
            document.getElementById('detail-client-address').textContent = process.clientAddress || '-';
            document.getElementById('detail-client-cep').textContent = process.clientCep || '-';
            document.getElementById('detail-client-profession').textContent = process.clientProfession || '-';
            document.getElementById('detail-client-notes').textContent = process.clientNotes || '-';

            // Abrir modal
            document.getElementById('process-details-modal').classList.add('active');
        }

        // Fechar detalhes
        function closeProcessDetails() {
            document.getElementById('process-details-modal').classList.remove('active');
        }

        // Add Process Handler
        document.getElementById('add-process-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Coletar todos os dados do formulário
            const processData = {
                id: Date.now(), // ID único baseado em timestamp
                // Dados do cliente
                clientName: document.getElementById('client-name').value,
                clientDocument: document.getElementById('client-document').value,
                clientRg: document.getElementById('client-rg').value,
                clientBirthdate: document.getElementById('client-birthdate').value,
                clientPhone: document.getElementById('client-phone').value,
                clientEmail: document.getElementById('client-email').value,
                clientAddress: document.getElementById('client-address').value,
                clientCep: document.getElementById('client-cep').value,
                clientProfession: document.getElementById('client-profession').value,
                clientNotes: document.getElementById('client-notes').value,
                // Dados do processo
                processNumber: document.getElementById('process-number').value,
                processType: document.getElementById('process-type').value,
                processCourt: document.getElementById('process-court').value,
                processDate: document.getElementById('process-date').value,
                processStatus: document.getElementById('process-status').value,
                processValue: document.getElementById('process-value').value,
                processDescription: document.getElementById('process-description').value,
                processOpponent: document.getElementById('process-opponent').value,
                processNotes: document.getElementById('process-notes').value,
                createdAt: new Date().toISOString()
            };

            // Salvar no localStorage
            const processes = JSON.parse(localStorage.getItem('systemProcesses') || '[]');
            processes.push(processData);
            localStorage.setItem('systemProcesses', JSON.stringify(processes));

            // Adicionar à lista visual
            const processList = document.getElementById('process-list');
            const newItem = document.createElement('li');
            newItem.className = 'process-item';
            newItem.style.cursor = 'pointer';
            newItem.onclick = function() { showProcessDetails(processData.id); };
            newItem.innerHTML = `
                <div>
                    <strong>${processData.processType} - ${processData.processDescription}</strong>
                    <p style="color: #666; font-size: 0.9rem;">Processo: ${processData.processNumber} | Cliente: ${processData.clientName}</p>
                </div>
                <span class="badge ${processData.processStatus}">${processData.processStatus.toUpperCase()}</span>
            `;
            
            processList.insertBefore(newItem, processList.firstChild);
            
            // Reset form and return to step 1
            this.reset();
            currentStep = 1;
            updateFormSteps();
            
            // Update counters
            updateCounters();
            
            alert('Processo adicionado com sucesso!');
        });

        // Update Counters
        function updateCounters() {
            const processList = document.getElementById('process-list');
            const totalProcesses = processList.children.length;
            const activeProcesses = processList.querySelectorAll('.badge.ativo').length;
            
            document.getElementById('total-processes').textContent = (31248 + totalProcesses - 5).toLocaleString('pt-BR');
            document.getElementById('active-processes').textContent = (8421 + activeProcesses - 2).toLocaleString('pt-BR');
        }

        // Smooth Scroll for Navigation
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                const href = this.getAttribute('href');
                if (href !== '#' && document.querySelector(href)) {
                    e.preventDefault();
                    document.querySelector(href).scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        // Close modal when clicking outside
        window.onclick = function(event) {
            const modal = document.getElementById('login-modal');
            if (event.target === modal) {
                closeLoginModal();
            }
        }

        // Carregar dados salvos quando a página carrega
        window.addEventListener('DOMContentLoaded', function() {
            initializeDefaultUsers();
            loadSavedData();
            loadUsersList();
            
            // Definir data atual no campo de transação
            const today = new Date().toISOString().split('T')[0];
            const transactionDateField = document.getElementById('transaction-date');
            if (transactionDateField) {
                transactionDateField.value = today;
            }
            
            // Definir mês atual no filtro
            const currentMonth = new Date().toISOString().slice(0, 7);
            const filterMonthField = document.getElementById('filter-month');
            if (filterMonthField) {
                filterMonthField.value = currentMonth;
            }
        });
    </script>
</body>
</html>

