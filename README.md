‏<!doctype html>
‏<html lang="ar" dir="rtl">
‏ <head>
‏  <meta charset="UTF-8">
‏  <meta name="viewport" content="width=device-width, initial-scale=1.0">
‏  <title>XSora - نصمم المستقبل ونبرمج التجربة</title>
‏  <script src="/_sdk/element_sdk.js"></script>
‏  <style>
‏        body {
‏            box-sizing: border-box;
        }
        
        * {
‏            margin: 0;
‏            padding: 0;
‏            box-sizing: border-box;
        }

‏        html, body {
‏            height: 100%;
‏            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
‏            overflow-x: hidden;
        }

‏        body {
‏            background: #0a0a0a;
‏            color: #ffffff;
‏            position: relative;
‏            overflow-x: hidden;
        }

‏        body::before {
‏            content: '';
‏            position: fixed;
‏            top: 0;
‏            left: 0;
‏            width: 100%;
‏            height: 100%;
‏            background: 
‏                radial-gradient(circle at 20% 50%, rgba(0, 212, 255, 0.15) 0%, transparent 40%),
‏                radial-gradient(circle at 80% 20%, rgba(0, 153, 204, 0.12) 0%, transparent 45%),
‏                radial-gradient(circle at 40% 80%, rgba(0, 212, 255, 0.08) 0%, transparent 35%),
‏                radial-gradient(circle at 60% 30%, rgba(0, 255, 200, 0.06) 0%, transparent 50%),
‏                radial-gradient(circle at 10% 90%, rgba(0, 100, 255, 0.1) 0%, transparent 40%);
‏            animation: backgroundMove 25s ease-in-out infinite;
‏            z-index: -1;
        }

‏        body::after {
‏            content: '';
‏            position: fixed;
‏            top: 0;
‏            left: 0;
‏            width: 100%;
‏            height: 100%;
‏            background: 
‏                linear-gradient(45deg, transparent 30%, rgba(0, 212, 255, 0.03) 50%, transparent 70%),
‏                linear-gradient(-45deg, transparent 40%, rgba(0, 153, 204, 0.02) 60%, transparent 80%);
‏            animation: backgroundWave 30s linear infinite;
‏            z-index: -1;
        }

‏        @keyframes backgroundMove {
            0%, 100% { 
‏                transform: translateX(0) translateY(0) scale(1) rotate(0deg);
‏                filter: hue-rotate(0deg);
            }
            20% { 
‏                transform: translateX(-30px) translateY(-40px) scale(1.1) rotate(2deg);
‏                filter: hue-rotate(10deg);
            }
            40% { 
‏                transform: translateX(25px) translateY(30px) scale(0.9) rotate(-1deg);
‏                filter: hue-rotate(20deg);
            }
            60% { 
‏                transform: translateX(-15px) translateY(40px) scale(1.05) rotate(1deg);
‏                filter: hue-rotate(15deg);
            }
            80% { 
‏                transform: translateX(20px) translateY(-25px) scale(0.95) rotate(-2deg);
‏                filter: hue-rotate(5deg);
            }
        }

‏        @keyframes backgroundWave {
            0% { 
‏                transform: translateX(-100%) rotate(0deg);
‏                opacity: 0.3;
            }
            50% { 
‏                transform: translateX(0%) rotate(180deg);
‏                opacity: 0.6;
            }
            100% { 
‏                transform: translateX(100%) rotate(360deg);
‏                opacity: 0.3;
            }
        }

‏        /* Loading Screen */
‏        .loading-screen {
‏            position: fixed;
‏            top: 0;
‏            left: 0;
‏            width: 100%;
‏            height: 100%;
‏            background: linear-gradient(135deg, #0a0a0a, #1a1a2e, #16213e);
‏            display: flex;
‏            justify-content: center;
‏            align-items: center;
‏            z-index: 10000;
‏            transition: opacity 0.5s ease;
        }

‏        .loading-content {
‏            text-align: center;
        }

‏        .loading-logo {
‏            font-size: 3rem;
‏            font-weight: bold;
‏            background: linear-gradient(45deg, #00d4ff, #0099cc, #ffffff);
‏            -webkit-background-clip: text;
‏            -webkit-text-fill-color: transparent;
‏            background-clip: text;
‏            margin-bottom: 2rem;
‏            animation: pulse 2s ease-in-out infinite;
        }

‏        .loading-spinner {
‏            width: 60px;
‏            height: 60px;
‏            border: 3px solid rgba(0, 212, 255, 0.3);
‏            border-top: 3px solid #00d4ff;
‏            border-radius: 50%;
‏            animation: spin 1s linear infinite;
‏            margin: 0 auto;
        }

‏        @keyframes spin {
‏            0% { transform: rotate(0deg); }
‏            100% { transform: rotate(360deg); }
        }

‏        @keyframes pulse {
‏            0%, 100% { opacity: 1; }
‏            50% { opacity: 0.7; }
        }

‏        /* Top Dropdown Menu */
‏        .top-dropdown {
‏            position: fixed;
‏            top: 0;
‏            width: 100%;
‏            background: #1a1a2e;
‏            border-bottom: 1px solid rgba(0, 212, 255, 0.2);
‏            z-index: 1001;
‏            padding: 0.5rem 0;
‏            transform: translateY(-100%);
‏            transition: transform 0.3s ease;
        }

‏        .top-dropdown.active {
‏            transform: translateY(0);
        }

‏        .top-dropdown-content {
‏            display: grid;
‏            grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
‏            gap: 0.8rem;
‏            max-width: 1200px;
‏            margin: 0 auto;
‏            padding: 1rem 2rem;
‏            justify-items: center;
        }

‏        .top-dropdown-item {
‏            color: #ffffff;
‏            text-decoration: none;
‏            padding: 0.8rem 1.5rem;
‏            border-radius: 25px;
‏            transition: all 0.4s ease;
‏            position: relative;
‏            overflow: hidden;
‏            font-weight: 600;
‏            background: linear-gradient(135deg, #1a1a2e, #2a2a4e);
‏            border: 1px solid rgba(0, 212, 255, 0.3);
‏            font-size: 0.95rem;
‏            text-align: center;
‏            min-width: 160px;
‏            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
‏            backdrop-filter: blur(10px);
        }

‏        .top-dropdown-item::before {
‏            content: '';
‏            position: absolute;
‏            top: 0;
‏            left: -100%;
‏            width: 100%;
‏            height: 100%;
‏            background: linear-gradient(45deg, #00d4ff, #0099cc, #00ffcc);
‏            transition: left 0.4s ease;
‏            z-index: -1;
        }

‏        .top-dropdown-item::after {
‏            content: '';
‏            position: absolute;
‏            top: 50%;
‏            left: 50%;
‏            width: 0;
‏            height: 0;
‏            background: radial-gradient(circle, rgba(255, 255, 255, 0.3), transparent);
‏            border-radius: 50%;
‏            transition: all 0.4s ease;
‏            transform: translate(-50%, -50%);
        }

‏        .top-dropdown-item:hover::before {
‏            left: 0;
        }

‏        .top-dropdown-item:hover::after {
‏            width: 100px;
‏            height: 100px;
        }

‏        .top-dropdown-item:hover {
‏            transform: translateY(-5px) scale(1.08);
‏            box-shadow: 0 12px 35px rgba(0, 212, 255, 0.6);
‏            border-color: #00d4ff;
‏            background: linear-gradient(135deg, #2a2a4e, #3a3a6e);
        }

‏        .dropdown-toggle {
‏            position: fixed;
‏            top: 20px;
‏            left: 20px;
‏            background: rgba(0, 212, 255, 0.2);
‏            border: 2px solid #00d4ff;
‏            border-radius: 50%;
‏            width: 50px;
‏            height: 50px;
‏            display: flex;
‏            align-items: center;
‏            justify-content: center;
‏            cursor: pointer;
‏            z-index: 1002;
‏            transition: all 0.3s ease;
‏            backdrop-filter: blur(10px);
        }

‏        .dropdown-toggle:hover {
‏            background: rgba(0, 212, 255, 0.4);
‏            transform: scale(1.1);
‏            box-shadow: 0 0 20px rgba(0, 212, 255, 0.5);
        }

‏        .dropdown-toggle span {
‏            display: block;
‏            width: 20px;
‏            height: 2px;
‏            background: #00d4ff;
‏            margin: 3px 0;
‏            transition: all 0.3s ease;
‏            border-radius: 2px;
        }

‏        .dropdown-toggle.active span:nth-child(1) {
‏            transform: rotate(45deg) translate(5px, 5px);
        }

‏        .dropdown-toggle.active span:nth-child(2) {
‏            opacity: 0;
        }

‏        .dropdown-toggle.active span:nth-child(3) {
‏            transform: rotate(-45deg) translate(7px, -6px);
        }

‏        /* Navigation */
‏        .navbar {
‏            position: fixed;
‏            top: 0;
‏            width: 100%;
‏            background: rgba(10, 10, 10, 0.9);
‏            backdrop-filter: blur(10px);
‏            z-index: 1000;
‏            padding: 1rem 2rem;
‏            transition: all 0.3s ease;
‏            margin-top: 0;
        }

‏        .nav-container {
‏            display: flex;
‏            justify-content: space-between;
‏            align-items: center;
‏            max-width: 1200px;
‏            margin: 0 auto;
        }

‏        .logo {
‏            font-size: 2rem;
‏            font-weight: bold;
‏            background: linear-gradient(45deg, #00d4ff, #0099cc);
‏            -webkit-background-clip: text;
‏            -webkit-text-fill-color: transparent;
‏            background-clip: text;
        }

‏        .nav-menu {
‏            display: flex;
‏            list-style: none;
‏            gap: 2rem;
        }

‏        .nav-item {
‏            position: relative;
        }

‏        .nav-link {
‏            color: #ffffff;
‏            text-decoration: none;
‏            padding: 0.5rem 1rem;
‏            border-radius: 25px;
‏            transition: all 0.3s ease;
‏            position: relative;
‏            overflow: hidden;
        }

‏        .nav-link:hover {
‏            background: linear-gradient(45deg, #00d4ff, #0099cc);
‏            transform: translateY(-2px);
‏            box-shadow: 0 5px 15px rgba(0, 212, 255, 0.3);
        }

‏        .dropdown {
‏            position: absolute;
‏            top: 100%;
‏            right: 0;
‏            background: rgba(26, 26, 46, 0.95);
‏            backdrop-filter: blur(10px);
‏            border-radius: 10px;
‏            padding: 1rem;
‏            min-width: 200px;
‏            opacity: 0;
‏            visibility: hidden;
‏            transform: translateY(-10px);
‏            transition: all 0.3s ease;
‏            border: 1px solid rgba(0, 212, 255, 0.2);
        }

‏        .nav-item:hover .dropdown {
‏            opacity: 1;
‏            visibility: visible;
‏            transform: translateY(0);
        }

‏        .dropdown-item {
‏            display: block;
‏            color: #ffffff;
‏            text-decoration: none;
‏            padding: 0.5rem 1rem;
‏            border-radius: 5px;
‏            transition: all 0.3s ease;
        }

‏        .dropdown-item:hover {
‏            background: linear-gradient(45deg, #00d4ff, #0099cc);
‏            transform: translateX(5px);
        }

‏        /* Hero Section */
‏        .hero {
‏            height: 100vh;
‏            display: flex;
‏            flex-direction: column;
‏            justify-content: center;
‏            align-items: center;
‏            text-align: center;
‏            position: relative;
‏            overflow: hidden;
        }

‏        .hero-title {
‏            font-size: 4rem;
‏            font-weight: bold;
‏            margin-bottom: 2rem;
‏            background: linear-gradient(45deg, #00d4ff, #ffffff, #0099cc);
‏            -webkit-background-clip: text;
‏            -webkit-text-fill-color: transparent;
‏            background-clip: text;
‏            animation: titleGlow 3s ease-in-out infinite;
        }

‏        @keyframes titleGlow {
‏            0%, 100% { filter: brightness(1); }
‏            50% { filter: brightness(1.2); }
        }

‏        .hero-3d {
‏            width: 200px;
‏            height: 200px;
‏            margin: 2rem 0;
‏            position: relative;
        }

‏        .ai-geometric-structure {
‏            width: 100%;
‏            height: 100%;
‏            position: relative;
‏            display: flex;
‏            justify-content: center;
‏            align-items: center;
‏            transform-style: preserve-3d;
        }

‏        .geometric-core {
‏            position: absolute;
‏            width: 120px;
‏            height: 120px;
‏            border: 3px solid #00d4ff;
‏            border-radius: 20px;
‏            background: linear-gradient(45deg, rgba(0, 212, 255, 0.1), rgba(0, 153, 204, 0.2));
‏            backdrop-filter: blur(15px);
‏            animation: coreRotate 8s linear infinite;
‏            transform-style: preserve-3d;
        }

‏        .geometric-ring {
‏            position: absolute;
‏            border: 2px solid rgba(0, 212, 255, 0.6);
‏            border-radius: 50%;
‏            background: transparent;
        }

‏        .ring-1 {
‏            width: 160px;
‏            height: 160px;
‏            top: -20px;
‏            left: -20px;
‏            animation: ringRotate1 6s linear infinite;
‏            border-style: dashed;
        }

‏        .ring-2 {
‏            width: 200px;
‏            height: 200px;
‏            top: -40px;
‏            left: -40px;
‏            animation: ringRotate2 10s linear infinite reverse;
‏            border-style: dotted;
        }

‏        .ring-3 {
‏            width: 240px;
‏            height: 240px;
‏            top: -60px;
‏            left: -60px;
‏            animation: ringRotate3 12s linear infinite;
‏            border-width: 1px;
        }

‏        .neural-node {
‏            position: absolute;
‏            width: 12px;
‏            height: 12px;
‏            background: #00d4ff;
‏            border-radius: 50%;
‏            box-shadow: 0 0 15px rgba(0, 212, 255, 0.8);
‏            animation: nodeGlow 2s ease-in-out infinite alternate;
        }

‏        .node-1 { top: 10px; left: 50%; transform: translateX(-50%); animation-delay: 0s; }
‏        .node-2 { top: 50%; right: 10px; transform: translateY(-50%); animation-delay: 0.3s; }
‏        .node-3 { bottom: 10px; left: 50%; transform: translateX(-50%); animation-delay: 0.6s; }
‏        .node-4 { top: 50%; left: 10px; transform: translateY(-50%); animation-delay: 0.9s; }
‏        .node-5 { top: 25%; right: 25%; animation-delay: 1.2s; }
‏        .node-6 { bottom: 25%; left: 25%; animation-delay: 1.5s; }

‏        .connection-line {
‏            position: absolute;
‏            height: 1px;
‏            background: linear-gradient(90deg, transparent, #00d4ff, transparent);
‏            animation: dataFlow 3s ease-in-out infinite;
        }

‏        .line-1 {
‏            width: 80px;
‏            top: 30px;
‏            left: 20px;
‏            transform: rotate(45deg);
‏            animation-delay: 0s;
        }

‏        .line-2 {
‏            width: 60px;
‏            top: 70px;
‏            right: 30px;
‏            transform: rotate(-30deg);
‏            animation-delay: 0.5s;
        }

‏        .line-3 {
‏            width: 70px;
‏            bottom: 40px;
‏            left: 30px;
‏            transform: rotate(-45deg);
‏            animation-delay: 1s;
        }

‏        .hexagon {
‏            position: absolute;
‏            width: 40px;
‏            height: 40px;
‏            background: rgba(0, 212, 255, 0.2);
‏            border: 1px solid #00d4ff;
‏            clip-path: polygon(50% 0%, 100% 25%, 100% 75%, 50% 100%, 0% 75%, 0% 25%);
‏            animation: hexFloat 4s ease-in-out infinite;
        }

‏        .hex-1 { top: -60px; left: -30px; animation-delay: 0s; }
‏        .hex-2 { top: -30px; right: -60px; animation-delay: 1s; }
‏        .hex-3 { bottom: -60px; right: -30px; animation-delay: 2s; }
‏        .hex-4 { bottom: -30px; left: -60px; animation-delay: 3s; }

‏        @keyframes coreRotate {
‏            0% { transform: rotateX(0deg) rotateY(0deg) rotateZ(0deg); }
‏            100% { transform: rotateX(360deg) rotateY(360deg) rotateZ(360deg); }
        }

‏        @keyframes ringRotate1 {
‏            0% { transform: rotate(0deg); }
‏            100% { transform: rotate(360deg); }
        }

‏        @keyframes ringRotate2 {
‏            0% { transform: rotate(0deg); }
‏            100% { transform: rotate(360deg); }
        }

‏        @keyframes ringRotate3 {
‏            0% { transform: rotate(0deg); }
‏            100% { transform: rotate(360deg); }
        }

‏        @keyframes nodeGlow {
            0% { 
‏                box-shadow: 0 0 15px rgba(0, 212, 255, 0.8);
‏                transform: scale(1);
            }
            100% { 
‏                box-shadow: 0 0 25px rgba(0, 212, 255, 1);
‏                transform: scale(1.2);
            }
        }

‏        @keyframes dataFlow {
‏            0% { opacity: 0; transform: scaleX(0); }
‏            50% { opacity: 1; transform: scaleX(1); }
‏            100% { opacity: 0; transform: scaleX(0); }
        }

‏        @keyframes hexFloat {
            0%, 100% { 
‏                transform: translateY(0) rotate(0deg);
‏                opacity: 0.6;
            }
            50% { 
‏                transform: translateY(-15px) rotate(180deg);
‏                opacity: 1;
            }
        }

‏        .cta-button {
‏            position: relative;
‏            padding: 1rem 2rem;
‏            font-size: 1.2rem;
‏            background: linear-gradient(45deg, #00d4ff, #0099cc);
‏            border: none;
‏            border-radius: 50px;
‏            color: white;
‏            cursor: pointer;
‏            overflow: hidden;
‏            transition: all 0.3s ease;
‏            margin-top: 2rem;
‏            text-decoration: none;
‏            display: inline-block;
        }

‏        .cta-button::before {
‏            content: '';
‏            position: absolute;
‏            top: -50%;
‏            left: -50%;
‏            width: 200%;
‏            height: 200%;
‏            background: conic-gradient(transparent, rgba(255, 255, 255, 0.3), transparent);
‏            animation: rotate 2s linear infinite;
‏            border-radius: 50%;
        }

‏        .cta-button::after {
‏            content: '';
‏            position: absolute;
‏            inset: 3px;
‏            background: linear-gradient(45deg, #00d4ff, #0099cc);
‏            border-radius: 50px;
‏            z-index: -1;
        }

‏        .cta-button:hover {
‏            transform: scale(1.1);
‏            box-shadow: 0 0 30px rgba(0, 212, 255, 0.5);
        }

‏        @keyframes rotate {
‏            0% { transform: rotate(0deg); }
‏            100% { transform: rotate(360deg); }
        }

‏        /* Services Section */
‏        .services {
‏            padding: 5rem 2rem;
‏            max-width: 1200px;
‏            margin: 0 auto;
        }

‏        .section-title {
‏            text-align: center;
‏            font-size: 3rem;
‏            margin-bottom: 3rem;
‏            background: linear-gradient(45deg, #00d4ff, #ffffff);
‏            -webkit-background-clip: text;
‏            -webkit-text-fill-color: transparent;
‏            background-clip: text;
        }

‏        .services-grid {
‏            display: grid;
‏            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
‏            gap: 2rem;
        }

‏        .service-card {
‏            background: rgba(26, 26, 46, 0.8);
‏            border-radius: 15px;
‏            padding: 2rem;
‏            text-align: center;
‏            transition: all 0.5s ease;
‏            transform-style: preserve-3d;
‏            cursor: pointer;
‏            border: 1px solid rgba(0, 212, 255, 0.2);
‏            position: relative;
‏            overflow: hidden;
        }

‏        .service-card::before {
‏            content: '';
‏            position: absolute;
‏            top: 0;
‏            left: -100%;
‏            width: 100%;
‏            height: 100%;
‏            background: linear-gradient(90deg, transparent, rgba(0, 212, 255, 0.2), transparent);
‏            transition: left 0.5s ease;
        }

‏        .service-card:hover::before {
‏            left: 100%;
        }

‏        .service-card:hover {
‏            transform: rotateY(180deg) scale(1.05);
‏            box-shadow: 0 10px 30px rgba(0, 212, 255, 0.3);
        }

‏        .service-card.flipped {
‏            background: linear-gradient(45deg, #00d4ff, #0099cc);
        }

‏        .service-icon {
‏            font-size: 3rem;
‏            margin-bottom: 1rem;
‏            transition: all 0.3s ease;
        }

‏        .service-card:hover .service-icon {
‏            transform: scale(1.2) rotate(360deg);
        }

‏        /* About Section */
‏        .about {
‏            padding: 5rem 2rem;
‏            max-width: 1200px;
‏            margin: 0 auto;
‏            position: relative;
        }

‏        .about-card {
‏            background: rgba(26, 26, 46, 0.8);
‏            border-radius: 15px;
‏            padding: 3rem;
‏            margin-bottom: 2rem;
‏            position: relative;
‏            overflow: hidden;
‏            border: 1px solid rgba(0, 212, 255, 0.2);
‏            cursor: pointer;
‏            transition: all 0.5s ease;
‏            transform-style: preserve-3d;
        }

‏        .about-card::before {
‏            content: '';
‏            position: absolute;
‏            top: -50%;
‏            left: -50%;
‏            width: 200%;
‏            height: 200%;
‏            background: radial-gradient(circle, rgba(0, 212, 255, 0.1) 0%, transparent 70%);
‏            animation: pulse-glow 4s ease-in-out infinite;
‏            transition: all 0.3s ease;
        }

‏        .about-card::after {
‏            content: '';
‏            position: absolute;
‏            top: 0;
‏            left: -100%;
‏            width: 100%;
‏            height: 100%;
‏            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.4), transparent);
‏            transition: left 0.6s ease;
        }

‏        .about-card:hover {
‏            transform: translateY(-10px) rotateX(5deg);
‏            box-shadow: 0 20px 40px rgba(0, 212, 255, 0.4);
‏            border-color: #00d4ff;
        }

‏        .about-card:hover::before {
‏            background: radial-gradient(circle, rgba(0, 212, 255, 0.3) 0%, transparent 70%);
‏            animation-duration: 2s;
        }

‏        .about-card:hover::after {
‏            left: 100%;
        }

‏        .about-card.clicked {
‏            animation: cardFlash 0.6s ease;
        }

‏        @keyframes cardFlash {
            0% { 
‏                box-shadow: 0 0 0 rgba(0, 212, 255, 0.8);
‏                transform: translateY(-10px) rotateX(5deg) scale(1);
            }
            50% { 
‏                box-shadow: 0 0 50px rgba(0, 212, 255, 1);
‏                transform: translateY(-15px) rotateX(8deg) scale(1.05);
            }
            100% { 
‏                box-shadow: 0 20px 40px rgba(0, 212, 255, 0.4);
‏                transform: translateY(-10px) rotateX(5deg) scale(1);
            }
        }

‏        @keyframes pulse-glow {
‏            0%, 100% { transform: scale(0.8); opacity: 0.5; }
‏            50% { transform: scale(1.2); opacity: 0.8; }
        }

‏        /* Achievements Section */
‏        .achievements {
‏            padding: 5rem 2rem;
‏            max-width: 1200px;
‏            margin: 0 auto;
        }

‏        .achievements-grid {
‏            display: grid;
‏            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
‏            gap: 2rem;
        }

‏        .achievement-card {
‏            background: rgba(26, 26, 46, 0.8);
‏            border-radius: 15px;
‏            padding: 2rem;
‏            text-align: center;
‏            position: relative;
‏            overflow: hidden;
‏            border: 1px solid rgba(0, 212, 255, 0.2);
        }

‏        .achievement-number {
‏            font-size: 3rem;
‏            font-weight: bold;
‏            color: #00d4ff;
‏            margin-bottom: 1rem;
        }

‏        .progress-bar {
‏            width: 100%;
‏            height: 4px;
‏            background: rgba(0, 212, 255, 0.2);
‏            border-radius: 2px;
‏            margin-top: 1rem;
‏            overflow: hidden;
        }

‏        .progress-fill {
‏            height: 100%;
‏            background: linear-gradient(45deg, #00d4ff, #0099cc);
‏            width: 0%;
‏            transition: width 2s ease;
‏            border-radius: 2px;
        }

‏        /* Testimonials */
‏        .testimonials {
‏            padding: 5rem 2rem;
‏            max-width: 1200px;
‏            margin: 0 auto;
‏            position: relative;
        }

‏        .testimonials-slider {
‏            position: relative;
‏            overflow: hidden;
‏            border-radius: 15px;
        }

‏        .testimonial-slide {
‏            background: rgba(26, 26, 46, 0.8);
‏            padding: 3rem;
‏            text-align: center;
‏            border-radius: 15px;
‏            margin: 1rem;
‏            border: 1px solid rgba(0, 212, 255, 0.2);
‏            display: none;
        }

‏        .testimonial-slide.active {
‏            display: block;
‏            animation: slideIn 0.5s ease;
        }

‏        @keyframes slideIn {
‏            from { opacity: 0; transform: translateX(50px); }
‏            to { opacity: 1; transform: translateX(0); }
        }

‏        /* Floating Icons */
‏        .floating-icons {
‏            position: absolute;
‏            width: 100%;
‏            height: 100%;
‏            pointer-events: none;
‏            overflow: hidden;
        }

‏        .floating-icon {
‏            position: absolute;
‏            font-size: 2rem;
‏            color: rgba(0, 212, 255, 0.3);
‏            animation: float 6s ease-in-out infinite;
        }

‏        .floating-icon:nth-child(1) { left: 10%; animation-delay: 0s; }
‏        .floating-icon:nth-child(2) { left: 20%; animation-delay: 1s; }
‏        .floating-icon:nth-child(3) { left: 30%; animation-delay: 2s; }
‏        .floating-icon:nth-child(4) { left: 40%; animation-delay: 3s; }
‏        .floating-icon:nth-child(5) { left: 50%; animation-delay: 4s; }
‏        .floating-icon:nth-child(6) { left: 60%; animation-delay: 5s; }

‏        @keyframes float {
‏            0%, 100% { transform: translateY(100vh) rotate(0deg); }
‏            50% { transform: translateY(-100px) rotate(180deg); }
        }

‏        /* Contact Section */
‏        .contact {
‏            padding: 5rem 2rem;
‏            max-width: 1200px;
‏            margin: 0 auto;
‏            text-align: center;
        }

‏        .contact-button {
‏            padding: 1.5rem 3rem;
‏            font-size: 1.3rem;
‏            background: linear-gradient(45deg, #00d4ff, #0099cc);
‏            border: none;
‏            border-radius: 50px;
‏            color: white;
‏            cursor: pointer;
‏            transition: all 0.3s ease;
‏            position: relative;
‏            overflow: hidden;
‏            text-decoration: none;
‏            display: inline-block;
        }

‏        .contact-button:hover {
‏            transform: scale(1.1);
‏            box-shadow: 0 0 30px rgba(0, 212, 255, 0.5);
        }

‏        /* Footer */
‏        .footer {
‏            background: rgba(10, 10, 10, 0.9);
‏            padding: 3rem 2rem 1rem;
‏            text-align: center;
        }

‏        .footer-links {
‏            display: flex;
‏            justify-content: center;
‏            gap: 2rem;
‏            margin-bottom: 2rem;
‏            flex-wrap: wrap;
        }

‏        .footer-link {
‏            color: #ffffff;
‏            text-decoration: none;
‏            transition: all 0.3s ease;
        }

‏        .footer-link:hover {
‏            color: #00d4ff;
‏            transform: translateY(-2px);
        }

‏        /* WhatsApp Button */
‏        .whatsapp-float {
‏            position: fixed;
‏            width: 60px;
‏            height: 60px;
‏            bottom: 40px;
‏            right: 40px;
‏            background: #25d366;
‏            color: white;
‏            border-radius: 50px;
‏            text-align: center;
‏            font-size: 30px;
‏            box-shadow: 2px 2px 3px #999;
‏            z-index: 1000;
‏            transition: all 0.3s ease;
‏            display: flex;
‏            align-items: center;
‏            justify-content: center;
‏            text-decoration: none;
        }

‏        .whatsapp-float:hover {
‏            transform: scale(1.1);
‏            box-shadow: 0 0 20px rgba(37, 211, 102, 0.5);
        }

‏        /* Responsive */
‏        @media (max-width: 768px) {
‏            .hero-title {
‏                font-size: 2.5rem;
            }
            
‏            .nav-menu {
‏                display: none;
            }
            
‏            .services-grid {
‏                grid-template-columns: 1fr;
            }
            
‏            .achievements-grid {
‏                grid-template-columns: repeat(2, 1fr);
            }
            
‏            .top-dropdown-content {
‏                grid-template-columns: repeat(2, 1fr);
‏                gap: 0.6rem;
‏                padding: 0.8rem 1rem;
            }
            
‏            .top-dropdown-item {
‏                padding: 0.6rem 1rem;
‏                font-size: 0.85rem;
‏                min-width: 140px;
            }
        }

‏        @media (max-width: 480px) {
‏            .top-dropdown-content {
‏                grid-template-columns: 1fr;
‏                gap: 0.5rem;
‏                padding: 0.6rem 0.8rem;
            }
            
‏            .top-dropdown-item {
‏                padding: 0.7rem 1.2rem;
‏                font-size: 0.9rem;
‏                min-width: auto;
‏                width: 100%;
‏                max-width: 280px;
            }
        }
‏    </style>
‏  <style>@view-transition { navigation: auto; }</style>
‏  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
‏  <script src="https://cdn.tailwindcss.com" type="text/javascript"></script>
‏ </head>
‏ <body><!-- Loading Screen -->
‏  <div class="loading-screen" id="loadingScreen">
‏   <div class="loading-content">
‏    <div class="loading-logo">
‏     XSora
‏    </div>
‏    <div class="loading-spinner"></div>
‏   </div>
‏  </div><!-- Top Dropdown Menu -->
‏  <div class="top-dropdown" id="topDropdown">
‏   <div class="top-dropdown-content"><a href="#home" class="top-dropdown-item">🏠 الرئيسية</a> <a href="#services" class="top-dropdown-item">⚙️ الخدمات</a> <a href="#about" class="top-dropdown-item">🏢 عن الشركة</a> <a href="#achievements" class="top-dropdown-item">🏆 الإنجازات</a> <a href="#testimonials" class="top-dropdown-item">💬 آراء العملاء</a> <a href="https://api.whatsapp.com/send?phone=966564661495" target="_blank" rel="noopener noreferrer" class="top-dropdown-item">📱 ابدأ مشروعك</a> <a href="https://fanlnk.to/CompanyLink" target="_blank" rel="noopener noreferrer" class="top-dropdown-item">📞 تواصل معنا</a>
‏   </div>
‏  </div><!-- Dropdown Toggle Button -->
‏  <div class="dropdown-toggle" id="dropdownToggle" onclick="toggleTopDropdown()"><span></span> <span></span> <span></span>
‏  </div><!-- Navigation -->
‏  <nav class="navbar">
‏   <div class="nav-container">
‏    <div class="logo" id="companyName">
‏     XSora
‏    </div>
‏    <ul class="nav-menu">
‏     <li class="nav-item"><a href="#home" class="nav-link">الرئيسية</a></li>
‏     <li class="nav-item"><a href="#services" class="nav-link">الخدمات</a>
‏      <div class="dropdown"><a href="#" class="dropdown-item">تصميم المواقع</a> <a href="#" class="dropdown-item">الذكاء الاصطناعي</a> <a href="#" class="dropdown-item">التسويق الرقمي</a>
‏      </div></li>
‏     <li class="nav-item"><a href="#about" class="nav-link">عن الشركة</a></li>
‏     <li class="nav-item"><a href="#contact" class="nav-link">تواصل معنا</a></li>
‏    </ul>
‏   </div>
‏  </nav><!-- Hero Section -->
‏  <section class="hero" id="home">
‏   <h1 class="hero-title" id="heroTitle">نصمم المستقبل<br>
    ونبرمج التجربة</h1>
‏   <div class="hero-3d">
‏    <div class="ai-geometric-structure">
‏     <div class="geometric-core">
‏      <div class="neural-node node-1"></div>
‏      <div class="neural-node node-2"></div>
‏      <div class="neural-node node-3"></div>
‏      <div class="neural-node node-4"></div>
‏      <div class="neural-node node-5"></div>
‏      <div class="neural-node node-6"></div>
‏      <div class="connection-line line-1"></div>
‏      <div class="connection-line line-2"></div>
‏      <div class="connection-line line-3"></div>
‏     </div>
‏     <div class="geometric-ring ring-1"></div>
‏     <div class="geometric-ring ring-2"></div>
‏     <div class="geometric-ring ring-3"></div>
‏     <div class="hexagon hex-1"></div>
‏     <div class="hexagon hex-2"></div>
‏     <div class="hexagon hex-3"></div>
‏     <div class="hexagon hex-4"></div>
‏    </div>
‏   </div><a href="https://api.whatsapp.com/send?phone=966564661495" target="_blank" rel="noopener noreferrer" class="cta-button" id="ctaButton"> <span id="ctaButtonText">ابدأ مشروعك</span> </a>
‏  </section><!-- Services Section -->
‏  <section class="services" id="services">
‏   <h2 class="section-title">خدماتنا</h2>
‏   <div class="services-grid">
‏    <div class="service-card" onclick="toggleCard(this)">
‏     <div class="service-icon">
      🌐
‏     </div>
‏     <h3>تصميم المواقع الذكية</h3>
‏     <p>نصمم مواقع ويب متطورة وذكية تجمع بين الجمال والوظائف المتقدمة</p>
‏    </div>
‏    <div class="service-card" onclick="toggleCard(this)">
‏     <div class="service-icon">
      🎨
‏     </div>
‏     <h3>تصميم الجرافيك والهويات البصرية</h3>
‏     <p>نبتكر هويات بصرية مميزة تعكس شخصية علامتك التجارية</p>
‏    </div>
‏    <div class="service-card" onclick="toggleCard(this)">
‏     <div class="service-icon">
      🤖
‏     </div>
‏     <h3>حلول الذكاء الاصطناعي في التسويق</h3>
‏     <p>نستخدم أحدث تقنيات الذكاء الاصطناعي لتحسين استراتيجيات التسويق</p>
‏    </div>
‏    <div class="service-card" onclick="toggleCard(this)">
‏     <div class="service-icon">
      📢
‏     </div>
‏     <h3>الحملات الإعلانية الموجهة</h3>
‏     <p>نصمم حملات إعلانية مستهدفة تحقق أفضل النتائج</p>
‏    </div>
‏    <div class="service-card" onclick="toggleCard(this)">
‏     <div class="service-icon">
      🏢
‏     </div>
‏     <h3>تطوير العلامات التجارية</h3>
‏     <p>نساعدك في بناء وتطوير علامة تجارية قوية ومؤثرة</p>
‏    </div>
‏   </div>
‏  </section><!-- About Section -->
‏  <section class="about" id="about">
‏   <h2 class="section-title">عن الشركة</h2>
‏   <div class="about-card" onclick="flashCard(this)">
‏    <h3>من نحن</h3>
‏    <p>شركة XSora هي شركة رائدة في مجال التكنولوجيا والذكاء الاصطناعي، نجمع بين الإبداع والتقنية لتقديم حلول مبتكرة تلبي احتياجات عملائنا وتتجاوز توقعاتهم.</p>
‏   </div>
‏   <div class="about-card" onclick="flashCard(this)">
‏    <h3>رسالتنا</h3>
‏    <p>نسعى لتمكين الشركات والأفراد من خلال تقديم حلول تقنية متطورة تساعدهم على تحقيق أهدافهم وبناء مستقبل رقمي مشرق.</p>
‏   </div>
‏   <div class="about-card" onclick="flashCard(this)">
‏    <h3>قيمنا</h3>
‏    <p>الإبداع، الجودة، الشفافية، والالتزام بالمواعيد هي القيم الأساسية التي نؤمن بها ونطبقها في جميع مشاريعنا.</p>
‏   </div>
‏   <div class="about-card" onclick="flashCard(this)">
‏    <h3>فلسفتنا</h3>
‏    <p>نؤمن بأن التكنولوجيا يجب أن تكون في خدمة الإنسان، ولذلك نركز على تطوير حلول تقنية سهلة الاستخدام وتحقق قيمة حقيقية لمستخدميها.</p>
‏   </div>
‏  </section><!-- Achievements Section -->
‏  <section class="achievements" id="achievements">
‏   <h2 class="section-title">إنجازاتنا</h2>
‏   <div class="achievements-grid">
‏    <div class="achievement-card">
‏     <div class="achievement-number" data-target="12">
      0
‏     </div>
‏     <p>سنة خبرة</p>
‏     <div class="progress-bar">
‏      <div class="progress-fill"></div>
‏     </div>
‏    </div>
‏    <div class="achievement-card">
‏     <div class="achievement-number" data-target="1200">
      0
‏     </div>
‏     <p>عميل</p>
‏     <div class="progress-bar">
‏      <div class="progress-fill"></div>
‏     </div>
‏    </div>
‏    <div class="achievement-card">
‏     <div class="achievement-number" data-target="800">
      0
‏     </div>
‏     <p>مشروع ناجح</p>
‏     <div class="progress-bar">
‏      <div class="progress-fill"></div>
‏     </div>
‏    </div>
‏    <div class="achievement-card">
‏     <div class="achievement-number" data-target="98">
      0
‏     </div>
‏     <p>% رضا العملاء</p>
‏     <div class="progress-bar">
‏      <div class="progress-fill"></div>
‏     </div>
‏    </div>
‏   </div>
‏  </section><!-- Testimonials Section -->
‏  <section class="testimonials" id="testimonials">
‏   <h2 class="section-title">آراء العملاء</h2>
‏   <div class="testimonials-slider">
‏    <div class="testimonial-slide active">
‏     <p>"تعاملت مع شركة XSora في مشروع تطوير واجهة موقعنا، وكانت التجربة أكثر من رائعة. دقة في التنفيذ، واحترافية في التواصل، والأهم أنهم يفهمون الفكرة قبل أن تبدأ في شرحها!"</p>
‏     <h4>- نورة الحربي، السعودية</h4>
‏    </div>
‏    <div class="testimonial-slide">
‏     <p>"شركة تجمع بين الذكاء التقني والذوق الإبداعي. لاحظت اهتمامهم بأدق التفاصيل، والنتائج فاقت توقعاتي من حيث السرعة والجودة."</p>
‏     <h4>- محمد الزهراني، الإمارات</h4>
‏    </div>
‏    <div class="testimonial-slide">
‏     <p>"فريق XSora يعرف كيف يحول الأفكار إلى تجربة بصرية متكاملة. شكر خاص لهم على التزامهم بالمواعيد وحرصهم على راحة العميل طوال فترة العمل."</p>
‏     <h4>- لينا خالد، قطر</h4>
‏    </div>
‏    <div class="testimonial-slide">
‏     <p>"الاحتراف واضح من أول تواصل معهم. قدموا لي استشارات تقنية ساعدتني في إعادة هيكلة موقعي بالكامل بطريقة ذكية وسهلة الإدارة."</p>
‏     <h4>- أحمد بخيت، مصر</h4>
‏    </div>
‏    <div class="testimonial-slide">
‏     <p>"تعاملت مع أكثر من شركة من قبل، لكن XSora كانت مختلفة تمامًا. اهتمامهم بالتجربة الرقمية جعلني أثق بهم كمستشار دائم لمشاريعي المستقبلية."</p>
‏     <h4>- ريم القحطاني، السعودية</h4>
‏    </div>
‏    <div class="testimonial-slide">
‏     <p>"أعجبني كيف أن فريق XSora يجمع بين التصميم الجمالي والجانب التقني المتقدم. النتيجة كانت مشروعاً يعكس هوية شركتنا بدقة."</p>
‏     <h4>- خالد الشمري، الكويت</h4>
‏    </div>
‏    <div class="testimonial-slide">
‏     <p>"خدمة العملاء عندهم استثنائية. تجاوب سريع، متابعة مستمرة، وتنفيذ احترافي يثبت أنهم يهتمون بالنتائج أكثر من الكلمات."</p>
‏     <h4>- سارة العتيبي، البحرين</h4>
‏    </div>
‏   </div>
‏  </section><!-- Floating Icons -->
‏  <div class="floating-icons">
‏   <div class="floating-icon">
    💻
‏   </div>
‏   <div class="floating-icon">
    🚀
‏   </div>
‏   <div class="floating-icon">
    ⚡
‏   </div>
‏   <div class="floating-icon">
    🎨
‏   </div>
‏   <div class="floating-icon">
    🤖
‏   </div>
‏   <div class="floating-icon">
    ✨
‏   </div>
‏  </div><!-- Contact Section -->
‏  <section class="contact" id="contact">
‏   <h2 class="section-title">تواصل معنا</h2>
‏   <p>هل أنت مستعد لبدء مشروعك التالي؟ تواصل معنا الآن!</p><a href="https://fanlnk.to/CompanyLink" target="_blank" rel="noopener noreferrer" class="contact-button"> تواصل معنا الآن </a>
‏  </section><!-- Footer -->
‏  <footer class="footer">
‏   <div class="footer-links"><a href="#home" class="footer-link">الرئيسية</a> <a href="#services" class="footer-link">الخدمات</a> <a href="#about" class="footer-link">عن الشركة</a> <a href="#contact" class="footer-link">تواصل معنا</a>
‏   </div>
‏   <p>جميع الحقوق محفوظة لشركة XSora © 2024</p>
‏   <p>مصمم الموقع: <a href="https://api.whatsapp.com/send?phone=966564661495" target="_blank" rel="noopener noreferrer" style="color: #00d4ff; text-decoration: none;" id="designerName">فوزية خالد</a></p>
‏  </footer><!-- WhatsApp Float Button --> <a href="https://api.whatsapp.com/send?phone=966564661495" target="_blank" rel="noopener noreferrer" class="whatsapp-float" title="تواصل معنا عبر الواتساب"> 📱 </a>
‏  <script>
‏        // Default configuration
‏        const defaultConfig = {
‏            company_name: "XSora",
‏            hero_title: "نصمم المستقبل\nونبرمج التجربة",
‏            cta_button: "ابدأ مشروعك",
‏            designer_name: "فوزية خالد"
        };

‏        // Loading screen
‏        window.addEventListener('load', function() {
‏            setTimeout(() => {
‏                document.getElementById('loadingScreen').style.opacity = '0';
‏                setTimeout(() => {
‏                    document.getElementById('loadingScreen').style.display = 'none';
                }, 500);
            }, 2000);
        });

‏        // Top dropdown toggle
‏        function toggleTopDropdown() {
‏            const dropdown = document.getElementById('topDropdown');
‏            const toggle = document.getElementById('dropdownToggle');
            
‏            dropdown.classList.toggle('active');
‏            toggle.classList.toggle('active');
        }

‏        // Close dropdown when clicking on menu items
‏        document.querySelectorAll('.top-dropdown-item').forEach(item => {
‏            item.addEventListener('click', () => {
‏                const dropdown = document.getElementById('topDropdown');
‏                const toggle = document.getElementById('dropdownToggle');
                
‏                dropdown.classList.remove('active');
‏                toggle.classList.remove('active');
            });
        });

‏        // Close dropdown when clicking outside
‏        document.addEventListener('click', function(event) {
‏            const dropdown = document.getElementById('topDropdown');
‏            const toggle = document.getElementById('dropdownToggle');
            
‏            if (!dropdown.contains(event.target) && !toggle.contains(event.target)) {
‏                dropdown.classList.remove('active');
‏                toggle.classList.remove('active');
            }
        });

‏        // Service card toggle
‏        function toggleCard(card) {
‏            card.classList.toggle('flipped');
‏            setTimeout(() => {
‏                card.classList.remove('flipped');
            }, 2000);
        }

‏        // Counter animation
‏        function animateCounters() {
‏            const counters = document.querySelectorAll('.achievement-number');
‏            const progressBars = document.querySelectorAll('.progress-fill');
            
‏            counters.forEach((counter, index) => {
‏                const target = parseInt(counter.getAttribute('data-target'));
‏                const increment = target / 100;
‏                let current = 0;
                
‏                const timer = setInterval(() => {
‏                    current += increment;
‏                    if (current >= target) {
‏                        current = target;
‏                        clearInterval(timer);
                    }
‏                    counter.textContent = Math.floor(current) + (target === 98 ? '' : '+');
                }, 20);
                
‏                // Animate progress bar
‏                setTimeout(() => {
‏                    progressBars[index].style.width = '100%';
‏                }, index * 200);
            });
        }

‏        // Testimonials slider
‏        let currentTestimonial = 0;
‏        const testimonials = document.querySelectorAll('.testimonial-slide');
        
‏        function showNextTestimonial() {
‏            testimonials[currentTestimonial].classList.remove('active');
‏            currentTestimonial = (currentTestimonial + 1) % testimonials.length;
‏            testimonials[currentTestimonial].classList.add('active');
        }
        
‏        setInterval(showNextTestimonial, 4000);

‏        // Intersection Observer for animations
‏        const observer = new IntersectionObserver((entries) => {
‏            entries.forEach(entry => {
‏                if (entry.isIntersecting) {
‏                    if (entry.target.id === 'achievements') {
‏                        animateCounters();
                    }
                }
            });
        });

‏        observer.observe(document.getElementById('achievements'));

‏        // WhatsApp and Links functions
‏        function openWhatsApp() {
‏            const whatsappUrl = 'https://api.whatsapp.com/send?phone=966564661495';
‏            window.open(whatsappUrl, '_blank', 'noopener,noreferrer');
        }

‏        function openDesignerWhatsApp() {
‏            const whatsappUrl = 'https://api.whatsapp.com/send?phone=966564661495';
‏            window.open(whatsappUrl, '_blank', 'noopener,noreferrer');
        }

‏        function openCompanyLink() {
‏            window.open('https://fanlnk.to/CompanyLink', '_blank', 'noopener,noreferrer');
        }

‏        // Flash card function
‏        function flashCard(card) {
‏            card.classList.add('clicked');
‏            setTimeout(() => {
‏                card.classList.remove('clicked');
            }, 600);
        }

‏        // Smooth scrolling
‏        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
‏            anchor.addEventListener('click', function (e) {
‏                e.preventDefault();
‏                const target = document.querySelector(this.getAttribute('href'));
‏                if (target) {
‏                    target.scrollIntoView({
‏                        behavior: 'smooth',
‏                        block: 'start'
                    });
                }
            });
        });

‏        // Element SDK Integration
‏        if (window.elementSdk) {
‏            window.elementSdk.init({
‏                defaultConfig: defaultConfig,
‏                onConfigChange: async (config) => {
‏                    // Update company name
‏                    const companyNameEl = document.getElementById('companyName');
‏                    if (companyNameEl) {
‏                        companyNameEl.textContent = config.company_name || defaultConfig.
