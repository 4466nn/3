<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ColorOS 16 便签系统</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link rel="stylesheet" href="style.css">
    <style>
        :root {
            --color-primary: #2563eb;
            --color-primary-light: #3b82f6;
            --color-secondary: #64748b;
            --color-success: #10b981;
            --color-warning: #f59e0b;
            --color-danger: #ef4444;
            --color-bg: #f8fafc;
            --color-card: #ffffff;
            --color-text: #1e293b;
            --color-text-light: #64748b;
            --color-border: #e2e8f0;
            --shadow-sm: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
            --shadow-md: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
            --shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
            --radius-sm: 8px;
            --radius-md: 12px;
            --radius-lg: 16px;
            --transition: all 0.3s ease;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', 'PingFang SC', 'Microsoft YaHei', sans-serif;
        }

        body {
            background-color: var(--color-bg);
            color: var(--color-text);
            line-height: 1.6;
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
        }

        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
            padding: 20px 0;
            border-bottom: 1px solid var(--color-border);
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .logo-icon {
            width: 40px;
            height: 40px;
            background: linear-gradient(135deg, var(--color-primary), var(--color-primary-light));
            border-radius: var(--radius-md);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 20px;
        }

        .logo-text h1 {
            font-size: 24px;
            font-weight: 600;
        }

        .logo-text p {
            font-size: 14px;
            color: var(--color-text-light);
        }

        .actions {
            display: flex;
            gap: 12px;
        }

        .btn {
            padding: 10px 18px;
            border-radius: var(--radius-sm);
            border: none;
            font-weight: 500;
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .btn-primary {
            background-color: var(--color-primary);
            color: white;
        }

        .btn-primary:hover {
            background-color: var(--color-primary-light);
            transform: translateY(-2px);
            box-shadow: var(--shadow-md);
        }

        .btn-outline {
            background-color: transparent;
            color: var(--color-primary);
            border: 1px solid var(--color-primary);
        }

        .btn-outline:hover {
            background-color: rgba(37, 99, 235, 0.05);
        }

        .btn-success {
            background-color: var(--color-success);
            color: white;
        }

        .btn-success:hover {
            background-color: #0da271;
        }

        .main-layout {
            display: grid;
            grid-template-columns: 300px 1fr;
            gap: 24px;
        }

        .sidebar {
            background-color: var(--color-card);
            border-radius: var(--radius-lg);
            padding: 24px;
            box-shadow: var(--shadow-sm);
            height: fit-content;
        }

        .sidebar-title {
            font-size: 18px;
            font-weight: 600;
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .categories {
            list-style: none;
        }

        .category-item {
            padding: 12px 16px;
            border-radius: var(--radius-sm);
            margin-bottom: 8px;
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .category-item:hover {
            background-color: rgba(37, 99, 235, 0.05);
        }

        .category-item.active {
            background-color: rgba(37, 99, 235, 0.1);
            color: var(--color-primary);
            font-weight: 500;
        }

        .category-icon {
            width: 24px;
            height: 24px;
            display: flex;
            align-items: center;
    
