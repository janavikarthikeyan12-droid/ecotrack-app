# ecotrack-app
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>EcoTrack - Your Green Journey</title>
    <style>
        body {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
            background: linear-gradient(135deg, #ecfdf5 0%, #d1fae5 100%);
            color: #065f46;
            height: 100%;
        }
        
        html {
            height: 100%;
        }
        
        /* Splash Screen Styles */
        .splash-screen {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(135deg, #10b981 0%, #059669 50%, #047857 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 9999;
            animation: splashFadeOut 0.5s ease-in-out 2.5s forwards;
        }
        
        .splash-content {
            text-align: center;
            color: white;
            animation: splashContentIn 1s ease-out;
        }
        
        .splash-logo {
            margin-bottom: 32px;
        }
        
        .logo-circle {
            width: 120px;
            height: 120px;
            background: rgba(255, 255, 255, 0.2);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto;
            backdrop-filter: blur(10px);
            border: 3px solid rgba(255, 255, 255, 0.3);
            animation: logoFloat 2s ease-in-out infinite;
        }
        
        .logo-icon {
            font-size: 48px;
        }
        
        .splash-title {
            font-size: 48px;
            font-weight: 800;
            margin: 0 0 16px 0;
            letter-spacing: -1px;
            animation: titleSlideUp 0.8s ease-out 0.3s both;
        }
        
        .splash-subtitle {
            font-size: 18px;
            opacity: 0.9;
            margin: 0 0 40px 0;
            font-weight: 500;
            animation: subtitleSlideUp 0.8s ease-out 0.5s both;
        }
        
        .loading-dots {
            display: flex;
            justify-content: center;
            gap: 8px;
            animation: dotsAppear 0.8s ease-out 0.7s both;
        }
        
        .dot {
            width: 12px;
            height: 12px;
            background: rgba(255, 255, 255, 0.8);
            border-radius: 50%;
            animation: dotBounce 1.4s ease-in-out infinite;
        }
        
        .dot:nth-child(1) { animation-delay: 0s; }
        .dot:nth-child(2) { animation-delay: 0.2s; }
        .dot:nth-child(3) { animation-delay: 0.4s; }
        
        @keyframes splashFadeOut {
            0% { opacity: 1; transform: scale(1); }
            100% { opacity: 0; transform: scale(1.1); display: none; }
        }
        
        @keyframes splashContentIn {
            0% { opacity: 0; transform: translateY(30px); }
            100% { opacity: 1; transform: translateY(0); }
        }
        
        @keyframes logoFloat {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }
        
        @keyframes titleSlideUp {
            0% { opacity: 0; transform: translateY(30px); }
            100% { opacity: 1; transform: translateY(0); }
        }
        
        @keyframes subtitleSlideUp {
            0% { opacity: 0; transform: translateY(20px); }
            100% { opacity: 0.9; transform: translateY(0); }
        }
        
        @keyframes dotsAppear {
            0% { opacity: 0; transform: translateY(10px); }
            100% { opacity: 1; transform: translateY(0); }
        }
        
        @keyframes dotBounce {
            0%, 80%, 100% { transform: scale(0.8); opacity: 0.5; }
            40% { transform: scale(1.2); opacity: 1; }
        }
        
        @keyframes fadeInUp {
            0% { opacity: 0; transform: translateY(30px); }
            100% { opacity: 1; transform: translateY(0); }
        }
        
        .app-container {
            max-width: 414px;
            margin: 0 auto;
            background: white;
            min-height: 100%;
            box-shadow: 0 0 40px rgba(0, 0, 0, 0.1);
            position: relative;
        }
        
        .header {
            background: linear-gradient(135deg, #10b981 0%, #059669 100%);
            color: white;
            padding: 60px 24px 24px;
            text-align: center;
            position: relative;
        }
        
        .header h1 {
            margin: 0;
            font-size: 28px;
            font-weight: 800;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }
        
        .points-display {
            background: rgba(255, 255, 255, 0.2);
            border-radius: 20px;
            padding: 12px 20px;
            margin-top: 16px;
            display: inline-block;
            backdrop-filter: blur(10px);
        }
        
        .points-display .points {
            font-size: 24px;
            font-weight: 700;
        }
        
        .points-display .label {
            font-size: 14px;
            opacity: 0.9;
        }
        
        .nav-tabs {
            display: flex;
            background: white;
            border-bottom: 1px solid #e5e7eb;
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        .nav-tab {
            flex: 1;
            padding: 16px 8px;
            text-align: center;
            background: none;
            border: none;
            font-size: 14px;
            font-weight: 600;
            color: #6b7280;
            cursor: pointer;
            transition: all 0.3s ease;
            border-bottom: 3px solid transparent;
        }
        
        .nav-tab.active {
            color: #10b981;
            border-bottom-color: #10b981;
        }
        
        .tab-content {
            display: none;
            padding: 24px;
            min-height: 400px;
        }
        
        .tab-content.active {
            display: block;
        }
        
        /* Daily Actions Tab */
        .action-item {
            background: #f9fafb;
            border-radius: 16px;
            padding: 20px;
            margin-bottom: 16px;
            display: flex;
            align-items: center;
            gap: 16px;
            transition: all 0.3s ease;
            border: 2px solid transparent;
        }
        
        .action-item.completed {
            background: #ecfdf5;
            border-color: #10b981;
        }
        
        .action-item.verified {
            background: linear-gradient(135deg, #ecfdf5 0%, #d1fae5 100%);
            border-color: #10b981;
            box-shadow: 0 4px 12px rgba(16, 185, 129, 0.2);
        }
        
        .verify-btn {
            background: #3b82f6;
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            margin-top: 8px;
        }
        
        .verify-btn:hover {
            background: #2563eb;
            transform: scale(1.05);
        }
        
        .verify-btn.verified {
            background: #10b981;
            cursor: default;
        }
        
        .verify-btn.verified:hover {
            transform: none;
        }
        
        .photo-upload {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0, 0, 0, 0.8);
            display: none;
            align-items: center;
            justify-content: center;
            z-index: 3000;
        }
        
        .photo-upload.show {
            display: flex;
        }
        
        .upload-modal {
            background: white;
            border-radius: 20px;
            padding: 32px;
            max-width: 350px;
            width: 90%;
            text-align: center;
        }
        
        .upload-header {
            margin-bottom: 24px;
        }
        
        .upload-title {
            font-size: 24px;
            font-weight: 700;
            margin: 0 0 8px 0;
            color: #111827;
        }
        
        .upload-subtitle {
            color: #6b7280;
            margin: 0;
        }
        
        .upload-area {
            border: 2px dashed #d1d5db;
            border-radius: 12px;
            padding: 32px 16px;
            margin-bottom: 24px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .upload-area:hover {
            border-color: #10b981;
            background: #f9fafb;
        }
        
        .upload-area.dragover {
            border-color: #10b981;
            background: #ecfdf5;
        }
        
        .upload-icon {
            font-size: 48px;
            margin-bottom: 16px;
            color: #6b7280;
        }
        
        .upload-text {
            font-size: 16px;
            font-weight: 600;
            color: #374151;
            margin-bottom: 8px;
        }
        
        .upload-hint {
            font-size: 14px;
            color: #6b7280;
        }
        
        .upload-actions {
            display: flex;
            gap: 12px;
        }
        
        .upload-btn {
            flex: 1;
            padding: 12px 24px;
            border-radius: 25px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            border: none;
        }
        
        .upload-btn.primary {
            background: #10b981;
            color: white;
        }
        
        .upload-btn.primary:hover {
            background: #059669;
        }
        
        .upload-btn.secondary {
            background: #f3f4f6;
            color: #6b7280;
        }
        
        .upload-btn.secondary:hover {
            background: #e5e7eb;
        }
        
        .preview-image {
            max-width: 100%;
            max-height: 200px;
            border-radius: 8px;
            margin-bottom: 16px;
        }
        
        .verification-badge {
            display: inline-flex;
            align-items: center;
            gap: 4px;
            background: #10b981;
            color: white;
            padding: 4px 8px;
            border-radius: 12px;
            font-size: 12px;
            font-weight: 600;
            margin-top: 4px;
        }
        
        .daily-reset-info {
            background: #fef3c7;
            border: 1px solid #f59e0b;
            border-radius: 12px;
            padding: 16px;
            margin-bottom: 24px;
            text-align: center;
        }
        
        .daily-reset-info .icon {
            font-size: 24px;
            margin-bottom: 8px;
        }
        
        .daily-reset-info .title {
            font-size: 16px;
            font-weight: 600;
            color: #92400e;
            margin-bottom: 4px;
        }
        
        .daily-reset-info .subtitle {
            font-size: 14px;
            color: #b45309;
        }
        
        .action-checkbox {
            width: 24px;
            height: 24px;
            border: 2px solid #d1d5db;
            border-radius: 6px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s ease;
            flex-shrink: 0;
        }
        
        .action-checkbox.checked {
            background: #10b981;
            border-color: #10b981;
            color: white;
        }
        
        .action-content {
            flex: 1;
        }
        
        .action-title {
            font-weight: 600;
            margin-bottom: 4px;
        }
        
        .action-points {
            font-size: 14px;
            color: #10b981;
            font-weight: 600;
        }
        
        .action-icon {
            font-size: 24px;
            flex-shrink: 0;
        }
        
        /* Leaderboard Tab */
        .leaderboard-item {
            display: flex;
            align-items: center;
            gap: 16px;
            padding: 16px;
            background: #f9fafb;
            border-radius: 12px;
            margin-bottom: 12px;
        }
        
        .leaderboard-item.current-user {
            background: #ecfdf5;
            border: 2px solid #10b981;
        }
        
        .rank {
            width: 32px;
            height: 32px;
            border-radius: 50%;
            background: #10b981;
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
            flex-shrink: 0;
        }
        
        .rank.gold { background: #f59e0b; }
        .rank.silver { background: #6b7280; }
        .rank.bronze { background: #d97706; }
        
        .user-info {
            flex: 1;
        }
        
        .user-name {
            font-weight: 600;
            margin-bottom: 2px;
        }
        
        .user-level {
            font-size: 12px;
            color: #6b7280;
        }
        
        .user-points {
            font-weight: 700;
            color: #10b981;
        }
        
        /* Tips Tab */
        .tip-card {
            background: linear-gradient(135deg, #10b981 0%, #059669 100%);
            color: white;
            border-radius: 20px;
            padding: 24px;
            margin-bottom: 16px;
            position: relative;
            overflow: hidden;
        }
        
        .tip-card::before {
            content: '';
            position: absolute;
            top: -50%;
            right: -50%;
            width: 100px;
            height: 100px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
        }
        
        .tip-title {
            font-size: 18px;
            font-weight: 700;
            margin-bottom: 12px;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .tip-content {
            line-height: 1.6;
            opacity: 0.95;
        }
        
        .tip-category {
            display: inline-block;
            background: rgba(255, 255, 255, 0.2);
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 12px;
            margin-top: 12px;
        }
        
        /* Progress Tab */
        .progress-header {
            text-align: center;
            margin-bottom: 32px;
        }
        
        .progress-title {
            font-size: 24px;
            font-weight: 700;
            margin-bottom: 8px;
        }
        
        .progress-subtitle {
            color: #6b7280;
        }
        
        .chart-container {
            background: #f9fafb;
            border-radius: 16px;
            padding: 24px;
            margin-bottom: 24px;
        }
        
        .chart {
            display: flex;
            align-items: end;
            gap: 8px;
            height: 200px;
            margin-bottom: 16px;
        }
        
        .chart-bar {
            flex: 1;
            background: #10b981;
            border-radius: 4px 4px 0 0;
            position: relative;
            transition: all 0.3s ease;
            cursor: pointer;
        }
        
        .chart-bar:hover {
            background: #059669;
        }
        
        .chart-bar::after {
            content: attr(data-value);
            position: absolute;
            top: -24px;
            left: 50%;
            transform: translateX(-50%);
            font-size: 12px;
            font-weight: 600;
            color: #374151;
        }
        
        .chart-labels {
            display: flex;
            gap: 8px;
        }
        
        .chart-label {
            flex: 1;
            text-align: center;
            font-size: 12px;
            color: #6b7280;
            font-weight: 500;
        }
        
        .stats-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 16px;
        }
        
        .stat-card {
            background: white;
            border-radius: 12px;
            padding: 20px;
            text-align: center;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
        }
        
        .stat-icon {
            font-size: 32px;
            margin-bottom: 8px;
        }
        
        .stat-value {
            font-size: 24px;
            font-weight: 700;
            color: #10b981;
            margin-bottom: 4px;
        }
        
        .stat-label {
            font-size: 14px;
            color: #6b7280;
        }
        
        .floating-action {
            position: fixed;
            bottom: 24px;
            right: 24px;
            width: 56px;
            height: 56px;
            background: #10b981;
            border-radius: 50%;
            border: none;
            color: white;
            font-size: 24px;
            cursor: pointer;
            box-shadow: 0 8px 24px rgba(16, 185, 129, 0.4);
            transition: all 0.3s ease;
            z-index: 1000;
        }
        
        .floating-action:hover {
            transform: scale(1.1);
            box-shadow: 0 12px 32px rgba(16, 185, 129, 0.5);
        }
        
        .celebration {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: white;
            border-radius: 20px;
            padding: 32px;
            text-align: center;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
            z-index: 2000;
            display: none;
        }
        
        .celebration.show {
            display: block;
            animation: celebrationPop 0.5s ease-out;
        }
        
        @keyframes celebrationPop {
            0% { transform: translate(-50%, -50%) scale(0.8); opacity: 0; }
            100% { transform: translate(-50%, -50%) scale(1); opacity: 1; }
        }
        
        .celebration-icon {
            font-size: 64px;
            margin-bottom: 16px;
        }
        
        .celebration-text {
            font-size: 20px;
            font-weight: 700;
            color: #10b981;
            margin-bottom: 8px;
        }
        
        .celebration-points {
            font-size: 16px;
            color: #6b7280;
        }
        
        /* Rewards Store Styles */
        .rewards-header {
            background: linear-gradient(135deg, #f59e0b 0%, #d97706 100%);
            color: white;
            padding: 24px;
            border-radius: 20px;
            margin-bottom: 24px;
        }
        
        .rewards-balance {
            display: flex;
            align-items: center;
            gap: 16px;
        }
        
        .balance-icon {
            font-size: 48px;
        }
        
        .balance-amount {
            font-size: 32px;
            font-weight: 800;
            margin-bottom: 4px;
        }
        
        .balance-label {
            font-size: 14px;
            opacity: 0.9;
        }
        
        .rewards-categories {
            display: flex;
            gap: 8px;
            margin-bottom: 24px;
            overflow-x: auto;
            padding-bottom: 8px;
        }
        
        .category-btn {
            background: #f3f4f6;
            border: none;
            padding: 12px 20px;
            border-radius: 25px;
            font-size: 14px;
            font-weight: 600;
            color: #6b7280;
            cursor: pointer;
            transition: all 0.3s ease;
            white-space: nowrap;
            flex-shrink: 0;
        }
        
        .category-btn.active {
            background: #10b981;
            color: white;
        }
        
        .category-btn:hover {
            background: #e5e7eb;
        }
        
        .category-btn.active:hover {
            background: #059669;
        }
        
        .rewards-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 16px;
            margin-bottom: 32px;
        }
        
        .reward-card {
            background: white;
            border-radius: 16px;
            padding: 20px;
            box-shadow: 0 2px 12px rgba(0, 0, 0, 0.1);
            display: flex;
            gap: 16px;
            position: relative;
            transition: all 0.3s ease;
            border: 2px solid transparent;
        }
        
        .reward-card:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.15);
        }
        
        .reward-card.affordable {
            border-color: #10b981;
        }
        
        .reward-image {
            font-size: 48px;
            flex-shrink: 0;
            display: flex;
            align-items: center;
            justify-content: center;
            width: 64px;
            height: 64px;
            background: #f3f4f6;
            border-radius: 12px;
        }
        
        .reward-content {
            flex: 1;
        }
        
        .reward-title {
            font-size: 18px;
            font-weight: 700;
            margin: 0 0 8px 0;
            color: #111827;
        }
        
        .reward-description {
            font-size: 14px;
            color: #6b7280;
            margin: 0 0 16px 0;
            line-height: 1.4;
        }
        
        .reward-footer {
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        
        .reward-cost {
            font-size: 18px;
            font-weight: 700;
            color: #10b981;
        }
        
        .redeem-btn {
            background: #10b981;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 25px;
            font-size: 14px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .redeem-btn:hover {
            background: #059669;
            transform: scale(1.05);
        }
        
        .redeem-btn:disabled {
            background: #d1d5db;
            color: #9ca3af;
            cursor: not-allowed;
            transform: none;
        }
        
        .reward-badge {
            position: absolute;
            top: -8px;
            right: -8px;
            background: #ef4444;
            color: white;
            padding: 4px 12px;
            border-radius: 12px;
            font-size: 12px;
            font-weight: 600;
            text-transform: uppercase;
        }
        
        .reward-badge.new { background: #10b981; }
        .reward-badge.hot { background: #f59e0b; }
        .reward-badge.impact { background: #8b5cf6; }
        
        /* Daily Spin Section */
        .daily-spin-section {
            margin-top: 32px;
        }
        
        .spin-card {
            background: linear-gradient(135deg, #8b5cf6 0%, #7c3aed 100%);
            color: white;
            border-radius: 20px;
            padding: 24px;
            text-align: center;
        }
        
        .spin-header h3 {
            margin: 0 0 8px 0;
            font-size: 24px;
            font-weight: 700;
        }
        
        .spin-header p {
            margin: 0 0 24px 0;
            opacity: 0.9;
        }
        
        .spin-wheel {
            width: 200px;
            height: 200px;
            border-radius: 50%;
            background: conic-gradient(
                #ef4444 0deg 60deg,
                #f59e0b 60deg 120deg,
                #10b981 120deg 180deg,
                #3b82f6 180deg 240deg,
                #8b5cf6 240deg 300deg,
                #ec4899 300deg 360deg
            );
            margin: 0 auto 24px;
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: transform 2s cubic-bezier(0.23, 1, 0.32, 1);
        }
        
        .spin-wheel::before {
            content: '▼';
            position: absolute;
            top: -10px;
            left: 50%;
            transform: translateX(-50%);
            font-size: 20px;
            color: white;
            z-index: 10;
        }
        
        .wheel-section {
            position: absolute;
            width: 100%;
            height: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 14px;
            font-weight: 700;
            color: white;
            text-shadow: 0 1px 2px rgba(0, 0, 0, 0.5);
        }
        
        .spin-btn {
            background: white;
            color: #8b5cf6;
            border: none;
            padding: 16px 32px;
            border-radius: 25px;
            font-size: 18px;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .spin-btn:hover {
            transform: scale(1.05);
            box-shadow: 0 8px 24px rgba(255, 255, 255, 0.3);
        }
        
        .spin-btn:disabled {
            background: rgba(255, 255, 255, 0.5);
            cursor: not-allowed;
            transform: none;
        }
        
        .spin-timer {
            margin-top: 16px;
            font-size: 16px;
            opacity: 0.9;
        }
        
        #countdown {
            font-weight: 700;
            color: #fbbf24;
        }
        
        @keyframes redeemSuccess {
            0% { transform: translate(-50%, -50%) scale(0.8); opacity: 0; }
            100% { transform: translate(-50%, -50%) scale(1); opacity: 1; }
        }
        
        @keyframes spinResult {
            0% { transform: translate(-50%, -50%) scale(0.8) rotate(-10deg); opacity: 0; }
            100% { transform: translate(-50%, -50%) scale(1) rotate(0deg); opacity: 1; }
        }
    </style>
</head>
<body>
    <!-- Splash Screen -->
    <div class="splash-screen" id="splashScreen">
        <div class="splash-content">
            <div class="splash-logo">
                <div class="logo-circle">
                    <span class="logo-icon">🌱</span>
                </div>
            </div>
            <h1 class="splash-title">EcoTrack</h1>
            <p class="splash-subtitle">Gamify Your Green Journey</p>
            <div class="loading-dots">
                <div class="dot"></div>
                <div class="dot"></div>
                <div class="dot"></div>
            </div>
        </div>
    </div>

    <div class="app-container" id="mainApp" style="display: none;">
        <header class="header">
            <h1>🌱 EcoTrack</h1>
            <div class="points-display">
                <div class="points" id="totalPoints">0</div>
                <div class="label">Green Points</div>
            </div>
        </header>
        
        <nav class="nav-tabs">
            <button class="nav-tab active" onclick="switchTab('actions')">📋 Actions</button>
            <button class="nav-tab" onclick="switchTab('leaderboard')">🏆 Leaders</button>
            <button class="nav-tab" onclick="switchTab('rewards')">🎁 Rewards</button>
            <button class="nav-tab" onclick="switchTab('tips')">💡 Tips</button>
            <button class="nav-tab" onclick="switchTab('progress')">📊 Progress</button>
        </nav>
        
        <main>
            <!-- Daily Actions Tab -->
            <div id="actions" class="tab-content active">
                <div class="daily-reset-info">
                    <div class="icon">🔄</div>
                    <div class="title">Daily Actions Reset</div>
                    <div class="subtitle">Actions reset daily, but your Green Points are saved forever!</div>
                </div>
                
                <div class="action-item" data-points="10" data-action="reusable-bottle">
                    <div class="action-checkbox" onclick="toggleAction(this)"></div>
                    <div class="action-icon">🍶</div>
                    <div class="action-content">
                        <div class="action-title">Used a reusable bottle</div>
                        <div class="action-points">+10 points</div>
                        <button class="verify-btn" onclick="openPhotoUpload(this, 'reusable-bottle', 'Show your reusable bottle in action!')">📸 Verify with Photo</button>
                    </div>
                </div>
                
                <div class="action-item" data-points="15" data-action="cycled-school">
                    <div class="action-checkbox" onclick="toggleAction(this)"></div>
                    <div class="action-icon">🚲</div>
                    <div class="action-content">
                        <div class="action-title">Cycled to school</div>
                        <div class="action-points">+15 points</div>
                        <button class="verify-btn" onclick="openPhotoUpload(this, 'cycled-school', 'Show yourself with your bike!')">📸 Verify with Photo</button>
                    </div>
                </div>
                
                <div class="action-item" data-points="8" data-action="recycled">
                    <div class="action-checkbox" onclick="toggleAction(this)"></div>
                    <div class="action-icon">♻️</div>
                    <div class="action-content">
                        <div class="action-title">Recycled waste properly</div>
                        <div class="action-points">+8 points</div>
                        <button class="verify-btn" onclick="openPhotoUpload(this, 'recycled', 'Show your recycling in action!')">📸 Verify with Photo</button>
                    </div>
                </div>
                
                <div class="action-item" data-points="12" data-action="saved-water">
                    <div class="action-checkbox" onclick="toggleAction(this)"></div>
                    <div class="action-icon">💧</div>
                    <div class="action-content">
                        <div class="action-title">Saved water (shorter shower)</div>
                        <div class="action-points">+12 points</div>
                        <button class="verify-btn" onclick="openPhotoUpload(this, 'saved-water', 'Show your water-saving setup!')">📸 Verify with Photo</button>
                    </div>
                </div>
                
                <div class="action-item" data-points="5" data-action="lights-off">
                    <div class="action-checkbox" onclick="toggleAction(this)"></div>
                    <div class="action-icon">💡</div>
                    <div class="action-content">
                        <div class="action-title">Turned off unused lights</div>
                        <div class="action-points">+5 points</div>
                        <button class="verify-btn" onclick="openPhotoUpload(this, 'lights-off', 'Show lights turned off in your room!')">📸 Verify with Photo</button>
                    </div>
                </div>
                
                <div class="action-item" data-points="20" data-action="no-plastic">
                    <div class="action-checkbox" onclick="toggleAction(this)"></div>
                    <div class="action-icon">🚫</div>
                    <div class="action-content">
                        <div class="action-title">Avoided single-use plastic</div>
                        <div class="action-points">+20 points</div>
                        <button class="verify-btn" onclick="openPhotoUpload(this, 'no-plastic', 'Show your plastic-free choices!')">📸 Verify with Photo</button>
                    </div>
                </div>
                
                <div class="action-item" data-points="10" data-action="public-transport">
                    <div class="action-checkbox" onclick="toggleAction(this)"></div>
                    <div class="action-icon">🚌</div>
                    <div class="action-content">
                        <div class="action-title">Used public transport</div>
                        <div class="action-points">+10 points</div>
                        <button class="verify-btn" onclick="openPhotoUpload(this, 'public-transport', 'Show yourself using public transport!')">📸 Verify with Photo</button>
                    </div>
                </div>
            </div>
            
            <!-- Rewards Store Tab -->
            <div id="rewards" class="tab-content">
                <div class="rewards-header">
                    <div class="rewards-balance">
                        <div class="balance-icon">💰</div>
                        <div class="balance-info">
                            <div class="balance-amount" id="rewardsBalance">0</div>
                            <div class="balance-label">Available Points</div>
                        </div>
                    </div>
                </div>
                
                <div class="rewards-categories">
                    <button class="category-btn active" onclick="filterRewards('all')">All</button>
                    <button class="category-btn" onclick="filterRewards('eco')">🌱 Eco Products</button>
                    <button class="category-btn" onclick="filterRewards('digital')">📱 Digital</button>
                    <button class="category-btn" onclick="filterRewards('experiences')">🎯 Experiences</button>
                </div>
                
                <div class="rewards-grid">
                    <div class="reward-card" data-category="eco" data-cost="50">
                        <div class="reward-image">🌱</div>
                        <div class="reward-content">
                            <h3 class="reward-title">Bamboo Toothbrush Set</h3>
                            <p class="reward-description">Eco-friendly bamboo toothbrushes (pack of 4)</p>
                            <div class="reward-footer">
                                <div class="reward-cost">50 pts</div>
                                <button class="redeem-btn" onclick="redeemReward(this, 50, 'Bamboo Toothbrush Set')">Redeem</button>
                            </div>
                        </div>
                        <div class="reward-badge">Popular</div>
                    </div>
                    
                    <div class="reward-card" data-category="digital" data-cost="100">
                        <div class="reward-image">🎵</div>
                        <div class="reward-content">
                            <h3 class="reward-title">Spotify Premium (1 Month)</h3>
                            <p class="reward-description">Ad-free music streaming for 30 days</p>
                            <div class="reward-footer">
                                <div class="reward-cost">100 pts</div>
                                <button class="redeem-btn" onclick="redeemReward(this, 100, 'Spotify Premium')">Redeem</button>
                            </div>
                        </div>
                    </div>
                    
                    <div class="reward-card" data-category="eco" data-cost="75">
                        <div class="reward-image">🌿</div>
                        <div class="reward-content">
                            <h3 class="reward-title">Reusable Water Bottle</h3>
                            <p class="reward-description">Stainless steel eco-bottle with temperature control</p>
                            <div class="reward-footer">
                                <div class="reward-cost">75 pts</div>
                                <button class="redeem-btn" onclick="redeemReward(this, 75, 'Reusable Water Bottle')">Redeem</button>
                            </div>
                        </div>
                        <div class="reward-badge new">New</div>
                    </div>
                    
                    <div class="reward-card" data-category="experiences" data-cost="200">
                        <div class="reward-image">🎬</div>
                        <div class="reward-content">
                            <h3 class="reward-title">Movie Theater Tickets</h3>
                            <p class="reward-description">2 tickets to any movie at participating theaters</p>
                            <div class="reward-footer">
                                <div class="reward-cost">200 pts</div>
                                <button class="redeem-btn" onclick="redeemReward(this, 200, 'Movie Tickets')">Redeem</button>
                            </div>
                        </div>
                    </div>
                    
                    <div class="reward-card" data-category="digital" data-cost="150">
                        <div class="reward-image">🎮</div>
                        <div class="reward-content">
                            <h3 class="reward-title">Gaming Gift Card</h3>
                            <p class="reward-description">$10 gift card for Steam, PlayStation, or Xbox</p>
                            <div class="reward-footer">
                                <div class="reward-cost">150 pts</div>
                                <button class="redeem-btn" onclick="redeemReward(this, 150, 'Gaming Gift Card')">Redeem</button>
                            </div>
                        </div>
                        <div class="reward-badge hot">Hot</div>
                    </div>
                    
                    <div class="reward-card" data-category="eco" data-cost="120">
                        <div class="reward-image">🌍</div>
                        <div class="reward-content">
                            <h3 class="reward-title">Plant a Tree</h3>
                            <p class="reward-description">We'll plant a real tree in your name + certificate</p>
                            <div class="reward-footer">
                                <div class="reward-cost">120 pts</div>
                                <button class="redeem-btn" onclick="redeemReward(this, 120, 'Plant a Tree')">Redeem</button>
                            </div>
                        </div>
                        <div class="reward-badge impact">Impact</div>
                    </div>
                    
                    <div class="reward-card" data-category="experiences" data-cost="300">
                        <div class="reward-image">🍕</div>
                        <div class="reward-content">
                            <h3 class="reward-title">Restaurant Voucher</h3>
                            <p class="reward-description">$25 voucher at eco-friendly local restaurants</p>
                            <div class="reward-footer">
                                <div class="reward-cost">300 pts</div>
                                <button class="redeem-btn" onclick="redeemReward(this, 300, 'Restaurant Voucher')">Redeem</button>
                            </div>
                        </div>
                    </div>
                    
                    <div class="reward-card" data-category="digital" data-cost="80">
                        <div class="reward-image">📚</div>
                        <div class="reward-content">
                            <h3 class="reward-title">E-book Bundle</h3>
                            <p class="reward-description">5 bestselling books on sustainability & environment</p>
                            <div class="reward-footer">
                                <div class="reward-cost">80 pts</div>
                                <button class="redeem-btn" onclick="redeemReward(this, 80, 'E-book Bundle')">Redeem</button>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="daily-spin-section">
                    <div class="spin-card">
                        <div class="spin-header">
                            <h3>🎰 Daily Lucky Spin</h3>
                            <p>Spin once per day for bonus rewards!</p>
                        </div>
                        <div class="spin-wheel" id="spinWheel">
                            <div class="wheel-section" data-reward="5">+5 pts</div>
                            <div class="wheel-section" data-reward="10">+10 pts</div>
                            <div class="wheel-section" data-reward="15">+15 pts</div>
                            <div class="wheel-section" data-reward="bonus">2x Bonus</div>
                            <div class="wheel-section" data-reward="5">+5 pts</div>
                            <div class="wheel-section" data-reward="20">+20 pts</div>
                        </div>
                        <button class="spin-btn" id="spinBtn" onclick="spinWheel()">Spin Now!</button>
                        <div class="spin-timer" id="spinTimer" style="display: none;">Next spin in: <span id="countdown">23:45:12</span></div>
                    </div>
                </div>
            </div>
            
            <!-- Leaderboard Tab -->
            <div id="leaderboard" class="tab-content">
                <div class="leaderboard-item">
                    <div class="rank gold">1</div>
                    <div class="user-info">
                        <div class="user-name">Emma Green 🌟</div>
                        <div class="user-level">Eco Champion</div>
                    </div>
                    <div class="user-points">2,450 pts</div>
                </div>
                
                <div class="leaderboard-item">
                    <div class="rank silver">2</div>
                    <div class="user-info">
                        <div class="user-name">Alex Earth</div>
                        <div class="user-level">Green Guardian</div>
                    </div>
                    <div class="user-points">2,180 pts</div>
                </div>
                
                <div class="leaderboard-item">
                    <div class="rank bronze">3</div>
                    <div class="user-info">
                        <div class="user-name">Sam Nature</div>
                        <div class="user-level">Eco Warrior</div>
                    </div>
                    <div class="user-points">1,920 pts</div>
                </div>
                
                <div class="leaderboard-item current-user">
                    <div class="rank">4</div>
                    <div class="user-info">
                        <div class="user-name">You 🎯</div>
                        <div class="user-level">Rising Star</div>
                    </div>
                    <div class="user-points" id="leaderboardPoints">0 pts</div>
                </div>
                
                <div class="leaderboard-item">
                    <div class="rank">5</div>
                    <div class="user-info">
                        <div class="user-name">Maya Forest</div>
                        <div class="user-level">Green Rookie</div>
                    </div>
                    <div class="user-points">1,340 pts</div>
                </div>
            </div>
            
            <!-- Tips Tab -->
            <div id="tips" class="tab-content">
                <div class="tip-card">
                    <div class="tip-title">🌊 Water Conservation</div>
                    <div class="tip-content">
                        A 5-minute shorter shower can save up to 25 gallons of water! Try timing your showers and challenge yourself to reduce by just 1 minute each week.
                    </div>
                    <div class="tip-category">Daily Habit</div>
                </div>
                
                <div class="tip-card">
                    <div class="tip-title">🚲 Green Transportation</div>
                    <div class="tip-content">
                        Cycling just 10 miles a week instead of driving can prevent 500 pounds of CO2 emissions per year. Plus, it's great exercise!
                    </div>
                    <div class="tip-category">Transport</div>
                </div>
                
                <div class="tip-card">
                    <div class="tip-title">♻️ Smart Recycling</div>
                    <div class="tip-content">
                        Clean containers before recycling! Food residue can contaminate entire batches of recyclables. A quick rinse makes a huge difference.
                    </div>
                    <div class="tip-category">Waste</div>
                </div>
                
                <div class="tip-card">
                    <div class="tip-title">💡 Energy Saving</div>
                    <div class="tip-content">
                        LED bulbs use 75% less energy than traditional bulbs and last 25 times longer. Switch one bulb at a time to spread the cost!
                    </div>
                    <div class="tip-category">Energy</div>
                </div>
            </div>
            
            <!-- Progress Tab -->
            <div id="progress" class="tab-content">
                <div class="progress-header">
                    <div class="progress-title">Your Weekly Progress</div>
                    <div class="progress-subtitle">Keep up the amazing work!</div>
                </div>
                
                <div class="chart-container">
                    <div class="chart" id="progressChart">
                        <div class="chart-bar" style="height: 20%" data-value="12"></div>
                        <div class="chart-bar" style="height: 35%" data-value="28"></div>
                        <div class="chart-bar" style="height: 60%" data-value="45"></div>
                        <div class="chart-bar" style="height: 45%" data-value="35"></div>
                        <div class="chart-bar" style="height: 80%" data-value="65"></div>
                        <div class="chart-bar" style="height: 70%" data-value="55"></div>
                        <div class="chart-bar" style="height: 0%" data-value="0" id="todayBar"></div>
                    </div>
                    <div class="chart-labels">
                        <div class="chart-label">Mon</div>
                        <div class="chart-label">Tue</div>
                        <div class="chart-label">Wed</div>
                        <div class="chart-label">Thu</div>
                        <div class="chart-label">Fri</div>
                        <div class="chart-label">Sat</div>
                        <div class="chart-label">Today</div>
                    </div>
                </div>
                
                <div class="stats-grid">
                    <div class="stat-card">
                        <div class="stat-icon">🔥</div>
                        <div class="stat-value" id="streakDays">0</div>
                        <div class="stat-label">Day Streak</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-icon">🌍</div>
                        <div class="stat-value">2.5kg</div>
                        <div class="stat-label">CO₂ Saved</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-icon">💧</div>
                        <div class="stat-value">150L</div>
                        <div class="stat-label">Water Saved</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-icon">⚡</div>
                        <div class="stat-value">12kWh</div>
                        <div class="stat-label">Energy Saved</div>
                    </div>
                </div>
            </div>
        </main>
        
        <button class="floating-action" onclick="showMotivation()" title="Daily Motivation">
            ✨
        </button>
        
        <div class="celebration" id="celebration">
            <div class="celebration-icon">🎉</div>
            <div class="celebration-text">Great job!</div>
            <div class="celebration-points">You earned <span id="earnedPoints">0</span> points!</div>
        </div>
        
        <!-- Photo Upload Modal -->
        <div class="photo-upload" id="photoUpload">
            <div class="upload-modal">
                <div class="upload-header">
                    <h3 class="upload-title" id="uploadTitle">Verify Your Action</h3>
                    <p class="upload-subtitle" id="uploadSubtitle">Upload a photo to prove your eco-action!</p>
                </div>
                
                <div class="upload-area" id="uploadArea" onclick="document.getElementById('fileInput').click()">
                    <div class="upload-icon">📷</div>
                    <div class="upload-text">Click to upload photo</div>
                    <div class="upload-hint">or drag and drop here</div>
                </div>
                
                <input type="file" id="fileInput" accept="image/*" style="display: none;" onchange="handleFileSelect(event)">
                
                <div id="imagePreview" style="display: none;">
                    <img id="previewImg" class="preview-image" alt="Preview">
                </div>
                
                <div class="upload-actions">
                    <button class="upload-btn secondary" onclick="closePhotoUpload()">Cancel</button>
                    <button class="upload-btn primary" id="confirmUpload" onclick="confirmPhotoUpload()" disabled>Verify Action</button>
                </div>
            </div>
        </div>
    </div>
    
    <script>
        let totalPoints = 0;
        let completedActions = new Set();
        let verifiedActions = new Set();
        let currentStreak = 0;
        let currentUploadAction = null;
        let currentUploadButton = null;
        
        // Load saved data from localStorage
        function loadSavedData() {
            const savedPoints = localStorage.getItem('ecotrack_points');
            const savedVerified = localStorage.getItem('ecotrack_verified');
            const savedStreak = localStorage.getItem('ecotrack_streak');
            
            if (savedPoints) {
                totalPoints = parseInt(savedPoints);
            }
            
            if (savedVerified) {
                verifiedActions = new Set(JSON.parse(savedVerified));
            }
            
            if (savedStreak) {
                currentStreak = parseInt(savedStreak);
            }
            
            // Check if it's a new day and reset daily actions
            const lastResetDate = localStorage.getItem('ecotrack_last_reset');
            const today = new Date().toDateString();
            
            if (lastResetDate !== today) {
                // Reset daily actions but keep points and verified actions
                completedActions.clear();
                localStorage.setItem('ecotrack_last_reset', today);
                resetDailyActions();
            }
        }
        
        // Save data to localStorage
        function saveData() {
            localStorage.setItem('ecotrack_points', totalPoints.toString());
            localStorage.setItem('ecotrack_verified', JSON.stringify([...verifiedActions]));
            localStorage.setItem('ecotrack_streak', currentStreak.toString());
        }
        
        // Reset daily action checkboxes
        function resetDailyActions() {
            document.querySelectorAll('.action-checkbox').forEach(checkbox => {
                checkbox.classList.remove('checked');
                checkbox.innerHTML = '';
                checkbox.closest('.action-item').classList.remove('completed');
            });
            
            // Update verify buttons based on saved verified actions
            document.querySelectorAll('.action-item').forEach(item => {
                const actionId = item.dataset.action;
                const verifyBtn = item.querySelector('.verify-btn');
                
                if (verifiedActions.has(actionId)) {
                    verifyBtn.textContent = '✅ Verified';
                    verifyBtn.classList.add('verified');
                    item.classList.add('verified');
                    
                    // Add verification badge
                    if (!item.querySelector('.verification-badge')) {
                        const badge = document.createElement('div');
                        badge.className = 'verification-badge';
                        badge.innerHTML = '✅ Verified';
                        item.querySelector('.action-content').appendChild(badge);
                    }
                }
            });
        }
        
        function switchTab(tabName) {
            // Hide all tabs
            document.querySelectorAll('.tab-content').forEach(tab => {
                tab.classList.remove('active');
            });
            
            // Remove active class from all nav tabs
            document.querySelectorAll('.nav-tab').forEach(tab => {
                tab.classList.remove('active');
            });
            
            // Show selected tab
            document.getElementById(tabName).classList.add('active');
            
            // Add active class to clicked nav tab
            event.target.classList.add('active');
        }
        
        function toggleAction(checkbox) {
            const actionItem = checkbox.closest('.action-item');
            const points = parseInt(actionItem.dataset.points);
            const actionId = actionItem.dataset.action;
            
            // Check if action is verified - if so, give bonus points
            const isVerified = verifiedActions.has(actionId);
            const actualPoints = isVerified ? points * 2 : points; // Double points for verified actions
            
            if (checkbox.classList.contains('checked')) {
                // Unchecking
                checkbox.classList.remove('checked');
                checkbox.innerHTML = '';
                actionItem.classList.remove('completed');
                totalPoints -= actualPoints;
                completedActions.delete(actionId);
            } else {
                // Checking
                checkbox.classList.add('checked');
                checkbox.innerHTML = '✓';
                actionItem.classList.add('completed');
                totalPoints += actualPoints;
                completedActions.add(actionId);
                
                // Show celebration with bonus message if verified
                if (isVerified) {
                    showCelebration(actualPoints, `Verified Action Bonus! +${actualPoints} points (2x multiplier)`);
                } else {
                    showCelebration(actualPoints);
                }
                
                // Update streak
                updateStreak();
            }
            
            updatePointsDisplay();
            updateProgressChart();
            saveData();
        }
        
        // Photo upload functions
        function openPhotoUpload(button, actionId, description) {
            currentUploadAction = actionId;
            currentUploadButton = button;
            
            document.getElementById('uploadTitle').textContent = 'Verify Your Action';
            document.getElementById('uploadSubtitle').textContent = description;
            document.getElementById('photoUpload').classList.add('show');
            
            // Reset upload area
            document.getElementById('imagePreview').style.display = 'none';
            document.getElementById('uploadArea').style.display = 'block';
            document.getElementById('confirmUpload').disabled = true;
            document.getElementById('fileInput').value = '';
        }
        
        function closePhotoUpload() {
            document.getElementById('photoUpload').classList.remove('show');
            currentUploadAction = null;
            currentUploadButton = null;
        }
        
        function handleFileSelect(event) {
            const file = event.target.files[0];
            if (file && file.type.startsWith('image/')) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    document.getElementById('previewImg').src = e.target.result;
                    document.getElementById('imagePreview').style.display = 'block';
                    document.getElementById('uploadArea').style.display = 'none';
                    document.getElementById('confirmUpload').disabled = false;
                };
                reader.readAsDataURL(file);
            }
        }
        
        function confirmPhotoUpload() {
            if (currentUploadAction && currentUploadButton) {
                // Mark action as verified
                verifiedActions.add(currentUploadAction);
                
                // Update button appearance
                currentUploadButton.textContent = '✅ Verified';
                currentUploadButton.classList.add('verified');
                
                // Add verification badge
                const actionItem = currentUploadButton.closest('.action-item');
                actionItem.classList.add('verified');
                
                if (!actionItem.querySelector('.verification-badge')) {
                    const badge = document.createElement('div');
                    badge.className = 'verification-badge';
                    badge.innerHTML = '✅ Verified';
                    actionItem.querySelector('.action-content').appendChild(badge);
                }
                
                // Save verification
                saveData();
                
                // Show success message
                showVerificationSuccess();
                
                // Close modal
                closePhotoUpload();
            }
        }
        
        function showVerificationSuccess() {
            const success = document.createElement('div');
            success.style.cssText = `
                position: fixed;
                top: 50%;
                left: 50%;
                transform: translate(-50%, -50%);
                background: #10b981;
                color: white;
                padding: 24px 32px;
                border-radius: 16px;
                font-weight: 600;
                z-index: 4000;
                box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
                text-align: center;
                animation: redeemSuccess 0.5s ease-out;
            `;
            success.innerHTML = `
                <div style="font-size: 48px; margin-bottom: 16px;">📸</div>
                <div style="font-size: 20px; margin-bottom: 8px;">Action Verified!</div>
                <div style="font-size: 16px; opacity: 0.9;">You'll get 2x points when you complete this action!</div>
            `;
            
            document.body.appendChild(success);
            
            setTimeout(() => {
                success.remove();
            }, 3000);
        }
        
        // Add drag and drop functionality
        document.addEventListener('DOMContentLoaded', function() {
            const uploadArea = document.getElementById('uploadArea');
            
            uploadArea.addEventListener('dragover', function(e) {
                e.preventDefault();
                uploadArea.classList.add('dragover');
            });
            
            uploadArea.addEventListener('dragleave', function(e) {
                e.preventDefault();
                uploadArea.classList.remove('dragover');
            });
            
            uploadArea.addEventListener('drop', function(e) {
                e.preventDefault();
                uploadArea.classList.remove('dragover');
                
                const files = e.dataTransfer.files;
                if (files.length > 0 && files[0].type.startsWith('image/')) {
                    const event = { target: { files: files } };
                    handleFileSelect(event);
                }
            });
        });
        
        function showCelebration(points, customMessage = null) {
            const celebration = document.getElementById('celebration');
            const earnedPoints = document.getElementById('earnedPoints');
            const celebrationText = celebration.querySelector('.celebration-text');
            
            earnedPoints.textContent = points;
            
            if (customMessage) {
                celebrationText.textContent = customMessage;
            } else {
                celebrationText.textContent = 'Great job!';
            }
            
            celebration.classList.add('show');
            
            setTimeout(() => {
                celebration.classList.remove('show');
                celebrationText.textContent = 'Great job!'; // Reset to default
            }, 3000);
        }
        
        function updatePointsDisplay() {
            document.getElementById('totalPoints').textContent = totalPoints;
            document.getElementById('leaderboardPoints').textContent = totalPoints + ' pts';
            document.getElementById('rewardsBalance').textContent = totalPoints;
            updateRewardAvailability();
        }
        
        function updateRewardAvailability() {
            document.querySelectorAll('.reward-card').forEach(card => {
                const cost = parseInt(card.dataset.cost);
                const redeemBtn = card.querySelector('.redeem-btn');
                
                if (totalPoints >= cost) {
                    card.classList.add('affordable');
                    redeemBtn.disabled = false;
                } else {
                    card.classList.remove('affordable');
                    redeemBtn.disabled = true;
                }
            });
        }
        
        function filterRewards(category) {
            // Update active button
            document.querySelectorAll('.category-btn').forEach(btn => {
                btn.classList.remove('active');
            });
            event.target.classList.add('active');
            
            // Filter cards
            document.querySelectorAll('.reward-card').forEach(card => {
                if (category === 'all' || card.dataset.category === category) {
                    card.style.display = 'flex';
                } else {
                    card.style.display = 'none';
                }
            });
        }
        
        function redeemReward(button, cost, itemName) {
            if (totalPoints >= cost) {
                totalPoints -= cost;
                updatePointsDisplay();
                
                // Show success message
                const successMsg = document.createElement('div');
                successMsg.style.cssText = `
                    position: fixed;
                    top: 50%;
                    left: 50%;
                    transform: translate(-50%, -50%);
                    background: #10b981;
                    color: white;
                    padding: 24px 32px;
                    border-radius: 16px;
                    font-weight: 600;
                    z-index: 3000;
                    box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
                    text-align: center;
                    animation: redeemSuccess 0.5s ease-out;
                `;
                successMsg.innerHTML = `
                    <div style="font-size: 48px; margin-bottom: 16px;">🎉</div>
                    <div style="font-size: 20px; margin-bottom: 8px;">Reward Redeemed!</div>
                    <div style="font-size: 16px; opacity: 0.9;">${itemName} is on its way!</div>
                `;
                
                document.body.appendChild(successMsg);
                
                setTimeout(() => {
                    successMsg.remove();
                }, 3000);
                
                // Temporarily disable button
                button.textContent = 'Redeemed!';
                button.disabled = true;
                button.style.background = '#059669';
                
                setTimeout(() => {
                    button.textContent = 'Redeem';
                    button.style.background = '#10b981';
                    updateRewardAvailability();
                }, 3000);
            }
        }
        
        let hasSpunToday = false;
        let spinCount = 0;
        
        function spinWheel() {
            if (hasSpunToday) return;
            
            const wheel = document.getElementById('spinWheel');
            const spinBtn = document.getElementById('spinBtn');
            const spinTimer = document.getElementById('spinTimer');
            
            // Disable button
            spinBtn.disabled = true;
            spinBtn.textContent = 'Spinning...';
            
            // Random rotation (multiple full rotations + random position)
            const randomRotation = 1440 + Math.random() * 360; // 4 full rotations + random
            wheel.style.transform = `rotate(${randomRotation}deg)`;
            
            setTimeout(() => {
                // Determine reward based on final position
                const finalPosition = randomRotation % 360;
                let reward;
                
                if (finalPosition < 60) reward = { type: 'points', value: 5 };
                else if (finalPosition < 120) reward = { type: 'points', value: 10 };
                else if (finalPosition < 180) reward = { type: 'points', value: 15 };
                else if (finalPosition < 240) reward = { type: 'bonus', value: 2 };
                else if (finalPosition < 300) reward = { type: 'points', value: 5 };
                else reward = { type: 'points', value: 20 };
                
                // Apply reward
                if (reward.type === 'points') {
                    totalPoints += reward.value;
                    showSpinResult(`+${reward.value} Points!`, '🎉');
                } else if (reward.type === 'bonus') {
                    // Double points for next action
                    showSpinResult('2x Bonus Active!', '⚡');
                    // You could implement bonus logic here
                }
                
                updatePointsDisplay();
                
                // Set daily cooldown
                hasSpunToday = true;
                spinBtn.style.display = 'none';
                spinTimer.style.display = 'block';
                
                // Start countdown (demo: 24 hours)
                startSpinCountdown();
                
            }, 2000);
        }
        
        function showSpinResult(message, icon) {
            const result = document.createElement('div');
            result.style.cssText = `
                position: fixed;
                top: 50%;
                left: 50%;
                transform: translate(-50%, -50%);
                background: #8b5cf6;
                color: white;
                padding: 24px 32px;
                border-radius: 16px;
                font-weight: 600;
                z-index: 3000;
                box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
                text-align: center;
                animation: spinResult 0.5s ease-out;
            `;
            result.innerHTML = `
                <div style="font-size: 48px; margin-bottom: 16px;">${icon}</div>
                <div style="font-size: 20px;">${message}</div>
            `;
            
            document.body.appendChild(result);
            
            setTimeout(() => {
                result.remove();
            }, 2500);
        }
        
        function startSpinCountdown() {
            let timeLeft = 24 * 60 * 60; // 24 hours in seconds
            
            const countdown = setInterval(() => {
                const hours = Math.floor(timeLeft / 3600);
                const minutes = Math.floor((timeLeft % 3600) / 60);
                const seconds = timeLeft % 60;
                
                document.getElementById('countdown').textContent = 
                    `${hours.toString().padStart(2, '0')}:${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
                
                timeLeft--;
                
                if (timeLeft < 0) {
                    clearInterval(countdown);
                    hasSpunToday = false;
                    document.getElementById('spinBtn').style.display = 'block';
                    document.getElementById('spinBtn').disabled = false;
                    document.getElementById('spinBtn').textContent = 'Spin Now!';
                    document.getElementById('spinTimer').style.display = 'none';
                }
            }, 1000);
        }
        
        function updateProgressChart() {
            const todayBar = document.getElementById('todayBar');
            const percentage = Math.min((totalPoints / 100) * 100, 100);
            todayBar.style.height = percentage + '%';
            todayBar.setAttribute('data-value', totalPoints);
        }
        
        function updateStreak() {
            if (completedActions.size > 0) {
                currentStreak = Math.max(1, currentStreak);
                if (completedActions.size >= 3) {
                    currentStreak++;
                }
            }
            document.getElementById('streakDays').textContent = currentStreak;
        }
        
        function showMotivation() {
            const motivations = [
                "🌟 Every small action makes a big difference!",
                "🌱 You're growing into an eco champion!",
                "💚 The planet thanks you for your efforts!",
                "🚀 Keep up the amazing green work!",
                "🌍 Together we can save our beautiful Earth!"
            ];
            
            const randomMotivation = motivations[Math.floor(Math.random() * motivations.length)];
            
            // Create temporary motivation popup
            const popup = document.createElement('div');
            popup.style.cssText = `
                position: fixed;
                top: 20px;
                left: 50%;
                transform: translateX(-50%);
                background: #10b981;
                color: white;
                padding: 16px 24px;
                border-radius: 25px;
                font-weight: 600;
                z-index: 2000;
                box-shadow: 0 8px 32px rgba(16, 185, 129, 0.4);
                animation: slideDown 0.5s ease-out;
            `;
            popup.textContent = randomMotivation;
            
            document.body.appendChild(popup);
            
            setTimeout(() => {
                popup.remove();
            }, 3000);
        }
        
        // Add slide down animation
        const style = document.createElement('style');
        style.textContent = `
            @keyframes slideDown {
                0% { transform: translateX(-50%) translateY(-100%); opacity: 0; }
                100% { transform: translateX(-50%) translateY(0); opacity: 1; }
            }
        `;
        document.head.appendChild(style);
        
        // Splash screen transition
        function showMainApp() {
            const splashScreen = document.getElementById('splashScreen');
            const mainApp = document.getElementById('mainApp');
            
            splashScreen.style.display = 'none';
            mainApp.style.display = 'block';
            mainApp.style.animation = 'fadeInUp 0.6s ease-out';
        }
        
        // Initialize app
        document.addEventListener('DOMContentLoaded', function() {
            // Load saved data first
            loadSavedData();
            
            // Show main app after 3 seconds
            setTimeout(showMainApp, 3000);
            
            updatePointsDisplay();
            
            // Initialize verification states after app loads
            setTimeout(() => {
                resetDailyActions(); // This will restore verification states
            }, 3500);
        });
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9942fae5519a802e',t:'MTc2MTQwODU4NC4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>

