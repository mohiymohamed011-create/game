<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>لعبة عجلة الحروف - مجمع حلقات الصديق</title>
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@700;900&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-bg: #8EC5FC;
            --secondary-bg: #E0C3FC;
            --wheel-border: #FFD700;
            --card-bg: #FFFFFF;
            --accent-color: #FF5722;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Tajawal', sans-serif;
            user-select: none;
        }

        body {
            background: linear-gradient(135deg, var(--primary-bg) 0%, var(--secondary-bg) 100%);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: space-between;
            padding: 15px;
            overflow-x: hidden;
        }

        header {
            text-align: center;
            background: rgba(255, 255, 255, 0.9);
            padding: 15px 30px;
            border-radius: 20px;
            box-shadow: 0 8px 20px rgba(0,0,0,0.15);
            margin-bottom: 10px;
            border: 3px solid #FF9800;
            width: 90%;
            max-width: 600px;
        }

        h1 {
            color: #2E7D32;
            font-size: 1.8rem;
            margin-bottom: 5px;
        }

        .credits {
            color: #D81B60;
            font-size: 1.2rem;
            font-weight: bold;
        }

        .wheel-container {
            position: relative;
            width: 340px;
            height: 340px;
            margin: 10px auto;
        }

        @media (min-width: 500px) {
            .wheel-container {
                width: 420px;
                height: 420px;
            }
        }

        .pointer {
            position: absolute;
            top: -15px;
            left: 50%;
            transform: translateX(-50%);
            width: 0;
            height: 0;
            border-left: 18px solid transparent;
            border-right: 18px solid transparent;
            border-top: 35px solid #FF1744;
            z-index: 10;
            filter: drop-shadow(0px 4px 4px rgba(0,0,0,0.3));
        }

        canvas {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            border: 8px solid var(--wheel-border);
            box-shadow: 0 10px 25px rgba(0,0,0,0.2);
            cursor: pointer;
        }

        .center-btn {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 70px;
            height: 70px;
            background: radial-gradient(circle, #FFD700, #FF9800);
            border: 4px solid #FFF;
            border-radius: 50%;
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.2rem;
            font-weight: bold;
            color: #333;
            cursor: pointer;
            z-index: 5;
            transition: transform 0.1s;
        }

        .center-btn:active {
            transform: translate(-50%, -50%) scale(0.95);
        }

        .spin-btn {
            background: linear-gradient(45deg, #FF5722, #FF9800);
            color: white;
            border: none;
            padding: 12px 40px;
            font-size: 1.5rem;
            font-weight: bold;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 6px 15px rgba(255, 87, 34, 0.4);
            margin-top: 10px;
            transition: all 0.2s;
        }

        .spin-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 20px rgba(255, 87, 34, 0.6)
          
