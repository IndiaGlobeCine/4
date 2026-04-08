<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>India GlobalCine - Ultimate Perfect Editor</title>
    
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
    <script src="https://unpkg.com/fix-webm-duration"></script>
    
    <!-- Expanded Premium 12 Fonts Collection -->
    <link href="https://fonts.googleapis.com/css2?family=Anton&family=Montserrat:ital,wght@0,500;0,600;0,800;0,900;1,500;1,900&family=Oswald:wght@500;700&family=Playfair+Display:ital,wght@0,700;1,700&family=Impact&family=Roboto:wght@400;700;900&family=Bebas+Neue&family=Lora:ital,wght@0,700;1,700&family=Merriweather:wght@700;900&family=Poppins:wght@600;800&family=Dancing+Script:wght@700&family=Cinzel:wght@700&display=swap" rel="stylesheet">
    
    <style>
        /* ==========================================================================
           INDIA GLOBALCINE - ADVANCED PREMIUM CSS
           ========================================================================== */
        
        :root {
            --bg-dark: #121212;
            --panel-bg: #1e1e1e;
            --primary-accent: #ff2a2a;
            --primary-hover: #cc0000;
            --text-light: #ffffff;
            --text-muted: #aaaaaa;
            --border-color: #333333;
            
            /* Perfect Instagram Portrait Feed Size (4:5 Aspect Ratio) */
            --post-width: 1080px;
            --post-height: 1350px; 
            
            --news-red: #e61919;
            --news-black: #000000;

            /* Multi-Highlight Global System */
            --hl1-bg-color: #e61919;
            --hl1-text-color: #ffffff;
            --hl2-bg-color: #000000;
            --hl2-text-color: #ffcc00;
            --hl3-bg-color: #00cc44;
            --hl3-text-color: #ffffff;

            /* Universal Blur Shading Color */
            --blur-shade-r: 255;
            --blur-shade-g: 255;
            --blur-shade-b: 255;
        }

        * { box-sizing: border-box; margin: 0; padding: 0; }

        body {
            font-family: 'Montserrat', sans-serif;
            background-color: var(--bg-dark);
            color: var(--text-light);
            display: flex;
            height: 100vh;
            overflow: hidden;
        }

        /* --- ADVANCED CONTROL PANEL --- */
        .editor-sidebar {
            width: 460px;
            background-color: var(--panel-bg);
            border-right: 1px solid var(--border-color);
            display: flex;
            flex-direction: column;
            box-shadow: 10px 0 30px rgba(0,0,0,0.8);
            z-index: 10;
        }

        .sidebar-header {
            padding: 20px;
            background: #111;
            border-bottom: 2px solid var(--primary-accent);
            text-align: center;
        }

        .sidebar-header h1 {
            font-family: 'Oswald', sans-serif;
            font-size: 26px;
            color: #ffffff;
            text-transform: uppercase;
            letter-spacing: 2px;
        }
        .sidebar-header h1 span { color: var(--primary-accent); }

        .control-group-container {
            padding: 20px;
            overflow-y: auto;
            flex-grow: 1;
        }
        .control-group-container::-webkit-scrollbar { width: 8px; }
        .control-group-container::-webkit-scrollbar-track { background: #111; }
        .control-group-container::-webkit-scrollbar-thumb { background: var(--primary-accent); border-radius: 4px; }

        .control-group {
            margin-bottom: 25px;
            background: #252525;
            padding: 15px;
            border-radius: 8px;
            border-left: 4px solid var(--primary-accent);
            transition: opacity 0.3s;
        }

        .control-group label {
            display: block;
            margin-bottom: 10px;
            font-weight: 800;
            font-size: 13px;
            color: var(--text-muted);
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .form-control {
            width: 100%;
            padding: 14px;
            background-color: #111;
            border: 1px solid var(--border-color);
            color: #fff;
            border-radius: 4px;
            font-size: 15px;
            font-family: 'Montserrat', sans-serif;
            font-weight: bold;
            margin-bottom: 5px;
        }
        .form-control:focus { outline: none; border-color: var(--primary-accent); }
        .form-control:disabled { opacity: 0.5; cursor: not-allowed; }
        textarea.form-control { resize: vertical; min-height: 100px; }

        .input-row { display: flex; gap: 8px; align-items: stretch; margin-bottom: 5px; }
        .input-stack { display: flex; flex-direction: column; gap: 5px; flex: 1; }
        
        .font-selector {
            background-color: #1a1a1a; color: #aaa; border: 1px solid #444;
            padding: 8px; border-radius: 4px; font-size: 11px; width: 100%; cursor: pointer;
        }
        .font-selector:disabled { opacity: 0.5; cursor: not-allowed; }

        .file-upload-wrapper {
            position: relative; width: 100%; height: 70px; border: 2px dashed #555;
            border-radius: 4px; display: flex; align-items: center; justify-content: center;
            cursor: pointer; background: #1a1a1a; transition: all 0.3s ease;
            margin-bottom: 10px;
        }
        .file-upload-wrapper:hover { border-color: var(--primary-accent); }
        .file-upload-wrapper input[type="file"] { position: absolute; width: 100%; height: 100%; opacity: 0; cursor: pointer; }
        .file-upload-wrapper input[type="file"]:disabled { cursor: not-allowed; }

        .action-buttons {
            padding: 20px; background-color: #111; border-top: 1px solid var(--border-color);
            display: flex; flex-direction: column; gap: 10px;
        }

        .btn {
            width: 100%; padding: 18px; border: none; border-radius: 6px; font-size: 16px;
            font-weight: 900; cursor: pointer; text-transform: uppercase; letter-spacing: 1px;
            transition: all 0.3s ease; position: relative; overflow: hidden;
        }
        .btn:disabled { opacity: 0.7; cursor: not-allowed; }
        .btn-primary { background-color: var(--primary-accent); color: white; }
        .btn-primary:hover:not(:disabled) { background-color: var(--primary-hover); }
        .btn-secondary { background-color: #2c3e50; color: white; border: 1px solid #34495e; }
        .btn-secondary:hover:not(:disabled) { background-color: #34495e; }
        .btn-success { background-color: #00cc44; color: white; box-shadow: 0 4px 15px rgba(0,204,68,0.3); }
        .btn-success:hover:not(:disabled) { background-color: #00b33c; }
        .btn-warning { background-color: #f39c12; color: white; box-shadow: 0 4px 15px rgba(243,156,18,0.3); }
        .btn-warning:hover:not(:disabled) { background-color: #d68910; }

        input[type=range] { -webkit-appearance: none; width: 100%; background: transparent; margin-bottom: 5px; }
        input[type=range]:disabled { opacity: 0.5; cursor: not-allowed; }
        input[type=range]::-webkit-slider-thumb { -webkit-appearance: none; height: 16px; width: 16px; border-radius: 50%; background: var(--primary-accent); cursor: pointer; margin-top: -6px; box-shadow: 0 0 5px rgba(0,0,0,0.5); }
        input[type=range]::-webkit-slider-runnable-track { width: 100%; height: 4px; cursor: pointer; background: #555; border-radius: 2px; }
        input[type=color] { width: 45px; border: 1px solid #555; border-radius: 4px; background: #111; cursor: pointer; height: auto; padding: 2px; }
        input[type=color]:disabled { opacity: 0.5; cursor: not-allowed; }

        /* --- PREVIEW CANVAS --- */
        .preview-area {
            flex-grow: 1; display: flex; align-items: center; justify-content: center;
            background: radial-gradient(circle at center, #333 0%, #000 100%);
            overflow: hidden; padding: 20px;
        }
        .canvas-scaler {
            position: relative; width: calc(100vh * (1080/1350) * 0.95); height: calc(100vh * 0.95);
            box-shadow: 0 0 50px rgba(0, 0, 0, 1);
        }
        .instagram-post {
            position: absolute; top: 0; left: 0; width: var(--post-width); height: var(--post-height);
            background-color: #ffffff; transform-origin: top left; overflow: hidden;
            display: flex; flex-direction: column;
        }

        /* --- UNIVERSAL HIGHLIGHT SPANS --- */
        .highlight-1 { background-color: var(--hl1-bg-color); color: var(--hl1-text-color); padding: 4px 12px; display: inline; -webkit-box-decoration-break: clone; box-decoration-break: clone; border-radius: 6px; line-height: 1.4; transition: all 0.3s; }
        .highlight-2 { background-color: var(--hl2-bg-color); color: var(--hl2-text-color); padding: 4px 12px; display: inline; -webkit-box-decoration-break: clone; box-decoration-break: clone; border-radius: 6px; line-height: 1.4; transition: all 0.3s; }
        .highlight-3 { background-color: var(--hl3-bg-color); color: var(--hl3-text-color); padding: 4px 12px; display: inline; -webkit-box-decoration-break: clone; box-decoration-break: clone; border-radius: 6px; line-height: 1.4; transition: all 0.3s; }

        /* --- ORIGINAL THEMES 1-7 CSS --- */
        .post-header-area {
            background-color: #ffffff; padding: 45px 30px 20px 30px; z-index: 5;
            position: relative; display: flex; flex-direction: column; align-items: center;
            width: 100%; overflow: hidden; 
        }
        .main-breaking { font-family: 'Impact', sans-serif; font-size: 215px; line-height: 0.8; color: var(--news-black); text-transform: uppercase; text-align: center; margin-bottom: 35px; letter-spacing: -1px; white-space: nowrap; transform: scale(1.25, 1.3); }
        .sub-headline { font-family: 'Montserrat', sans-serif; font-weight: 900; font-size: 50px; line-height: 1.25; color: var(--news-black); text-transform: uppercase; text-align: center; width: 95%; }
        
        .theme-global-news { background-color: #000000 !important; }
        .theme-global-news .post-header-area { background-color: transparent !important; padding: 25px 20px 10px 20px !important; z-index: 10 !important; height: auto !important; position: absolute !important; top: 0 !important; left: 0 !important; width: 100% !important; overflow: visible !important; }
        .theme-global-news .post-media-area { position: absolute !important; top: 0 !important; left: 0 !important; width: 100% !important; height: 100% !important; }
        
        .main-breaking-v2 { font-family: 'Impact', sans-serif; font-size: 195px; line-height: 0.8; color: #ffffff; text-transform: uppercase; text-align: center; margin-bottom: 50px; letter-spacing: -2px; white-space: nowrap; transform: scale(1.35, 1.3); width: 100%; display: block; }
        .red-headline-container { display: flex; flex-direction: column; gap: 15px; width: 100%; align-items: center; }
        .red-headline-line { background-color: #cc0000; color: #ffffff; font-family: 'Montserrat', sans-serif; font-weight: 900; font-size: 42px; padding: 6px 20px; text-transform: uppercase; text-align: center; line-height: 1.1; display: inline-block; }
        .yellow-headline-line { color: #ffcc00; font-family: 'Montserrat', sans-serif; font-weight: 900; font-size: 46px; padding: 5px 20px; text-transform: uppercase; text-align: center; margin-top: 15px; line-height: 1.1;}
        .sub-italic-headline { color: #ffffff; font-family: 'Montserrat', sans-serif; font-weight: 500; font-style: italic; font-size: 24px; margin-top: 20px; text-align: center; width: 90%;}

        .theme-minimal-quote .post-media-area { position: absolute !important; top: 0 !important; left: 0 !important; width: 100% !important; height: 100% !important; }
        .theme-minimal-quote .post-header-area { background-color: rgba(0,0,0,0.7) !important; backdrop-filter: blur(10px); position: absolute !important; top: 50% !important; left: 5% !important; width: 90% !important; transform: translateY(-50%); border-radius: 20px; padding: 60px 40px !important; z-index: 10; }
        .minimal-quote-text { font-family: 'Montserrat', sans-serif; font-weight: 900; font-size: 55px; line-height: 1.3; color: #ffffff; text-align: center; text-transform: uppercase; }
        .minimal-quote-author { font-family: 'Montserrat', sans-serif; font-weight: 500; font-size: 28px; color: #ffcc00; text-align: center; margin-top: 30px; letter-spacing: 2px; }

        .theme-split-screen .post-media-area { height: 50% !important; top: 0 !important; position: absolute !important; left: 0; width: 100%; border-bottom: 10px solid var(--primary-accent); z-index: 2; }
        .theme-split-screen .post-header-area { background-color: #0a0a0a !important; height: 50% !important; position: absolute !important; bottom: 0 !important; top: auto !important; left: 0; width: 100%; display: flex; flex-direction: column; justify-content: center; padding: 40px !important; z-index: 10; }
        .split-main-headline { font-family: 'Anton', sans-serif; font-size: 80px; line-height: 1.1; color: #ffffff; text-transform: uppercase; margin-bottom: 20px; }
        .split-sub-headline { font-family: 'Montserrat', sans-serif; font-weight: 600; font-size: 30px; color: #aaaaaa; }

        .theme-cyberpunk { background-color: #050510 !important; }
        .theme-cyberpunk .post-media-area { position: absolute !important; top: 0 !important; left: 0 !important; width: 100% !important; height: 100% !important; opacity: 0.6; mix-blend-mode: luminosity; }
        .theme-cyberpunk .post-header-area { background-color: transparent !important; position: absolute !important; top: 10% !important; left: 5% !important; width: 90% !important; border-left: 10px solid #00ffcc; padding: 30px !important; z-index: 10; }
        .cyber-alert { font-family: 'Montserrat', sans-serif; font-weight: 900; font-size: 35px; color: #00ffcc; letter-spacing: 5px; margin-bottom: 15px; }
        .cyber-headline { font-family: 'Montserrat', sans-serif; font-weight: 900; font-size: 70px; line-height: 1.1; color: #ffffff; text-transform: uppercase; text-shadow: 2px 2px 0px #ff0055; }

        .theme-sports { background-color: #111 !important; }
        .theme-sports .post-media-area { position: absolute !important; top: 0 !important; left: 0 !important; width: 100% !important; height: 100% !important; }
        .theme-sports .post-header-area { background-color: transparent !important; position: absolute !important; bottom: 15% !important; left: 0 !important; width: 100% !important; padding: 0 !important; z-index: 10; display: flex; flex-direction: column; align-items: flex-start; }
        .sports-box-1 { background-color: #ff2a2a; color: white; padding: 15px 40px; font-family: 'Anton', sans-serif; font-size: 50px; text-transform: uppercase; transform: skew(-15deg) translateX(-20px); margin-bottom: 10px; box-shadow: 10px 10px 0px rgba(0,0,0,0.5); }
        .sports-box-2 { background-color: #ffffff; color: #000000; padding: 20px 40px; font-family: 'Anton', sans-serif; font-size: 80px; line-height: 1; text-transform: uppercase; transform: skew(-15deg) translateX(20px); box-shadow: 10px 10px 0px rgba(0,0,0,0.5); }

        .theme-editorial .post-media-area { position: absolute !important; top: 5% !important; left: 5% !important; width: 90% !important; height: 50% !important; z-index: 1; }
        .theme-editorial .post-header-area { background-color: #f4f4f4 !important; position: absolute !important; bottom: 0 !important; top: auto !important; left: 0; width: 100%; height: 45% !important; display: flex; flex-direction: column; justify-content: center; align-items: center; padding: 40px !important; z-index: 10; border-top: 2px solid #000; }
        .editorial-title { font-family: 'Playfair Display', serif; font-size: 85px; font-weight: 700; color: #000000; text-align: center; line-height: 1.1; margin-bottom: 25px; }
        .editorial-sub { font-family: 'Montserrat', sans-serif; font-size: 22px; font-weight: 500; color: #555555; text-align: center; text-transform: uppercase; letter-spacing: 3px; border-top: 1px solid #000; border-bottom: 1px solid #000; padding: 15px 0; width: 80%; }

        /* ==========================================================================
           BRAND NEW THEMES (8-16) CSS
           ========================================================================== */
        .theme-t8 { background-color: #000; }
        .theme-t8 .post-media-area { position: absolute !important; top: 15% !important; height: 65% !important; width: 100% !important; }
        .theme-t8 .post-header-area { background-color: #ffff00 !important; position: absolute !important; top: 0 !important; left: 0 !important; width: 100% !important; height: 15% !important; justify-content: center; padding: 20px !important; }
        .theme-t8 .t8-top-text { font-family: 'Bebas Neue', Impact, sans-serif; font-size: 90px; color: #000; line-height: 0.9; text-align: center; width: 100%; }
        .theme-t8 .t8-bottom-box { position: absolute; bottom: 0; left: 0; width: 100%; height: 20%; background-color: #000; z-index: 10; display: flex; flex-direction: column; justify-content: center; align-items: center; padding: 30px; }
        .theme-t8 .t8-bot-title { font-family: 'Montserrat', sans-serif; font-size: 45px; font-weight: 900; color: #fff; text-align: center; line-height: 1.2; margin-bottom: 15px; }
        .theme-t8 .t8-bot-sub { font-family: 'Montserrat', sans-serif; font-size: 24px; font-weight: 500; color: #aaa; text-align: center; }

        .theme-t9 .post-media-area { position: absolute !important; top: 0 !important; left: 0 !important; width: 100% !important; height: 100% !important; }
        .theme-t9 .post-header-area { background: transparent !important; position: absolute !important; bottom: 0 !important; left: 0 !important; width: 100% !important; padding: 40px !important; display: flex; flex-direction: column; align-items: flex-start; justify-content: flex-end; height: 50% !important; }
        .theme-t9 .t9-gradient { position: absolute; bottom: 0; left: 0; width: 100%; height: 100%; background: linear-gradient(to top, rgba(0,0,0,1) 0%, rgba(0,0,0,0.8) 50%, transparent 100%); z-index: -1; }
        .theme-t9 .t9-title { font-family: 'Montserrat', sans-serif; font-size: 55px; font-weight: 900; color: #fff; text-transform: uppercase; margin-bottom: 20px; text-shadow: 2px 2px 10px rgba(0,0,0,0.8); }
        .theme-t9 .t9-quote-box { display: flex; flex-direction: column; gap: 10px; margin-bottom: 20px; }
        .theme-t9 .t9-quote-line { background-color: #ffcc00; color: #000; font-family: 'Montserrat', sans-serif; font-size: 40px; font-weight: 900; padding: 5px 15px; width: fit-content; }
        .theme-t9 .t9-footer { font-family: 'Montserrat', sans-serif; font-size: 30px; font-weight: 700; color: #fff; text-transform: uppercase; border-top: 2px solid #555; padding-top: 15px; width: 100%; }

        .theme-t10 .post-media-area { position: absolute !important; top: 0 !important; left: 0 !important; width: 100% !important; height: 60% !important; }
        .theme-t10 .post-header-area { background-color: #000 !important; position: absolute !important; bottom: 0 !important; left: 0 !important; width: 100% !important; height: 40% !important; justify-content: center; padding: 40px 30px !important; border-top: 5px solid #222; }
        .theme-t10 .t10-badge { background-color: #cc0000; color: #fff; font-family: 'Lora', serif; font-size: 45px; font-weight: 700; padding: 10px 30px; margin-bottom: 30px; border-radius: 5px; text-transform: uppercase; letter-spacing: 2px;}
        .theme-t10 .t10-text { font-family: 'Lora', serif; font-size: 48px; color: #fff; line-height: 1.4; text-align: center; font-weight: 500;}

        .theme-t11 .post-media-area { position: absolute !important; top: 0 !important; left: 0 !important; width: 100% !important; height: 100% !important; }
        .theme-t11 .post-header-area { background: transparent !important; position: absolute !important; bottom: 5% !important; left: 5% !important; width: 90% !important; padding: 0 !important; display: flex; flex-direction: column; align-items: flex-start; }
        .theme-t11 .t11-box { background: rgba(0,0,0,0.85); border-left: 15px solid #cc0000; padding: 30px; border-radius: 0 15px 15px 0; width: 100%; box-shadow: 0 10px 30px rgba(0,0,0,0.5); }
        .theme-t11 .t11-head { font-family: 'Montserrat', sans-serif; font-size: 50px; font-weight: 900; color: #fff; text-transform: uppercase; border-bottom: 2px solid #cc0000; padding-bottom: 10px; margin-bottom: 20px; display: inline-block;}
        .theme-t11 .t11-body { font-family: 'Montserrat', sans-serif; font-size: 42px; font-weight: 700; color: #fff; line-height: 1.3; }

        .theme-t12 .post-media-area { position: absolute !important; top: 0 !important; left: 0 !important; width: 100% !important; height: 100% !important; }
        .theme-t12 .post-header-area { background: transparent !important; position: absolute !important; bottom: 0 !important; left: 0 !important; width: 100% !important; height: 50% !important; padding: 50px !important; display: flex; flex-direction: column; justify-content: center; align-items: flex-start; }
        .theme-t12 .t12-gradient { position: absolute; bottom: 0; left: 0; width: 100%; height: 100%; background: linear-gradient(to top, rgba(10,0,50,0.95) 0%, rgba(10,0,50,0.8) 60%, transparent 100%); z-index: -1; }
        .theme-t12 .t12-text { font-family: 'Montserrat', sans-serif; font-size: 65px; font-weight: 900; color: #fff; line-height: 1.1; }

        .theme-t13 .post-media-area { position: absolute !important; top: 0 !important; left: 0 !important; width: 100% !important; height: 100% !important; }
        .theme-t13 .post-header-area { background: rgba(0,0,0,0.7) !important; position: absolute !important; top: 50% !important; left: 0 !important; width: 100% !important; transform: translateY(-50%); padding: 40px !important; display: flex; flex-direction: column; justify-content: center; align-items: center; border-top: 2px solid #ffcc00; border-bottom: 2px solid #ffcc00; }
        .theme-t13 .t13-title { font-family: 'Impact', sans-serif; font-size: 100px; color: #ffcc00; text-transform: uppercase; letter-spacing: 2px; margin-bottom: 15px; text-shadow: 3px 3px 0 #000; }
        .theme-t13 .t13-sub { font-family: 'Montserrat', sans-serif; font-size: 38px; font-weight: 700; color: #fff; text-align: center; line-height: 1.3; }

        .theme-t14 { background-color: #0f4c5c; }
        .theme-t14 .post-header-area { background: transparent !important; position: absolute !important; top: 0 !important; left: 0 !important; width: 100% !important; height: 25% !important; padding: 30px 20px !important; justify-content: center; }
        .theme-t14 .t14-shock { font-family: 'Bebas Neue', Impact, sans-serif; font-size: 110px; color: #fff; text-align: center; letter-spacing: 4px; margin-bottom: 15px; text-shadow: 2px 2px 5px rgba(0,0,0,0.5); }
        .theme-t14 .t14-red-box { background-color: #e63946; color: #fff; font-family: 'Montserrat', sans-serif; font-size: 28px; font-weight: 800; text-align: center; padding: 15px 30px; border-radius: 10px; box-shadow: 0 5px 15px rgba(0,0,0,0.3); text-transform: uppercase; line-height: 1.3; }
        .theme-t14 .post-media-area { position: absolute !important; top: 27% !important; left: 5% !important; width: 90% !important; height: 68% !important; border-radius: 20px; border: 5px solid #fff; box-shadow: 0 10px 40px rgba(0,0,0,0.5); overflow: hidden; }

        .theme-t15 { background-color: #fff; }
        .theme-t15 .post-media-area { position: absolute !important; top: 0 !important; left: 0 !important; width: 100% !important; height: 75% !important; }
        .theme-t15 .post-header-area { background: #fff !important; position: absolute !important; bottom: 0 !important; left: 0 !important; width: 100% !important; height: 25% !important; padding: 30px !important; display: flex; flex-direction: column; justify-content: center; align-items: center; overflow: visible !important;}
        .theme-t15 .t15-curve { position: absolute; top: -50px; left: -50px; width: 150px; height: 150px; background-color: #cc0000; border-radius: 50%; z-index: 11; }
        .theme-t15 .t15-text-1 { font-family: 'Montserrat', sans-serif; font-size: 50px; font-weight: 900; color: #000; text-align: center; margin-bottom: 10px; z-index: 12;}
        .theme-t15 .t15-text-2 { font-family: 'Montserrat', sans-serif; font-size: 50px; font-weight: 900; color: #cc0000; text-align: center; z-index: 12;}

        .theme-t16 .post-media-area { position: absolute !important; top: 0 !important; left: 0 !important; width: 100% !important; height: 100% !important; }
        .theme-t16 .post-header-area { background: transparent !important; position: absolute !important; top: 0 !important; left: 0 !important; width: 100% !important; height: 45% !important; padding: 40px 30px !important; display: flex; flex-direction: column; align-items: center; justify-content: center; z-index: 10; }
        .theme-t16 .t16-gradient { position: absolute; top: 0; left: 0; width: 100%; height: 100%; background: linear-gradient(to bottom, rgba(0,0,0,0.95) 0%, rgba(0,0,0,0.8) 70%, transparent 100%); z-index: -1; }
        .theme-t16 .t16-title { font-family: 'Oswald', sans-serif; font-size: 70px; font-weight: 700; color: #fff; text-transform: uppercase; text-align: center; margin-bottom: 20px; }
        .theme-t16 .t16-sub { font-family: 'Lora', serif; font-size: 38px; color: #fff; text-align: center; line-height: 1.4; font-weight: 500;}

        /* --- GLOBAL MEDIA & BLUR --- */
        .post-media-area { flex-grow: 1; position: relative; background-color: #000000; width: 100%; overflow: hidden; }
        .media-content { width: 100%; height: 100%; object-fit: cover; object-position: 50% 50%; position: absolute; top: 0; left: 0; z-index: 1; }
        
        .blur-overlay-div {
            position: absolute; top: -5px; left: 0; width: 100%; height: 165px;
            background: linear-gradient(to bottom, 
                rgba(var(--blur-shade-r), var(--blur-shade-g), var(--blur-shade-b), 1) 0%, 
                rgba(var(--blur-shade-r), var(--blur-shade-g), var(--blur-shade-b), 0.8) 30%, 
                transparent 100%);
            z-index: 2; pointer-events: none; transition: background 0.3s;
        }
        .theme-global-blur {
            background: linear-gradient(to bottom, 
                rgba(var(--blur-shade-r), var(--blur-shade-g), var(--blur-shade-b), 1) 0%, 
                rgba(var(--blur-shade-r), var(--blur-shade-g), var(--blur-shade-b), 0.9) 45%, 
                transparent 100%) !important;
        }

        /* --- OVERLAYS (DATE & LOGO RESTORED) --- */
        .overlay-layer { position: absolute; top: 0; left: 0; width: 100%; height: 100%; pointer-events: none; z-index: 100; }
        
        .date-box { position: absolute; bottom: 30px; left: 30px; background-color: var(--news-red); color: white; padding: 10px 25px; text-align: center; display: flex; flex-direction: column; align-items: center; justify-content: center; transform-origin: bottom left;}
        .date-number { font-family: 'Impact', sans-serif; font-size: 90px; line-height: 0.9; letter-spacing: -2px; }
        .date-month { font-family: 'Montserrat', sans-serif; font-weight: 900; font-size: 32px; text-transform: uppercase; letter-spacing: 1px; margin-top: -5px; }
        
        .branding-corner { position: absolute; bottom: 30px; right: 30px; display: flex; flex-direction: column; align-items: flex-end; text-shadow: 2px 2px 8px rgba(0,0,0,0.8); }
        .custom-logo { width: 180px; height: auto; margin-bottom: 10px; border-radius: 50%; box-shadow: 0 5px 15px rgba(0,0,0,0.5); display: none; }
        .brand-text { font-family: 'Montserrat', sans-serif; color: white; font-size: 28px; font-weight: 900; text-transform: uppercase; letter-spacing: 1px; }
        .brand-text span { color: var(--news-red); }

        /* --- PREMIUM NOTIFICATION & MODALS --- */
        #advanced-toast { position: fixed; top: -100px; left: 50%; transform: translateX(-50%); background: #00cc44; color: white; padding: 15px 30px; border-radius: 50px; font-family: 'Montserrat', sans-serif; font-weight: 800; font-size: 16px; box-shadow: 0 10px 30px rgba(0, 204, 68, 0.4); z-index: 100000; transition: top 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275); display: flex; align-items: center; gap: 10px; white-space: nowrap; }
        #advanced-toast.show { top: 30px; }
        #recording-overlay { position: fixed; top: 0; left: 0; width: 100vw; height: 100vh; background: rgba(0,0,0,0.9); z-index: 9999; display: none; flex-direction: column; align-items: center; justify-content: center; color: white; font-family: 'Montserrat', sans-serif; text-align: center; }
        #recording-overlay h2 { font-size: 24px; margin-bottom: 10px; color: #00cc44; }
        .mobile-modal { position: fixed; top: 0; left: 0; width: 100vw; height: 100vh; background: rgba(0,0,0,0.95); z-index: 10000; display: none; flex-direction: column; align-items: center; justify-content: center; padding: 20px; }
        .mobile-modal.active { display: flex; }
        .mobile-modal video { width: 100%; max-width: 400px; border: 2px solid #333; border-radius: 10px; margin-bottom: 20px; }
        .download-btn-massive { display: block; width: 100%; max-width: 350px; padding: 25px; background: #00cc44; color: white; text-decoration: none; text-align: center; font-size: 20px; font-weight: 900; border-radius: 10px; margin-bottom: 15px; text-transform: uppercase; font-family: 'Montserrat', sans-serif; box-shadow: 0 10px 20px rgba(0, 204, 68, 0.3); }
        .close-btn { background: #333; color: white; padding: 15px 40px; border: none; border-radius: 8px; font-weight: bold; font-size: 16px; cursor: pointer; }

        @media (max-width: 900px) {
            body { flex-direction: column; overflow-y: auto; }
            .editor-sidebar { width: 100%; border-right: none; }
            .preview-area { min-height: 80vh; padding: 10px; }
            .canvas-scaler { width: calc(100vw * 0.95); height: calc((100vw * 0.95) * (1350/1080)); }
        }
    </style>
</head>
<body>

    <div id="advanced-toast">✅ Action Successful!</div>

    <aside class="editor-sidebar">
        <div class="sidebar-header">
            <h1>India <span>GlobalCine</span> Pro</h1>
        </div>

        <div class="control-group-container" id="main-controls-scroll">
            
            <div class="control-group" style="background: #2a2a2a; border-left: 4px solid #ffcc00;">
                <label style="color: #ffcc00;">🎨 SELECT PREMIUM POST THEME</label>
                <select id="layout-selector" class="form-control" style="background: #000; border: 1px solid #555; padding: 15px; font-size: 16px;">
                    <optgroup label="Original Core Themes">
                        <option value="theme-default">Layout 1: Classic Breaking (Default)</option>
                        <option value="theme-global">Layout 2: Global News Red/Yellow</option>
                        <option value="theme-minimal">Layout 3: Minimalist Quote</option>
                        <option value="theme-split">Layout 4: Cinematic Split</option>
                        <option value="theme-cyber">Layout 5: Cyberpunk Alert</option>
                        <option value="theme-sports">Layout 6: Sports Action</option>
                        <option value="theme-editorial">Layout 7: Premium Editorial</option>
                    </optgroup>
                    <optgroup label="New Advanced Layouts">
                        <option value="theme-t8">Layout 8: Fact / History</option>
                        <option value="theme-t9">Layout 9: Political Quote</option>
                        <option value="theme-t10">Layout 10: Financial Alert</option>
                        <option value="theme-t11">Layout 11: Headline Meme</option>
                        <option value="theme-t12">Layout 12: War Room Doc</option>
                        <option value="theme-t13">Layout 13: Center Impact</option>
                        <option value="theme-t14">Layout 14: Shocking Reveal</option>
                        <option value="theme-t15">Layout 15: News Footer Curve</option>
                        <option value="theme-t16">Layout 16: Top Header Story</option>
                    </optgroup>
                </select>
            </div>

            <!-- GLOBAL MULTI-HIGHLIGHT SYSTEM -->
            <div class="control-group" style="background: #1a1a2e; border-left: 4px solid #00f0ff;">
                <label style="color: #00f0ff; font-size: 14px;">🖌️ ADVANCED HIGHLIGHT SYSTEM</label>
                <small style="color:#aaa; font-size: 11px; display:block; margin-bottom:10px; line-height: 1.4;">
                    Use syntax inside any text box to apply highlights:<br>
                    <strong>{text}</strong> = Highlight Type 1<br>
                    <strong>[text]</strong> = Highlight Type 2<br>
                    <strong>*text*</strong> = Highlight Type 3
                </small>
                
                <div style="display: flex; gap: 10px; margin-bottom: 10px; border-bottom: 1px solid #333; padding-bottom: 10px;">
                    <div style="flex:1;"><span style="font-size:10px; color:#fff;">{HL1} BG</span><input type="color" id="hl1-bg" value="#e61919"></div>
                    <div style="flex:1;"><span style="font-size:10px; color:#fff;">{HL1} Text</span><input type="color" id="hl1-text" value="#ffffff"></div>
                </div>
                <div style="display: flex; gap: 10px; margin-bottom: 10px; border-bottom: 1px solid #333; padding-bottom: 10px;">
                    <div style="flex:1;"><span style="font-size:10px; color:#fff;">[HL2] BG</span><input type="color" id="hl2-bg" value="#000000"></div>
                    <div style="flex:1;"><span style="font-size:10px; color:#fff;">[HL2] Text</span><input type="color" id="hl2-text" value="#ffcc00"></div>
                </div>
                <div style="display: flex; gap: 10px;">
                    <div style="flex:1;"><span style="font-size:10px; color:#fff;">*HL3* BG</span><input type="color" id="hl3-bg" value="#00cc44"></div>
                    <div style="flex:1;"><span style="font-size:10px; color:#fff;">*HL3* Text</span><input type="color" id="hl3-text" value="#ffffff"></div>
                </div>
            </div>

            <!-- ==========================================
                 THEME CONTROL PANELS (1 to 16)
                 ========================================== -->
                 
            <!-- THEME 1 CONTROLS -->
            <div id="theme-default-controls" class="theme-controls-panel">
                <div class="control-group">
                    <label>Main Heading (Giant Text)</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <input type="text" id="input-breaking" class="form-control" value="BREAKING">
                            <select id="font-t1-breaking" class="font-selector">
                                <option value="'Impact', sans-serif">Impact</option>
                                <option value="'Anton', sans-serif">Anton</option>
                                <option value="'Montserrat', sans-serif">Montserrat</option>
                                <option value="'Bebas Neue', sans-serif">Bebas Neue</option>
                                <option value="'Poppins', sans-serif">Poppins</option>
                            </select>
                        </div>
                        <input type="color" id="color-t1-breaking" value="#000000" title="Font Color">
                    </div>
                </div>
                <div class="control-group">
                    <label>Full Headline</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <textarea id="input-headline" class="form-control">MP RAGHAV CHADHA REPLIED AFTER {AAP STOPPED HIM} FROM SPEAKING IN PARLIAMENT</textarea>
                            <select id="font-t1-headline" class="font-selector">
                                <option value="'Montserrat', sans-serif">Montserrat</option>
                                <option value="'Oswald', sans-serif">Oswald</option>
                                <option value="'Roboto', sans-serif">Roboto</option>
                                <option value="'Lora', serif">Lora</option>
                                <option value="'Poppins', sans-serif">Poppins</option>
                            </select>
                        </div>
                        <input type="color" id="color-t1-headline" value="#000000" title="Font Color">
                    </div>
                </div>
                <div class="control-group">
                    <label>Sub Headline</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <input type="text" id="input-sub-italic-t1" class="form-control" value="India was set to receive Iranian oil after nearly [7 years], but it was rerouted.">
                            <select id="font-t1-sub" class="font-selector">
                                <option value="'Montserrat', sans-serif">Montserrat</option>
                                <option value="'Roboto', sans-serif">Roboto</option>
                                <option value="'Playfair Display', serif">Playfair Display</option>
                                <option value="'Cinzel', serif">Cinzel</option>
                            </select>
                        </div>
                        <input type="color" id="color-t1-sub" value="#333333" title="Font Color">
                    </div>
                </div>
            </div>

            <!-- THEME 2 CONTROLS -->
            <div id="theme-global-controls" class="theme-controls-panel" style="display: none;">
                <div class="control-group">
                    <label>Red Headline Line 1 & 2</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <input type="text" id="input-red-1" class="form-control" value="Ship carrying 600,000 barrels Iranian">
                            <input type="text" id="input-red-2" class="form-control" value="crude changes route from India to">
                            <select id="font-t2-red" class="font-selector">
                                <option value="'Montserrat', sans-serif">Montserrat</option>
                                <option value="'Oswald', sans-serif">Oswald</option>
                                <option value="'Bebas Neue', sans-serif">Bebas Neue</option>
                            </select>
                        </div>
                        <div class="input-stack" style="flex:0.2;">
                            <input type="color" id="color-t2-red1" value="#ffffff" title="Line 1 Color">
                            <input type="color" id="color-t2-redbox" value="#cc0000" title="Box Color">
                        </div>
                    </div>
                </div>
                <div class="control-group">
                    <label>Yellow Headline</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <input type="text" id="input-yellow" class="form-control" value="China midway {due to US sanctions}.">
                            <select id="font-t2-yellow" class="font-selector"><option value="'Montserrat', sans-serif">Montserrat</option><option value="'Poppins', sans-serif">Poppins</option></select>
                        </div>
                        <input type="color" id="color-t2-yellow" value="#ffcc00" title="Font Color">
                    </div>
                </div>
                <div class="control-group">
                    <label>Sub Headline</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <input type="text" id="input-sub-italic" class="form-control" value="India was set to receive Iranian oil after nearly 7 years, but it was rerouted.">
                            <select id="font-t2-sub" class="font-selector"><option value="'Montserrat', sans-serif">Montserrat</option></select>
                        </div>
                        <input type="color" id="color-t2-sub" value="#ffffff" title="Font Color">
                    </div>
                </div>
            </div>

            <!-- THEME 3 CONTROLS -->
            <div id="theme-minimal-controls" class="theme-controls-panel" style="display: none;">
                <div class="control-group">
                    <label>Main Quote</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <textarea id="input-t3-quote" class="form-control">"{SUCCESS} IS NOT FINAL, FAILURE IS NOT FATAL: IT IS THE COURAGE TO CONTINUE THAT COUNTS."</textarea>
                            <select id="font-t3-quote" class="font-selector">
                                <option value="'Montserrat', sans-serif">Montserrat</option>
                                <option value="'Lora', serif">Lora</option>
                                <option value="'Playfair Display', serif">Playfair Display</option>
                                <option value="'Cinzel', serif">Cinzel</option>
                            </select>
                        </div>
                        <input type="color" id="color-t3-quote" value="#ffffff">
                    </div>
                </div>
                <div class="control-group">
                    <label>Author</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <input type="text" id="input-t3-author" class="form-control" value="- WINSTON CHURCHILL">
                            <select id="font-t3-author" class="font-selector"><option value="'Montserrat', sans-serif">Montserrat</option><option value="'Dancing Script', cursive">Dancing Script</option></select>
                        </div>
                        <input type="color" id="color-t3-author" value="#ffcc00">
                    </div>
                </div>
            </div>

            <!-- THEME 4 CONTROLS -->
            <div id="theme-split-controls" class="theme-controls-panel" style="display: none;">
                <div class="control-group">
                    <label>Split Headline</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <textarea id="input-t4-head" class="form-control">NEW ERA OF {CINEMA} BEGINS</textarea>
                            <select id="font-t4-head" class="font-selector">
                                <option value="'Anton', sans-serif">Anton</option>
                                <option value="'Bebas Neue', sans-serif">Bebas Neue</option>
                                <option value="'Impact', sans-serif">Impact</option>
                            </select>
                        </div>
                        <input type="color" id="color-t4-head" value="#ffffff">
                    </div>
                </div>
                <div class="control-group">
                    <label>Split Sub-Text</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <textarea id="input-t4-sub" class="form-control">Directors are now moving towards purely digital environments for modern blockbusters.</textarea>
                            <select id="font-t4-sub" class="font-selector"><option value="'Montserrat', sans-serif">Montserrat</option></select>
                        </div>
                        <input type="color" id="color-t4-sub" value="#aaaaaa">
                    </div>
                </div>
            </div>

            <!-- THEME 5 CONTROLS -->
            <div id="theme-cyber-controls" class="theme-controls-panel" style="display: none;">
                <div class="control-group">
                    <label>System Alert Line</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <input type="text" id="input-t5-alert" class="form-control" value="[ SYSTEM_OVERRIDE_ACTIVE ]">
                            <select id="font-t5-alert" class="font-selector"><option value="'Montserrat', sans-serif">Montserrat</option></select>
                        </div>
                        <input type="color" id="color-t5-alert" value="#00ffcc">
                    </div>
                </div>
                <div class="control-group">
                    <label>Neon Headline</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <textarea id="input-t5-head" class="form-control">GLOBAL NETWORKS {COMPROMISED} IN MASSIVE ATTACK</textarea>
                            <select id="font-t5-head" class="font-selector"><option value="'Montserrat', sans-serif">Montserrat</option></select>
                        </div>
                        <input type="color" id="color-t5-head" value="#ffffff">
                    </div>
                </div>
            </div>

            <!-- THEME 6 CONTROLS -->
            <div id="theme-sports-controls" class="theme-controls-panel" style="display: none;">
                <div class="control-group">
                    <label>Top Slant Box</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <input type="text" id="input-t6-top" class="form-control" value="FULL TIME RESULT">
                            <select id="font-t6-top" class="font-selector"><option value="'Anton', sans-serif">Anton</option><option value="'Impact', sans-serif">Impact</option></select>
                        </div>
                        <div class="input-stack" style="flex:0.2;">
                            <input type="color" id="color-t6-top-text" value="#ffffff" title="Text Color">
                            <input type="color" id="color-t6-top-bg" value="#ff2a2a" title="Box Color">
                        </div>
                    </div>
                </div>
                <div class="control-group">
                    <label>Bottom Slant Box</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <input type="text" id="input-t6-bot" class="form-control" value="{INDIA} WON BY 5 WICKETS">
                            <select id="font-t6-bot" class="font-selector"><option value="'Anton', sans-serif">Anton</option></select>
                        </div>
                        <div class="input-stack" style="flex:0.2;">
                            <input type="color" id="color-t6-bot-text" value="#000000" title="Text Color">
                            <input type="color" id="color-t6-bot-bg" value="#ffffff" title="Box Color">
                        </div>
                    </div>
                </div>
            </div>

            <!-- THEME 7 CONTROLS -->
            <div id="theme-editorial-controls" class="theme-controls-panel" style="display: none;">
                <div class="control-group">
                    <label>Magazine Title</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <textarea id="input-t7-title" class="form-control">The Future of {Modern} Architecture</textarea>
                            <select id="font-t7-title" class="font-selector">
                                <option value="'Playfair Display', serif">Playfair Display</option>
                                <option value="'Merriweather', serif">Merriweather</option>
                                <option value="'Lora', serif">Lora</option>
                                <option value="'Cinzel', serif">Cinzel</option>
                            </select>
                        </div>
                        <input type="color" id="color-t7-title" value="#000000">
                    </div>
                </div>
                <div class="control-group">
                    <label>Subtitle / Date</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <input type="text" id="input-t7-sub" class="form-control" value="SPECIAL EDITION  |  VOL. 42">
                            <select id="font-t7-sub" class="font-selector"><option value="'Montserrat', sans-serif">Montserrat</option></select>
                        </div>
                        <input type="color" id="color-t7-sub" value="#555555">
                    </div>
                </div>
            </div>

            <!-- THEME 8 CONTROLS (Fact/History) -->
            <div id="theme-t8-controls" class="theme-controls-panel" style="display: none;">
                <div class="control-group">
                    <label>Top Yellow Bar Text</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <input type="text" id="input-t8-top" class="form-control" value="BADMINTON WAS INVENTED IN PUNE, INDIA">
                            <select id="font-t8-top" class="font-selector"><option value="'Bebas Neue', Impact, sans-serif">Bebas Neue</option><option value="'Anton', sans-serif">Anton</option></select>
                        </div>
                        <div class="input-stack" style="flex:0.2;">
                            <input type="color" id="color-t8-top-text" value="#000000" title="Text Color">
                            <input type="color" id="color-t8-top-bg" value="#ffff00" title="Bar Background">
                        </div>
                    </div>
                </div>
                <div class="control-group">
                    <label>Bottom Box Title</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <textarea id="input-t8-bot-title" class="form-control">Badminton started in Pune as "{Poona}" before British officers renamed and [popularized] it</textarea>
                            <select id="font-t8-bot-title" class="font-selector"><option value="'Montserrat', sans-serif">Montserrat</option><option value="'Roboto', sans-serif">Roboto</option></select>
                        </div>
                        <div class="input-stack" style="flex:0.2;">
                            <input type="color" id="color-t8-bot-title" value="#ffffff" title="Text Color">
                            <input type="color" id="color-t8-bot-bg" value="#000000" title="Box Background">
                        </div>
                    </div>
                </div>
                <div class="control-group">
                    <label>Bottom Box Sub-Text</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <textarea id="input-t8-bot-sub" class="form-control">The sport was played by locals in India long before it got global recognition, making it a hidden part of Indian history.</textarea>
                            <select id="font-t8-bot-sub" class="font-selector"><option value="'Montserrat', sans-serif">Montserrat</option></select>
                        </div>
                        <input type="color" id="color-t8-bot-sub" value="#aaaaaa" title="Text Color">
                    </div>
                </div>
            </div>

            <!-- THEME 9 CONTROLS (Political Quote) -->
            <div id="theme-t9-controls" class="theme-controls-panel" style="display: none;">
                <div class="control-group">
                    <label>Main White Title</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <textarea id="input-t9-title" class="form-control">PM MODI ON DHURANDHAR</textarea>
                            <select id="font-t9-title" class="font-selector"><option value="'Montserrat', sans-serif">Montserrat</option><option value="'Anton', sans-serif">Anton</option></select>
                        </div>
                        <input type="color" id="color-t9-title" value="#ffffff" title="Text Color">
                    </div>
                </div>
                <div class="control-group">
                    <label>Yellow Highlights Box Lines</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <input type="text" id="input-t9-q1" class="form-control" value="They Said Dhurandhar, Kerala">
                            <input type="text" id="input-t9-q2" class="form-control" value="Files Are Lies: PM Modi Replies">
                            <select id="font-t9-quote" class="font-selector"><option value="'Montserrat', sans-serif">Montserrat</option></select>
                        </div>
                        <div class="input-stack" style="flex:0.2;">
                            <input type="color" id="color-t9-q-text" value="#000000" title="Text Color">
                            <input type="color" id="color-t9-q-bg" value="#ffff00" title="Box Background">
                        </div>
                    </div>
                </div>
                <div class="control-group">
                    <label>Footer Text</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <input type="text" id="input-t9-foot" class="form-control" value="UDF | Swipe To {WATCH}">
                            <select id="font-t9-foot" class="font-selector"><option value="'Montserrat', sans-serif">Montserrat</option></select>
                        </div>
                        <input type="color" id="color-t9-foot" value="#ffffff" title="Text Color">
                    </div>
                </div>
            </div>

            <!-- THEME 10 CONTROLS (Financial Alert) -->
            <div id="theme-t10-controls" class="theme-controls-panel" style="display: none;">
                <div class="control-group">
                    <label>Red Badge Text</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <input type="text" id="input-t10-badge" class="form-control" value="BREAKING !!">
                            <select id="font-t10-badge" class="font-selector"><option value="'Lora', serif">Lora</option><option value="'Montserrat', sans-serif">Montserrat</option></select>
                        </div>
                        <div class="input-stack" style="flex:0.2;">
                            <input type="color" id="color-t10-badge-text" value="#ffffff" title="Text Color">
                            <input type="color" id="color-t10-badge-bg" value="#cc0000" title="Badge BG">
                        </div>
                    </div>
                </div>
                <div class="control-group">
                    <label>Main Body Text</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <textarea id="input-t10-text" class="form-control">{For the first time} in Nepal's history Balen's government, *will publicly apologize* to Dalit and marginalized communities for the past discrimination and {start reforms for justice.}</textarea>
                            <select id="font-t10-text" class="font-selector"><option value="'Lora', serif">Lora</option><option value="'Merriweather', serif">Merriweather</option></select>
                        </div>
                        <div class="input-stack" style="flex:0.2;">
                            <input type="color" id="color-t10-text" value="#ffffff" title="Text Color">
                            <input type="color" id="color-t10-bg" value="#000000" title="Box BG">
                        </div>
                    </div>
                </div>
            </div>

            <!-- THEME 11 CONTROLS (Headline Meme) -->
            <div id="theme-t11-controls" class="theme-controls-panel" style="display: none;">
                <div class="control-group">
                    <label>HEADLINE Top Text</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <input type="text" id="input-t11-head" class="form-control" value="HEADLINE: 😆">
                            <select id="font-t11-head" class="font-selector"><option value="'Montserrat', sans-serif">Montserrat</option></select>
                        </div>
                        <div class="input-stack" style="flex:0.2;">
                            <input type="color" id="color-t11-head-text" value="#ffffff" title="Text Color">
                            <input type="color" id="color-t11-border" value="#cc0000" title="Side Border">
                        </div>
                    </div>
                </div>
                <div class="control-group">
                    <label>Main Text Content</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <textarea id="input-t11-body" class="form-control">*Nagpur* Zilha Parishad Staff organised [cultural] event, [judge] honored during celebrations</textarea>
                            <select id="font-t11-body" class="font-selector"><option value="'Montserrat', sans-serif">Montserrat</option><option value="'Roboto', sans-serif">Roboto</option></select>
                        </div>
                        <div class="input-stack" style="flex:0.2;">
                            <input type="color" id="color-t11-body-text" value="#ffffff" title="Text Color">
                            <input type="color" id="color-t11-box-bg" value="rgba(0,0,0,0.85)" title="Box BG">
                        </div>
                    </div>
                </div>
            </div>

            <!-- THEME 12 CONTROLS (War Room Doc) -->
            <div id="theme-t12-controls" class="theme-controls-panel" style="display: none;">
                <div class="control-group">
                    <label>Docu-Style Text</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <textarea id="input-t12-text" class="form-control">Iran Releases First Ever Video of [Mojtaba Khamenei] From {War Room}</textarea>
                            <select id="font-t12-text" class="font-selector"><option value="'Montserrat', sans-serif">Montserrat</option><option value="'Impact', sans-serif">Impact</option></select>
                        </div>
                        <input type="color" id="color-t12-text" value="#ffffff" title="Text Color">
                    </div>
                </div>
            </div>

            <!-- THEME 13 CONTROLS (Center Impact) -->
            <div id="theme-t13-controls" class="theme-controls-panel" style="display: none;">
                <div class="control-group">
                    <label>Impact Title</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <input type="text" id="input-t13-title" class="form-control" value="HISTORY MADE!">
                            <select id="font-t13-title" class="font-selector"><option value="'Impact', sans-serif">Impact</option><option value="'Anton', sans-serif">Anton</option></select>
                        </div>
                        <input type="color" id="color-t13-title" value="#ffcc00" title="Text Color">
                    </div>
                </div>
                <div class="control-group">
                    <label>Center Sub-Text</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <textarea id="input-t13-sub" class="form-control">Dr. Menaka Guruswamy takes oath in the [Rajya Sabha], becoming the country's first openly queer MP.</textarea>
                            <select id="font-t13-sub" class="font-selector"><option value="'Montserrat', sans-serif">Montserrat</option></select>
                        </div>
                        <input type="color" id="color-t13-sub" value="#ffffff" title="Text Color">
                    </div>
                </div>
            </div>

            <!-- THEME 14 CONTROLS (Shocking Reveal) -->
            <div id="theme-t14-controls" class="theme-controls-panel" style="display: none;">
                <div class="control-group">
                    <label>Top Shock Title</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <input type="text" id="input-t14-shock" class="form-control" value="SHOCKING">
                            <select id="font-t14-shock" class="font-selector"><option value="'Bebas Neue', Impact, sans-serif">Bebas Neue</option></select>
                        </div>
                        <div class="input-stack" style="flex:0.2;">
                            <input type="color" id="color-t14-shock" value="#ffffff" title="Text Color">
                            <input type="color" id="color-t14-bg" value="#0f4c5c" title="Global BG">
                        </div>
                    </div>
                </div>
                <div class="control-group">
                    <label>Red Box Alert</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <textarea id="input-t14-red" class="form-control">ARMY OFFICER SHARES HAUNTING MIDNIGHT VIDEO, SAYS JUDGING SOLDIERS IS EASY BUT LIVING THEIR REALITY TAKES COURAGE</textarea>
                            <select id="font-t14-red" class="font-selector"><option value="'Montserrat', sans-serif">Montserrat</option></select>
                        </div>
                        <div class="input-stack" style="flex:0.2;">
                            <input type="color" id="color-t14-red-text" value="#ffffff" title="Text Color">
                            <input type="color" id="color-t14-red-bg" value="#e63946" title="Box BG">
                        </div>
                    </div>
                </div>
            </div>

            <!-- THEME 15 CONTROLS (News Footer) -->
            <div id="theme-t15-controls" class="theme-controls-panel" style="display: none;">
                <div class="control-group">
                    <label>Line 1 Text</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <input type="text" id="input-t15-L1" class="form-control" value="गुजरात में बन रहा भारत का तीसरा">
                            <select id="font-t15-L1" class="font-selector"><option value="'Montserrat', sans-serif">Montserrat</option></select>
                        </div>
                        <div class="input-stack" style="flex:0.2;">
                            <input type="color" id="color-t15-L1" value="#000000" title="Text Color">
                            <input type="color" id="color-t15-bg" value="#ffffff" title="Box BG">
                        </div>
                    </div>
                </div>
                <div class="control-group">
                    <label>Line 2 Text</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <input type="text" id="input-t15-L2" class="form-control" value="सैटेलाइट लॉन्च सेंटर? जानें कहां होगा">
                            <select id="font-t15-L2" class="font-selector"><option value="'Montserrat', sans-serif">Montserrat</option></select>
                        </div>
                        <div class="input-stack" style="flex:0.2;">
                            <input type="color" id="color-t15-L2" value="#cc0000" title="Text Color">
                            <input type="color" id="color-t15-curve" value="#cc0000" title="Curve Detail Color">
                        </div>
                    </div>
                </div>
            </div>

            <!-- THEME 16 CONTROLS (Top Header Story) -->
            <div id="theme-t16-controls" class="theme-controls-panel" style="display: none;">
                <div class="control-group">
                    <label>Top Story Title</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <input type="text" id="input-t16-title" class="form-control" value="THE RISE & FALL OF {KINGFISHER} AIRLINES">
                            <select id="font-t16-title" class="font-selector"><option value="'Oswald', sans-serif">Oswald</option><option value="'Anton', sans-serif">Anton</option></select>
                        </div>
                        <input type="color" id="color-t16-title" value="#ffffff" title="Text Color">
                    </div>
                </div>
                <div class="control-group">
                    <label>Story Sub Text</label>
                    <div class="input-row">
                        <div class="input-stack">
                            <textarea id="input-t16-sub" class="form-control">Launched in 2005, the {airline became popular for its premium services.} Heavy losses and competition led to its shutdown in 2012.</textarea>
                            <select id="font-t16-sub" class="font-selector"><option value="'Lora', serif">Lora</option><option value="'Montserrat', sans-serif">Montserrat</option></select>
                        </div>
                        <input type="color" id="color-t16-sub" value="#ffffff" title="Text Color">
                    </div>
                </div>
            </div>

            <!-- ==========================================
                 UNIVERSAL OVERLAYS (DATE & LOGO RESTORED)
                 ========================================== -->
            <div class="control-group" style="border-left: 4px solid #ff00ff;">
                <label style="color: #ff00ff;">🗓️ Overlays (Date & Logo)</label>
                <div style="display:flex; gap:10px; margin-bottom: 10px;">
                    <div class="input-stack">
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">Date (Num)</label>
                        <input type="text" id="input-date-num" class="form-control" value="03">
                    </div>
                    <div class="input-stack">
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">Month</label>
                        <input type="text" id="input-date-month" class="form-control" value="APRIL">
                    </div>
                </div>
                
                <div style="margin-bottom: 10px;">
                    <label style="font-size:10px; color:#888; margin-bottom:2px;">Upload Logo</label>
                    <div class="file-upload-wrapper" style="height: 50px;">
                        <span style="color: #888; font-weight: bold; pointer-events: none; font-size:12px;">🛡️ Choose Logo Image</span>
                        <input type="file" id="logo-upload" accept="image/*">
                    </div>
                </div>

                <div style="display:flex; gap:10px;">
                    <div class="input-stack">
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">Date Box Size</label>
                        <input type="range" id="size-date" min="0.5" max="2" step="0.1" value="1">
                    </div>
                    <div class="input-stack">
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">Logo & Text Size</label>
                        <input type="range" id="size-logo" min="50" max="300" value="180">
                    </div>
                </div>
            </div>

            <!-- ==========================================
                 UNIVERSAL MEDIA & LAYOUT CONTROLS
                 ========================================== -->

            <div class="control-group">
                <label>Upload Background Media</label>
                <div class="file-upload-wrapper">
                    <span style="color: #888; font-weight: bold; pointer-events: none;">📸 Image / Video</span>
                    <input type="file" id="media-upload" accept="image/*,video/*">
                </div>
            </div>

            <div class="control-group" style="border-left: 4px solid #00cc44;">
                <label>🎚️ Advanced Transformation Controls</label>
                <div style="display: flex; flex-direction: column; gap: 12px; margin-top: 10px;">
                    
                    <!-- NEW DYNAMIC SIZE SLIDERS (1-16) -->
                    <div id="size-group-t1" class="theme-size-group">
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">BREAKING Size</label>
                        <input type="range" id="size-breaking" min="100" max="350" value="215">
                        <label style="font-size:10px; color:#888; margin-bottom:2px; margin-top:10px; display:block;">Main Headline Size</label>
                        <input type="range" id="size-t1-headline" min="20" max="100" value="50">
                        <label style="font-size:10px; color:#888; margin-bottom:2px; margin-top:10px; display:block;">Small Paragraph Size</label>
                        <input type="range" id="size-t1-sub" min="10" max="50" value="20">
                    </div>
                    <div id="size-group-t2" class="theme-size-group" style="display: none;">
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">BREAKING Size</label>
                        <input type="range" id="size-breaking-t2" min="100" max="350" value="215">
                        <label style="font-size:10px; color:#888; margin-bottom:2px; margin-top:10px; display:block;">Red Line 1 Size</label>
                        <input type="range" id="size-t2-red1" min="20" max="80" value="42">
                        <label style="font-size:10px; color:#888; margin-bottom:2px; margin-top:10px; display:block;">Red Line 2 Size</label>
                        <input type="range" id="size-t2-red2" min="20" max="80" value="42">
                        <label style="font-size:10px; color:#888; margin-bottom:2px; margin-top:10px; display:block;">Yellow Headline Size</label>
                        <input type="range" id="size-t2-yellow" min="20" max="80" value="46">
                        <label style="font-size:10px; color:#888; margin-bottom:2px; margin-top:10px; display:block;">White Italic Size</label>
                        <input type="range" id="size-t2-sub" min="15" max="50" value="24">
                    </div>
                    <div id="size-group-t3" class="theme-size-group" style="display: none;">
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">Quote Size</label>
                        <input type="range" id="size-t3-quote" min="20" max="100" value="55">
                        <label style="font-size:10px; color:#888; margin-bottom:2px; margin-top:10px; display:block;">Author Size</label>
                        <input type="range" id="size-t3-author" min="15" max="60" value="28">
                    </div>
                    <div id="size-group-t4" class="theme-size-group" style="display: none;">
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">Headline Size</label>
                        <input type="range" id="size-t4-head" min="30" max="150" value="80">
                        <label style="font-size:10px; color:#888; margin-bottom:2px; margin-top:10px; display:block;">Sub-Text Size</label>
                        <input type="range" id="size-t4-sub" min="15" max="60" value="30">
                    </div>
                    <div id="size-group-t5" class="theme-size-group" style="display: none;">
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">Alert Line Size</label>
                        <input type="range" id="size-t5-alert" min="15" max="60" value="35">
                        <label style="font-size:10px; color:#888; margin-bottom:2px; margin-top:10px; display:block;">Headline Size</label>
                        <input type="range" id="size-t5-head" min="30" max="120" value="70">
                    </div>
                    <div id="size-group-t6" class="theme-size-group" style="display: none;">
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">Top Box Size</label>
                        <input type="range" id="size-t6-top" min="20" max="100" value="50">
                        <label style="font-size:10px; color:#888; margin-bottom:2px; margin-top:10px; display:block;">Bottom Box Size</label>
                        <input type="range" id="size-t6-bot" min="30" max="150" value="80">
                    </div>
                    <div id="size-group-t7" class="theme-size-group" style="display: none;">
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">Title Size</label>
                        <input type="range" id="size-t7-title" min="40" max="150" value="85">
                        <label style="font-size:10px; color:#888; margin-bottom:2px; margin-top:10px; display:block;">Subtitle Size</label>
                        <input type="range" id="size-t7-sub" min="10" max="50" value="22">
                    </div>
                    <div id="size-group-t8" class="theme-size-group" style="display: none;">
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">Top Bar Text Size</label>
                        <input type="range" id="size-t8-top" min="40" max="150" value="90">
                        <label style="font-size:10px; color:#888; margin-bottom:2px; margin-top:10px; display:block;">Bottom Box Title Size</label>
                        <input type="range" id="size-t8-bot-title" min="20" max="80" value="45">
                        <label style="font-size:10px; color:#888; margin-bottom:2px; margin-top:10px; display:block;">Bottom Box Sub Size</label>
                        <input type="range" id="size-t8-bot-sub" min="10" max="50" value="24">
                    </div>
                    <div id="size-group-t9" class="theme-size-group" style="display: none;">
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">Main Title Size</label>
                        <input type="range" id="size-t9-title" min="20" max="100" value="55">
                        <label style="font-size:10px; color:#888; margin-bottom:2px; margin-top:10px; display:block;">Quote Box Size</label>
                        <input type="range" id="size-t9-quote" min="20" max="80" value="40">
                        <label style="font-size:10px; color:#888; margin-bottom:2px; margin-top:10px; display:block;">Footer Size</label>
                        <input type="range" id="size-t9-foot" min="15" max="60" value="30">
                    </div>
                    <div id="size-group-t10" class="theme-size-group" style="display: none;">
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">Badge Size</label>
                        <input type="range" id="size-t10-badge" min="20" max="80" value="45">
                        <label style="font-size:10px; color:#888; margin-bottom:2px; margin-top:10px; display:block;">Body Text Size</label>
                        <input type="range" id="size-t10-text" min="20" max="100" value="48">
                    </div>
                    <div id="size-group-t11" class="theme-size-group" style="display: none;">
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">Headline Size</label>
                        <input type="range" id="size-t11-head" min="20" max="100" value="50">
                        <label style="font-size:10px; color:#888; margin-bottom:2px; margin-top:10px; display:block;">Body Text Size</label>
                        <input type="range" id="size-t11-body" min="20" max="80" value="42">
                    </div>
                    <div id="size-group-t12" class="theme-size-group" style="display: none;">
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">Documentary Text Size</label>
                        <input type="range" id="size-t12-text" min="30" max="120" value="65">
                    </div>
                    <div id="size-group-t13" class="theme-size-group" style="display: none;">
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">Impact Title Size</label>
                        <input type="range" id="size-t13-title" min="40" max="180" value="100">
                        <label style="font-size:10px; color:#888; margin-bottom:2px; margin-top:10px; display:block;">Sub-Text Size</label>
                        <input type="range" id="size-t13-sub" min="20" max="80" value="38">
                    </div>
                    <div id="size-group-t14" class="theme-size-group" style="display: none;">
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">SHOCKING Size</label>
                        <input type="range" id="size-t14-shock" min="50" max="200" value="110">
                        <label style="font-size:10px; color:#888; margin-bottom:2px; margin-top:10px; display:block;">Red Box Alert Size</label>
                        <input type="range" id="size-t14-red" min="15" max="60" value="28">
                    </div>
                    <div id="size-group-t15" class="theme-size-group" style="display: none;">
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">Line 1 Size</label>
                        <input type="range" id="size-t15-l1" min="20" max="100" value="50">
                        <label style="font-size:10px; color:#888; margin-bottom:2px; margin-top:10px; display:block;">Line 2 Size</label>
                        <input type="range" id="size-t15-l2" min="20" max="100" value="50">
                    </div>
                    <div id="size-group-t16" class="theme-size-group" style="display: none;">
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">Top Story Title Size</label>
                        <input type="range" id="size-t16-title" min="30" max="150" value="70">
                        <label style="font-size:10px; color:#888; margin-bottom:2px; margin-top:10px; display:block;">Sub Text Size</label>
                        <input type="range" id="size-t16-sub" min="15" max="80" value="38">
                    </div>

                    <div style="border-top: 1px solid #444; padding-top: 10px; margin-top: 5px;">
                        <label style="font-size:10px; color:#ffcc00; margin-bottom:2px;">Global Image/Video Zoom</label>
                        <input type="range" id="slider-zoom" min="50" max="250" value="100">
                    </div>
                    <div>
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">Media Pan X (Left/Right)</label>
                        <input type="range" id="slider-x" min="0" max="100" value="50">
                    </div>
                    <div>
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">Media Pan Y (Up/Down)</label>
                        <input type="range" id="slider-y" min="0" max="100" value="50">
                    </div>
                    
                    <div style="border-top: 1px solid #444; padding-top: 10px; margin-top: 5px;">
                        <label style="font-size:10px; color:#00f0ff; margin-bottom:2px;">Blur Overlay Coverage (Grow small to big)</label>
                        <input type="range" id="slider-blur" min="0" max="1350" value="165">
                    </div>
                    
                    <!-- NEW BLUR/SHADE COLOR -->
                    <div style="display:flex; align-items:center; gap: 10px;">
                        <label style="font-size:10px; color:#00f0ff; margin-bottom:2px;">Blur Shading Color:</label>
                        <input type="color" id="color-blur-shade" value="#ffffff" title="Change Blur Fade Color">
                    </div>
                </div>
            </div>

        </div>

        <div class="action-buttons">
            <!-- RESTORED BUTTONS -->
            <div style="display: flex; gap: 10px; margin-bottom: 5px;">
                <button id="btn-reset-style" class="btn btn-secondary" style="font-size: 13px; padding: 12px; flex: 1;">Reset Style</button>
                <button id="btn-auto-style" class="btn btn-secondary" style="font-size: 13px; padding: 12px; flex: 1;">Auto Style</button>
            </div>
            
            <!-- NEW LOCK EDITS BUTTON -->
            <button id="btn-lock-ui" class="btn btn-warning" style="margin-bottom: 5px;">
                🔓 LOCK UI / EDITS
            </button>

            <button id="btn-download-vid" class="btn btn-success" style="display: none;">
                📥 DOWNLOAD HD MP4 VIDEO
            </button>
            <button id="btn-download-img" class="btn btn-primary">
                Download HD Image Post
            </button>
        </div>
    </aside>

    <main class="preview-area">
        
        <div id="recording-overlay">
            <h2 id="rec-status">STITCHING HD VIDEO & TEXT...</h2>
            <p>Please wait. Do not close the browser or tab.</p>
        </div>

        <div class="canvas-scaler" id="scaler">
            
            <div id="post-canvas" class="instagram-post">
                
                <div id="zoom-wrapper" style="width: 100%; height: 100%; display: flex; flex-direction: column; transform: scale(1); transform-origin: center center; position:relative;">
                    
                    <!-- THEME 1 HEADER -->
                    <div class="post-header-area" id="header-theme-1">
                        <div class="main-breaking" id="render-breaking">BREAKING</div>
                        <div class="sub-headline" id="render-headline">
                            MP RAGHAV CHADHA REPLIED AFTER <span class="highlight-1">AAP STOPPED HIM</span> FROM SPEAKING IN PARLIAMENT
                        </div>
                        <div class="sub-italic-headline" id="render-sub-italic-t1-display" style="color: #333333; margin-top: 15px; font-weight: 700; text-transform: uppercase; font-style: normal; font-size: 20px;">
                            India was set to receive Iranian oil after nearly <span class="highlight-2">7 years</span>, but it was rerouted.
                        </div>
                    </div>

                    <!-- THEME 2 HEADER -->
                    <div class="post-header-area" id="header-theme-2" style="display: none;">
                        <div class="main-breaking-v2" id="render-breaking-t2">BREAKING<span style="color:#ffcc00;">!</span></div>
                        <div class="red-headline-container">
                            <div class="red-headline-line" id="render-red-1">SHIP CARRYING 600,000 BARRELS IRANIAN</div>
                            <div class="red-headline-line" id="render-red-2">CRUDE CHANGES ROUTE FROM INDIA TO</div>
                        </div>
                        <div class="yellow-headline-line" id="render-yellow">CHINA MIDWAY <span class="highlight-1">DUE TO US SANCTIONS</span>.</div>
                        <div class="sub-italic-headline" id="render-sub-italic">India was set to receive Iranian oil after nearly 7 years, but it was rerouted.</div>
                    </div>

                    <!-- THEME 3 HEADER -->
                    <div class="post-header-area" id="header-theme-3" style="display: none;">
                        <div class="minimal-quote-text" id="render-t3-quote">"<span class="highlight-1">SUCCESS</span> IS NOT FINAL, FAILURE IS NOT FATAL: IT IS THE COURAGE TO CONTINUE THAT COUNTS."</div>
                        <div class="minimal-quote-author" id="render-t3-author">- WINSTON CHURCHILL</div>
                    </div>

                    <!-- THEME 4 HEADER -->
                    <div class="post-header-area" id="header-theme-4" style="display: none;">
                        <div class="split-main-headline" id="render-t4-head">NEW ERA OF <span class="highlight-1">CINEMA</span> BEGINS</div>
                        <div class="split-sub-headline" id="render-t4-sub">Directors are now moving towards purely digital environments for modern blockbusters.</div>
                    </div>

                    <!-- THEME 5 HEADER -->
                    <div class="post-header-area" id="header-theme-5" style="display: none;">
                        <div class="cyber-alert" id="render-t5-alert">[ SYSTEM_OVERRIDE_ACTIVE ]</div>
                        <div class="cyber-headline" id="render-t5-head">GLOBAL NETWORKS <span class="highlight-1">COMPROMISED</span> IN MASSIVE ATTACK</div>
                    </div>

                    <!-- THEME 6 HEADER -->
                    <div class="post-header-area" id="header-theme-6" style="display: none;">
                        <div class="sports-box-1" id="render-t6-top">FULL TIME RESULT</div>
                        <div class="sports-box-2" id="render-t6-bot"><span class="highlight-1">INDIA</span> WON BY 5 WICKETS</div>
                    </div>

                    <!-- THEME 7 HEADER -->
                    <div class="post-header-area" id="header-theme-7" style="display: none;">
                        <div class="editorial-title" id="render-t7-title">The Future of <span class="highlight-1">Modern</span> Architecture</div>
                        <div class="editorial-sub" id="render-t7-sub">SPECIAL EDITION  |  VOL. 42</div>
                    </div>

                    <!-- THEME 8 HEADER (Time4Media) -->
                    <div class="post-header-area" id="header-theme-8" style="display: none;">
                        <div class="t8-top-text" id="render-t8-top">BADMINTON WAS INVENTED IN PUNE, INDIA</div>
                    </div>
                    <div class="t8-bottom-box" id="footer-theme-8" style="display: none;">
                        <div class="t8-bot-title" id="render-t8-bot-title">Badminton started in Pune as "<span class="highlight-1">Poona</span>" before British officers renamed and <span class="highlight-2">popularized</span> it</div>
                        <div class="t8-bot-sub" id="render-t8-bot-sub">The sport was played by locals in India long before it got global recognition, making it a hidden part of Indian history.</div>
                    </div>

                    <!-- THEME 9 HEADER (IND Vibe) -->
                    <div class="post-header-area" id="header-theme-9" style="display: none;">
                        <div class="t9-gradient" id="gradient-t9"></div>
                        <div class="t9-title" id="render-t9-title">PM MODI ON DHURANDHAR</div>
                        <div class="t9-quote-box">
                            <div class="t9-quote-line" id="render-t9-q1">They Said Dhurandhar, Kerala</div>
                            <div class="t9-quote-line" id="render-t9-q2">Files Are Lies: PM Modi Replies</div>
                        </div>
                        <div class="t9-footer" id="render-t9-foot">UDF | Swipe To <span class="highlight-1">WATCH</span></div>
                    </div>

                    <!-- THEME 10 HEADER (ShareSanskar) -->
                    <div class="post-header-area" id="header-theme-10" style="display: none;">
                        <div class="t10-badge" id="render-t10-badge">BREAKING !!</div>
                        <div class="t10-text" id="render-t10-text"><span class="highlight-1">For the first time</span> in Nepal's history Balen's government, <span class="highlight-3">will publicly apologize</span> to Dalit and marginalized communities for the past discrimination and <span class="highlight-1">start reforms for justice.</span></div>
                    </div>

                    <!-- THEME 11 HEADER (Comedy) -->
                    <div class="post-header-area" id="header-theme-11" style="display: none;">
                        <div class="t11-box" id="render-t11-box">
                            <div class="t11-head" id="render-t11-head">HEADLINE: 😆</div>
                            <div class="t11-body" id="render-t11-body"><span class="highlight-3">Nagpur</span> Zilha Parishad Staff organised <span class="highlight-2">cultural</span> event, <span class="highlight-2">judge</span> honored during celebrations</div>
                        </div>
                    </div>

                    <!-- THEME 12 HEADER (Rawalpindi) -->
                    <div class="post-header-area" id="header-theme-12" style="display: none;">
                        <div class="t12-gradient" id="gradient-t12"></div>
                        <div class="t12-text" id="render-t12-text">Iran Releases First Ever Video of <span class="highlight-2">Mojtaba Khamenei</span> From <span class="highlight-1">War Room</span></div>
                    </div>

                    <!-- THEME 13 HEADER (One Vision) -->
                    <div class="post-header-area" id="header-theme-13" style="display: none;">
                        <div class="t13-title" id="render-t13-title">HISTORY MADE!</div>
                        <div class="t13-sub" id="render-t13-sub">Dr. Menaka Guruswamy takes oath in the <span class="highlight-2">Rajya Sabha</span>, becoming the country's first openly queer MP.</div>
                    </div>

                    <!-- THEME 14 HEADER (Shocking) -->
                    <div class="post-header-area" id="header-theme-14" style="display: none;">
                        <div class="t14-shock" id="render-t14-shock">SHOCKING</div>
                        <div class="t14-red-box" id="render-t14-red">ARMY OFFICER SHARES HAUNTING MIDNIGHT VIDEO, SAYS JUDGING SOLDIERS IS EASY BUT LIVING THEIR REALITY TAKES COURAGE</div>
                    </div>

                    <!-- THEME 15 HEADER (NBT Curve) -->
                    <div class="post-header-area" id="header-theme-15" style="display: none;">
                        <div class="t15-curve" id="render-t15-curve"></div>
                        <div class="t15-text-1" id="render-t15-L1">गुजरात में बन रहा भारत का तीसरा</div>
                        <div class="t15-text-2" id="render-t15-L2">सैटेलाइट लॉन्च सेंटर? जानें कहां होगा</div>
                    </div>

                    <!-- THEME 16 HEADER (Desh Top) -->
                    <div class="post-header-area" id="header-theme-16" style="display: none;">
                        <div class="t16-gradient" id="gradient-t16"></div>
                        <div class="t16-title" id="render-t16-title">THE RISE & FALL OF <span class="highlight-1">KINGFISHER</span> AIRLINES</div>
                        <div class="t16-sub" id="render-t16-sub">Launched in 2005, the <span class="highlight-1">airline became popular for its premium services.</span> Heavy losses and competition led to its shutdown in 2012.</div>
                    </div>

                    <!-- MEDIA AREA FOR ALL THEMES -->
                    <div class="post-media-area" id="post-media-area">
                        <div id="blur-overlay-div" class="blur-overlay-div"></div>
                        
                        <div id="media-zoom-wrapper" style="width: 100%; height: 100%; transform: scale(1); transform-origin: center center; position: absolute; top: 0; left: 0;">
                            <img id="render-media-img" class="media-content" src="" style="display:none;" alt="">
                            <video id="render-media-vid" class="media-content" style="display:none;" loop playsinline webkit-playsinline muted crossorigin="anonymous"></video>
                        </div>
                        
                        <!-- RESTORED OVERLAYS -->
                        <div class="overlay-layer" id="overlays-theme-1">
                            <div class="date-box" id="render-date-box">
                                <div class="date-number" id="render-date-num">03</div>
                                <div class="date-month" id="render-date-month">APRIL</div>
                            </div>

                            <div class="branding-corner" id="render-branding-wrapper">
                                <img id="render-logo" class="custom-logo" src="" alt="Logo">
                                <div class="brand-text">
                                    INDIA <span>GLOBALCINE</span>
                                </div>
                            </div>
                        </div>
                    </div>
                
                </div>
            </div>

        </div>
    </main>

    <div class="mobile-modal" id="download-modal">
        <h2 style="color:white; margin-bottom: 20px; text-align:center;">✅ HD MP4 Video Ready!</h2>
        <video id="final-video-preview" controls playsinline webkit-playsinline loop></video>
        <a id="force-download-link" class="download-btn-massive" href="#" download="IndiaGlobalCine_Premium_Video.mp4">
            📥 CLICK HERE TO SAVE VIDEO
        </a>
        <button class="close-btn" onclick="document.getElementById('download-modal').classList.remove('active')">Close</button>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            
            function showNotification(message) {
                const toast = document.getElementById('advanced-toast');
                toast.innerHTML = message;
                toast.classList.add('show');
                setTimeout(() => toast.classList.remove('show'), 4000);
            }

            function scaleCanvas() {
                const scaler = document.getElementById('scaler');
                const post = document.getElementById('post-canvas');
                const parentW = scaler.parentElement.offsetWidth;
                const parentH = scaler.parentElement.offsetHeight;
                const scale = Math.min(parentW / 1080, parentH / 1350) * 0.95;
                post.style.transform = `scale(${scale})`;
                scaler.style.width = `${1080 * scale}px`;
                scaler.style.height = `${1350 * scale}px`;
            }
            window.addEventListener('resize', scaleCanvas);
            scaleCanvas();

            // --- UNIVERSAL MULTI-HIGHLIGHT SYSTEM ---
            function applyHighlight(text) {
                if(!text) return "";
                let html = text.replace(/\{(.*?)\}/g, '<span class="highlight-1">$1</span>');
                html = html.replace(/\[(.*?)\]/g, '<span class="highlight-2">$1</span>');
                html = html.replace(/\*(.*?)\*/g, '<span class="highlight-3">$1</span>');
                return html;
            }

            // Bind Global Highlight Colors
            const cssRoot = document.documentElement.style;
            document.getElementById('hl1-bg').addEventListener('input', e => cssRoot.setProperty('--hl1-bg-color', e.target.value));
            document.getElementById('hl1-text').addEventListener('input', e => cssRoot.setProperty('--hl1-text-color', e.target.value));
            document.getElementById('hl2-bg').addEventListener('input', e => cssRoot.setProperty('--hl2-bg-color', e.target.value));
            document.getElementById('hl2-text').addEventListener('input', e => cssRoot.setProperty('--hl2-text-color', e.target.value));
            document.getElementById('hl3-bg').addEventListener('input', e => cssRoot.setProperty('--hl3-bg-color', e.target.value));
            document.getElementById('hl3-text').addEventListener('input', e => cssRoot.setProperty('--hl3-text-color', e.target.value));

            // --- NEW: BLUR/SHADING COLOR SYSTEM ---
            function hexToRgb(hex) {
                var result = /^#?([a-f\d]{2})([a-f\d]{2})([a-f\d]{2})$/i.exec(hex);
                return result ? {
                    r: parseInt(result[1], 16),
                    g: parseInt(result[2], 16),
                    b: parseInt(result[3], 16)
                } : null;
            }

            document.getElementById('color-blur-shade').addEventListener('input', (e) => {
                const rgb = hexToRgb(e.target.value);
                if(rgb) {
                    cssRoot.setProperty('--blur-shade-r', rgb.r);
                    cssRoot.setProperty('--blur-shade-g', rgb.g);
                    cssRoot.setProperty('--blur-shade-b', rgb.b);
                }
            });


            // --- INPUT BINDING FACTORY ---
            function bindControl(inputId, targetId, colorId = null, bgId = null, fontId = null, isTextarea = false) {
                const inputEl = document.getElementById(inputId);
                const targetEl = document.getElementById(targetId);
                if(inputEl && targetEl) {
                    inputEl.addEventListener('input', e => {
                        targetEl.innerHTML = applyHighlight(isTextarea ? e.target.value.replace(/\n/g, '<br>') : e.target.value);
                    });
                }
                if(colorId && document.getElementById(colorId)) {
                    document.getElementById(colorId).addEventListener('input', e => { targetEl.style.color = e.target.value; });
                }
                if(bgId && document.getElementById(bgId)) {
                    document.getElementById(bgId).addEventListener('input', e => {
                        if(targetId === 'render-t15-curve') targetEl.style.backgroundColor = e.target.value;
                        else if(targetId === 'render-t11-box') targetEl.style.borderLeftColor = e.target.value;
                        else if(targetId === 'render-t8-top') targetEl.parentElement.style.backgroundColor = e.target.value;
                        else targetEl.style.backgroundColor = e.target.value;
                    });
                }
                if(fontId && document.getElementById(fontId)) {
                    document.getElementById(fontId).addEventListener('change', e => { targetEl.style.fontFamily = e.target.value; });
                }
            }

            // BINDING ALL 16 THEMES
            bindControl('input-breaking', 'render-breaking', 'color-t1-breaking', null, 'font-t1-breaking');
            bindControl('input-headline', 'render-headline', 'color-t1-headline', null, 'font-t1-headline', true);
            bindControl('input-sub-italic-t1', 'render-sub-italic-t1-display', 'color-t1-sub', null, 'font-t1-sub');

            bindControl('input-red-1', 'render-red-1', 'color-t2-red1', 'color-t2-redbox', 'font-t2-red');
            bindControl('input-red-2', 'render-red-2', 'color-t2-red1', 'color-t2-redbox', 'font-t2-red');
            bindControl('input-yellow', 'render-yellow', 'color-t2-yellow', null, 'font-t2-yellow');
            bindControl('input-sub-italic', 'render-sub-italic', 'color-t2-sub', null, 'font-t2-sub');

            bindControl('input-t3-quote', 'render-t3-quote', 'color-t3-quote', null, 'font-t3-quote', true);
            bindControl('input-t3-author', 'render-t3-author', 'color-t3-author', null, 'font-t3-author');

            bindControl('input-t4-head', 'render-t4-head', 'color-t4-head', null, 'font-t4-head', true);
            bindControl('input-t4-sub', 'render-t4-sub', 'color-t4-sub', null, 'font-t4-sub', true);

            bindControl('input-t5-alert', 'render-t5-alert', 'color-t5-alert', null, 'font-t5-alert');
            bindControl('input-t5-head', 'render-t5-head', 'color-t5-head', null, 'font-t5-head', true);

            bindControl('input-t6-top', 'render-t6-top', 'color-t6-top-text', 'color-t6-top-bg', 'font-t6-top');
            bindControl('input-t6-bot', 'render-t6-bot', 'color-t6-bot-text', 'color-t6-bot-bg', 'font-t6-bot');

            bindControl('input-t7-title', 'render-t7-title', 'color-t7-title', null, 'font-t7-title', true);
            bindControl('input-t7-sub', 'render-t7-sub', 'color-t7-sub', null, 'font-t7-sub');

            bindControl('input-t8-top', 'render-t8-top', 'color-t8-top-text', 'color-t8-top-bg', 'font-t8-top');
            bindControl('input-t8-bot-title', 'render-t8-bot-title', 'color-t8-bot-title', 'color-t8-bot-bg', 'font-t8-bot-title', true);
            bindControl('input-t8-bot-sub', 'render-t8-bot-sub', 'color-t8-bot-sub', null, 'font-t8-bot-sub', true);
            document.getElementById('color-t8-bot-bg').addEventListener('input', e=> document.getElementById('footer-theme-8').style.backgroundColor = e.target.value);

            bindControl('input-t9-title', 'render-t9-title', 'color-t9-title', null, 'font-t9-title', true);
            bindControl('input-t9-q1', 'render-t9-q1', 'color-t9-q-text', 'color-t9-q-bg', 'font-t9-quote');
            bindControl('input-t9-q2', 'render-t9-q2', 'color-t9-q-text', 'color-t9-q-bg', 'font-t9-quote');
            bindControl('input-t9-foot', 'render-t9-foot', 'color-t9-foot', null, 'font-t9-foot');

            bindControl('input-t10-badge', 'render-t10-badge', 'color-t10-badge-text', 'color-t10-badge-bg', 'font-t10-badge');
            bindControl('input-t10-text', 'render-t10-text', 'color-t10-text', null, 'font-t10-text', true);
            document.getElementById('color-t10-bg').addEventListener('input', e=> document.getElementById('header-theme-10').style.backgroundColor = e.target.value);

            bindControl('input-t11-head', 'render-t11-head', 'color-t11-head-text', null, 'font-t11-head');
            bindControl('input-t11-body', 'render-t11-body', 'color-t11-body-text', null, 'font-t11-body', true);
            document.getElementById('color-t11-border').addEventListener('input', e=> document.getElementById('render-t11-box').style.borderLeftColor = e.target.value);
            document.getElementById('color-t11-box-bg').addEventListener('input', e=> document.getElementById('render-t11-box').style.backgroundColor = e.target.value);

            bindControl('input-t12-text', 'render-t12-text', 'color-t12-text', null, 'font-t12-text', true);

            bindControl('input-t13-title', 'render-t13-title', 'color-t13-title', null, 'font-t13-title');
            bindControl('input-t13-sub', 'render-t13-sub', 'color-t13-sub', null, 'font-t13-sub', true);

            bindControl('input-t14-shock', 'render-t14-shock', 'color-t14-shock', null, 'font-t14-shock');
            bindControl('input-t14-red', 'render-t14-red', 'color-t14-red-text', 'color-t14-red-bg', 'font-t14-red', true);
            document.getElementById('color-t14-bg').addEventListener('input', e=> document.getElementById('post-canvas').style.backgroundColor = e.target.value);

            bindControl('input-t15-L1', 'render-t15-L1', 'color-t15-L1', null, 'font-t15-L1');
            bindControl('input-t15-L2', 'render-t15-L2', 'color-t15-L2', null, 'font-t15-L2');
            document.getElementById('color-t15-bg').addEventListener('input', e=> { document.getElementById('post-canvas').style.backgroundColor = e.target.value; document.getElementById('header-theme-15').style.backgroundColor = e.target.value;});
            document.getElementById('color-t15-curve').addEventListener('input', e=> document.getElementById('render-t15-curve').style.backgroundColor = e.target.value);

            bindControl('input-t16-title', 'render-t16-title', 'color-t16-title', null, 'font-t16-title');
            bindControl('input-t16-sub', 'render-t16-sub', 'color-t16-sub', null, 'font-t16-sub', true);

            // --- RESTORED DATE BINDINGS ---
            document.getElementById('input-date-num').addEventListener('input', e => document.getElementById('render-date-num').innerHTML = applyHighlight(e.target.value));
            document.getElementById('input-date-month').addEventListener('input', e => document.getElementById('render-date-month').innerHTML = applyHighlight(e.target.value.toUpperCase()));

            // --- NEW: DYNAMIC SIZE MAPPINGS (ALL 1-16) ---
            const sizeMappings = {
                'size-breaking': ['render-breaking', 1],
                'size-breaking-t2': ['render-breaking-t2', 0.9],
                'size-t1-headline': ['render-headline', 1],
                'size-t1-sub': ['render-sub-italic-t1-display', 1],
                'size-t2-red1': ['render-red-1', 1],
                'size-t2-red2': ['render-red-2', 1],
                'size-t2-yellow': ['render-yellow', 1],
                'size-t2-sub': ['render-sub-italic', 1],
                'size-t3-quote': ['render-t3-quote', 1],
                'size-t3-author': ['render-t3-author', 1],
                'size-t4-head': ['render-t4-head', 1],
                'size-t4-sub': ['render-t4-sub', 1],
                'size-t5-alert': ['render-t5-alert', 1],
                'size-t5-head': ['render-t5-head', 1],
                'size-t6-top': ['render-t6-top', 1],
                'size-t6-bot': ['render-t6-bot', 1],
                'size-t7-title': ['render-t7-title', 1],
                'size-t7-sub': ['render-t7-sub', 1],
                'size-t8-top': ['render-t8-top', 1],
                'size-t8-bot-title': ['render-t8-bot-title', 1],
                'size-t8-bot-sub': ['render-t8-bot-sub', 1],
                'size-t9-title': ['render-t9-title', 1],
                'size-t9-foot': ['render-t9-foot', 1],
                'size-t10-badge': ['render-t10-badge', 1],
                'size-t10-text': ['render-t10-text', 1],
                'size-t11-head': ['render-t11-head', 1],
                'size-t11-body': ['render-t11-body', 1],
                'size-t12-text': ['render-t12-text', 1],
                'size-t13-title': ['render-t13-title', 1],
                'size-t13-sub': ['render-t13-sub', 1],
                'size-t14-shock': ['render-t14-shock', 1],
                'size-t14-red': ['render-t14-red', 1],
                'size-t15-l1': ['render-t15-L1', 1],
                'size-t15-l2': ['render-t15-L2', 1],
                'size-t16-title': ['render-t16-title', 1],
                'size-t16-sub': ['render-t16-sub', 1],
            };

            for (const [inputId, [targetId, multiplier]] of Object.entries(sizeMappings)) {
                const el = document.getElementById(inputId);
                if(el) {
                    el.addEventListener('input', e => {
                        const target = document.getElementById(targetId);
                        if(target) target.style.fontSize = `${e.target.value * multiplier}px`;
                    });
                }
            }

            // Special mapping for Theme 9 Quote (affects 2 lines)
            const sizeT9Quote = document.getElementById('size-t9-quote');
            if (sizeT9Quote) {
                sizeT9Quote.addEventListener('input', e => {
                    document.getElementById('render-t9-q1').style.fontSize = `${e.target.value}px`;
                    document.getElementById('render-t9-q2').style.fontSize = `${e.target.value}px`;
                });
            }

            // --- RESTORED LOGO & DATE SIZES ---
            document.getElementById('size-date').addEventListener('input', e => {
                document.getElementById('render-date-box').style.transform = `scale(${e.target.value})`;
            });
            document.getElementById('size-logo').addEventListener('input', e => {
                document.getElementById('render-branding-wrapper').style.transform = `scale(${e.target.value / 180})`;
                document.getElementById('render-branding-wrapper').style.transformOrigin = `bottom right`;
            });


            // --- MEDIA & TRANSFORMS ---
            const mediaX = document.getElementById('slider-x');
            const mediaY = document.getElementById('slider-y');
            const blurSlider = document.getElementById('slider-blur');
            const zoomSlider = document.getElementById('slider-zoom');
            const imgEl = document.getElementById('render-media-img');
            const vidEl = document.getElementById('render-media-vid');
            const blurDiv = document.getElementById('blur-overlay-div');
            const mediaZoomWrapper = document.getElementById('media-zoom-wrapper');

            function updateMediaPos() {
                const pos = `${mediaX.value}% ${mediaY.value}%`;
                imgEl.style.objectPosition = pos;
                vidEl.style.objectPosition = pos;
            }
            mediaX.addEventListener('input', updateMediaPos);
            mediaY.addEventListener('input', updateMediaPos);
            
            // RESTORED: BLUR SLIDER LOGIC (Small to Big mapping to height)
            blurSlider.addEventListener('input', (e) => blurDiv.style.height = `${e.target.value}px`);
            zoomSlider.addEventListener('input', (e) => mediaZoomWrapper.style.transform = `scale(${e.target.value / 100})`);

            // --- 16 THEME SWITCHER LOGIC ---
            document.getElementById('layout-selector').addEventListener('change', function(e) {
                const theme = e.target.value;
                const postCanvas = document.getElementById('post-canvas');
                
                // Hide all panels & headers
                document.querySelectorAll('.theme-controls-panel').forEach(el => el.style.display = 'none');
                document.querySelectorAll('.post-header-area').forEach(el => el.style.display = 'none');
                document.querySelectorAll('[id^="footer-theme-"]').forEach(el => el.style.display = 'none');
                document.querySelectorAll('.theme-size-group').forEach(el => el.style.display = 'none');
                
                // Reset canvas
                postCanvas.className = 'instagram-post';
                postCanvas.style.backgroundColor = '#ffffff'; // default
                blurDiv.classList.remove('theme-global-blur');
                blurSlider.value = 165; blurDiv.style.height = '165px';

                // Map UI display
                if (theme === 'theme-global') {
                    postCanvas.classList.add('theme-global-news');
                    document.getElementById('theme-global-controls').style.display = 'block';
                    document.getElementById('header-theme-2').style.display = 'flex';
                    document.getElementById('size-group-t2').style.display = 'block';
                    blurDiv.classList.add('theme-global-blur');
                    blurSlider.value = 580; blurDiv.style.height = '580px';
                } else if (theme === 'theme-minimal') {
                    postCanvas.classList.add('theme-minimal-quote');
                    document.getElementById('theme-minimal-controls').style.display = 'block';
                    document.getElementById('header-theme-3').style.display = 'block';
                    document.getElementById('size-group-t3').style.display = 'block';
                } else if (theme === 'theme-split') {
                    postCanvas.classList.add('theme-split-screen');
                    document.getElementById('theme-split-controls').style.display = 'block';
                    document.getElementById('header-theme-4').style.display = 'flex';
                    document.getElementById('size-group-t4').style.display = 'block';
                } else if (theme === 'theme-cyber') {
                    postCanvas.classList.add('theme-cyberpunk');
                    document.getElementById('theme-cyber-controls').style.display = 'block';
                    document.getElementById('header-theme-5').style.display = 'block';
                    document.getElementById('size-group-t5').style.display = 'block';
                } else if (theme === 'theme-sports') {
                    postCanvas.classList.add('theme-sports');
                    document.getElementById('theme-sports-controls').style.display = 'block';
                    document.getElementById('header-theme-6').style.display = 'flex';
                    document.getElementById('size-group-t6').style.display = 'block';
                } else if (theme === 'theme-editorial') {
                    postCanvas.classList.add('theme-editorial');
                    document.getElementById('theme-editorial-controls').style.display = 'block';
                    document.getElementById('header-theme-7').style.display = 'flex';
                    document.getElementById('size-group-t7').style.display = 'block';
                } else if (theme === 'theme-t8') {
                    postCanvas.classList.add('theme-t8');
                    document.getElementById('theme-t8-controls').style.display = 'block';
                    document.getElementById('header-theme-8').style.display = 'flex';
                    document.getElementById('footer-theme-8').style.display = 'flex';
                    document.getElementById('size-group-t8').style.display = 'block';
                } else if (theme === 'theme-t9') {
                    postCanvas.classList.add('theme-t9');
                    document.getElementById('theme-t9-controls').style.display = 'block';
                    document.getElementById('header-theme-9').style.display = 'flex';
                    document.getElementById('size-group-t9').style.display = 'block';
                } else if (theme === 'theme-t10') {
                    postCanvas.classList.add('theme-t10');
                    document.getElementById('theme-t10-controls').style.display = 'block';
                    document.getElementById('header-theme-10').style.display = 'flex';
                    document.getElementById('size-group-t10').style.display = 'block';
                } else if (theme === 'theme-t11') {
                    postCanvas.classList.add('theme-t11');
                    document.getElementById('theme-t11-controls').style.display = 'block';
                    document.getElementById('header-theme-11').style.display = 'flex';
                    document.getElementById('size-group-t11').style.display = 'block';
                } else if (theme === 'theme-t12') {
                    postCanvas.classList.add('theme-t12');
                    document.getElementById('theme-t12-controls').style.display = 'block';
                    document.getElementById('header-theme-12').style.display = 'flex';
                    document.getElementById('size-group-t12').style.display = 'block';
                } else if (theme === 'theme-t13') {
                    postCanvas.classList.add('theme-t13');
                    document.getElementById('theme-t13-controls').style.display = 'block';
                    document.getElementById('header-theme-13').style.display = 'flex';
                    document.getElementById('size-group-t13').style.display = 'block';
                } else if (theme === 'theme-t14') {
                    postCanvas.classList.add('theme-t14');
                    document.getElementById('theme-t14-controls').style.display = 'block';
                    document.getElementById('header-theme-14').style.display = 'flex';
                    postCanvas.style.backgroundColor = document.getElementById('color-t14-bg').value;
                    document.getElementById('size-group-t14').style.display = 'block';
                } else if (theme === 'theme-t15') {
                    postCanvas.classList.add('theme-t15');
                    document.getElementById('theme-t15-controls').style.display = 'block';
                    document.getElementById('header-theme-15').style.display = 'flex';
                    postCanvas.style.backgroundColor = document.getElementById('color-t15-bg').value;
                    document.getElementById('size-group-t15').style.display = 'block';
                } else if (theme === 'theme-t16') {
                    postCanvas.classList.add('theme-t16');
                    document.getElementById('theme-t16-controls').style.display = 'block';
                    document.getElementById('header-theme-16').style.display = 'flex';
                    document.getElementById('size-group-t16').style.display = 'block';
                } else {
                    document.getElementById('theme-default-controls').style.display = 'block';
                    document.getElementById('header-theme-1').style.display = 'flex';
                    document.getElementById('size-group-t1').style.display = 'block';
                }
            });

            // --- NEW: LOCK EDITS BUTTON ---
            let isUILocked = false;
            document.getElementById('btn-lock-ui').addEventListener('click', function() {
                isUILocked = !isUILocked;
                const inputs = document.querySelectorAll('.editor-sidebar input, .editor-sidebar select, .editor-sidebar textarea, .editor-sidebar button');
                
                inputs.forEach(el => {
                    // Do not disable the lock button or the download buttons
                    if(el.id !== 'btn-lock-ui' && el.id !== 'btn-download-img' && el.id !== 'btn-download-vid') {
                        el.disabled = isUILocked;
                    }
                });

                if (isUILocked) {
                    this.innerHTML = '🔒 UNLOCK UI / EDITS';
                    this.style.backgroundColor = '#e74c3c';
                    showNotification("🔒 All settings locked for safe downloading!");
                } else {
                    this.innerHTML = '🔓 LOCK UI / EDITS';
                    this.style.backgroundColor = '#f39c12';
                    showNotification("🔓 Settings unlocked!");
                }
            });


            // --- RESTORED: RESET AND AUTO STYLE BUTTONS ---
            document.getElementById('btn-reset-style').addEventListener('click', () => {
                const setVal = (id, val) => {
                    const el = document.getElementById(id);
                    if(el) el.value = val;
                };

                // Reset Sizes & Sliders
                setVal('size-breaking', 215);
                setVal('size-t1-headline', 50);
                setVal('size-t1-sub', 20);
                setVal('size-t2-red1', 42);
                setVal('size-t2-red2', 42);
                setVal('size-t2-yellow', 46);
                setVal('size-t2-sub', 24);
                setVal('size-date', 1);
                setVal('size-logo', 180);
                setVal('slider-zoom', 100);
                setVal('slider-x', 50);
                setVal('slider-y', 50);
                
                let isGlobal = document.getElementById('layout-selector').value === 'theme-global';
                setVal('slider-blur', isGlobal ? 580 : 165);

                // Reset Blur Shading Color
                setVal('color-blur-shade', "#ffffff");
                cssRoot.setProperty('--blur-shade-r', '255');
                cssRoot.setProperty('--blur-shade-g', '255');
                cssRoot.setProperty('--blur-shade-b', '255');

                // Reset Colors
                setVal('color-t1-breaking', "#000000");
                setVal('color-t1-headline', "#000000");
                setVal('color-t1-sub', "#333333");
                setVal('color-t2-red1', "#ffffff");
                setVal('color-t2-redbox', "#cc0000");
                setVal('color-t2-yellow', "#ffcc00");
                setVal('color-t2-sub', "#ffffff");
                
                // Reset Highlight UI variables
                setVal('hl1-bg', "#e61919");
                setVal('hl1-text', "#ffffff");
                setVal('hl2-bg', "#000000");
                setVal('hl2-text', "#ffcc00");
                setVal('hl3-bg', "#00cc44");
                setVal('hl3-text', "#ffffff");
                
                cssRoot.setProperty('--hl1-bg-color', "#e61919");
                cssRoot.setProperty('--hl1-text-color', "#ffffff");
                cssRoot.setProperty('--hl2-bg-color', "#000000");
                cssRoot.setProperty('--hl2-text-color', "#ffcc00");
                cssRoot.setProperty('--hl3-bg-color', "#00cc44");
                cssRoot.setProperty('--hl3-text-color', "#ffffff");

                // Dispatch event trick to force UI to update everything
                const allSlidersAndColors = [
                    'size-breaking', 'size-t1-headline', 'size-t1-sub', 
                    'size-t2-red1', 'size-t2-red2', 'size-t2-yellow', 'size-t2-sub', 
                    'size-date', 'size-logo', 'slider-zoom', 'slider-x', 'slider-y', 'slider-blur', 
                    'color-t1-breaking', 'color-t1-headline', 'color-t1-sub', 
                    'color-t2-red1', 'color-t2-redbox', 'color-t2-yellow', 'color-t2-sub'
                ];
                allSlidersAndColors.forEach(id => {
                    const el = document.getElementById(id);
                    if(el) el.dispatchEvent(new Event('input'));
                });
                
                showNotification("⚙️ Styles Reset to Default!");
            });

            document.getElementById('btn-auto-style').addEventListener('click', () => {
                const setVal = (id, val) => {
                    const el = document.getElementById(id);
                    if(el) el.value = val;
                };

                setVal('color-t1-breaking', "#e61919"); 
                setVal('color-t1-headline', "#222222"); 
                setVal('color-t1-sub', "#555555"); 
                
                setVal('color-t2-red1', "#ffff00"); 
                setVal('color-t2-redbox', "#cc0000"); 
                setVal('color-t2-yellow', "#ffffff"); 
                
                setVal('slider-zoom', 110); 
                
                ['color-t1-breaking', 'color-t1-headline', 'color-t1-sub', 'color-t2-red1', 'color-t2-redbox', 'color-t2-yellow', 'slider-zoom'].forEach(id => {
                    const el = document.getElementById(id);
                    if(el) el.dispatchEvent(new Event('input'));
                });
                showNotification("✨ Auto Aesthetic Style Applied!");
            });


            // --- MEDIA UPLOAD HANDLING ---
            document.getElementById('media-upload').addEventListener('change', function(e) {
                const file = e.target.files[0];
                if (!file) return;

                const fileURL = URL.createObjectURL(file);
                const isVideo = file.type.startsWith('video/');
                const vidDownloadBtn = document.getElementById('btn-download-vid');

                if (isVideo) {
                    imgEl.style.display = 'none'; vidEl.style.display = 'block';
                    vidEl.src = fileURL; vidEl.muted = true; vidEl.play();
                    vidDownloadBtn.style.display = 'block';
                } else {
                    vidEl.style.display = 'none'; vidEl.pause();
                    imgEl.style.display = 'block'; imgEl.src = fileURL;
                    vidDownloadBtn.style.display = 'none';
                }
            });

            document.getElementById('logo-upload').addEventListener('change', function(e) {
                const file = e.target.files[0];
                if (!file) return;
                document.getElementById('render-logo').src = URL.createObjectURL(file);
                document.getElementById('render-logo').style.display = 'block'; 
            });

            // --- HD IMAGE DOWNLOADER ---
            document.getElementById('btn-download-img').addEventListener('click', function() {
                const postCanvas = document.getElementById('post-canvas');
                const originalTransform = postCanvas.style.transform;
                postCanvas.style.transform = 'none';
                
                const btn = this;
                const originalText = btn.innerHTML;
                btn.innerHTML = 'GENERATING HD IMAGE...';
                btn.disabled = true;

                html2canvas(postCanvas, { scale: 2, useCORS: true, backgroundColor: null }).then(canvas => {
                    const link = document.createElement('a');
                    link.download = `IndiaGlobalCine_Premium_${new Date().getTime()}.jpg`;
                    link.href = canvas.toDataURL('image/jpeg', 1.0); 
                    link.click();
                    
                    postCanvas.style.transform = originalTransform;
                    btn.innerHTML = originalText;
                    btn.disabled = false;
                    showNotification("📸 Premium HD Image Downloaded Successfully!");
                });
            });

            // --- ADVANCED HD MP4 VIDEO DOWNLOADER ---
            document.getElementById('btn-download-vid').addEventListener('click', async function() {
                if (vidEl.style.display === 'none' && imgEl.style.display === 'none') {
                    alert("Please upload a video or image first!"); return;
                }

                const btn = this;
                const originalText = btn.innerHTML;
                btn.disabled = true;

                const postCanvas = document.getElementById('post-canvas');
                const mediaArea = document.getElementById('post-media-area');
                const overlay = document.getElementById('recording-overlay');
                const statusTxt = document.getElementById('rec-status');

                const originalTransform = postCanvas.style.transform;
                postCanvas.style.transform = 'none'; 
                overlay.style.display = 'flex';
                statusTxt.innerText = 'READING TEXT & DESIGN (1080x1350)...';

                try {
                    const originalPostBg = postCanvas.style.backgroundColor;
                    const originalMediaBg = mediaArea.style.backgroundColor;
                    const originalVidDisplay = vidEl.style.display;
                    const originalImgDisplay = imgEl.style.display;

                    postCanvas.style.backgroundColor = 'transparent';
                    mediaArea.style.backgroundColor = 'transparent';
                    vidEl.style.display = 'none'; 
                    imgEl.style.display = 'none'; 
                    
                    const uiCanvas = await html2canvas(postCanvas, { scale: 1, backgroundColor: null, useCORS: true });
                    
                    postCanvas.style.backgroundColor = originalPostBg;
                    mediaArea.style.backgroundColor = originalMediaBg;
                    vidEl.style.display = originalVidDisplay;
                    imgEl.style.display = originalImgDisplay;
                    postCanvas.style.transform = originalTransform;

                    const recCanvas = document.createElement('canvas');
                    recCanvas.width = 1080; recCanvas.height = 1350;
                    const ctx = recCanvas.getContext('2d');
                    
                    const pRect = postCanvas.getBoundingClientRect();
                    const mRect = mediaArea.getBoundingClientRect();
                    const scaleY = 1350 / pRect.height;
                    const scaleX = 1080 / pRect.width;
                    
                    const mY = (mRect.top - pRect.top) * scaleY;
                    const mH = mRect.height * scaleY;
                    const mX = (mRect.left - pRect.left) * scaleX;
                    const mW = mRect.width * scaleX;

                    const canvasStream = recCanvas.captureStream(30);
                    let audioTracks = [];
                    if (vidEl.captureStream) audioTracks = vidEl.captureStream().getAudioTracks();
                    else if (vidEl.mozCaptureStream) audioTracks = vidEl.mozCaptureStream().getAudioTracks();
                    
                    let finalStream = canvasStream;
                    if (audioTracks.length > 0) finalStream = new MediaStream([...canvasStream.getVideoTracks(), ...audioTracks]);

                    let mimeType = 'video/webm'; 
                    if (!MediaRecorder.isTypeSupported(mimeType)) mimeType = 'video/webm;codecs=vp8,opus';

                    const recorder = new MediaRecorder(finalStream, { mimeType: mimeType, videoBitsPerSecond: 15000000 });
                    const chunks = [];
                    recorder.ondataavailable = e => { if (e.data.size > 0) chunks.push(e.data); };

                    vidEl.loop = false; vidEl.muted = false; vidEl.currentTime = 0;
                    await vidEl.play();
                    await new Promise(r => setTimeout(r, 200)); 

                    statusTxt.innerText = 'RECORDING HD VIDEO... DO NOT CLOSE';

                    let isRecording = true;
                    let startRecordingTime = Date.now(); 
                    function drawVideoFrame() {
                        if (!isRecording) return;
                        
                        ctx.fillStyle = originalPostBg || '#000000';
                        ctx.fillRect(0, 0, 1080, 1350);
                        ctx.fillStyle = '#000000';
                        ctx.fillRect(mX, mY, mW, mH);

                        if (vidEl.readyState >= 2) {
                            const ratio = vidEl.videoWidth / vidEl.videoHeight;
                            const targetRatio = mW / mH;
                            let sw, sh, sx, sy;
                            const xPerc = parseInt(mediaX.value) / 100;
                            const yPerc = parseInt(mediaY.value) / 100;
                            const zoomLvl = parseInt(zoomSlider.value) / 100;

                            if (ratio > targetRatio) {
                                sh = vidEl.videoHeight; sw = sh * targetRatio; sx = (vidEl.videoWidth - sw) * xPerc; sy = 0;
                            } else {
                                sw = vidEl.videoWidth; sh = sw / targetRatio; sx = 0; sy = (vidEl.videoHeight - sh) * yPerc;
                            }
                            
                            const cx = 1080 / 2; const cy = mY + (mH / 2);
                            ctx.save();
                            ctx.translate(cx, cy); ctx.scale(zoomLvl, zoomLvl); ctx.translate(-cx, -cy);
                            ctx.drawImage(vidEl, sx, sy, sw, sh, mX, mY, mW, mH);
                            ctx.restore();
                        }

                        ctx.drawImage(uiCanvas, 0, 0, 1080, 1350);
                        requestAnimationFrame(drawVideoFrame);
                    }

                    recorder.start();
                    drawVideoFrame();

                    vidEl.onended = () => { isRecording = false; recorder.stop(); };

                    recorder.onstop = async () => {
                        let blob = new Blob(chunks, { type: mimeType });
                        let actualDurationMs = Date.now() - startRecordingTime;

                        if (window.ysFixWebmDuration) {
                            blob = await window.ysFixWebmDuration(blob, actualDurationMs, { logger: false });
                        }

                        const url = URL.createObjectURL(blob);
                        const filename = `IndiaGlobalCine_HD_Video_${Date.now()}.mp4`;

                        overlay.style.display = 'none';
                        vidEl.loop = true; vidEl.muted = true; vidEl.play();

                        const downloadLink = document.createElement('a');
                        downloadLink.style.display = 'none';
                        downloadLink.href = url; downloadLink.download = filename;
                        document.body.appendChild(downloadLink);
                        
                        downloadLink.click();
                        showNotification("✅ HD Video Download Started! Check your browser downloads.");
                        
                        setTimeout(() => {
                            document.body.removeChild(downloadLink);
                            const modal = document.getElementById('download-modal');
                            const finalVideoPreview = document.getElementById('final-video-preview');
                            const forceDownloadBtn = document.getElementById('force-download-link');

                            finalVideoPreview.src = url;
                            forceDownloadBtn.href = url;
                            forceDownloadBtn.download = filename;
                            modal.classList.add('active');
                            
                            btn.innerHTML = originalText; btn.disabled = false;
                        }, 500);
                    };

                    setTimeout(() => {
                        if (isRecording) { isRecording = false; recorder.stop(); }
                    }, (vidEl.duration * 1000) + 2000 || 15000);

                } catch(error) {
                    console.error(error);
                    alert("Error processing HD video.");
                    overlay.style.display = 'none';
                    postCanvas.style.transform = originalTransform;
                    btn.innerHTML = originalText; btn.disabled = false;
                }
            });

        });
    </script>
</body>
</html>
