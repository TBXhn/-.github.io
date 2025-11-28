<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>武汉市七十九中学</title>
    <!-- 引入Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- 引入Font Awesome -->
    <link href="https://cdn.jsdelivr.net/npm/font-awesome@4.7.0/css/font-awesome.min.css" rel="stylesheet">
    <!-- 引入Chart.js -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.8/dist/chart.umd.min.js"></script>
    
    <!-- 配置Tailwind自定义主题 -->
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        primary: '#1E40AF', // 深蓝色作为主色调
                        secondary: '#3B82F6', // 浅蓝色作为辅助色
                        accent: '#F59E0B', // 橙色作为强调色
                        dark: '#1E293B',
                        light: '#F8FAFC'
                    },
                    fontFamily: {
                        sans: ['Inter', 'system-ui', 'sans-serif'],
                        display: ['Montserrat', 'sans-serif']
                    },
                }
            }
        }
    </script>
    
    <!-- 自定义工具类 -->
    <style type="text/tailwindcss">
        @layer utilities {
            .content-auto {
                content-visibility: auto;
            }
            .text-shadow {
                text-shadow: 0 2px 4px rgba(0,0,0,0.1);
            }
            .text-shadow-lg {
                text-shadow: 0 4px 8px rgba(0,0,0,0.2);
            }
            .animate-float {
                animation: float 6s ease-in-out infinite;
            }
            .animate-fade-in {
                animation: fadeIn 1.5s ease-out forwards;
            }
            .animate-slide-up {
                animation: slideUp 1.2s ease-out forwards;
            }
        }
        
        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-15px); }
            100% { transform: translateY(0px); }
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        @keyframes slideUp {
            from { transform: translateY(50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
    </style>
    
    <!-- 引入Google字体 -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Montserrat:wght@400;500;600;700&display=swap" rel="stylesheet">
    
    <style>
        /* 基础样式 */
        html {
            scroll-behavior: smooth;
        }
        
        body {
            overflow-x: hidden;
        }
        
        /* 加载动画 */
        .loader {
            border-top-color: #1E40AF;
            animation: spinner 0.8s linear infinite;
        }
        
        @keyframes spinner {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        /* 渐变背景 */
        .hero-gradient {
            background: linear-gradient(135deg, #1E40AF 0%, #3B82F6 100%);
        }
        
        /* 卡片悬停效果 */
        .card-hover {
            transition: all 0.3s ease;
        }
        
        .card-hover:hover {
            transform: translateY(-8px);
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
        }
        
        /* 导航栏滚动效果 */
        .nav-scrolled {
            background-color: rgba(30, 64, 175, 0.95);
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
        }
        
        /* 视差滚动效果 */
        .parallax {
            background-attachment: fixed;
            background-position: center;
            background-repeat: no-repeat;
            background-size: cover;
        }
    </style>
</head>

<body class="bg-light text-dark font-sans">
    <!-- 加载屏幕 -->
    <div id="loader" class="fixed inset-0 flex items-center justify-center bg-white z-50">
        <div class="loader h-16 w-16 rounded-full border-4 border-gray-200"></div>
    </div>

    <!-- 导航栏 -->
    <nav id="navbar" class="fixed w-full top-0 z-40 transition-all duration-300 py-4">
        <div class="container mx-auto px-4 md:px-6 flex justify-between items-center">
            <a href="#" class="flex items-center space-x-2">
                <div class="bg-accent text-white h-10 w-10 rounded-full flex items-center justify-center text-xl font-bold">79</div>
                <span class="text-white font-bold text-lg md:text-xl">武汉市七十九中学</span>
            </a>
            
            <!-- 桌面导航 -->
            <div class="hidden md:flex space-x-8">
                <a href="#about" class="text-white hover:text-accent transition-colors">学校简介</a>
                <a href="#features" class="text-white hover:text-accent transition-colors">办学特色</a>
                <a href="#news" class="text-white hover:text-accent transition-colors">校园新闻</a>
                <a href="#gallery" class="text-white hover:text-accent transition-colors">校园风光</a>
                <a href="#contact" class="text-white hover:text-accent transition-colors">联系我们</a>
            </div>
            
            <!-- 移动端菜单按钮 -->
            <button id="menu-toggle" class="md:hidden text-white text-2xl">
                <i class="fa fa-bars"></i>
            </button>
        </div>
        
        <!-- 移动端导航菜单 -->
        <div id="mobile-menu" class="hidden md:hidden bg-primary absolute w-full mt-4 py-4 px-4">
            <div class="flex flex-col space-y-4">
                <a href="#about" class="text-white hover:text-accent transition-colors py-2">学校简介</a>
                <a href="#features" class="text-white hover:text-accent transition-colors py-2">办学特色</a>
                <a href="#news" class="text-white hover:text-accent transition-colors py-2">校园新闻</a>
                <a href="#gallery" class="text-white hover:text-accent transition-colors py-2">校园风光</a>
                <a href="#contact" class="text-white hover:text-accent transition-colors py-2">联系我们</a>
            </div>
        </div>
    </nav>

    <!-- 英雄区域 -->
    <header class="hero-gradient min-h-screen flex items-center pt-20 relative overflow-hidden">
        <!-- 装饰元素 -->
        <div class="absolute top-0 right-0 w-full h-full overflow-hidden opacity-10">
            <div class="absolute -right-20 -top-20 w-96 h-96 bg-white rounded-full"></div>
            <div class="absolute right-1/4 bottom-0 w-64 h-64 bg-white rounded-full"></div>
            <div class="absolute left-10 top-1/3 w-40 h-40 bg-white rounded-full"></div>
        </div>
        
        <div class="container mx-auto px-4 md:px-6 py-20 relative z-10">
            <div class="grid md:grid-cols-2 gap-12 items-center">
                <div class="text-white space-y-6 animate-fade-in opacity-0">
                    <h1 class="text-[clamp(2.5rem,5vw,4rem)] font-bold leading-tight text-shadow-lg">
                        武汉市七十九中学
                    </h1>
                    <p class="text-lg md:text-xl opacity-90 max-w-lg">
                        培养全面发展的优秀人才，打造现代化优质教育品牌
                    </p>
                    <div class="flex flex-wrap gap-4 pt-4">
                        <a href="#about" class="bg-accent hover:bg-amber-500 text-white px-6 py-3 rounded-full font-medium transition-all shadow-lg hover:shadow-xl">
                            了解更多 <i class="fa fa-arrow-right ml-2"></i>
                        </a>
                        <a href="#contact" class="bg-white/20 hover:bg-white/30 backdrop-blur-sm text-white px-6 py-3 rounded-full font-medium transition-all border border-white/30">
                            联系我们
                        </a>
                    </div>
                </div>
                
                <div class="hidden md:block animate-slide-up opacity-0">
                    <img src="https://picsum.photos/id/20/800/600" alt="武汉市七十九中学" class="rounded-2xl shadow-2xl animate-float">
                </div>
            </div>
            
            <!-- 数据统计 -->
            <div class="grid grid-cols-2 md:grid-cols-4 gap-6 mt-20 animate-slide-up opacity-0" style="animation-delay: 0.3s">
                <div class="bg-white/10 backdrop-blur-sm rounded-xl p-6 text-center">
                    <div class="text-4xl font-bold text-white mb-2">50+</div>
                    <div class="text-white/80">办学历史</div>
                </div>
                <div class="bg-white/10 backdrop-blur-sm rounded-xl p-6 text-center">
                    <div class="text-4xl font-bold text-white mb-2">100+</div>
                    <div class="text-white/80">优秀教师</div>
                </div>
                <div class="bg-white/10 backdrop-blur-sm rounded-xl p-6 text-center">
                    <div class="text-4xl font-bold text-white mb-2">2000+</div>
                    <div class="text-white/80">在校学生</div>
                </div>
                <div class="bg-white/10 backdrop-blur-sm rounded-xl p-6 text-center">
                    <div class="text-4xl font-bold text-white mb-2">98%</div>
                    <div class="text-white/80">升学率</div>
                </div>
            </div>
        </div>
        
        <!-- 波浪分隔符 -->
        <div class="absolute bottom-0 left-0 w-full">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 100" class="fill-light">
                <path d="M0,64L80,69.3C160,75,320,85,480,80C640,75,800,53,960,42.7C1120,32,1280,32,1360,32L1440,32L1440,100L1360,100C1280,100,1120,100,960,100C800,100,640,100,480,100C320,100,160,100,80,100L0,100Z"></path>
            </svg>
        </div>
    </header>

    <!-- 学校简介 -->
    <section id="about" class="py-20">
        <div class="container mx-auto px-4 md:px-6">
            <div class="text-center mb-16">
                <h2 class="text-[clamp(1.8rem,3vw,2.5rem)] font-bold mb-4">学校简介</h2>
                <div class="h-1 w-20 bg-primary mx-auto rounded-full mb-6"></div>
                <p class="text-gray-600 max-w-2xl mx-auto">武汉市七十九中学是一所具有深厚文化底蕴和优良办学传统的学校</p>
            </div>
            
            <div class="grid md:grid-cols-2 gap-12 items-center">
                <div class="rounded-2xl overflow-hidden shadow-xl">
                    <img src="https://picsum.photos/id/30/800/600" alt="学校环境" class="w-full h-auto object-cover">
                </div>
                
                <div class="space-y-6">
                    <h3 class="text-2xl font-bold text-primary">武汉市七十九中学</h3>
                    <p class="text-gray-700 leading-relaxed">
                        武汉市七十九中学创建于1965年，是武汉市重点中学之一。学校位于武汉市中心区域，占地面积30余亩，建筑面积近2万平方米。校园环境优美，设施齐全，拥有现代化的教学楼、实验楼、图书馆、体育馆等设施。
                    </p>
                    <p class="text-gray-700 leading-relaxed">
                        学校师资力量雄厚，现有教职工120余人，其中高级教师45人，省市级骨干教师20人。学校坚持"以人为本，全面发展"的办学理念，注重培养学生的创新精神和实践能力。
                    </p>
                    <div class="grid grid-cols-2 gap-4 mt-8">
                        <div class="bg-gray-100 p-4 rounded-lg">
                            <div class="text-primary text-xl font-bold mb-1">校训</div>
                            <div class="text-gray-700">崇德、尚学、笃行、创新</div>
                        </div>
                        <div class="bg-gray-100 p-4 rounded-lg">
                            <div class="text-primary text-xl font-bold mb-1">校风</div>
                            <div class="text-gray-700">团结、奋进、求实、创新</div>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- 数据图表 -->
            <div class="mt-20 bg-white rounded-xl shadow-lg p-6 md:p-8">
                <h3 class="text-xl font-bold mb-6 text-center">学校发展数据</h3>
                <div class="h-80">
                    <canvas id="schoolChart"></canvas>
                </div>
            </div>
        </div>
    </section>

    <!-- 办学特色 -->
    <section id="features" class="py-20 bg-gray-50">
        <div class="container mx-auto px-4 md:px-6">
            <div class="text-center mb-16">
                <h2 class="text-[clamp(1.8rem,3vw,2.5rem)] font-bold mb-4">办学特色</h2>
                <div class="h-1 w-20 bg-primary mx-auto rounded-full mb-6"></div>
                <p class="text-gray-600 max-w-2xl mx-auto">多元化的教育特色，培养全面发展的优秀人才</p>
            </div>
            
            <div class="grid md:grid-cols-3 gap-8">
                <!-- 特色1 -->
                <div class="bg-white rounded-xl shadow-lg p-6 card-hover">
                    <div class="bg-primary/10 w-16 h-16 rounded-full flex items-center justify-center mb-6">
                        <i class="fa fa-book text-primary text-2xl"></i>
                    </div>
                    <h3 class="text-xl font-bold mb-3">优质教学</h3>
                    <p class="text-gray-600">实施素质教育，注重学生全面发展，开设多种选修课程，培养学生的兴趣特长。</p>
                </div>
                
                <!-- 特色2 -->
                <div class="bg-white rounded-xl shadow-lg p-6 card-hover">
                    <div class="bg-primary/10 w-16 h-16 rounded-full flex items-center justify-center mb-6">
                        <i class="fa fa-flask text-primary text-2xl"></i>
                    </div>
                    <h3 class="text-xl font-bold mb-3">科技创新</h3>
                    <p class="text-gray-600">设立科技创新实验室，开展机器人、编程等科技活动，培养学生的创新能力。</p>
                </div>
                
                <!-- 特色3 -->
                <div class="bg-white rounded-xl shadow-lg p-6 card-hover">
                    <div class="bg-primary/10 w-16 h-16 rounded-full flex items-center justify-center mb-6">
                        <i class="fa fa-music text-primary text-2xl"></i>
                    </div>
                    <h3 class="text-xl font-bold mb-3">艺术教育</h3>
                    <p class="text-gray-600">重视艺术教育，开设美术、音乐、舞蹈等课程，培养学生的审美能力和艺术素养。</p>
                </div>
                
                <!-- 特色4 -->
                <div class="bg-white rounded-xl shadow-lg p-6 card-hover">
                    <div class="bg-primary/10 w-16 h-16 rounded-full flex items-center justify-center mb-6">
                        <i class="fa fa-futbol-o text-primary text-2xl"></i>
                    </div>
                    <h3 class="text-xl font-bold mb-3">体育特色</h3>
                    <p class="text-gray-600">开展丰富多彩的体育活动，培养学生的体育兴趣和健康体魄，设有多个体育特色项目。</p>
                </div>
                
                <!-- 特色5 -->
                <div class="bg-white rounded-xl shadow-lg p-6 card-hover">
                    <div class="bg-primary/10 w-16 h-16 rounded-full flex items-center justify-center mb-6">
                        <i class="fa fa-users text-primary text-2xl"></i>
                    </div>
                    <h3 class="text-xl font-bold mb-3">德育教育</h3>
                    <p class="text-gray-600">注重品德教育，开展各类主题教育活动，培养学生的社会责任感和良好品德。</p>
                </div>
                
                <!-- 特色6 -->
                <div class="bg-white rounded-xl shadow-lg p-6 card-hover">
                    <div class="bg-primary/10 w-16 h-16 rounded-full flex items-center justify-center mb-6">
                        <i class="fa fa-globe text-primary text-2xl"></i>
                    </div>
                    <h3 class="text-xl font-bold mb-3">国际交流</h3>
                    <p class="text-gray-600">开展国际交流合作，与多所国外学校建立友好关系，拓展学生的国际视野。</p>
                </div>
            </div>
        </div>
    </section>

    <!-- 校园新闻 -->
    <section id="news" class="py-20">
        <div class="container mx-auto px-4 md:px-6">
            <div class="text-center mb-16">
                <h2 class="text-[clamp(1.8rem,3vw,2.5rem)] font-bold mb-4">校园新闻</h2>
                <div class="h-1 w-20 bg-primary mx-auto rounded-full mb-6"></div>
                <p class="text-gray-600 max-w-2xl mx-auto">最新校园动态，了解学校发展</p>
            </div>
            
            <div class="grid md:grid-cols-3 gap-8">
                <!-- 新闻1 -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden card-hover">
                    <img src="https://picsum.photos/id/40/600/400" alt="校园活动" class="w-full h-48 object-cover">
                    <div class="p-6">
                        <div class="text-sm text-gray-500 mb-2">2023年9月10日</div>
                        <h3 class="text-xl font-bold mb-3">我校举行教师节表彰大会</h3>
                        <p class="text-gray-600 mb-4">9月10日，我校隆重举行教师节表彰大会，表彰了一批优秀教师和教育工作者...</p>
                        <a href="#" class="text-primary font-medium hover:text-accent transition-colors">
                            阅读更多 <i class="fa fa-angle-right ml-1"></i>
                        </a>
                    </div>
                </div>
                
                <!-- 新闻2 -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden card-hover">
                    <img src="https://picsum.photos/id/42/600/400" alt="校园活动" class="w-full h-48 object-cover">
                    <div class="p-6">
                        <div class="text-sm text-gray-500 mb-2">2023年8月15日</div>
                        <h3 class="text-xl font-bold mb-3">我校学生在市科技创新大赛中获佳绩</h3>
                        <p class="text-gray-600 mb-4">在刚刚结束的武汉市青少年科技创新大赛中，我校学生表现优异，获得多个奖项...</p>
                        <a href="#" class="text-primary font-medium hover:text-accent transition-colors">
                            阅读更多 <i class="fa fa-angle-right ml-1"></i>
                        </a>
                    </div>
                </div>
                
                <!-- 新闻3 -->
                <div class="bg-white rounded-xl shadow-lg overflow-hidden card-hover">
                    <img src="https://picsum.photos/id/43/600/400" alt="校园活动" class="w-full h-48 object-cover">
                    <div class="p-6">
                        <div class="text-sm text-gray-500 mb-2">2023年7月5日</div>
                        <h3 class="text-xl font-bold mb-3">我校举行2023届毕业典礼</h3>
                        <p class="text-gray-600 mb-4">7月5日，我校隆重举行2023届毕业典礼，全体毕业生和教职工共同见证这一难忘时刻...</p>
                        <a href="#" class="text-primary font-medium hover:text-accent transition-colors">
                            阅读更多 <i class="fa fa-angle-right ml-1"></i>
                        </a>
                    </div>
                </div>
            </div>
            
            <div class="text-center mt-12">
                <a href="#" class="inline-block bg-primary hover:bg-primary/90 text-white px-8 py-3 rounded-full font-medium transition-all shadow-lg hover:shadow-xl">
                    查看更多新闻
                </a>
            </div>
        </div>
    </section>

    <!-- 校园风光 -->
    <section id="gallery" class="py-20 bg-gray-50">
        <div class="container mx-auto px-4 md:px-6">
            <div class="text-center mb-16">
                <h2 class="text-[clamp(1.8rem,3vw,2.5rem)] font-bold mb-4">校园风光</h2>
                <div class="h-1 w-20 bg-primary mx-auto rounded-full mb-6"></div>
                <p class="text-gray-600 max-w-2xl mx-auto">美丽的校园环境，优良的学习氛围</p>
            </div>
            
            <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
                <div class="overflow-hidden rounded-xl shadow-lg group">
                    <img src="https://picsum.photos/id/28/600/400" alt="校园风光" class="w-full h-64 object-cover transition-transform duration-500 group-hover:scale-110">
                </div>
                <div class="overflow-hidden rounded-xl shadow-lg group">
                    <img src="https://picsum.photos/id/29/600/400" alt="校园风光" class="w-full h-64 object-cover transition-transform duration-500 group-hover:scale-110">
                </div>
                <div class="overflow-hidden rounded-xl shadow-lg group">
                    <img src="https://picsum.photos/id/31/600/400" alt="校园风光" class="w-full h-64 object-cover transition-transform duration-500 group-hover:scale-110">
                </div>
                <div class="overflow-hidden rounded-xl shadow-lg group">
                    <img src="https://picsum.photos/id/32/600/400" alt="校园风光" class="w-full h-64 object-cover transition-transform duration-500 group-hover:scale-110">
                </div>
                <div class="overflow-hidden rounded-xl shadow-lg group">
                    <img src="https://picsum.photos/id/33/600/400" alt="校园风光" class="w-full h-64 object-cover transition-transform duration-500 group-hover:scale-110">
                </div>
                <div class="overflow-hidden rounded-xl shadow-lg group">
                    <img src="https://picsum.photos/id/34/600/400" alt="校园风光" class="w-full h-64 object-cover transition-transform duration-500 group-hover:scale-110">
                </div>
                <div class="overflow-hidden rounded-xl shadow-lg group">
                    <img src="https://picsum.photos/id/35/600/400" alt="校园风光" class="w-full h-64 object-cover transition-transform duration-500 group-hover:scale-110">
                </div>
                <div class="overflow-hidden rounded-xl shadow-lg group">
                    <img src="https://picsum.photos/id/36/600/400" alt="校园风光" class="w-full h-64 object-cover transition-transform duration-500 group-hover:scale-110">
                </div>
            </div>
        </div>
    </section>

    <!-- 联系我们 -->
    <section id="contact" class="py-20">
        <div class="container mx-auto px-4 md:px-6">
            <div class="text-center mb-16">
                <h2 class="text-[clamp(1.8rem,3vw,2.5rem)] font-bold mb-4">联系我们</h2>
                <div class="h-1 w-20 bg-primary mx-auto rounded-full mb-6"></div>
                <p class="text-gray-600 max-w-2xl mx-auto">欢迎联系我们，了解更多学校信息</p>
            </div>
            
            <div class="grid md:grid-cols-2 gap-12">
                <div class="bg-white rounded-xl shadow-lg p-8">
                    <h3 class="text-2xl font-bold mb-6">联系方式</h3>
                    
                    <div class="space-y-6">
                        <div class="flex items-start">
                            <div class="bg-primary/10 w-12 h-12 rounded-full flex items-center justify-center mr-4 flex-shrink-0">
                                <i class="fa fa-map-marker text-primary"></i>
                            </div>
                            <div>
                                <h4 class="font-bold mb-1">学校地址</h4>
                                <p class="text-gray-600">武汉市江汉区常青街发展大道45号</p>
                            </div>
                        </div>
                        
                        <div class="flex items-start">
                            <div class="bg-primary/10 w-12 h-12 rounded-full flex items-center justify-center mr-4 flex-shrink-0">
                                <i class="fa fa-phone text-primary"></i>
                            </div>
                            <div>
                                <h4 class="font-bold mb-1">联系电话</h4>
                                <p class="text-gray-600">027-83521779</p>
                            </div>
                        </div>
                        
                        <div class="flex items-start">
                            <div class="bg-primary/10 w-12 h-12 rounded-full flex items-center justify-center mr-4 flex-shrink-0">
                                <i class="fa fa-envelope text-primary"></i>
                            </div>
                            <div>
                                <h4 class="font-bold mb-1">电子邮箱</h4>
                                <p class="text-gray-600">wh79zx@163.com</p>
                            </div>
                        </div>
                        
                        <div class="flex items-start">
                            <div class="bg-primary/10 w-12 h-12 rounded-full flex items-center justify-center mr-4 flex-shrink-0">
                                <i class="fa fa-clock-o text-primary"></i>
                            </div>
                            <div>
                                <h4 class="font-bold mb-1">工作时间</h4>
                                <p class="text-gray-600">周一至周五: 8:00 - 17:30</p>
                            </div>
                        </div>
                    </div>
                    
                    <div class="mt-8">
                        <h4 class="font-bold mb-3">关注我们</h4>
                        <div class="flex space-x-4">
                            <a href="#" class="bg-primary/10 hover:bg-primary/20 w-10 h-10 rounded-full flex items-center justify-center text-primary transition-colors">
                                <i class="fa fa-weixin"></i>
                            </a>
                            <a href="#" class="bg-primary/10 hover:bg-primary/20 w-10 h-10 rounded-full flex items-center justify-center text-primary transition-colors">
                                <i class="fa fa-weibo"></i>
                            </a>
                            <a href="#" class="bg-primary/10 hover:bg-primary/20 w-10 h-10 rounded-full flex items-center justify-center text-primary transition-colors">
                                <i class="fa fa-qq"></i>
                            </a>
                        </div>
                    </div>
                </div>
                
                <div class="bg-white rounded-xl shadow-lg p-8">
                    <h3 class="text-2xl font-bold mb-6">留言咨询</h3>
                    
                    <form>
                        <div class="grid md:grid-cols-2 gap-6 mb-6">
                            <div>
                                <label for="name" class="block text-gray-700 mb-2">姓名</label>
                                <input type="text" id="name" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-primary/50 focus:border-primary transition-colors">
                            </div>
                            <div>
                                <label for="phone" class="block text-gray-700 mb-2">电话</label>
                                <input type="tel" id="phone" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-primary/50 focus:border-primary transition-colors">
                            </div>
                        </div>
                        
                        <div class="mb-6">
                            <label for="email" class="block text-gray-700 mb-2">邮箱</label>
                            <input type="email" id="email" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-primary/50 focus:border-primary transition-colors">
                        </div>
                        
                        <div class="mb-6">
                            <label for="subject" class="block text-gray-700 mb-2">主题</label>
                            <select id="subject" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-primary/50 focus:border-primary transition-colors">
                                <option>招生咨询</option>
                                <option>合作洽谈</option>
                                <option>建议反馈</option>
                                <option>其他咨询</option>
                            </select>
                        </div>
                        
                        <div class="mb-6">
                            <label for="message" class="block text-gray-700 mb-2">留言内容</label>
                            <textarea id="message" rows="4" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-primary/50 focus:border-primary transition-colors"></textarea>
                        </div>
                        
                        <button type="submit" class="w-full bg-primary hover:bg-primary/90 text-white py-3 rounded-lg font-medium transition-all shadow-lg hover:shadow-xl">
                            提交留言
                        </button>
                    </form>
                </div>
            </div>
        </div>
    </section>

    <!-- 页脚 -->
    <footer class="bg-dark text-white py-12">
        <div class="container mx-auto px-4 md:px-6">
            <div class="grid md:grid-cols-4 gap-8 mb-12">
                <div>
                    <div class="flex items-center space-x-2 mb-6">
                        <div class="bg-accent text-white h-10 w-10 rounded-full flex items-center justify-center text-xl font-bold">79</div>
                        <span class="font-bold text-lg">武汉市七十九中学</span>
                    </div>
                    <p class="text-gray-400 mb-6">培养全面发展的优秀人才，打造现代化优质教育品牌</p>
                    <div class="flex space-x-4">
                        <a href="#" class="text-gray-400 hover:text-white transition-colors">
                            <i class="fa fa-weixin"></i>
                        </a>
                        <a href="#" class="text-gray-400 hover:text-white transition-colors">
                            <i class="fa fa-weibo"></i>
                        </a>
                        <a href="#" class="text-gray-400 hover:text-white transition-colors">
                            <i class="fa fa-qq"></i>
                        </a>
                    </div>
                </div>
                
                <div>
                    <h4 class="font-bold text-lg mb-6">快速链接</h4>
                    <ul class="space-y-3">
                        <li><a href="#about" class="text-gray-400 hover:text-white transition-colors">学校简介</a></li>
                        <li><a href="#features" class="text-gray-400 hover:text-white transition-colors">办学特色</a></li>
                        <li><a href="#news" class="text-gray-400 hover:text-white transition-colors">校园新闻</a></li>
                        <li><a href="#gallery" class="text-gray-400 hover:text-white transition-colors">校园风光</a></li>
                        <li><a href="#contact" class="text-gray-400 hover:text-white transition-colors">联系我们</a></li>
                    </ul>
                </div>
                
                <div>
                    <h4 class="font-bold text-lg mb-6">联系方式</h4>
                    <ul class="space-y-3">
                        <li class="flex items-start">
                            <i class="fa fa-map-marker mt-1 mr-3 text-accent"></i>
                            <span class="text-gray-400">武汉市江汉区常青街发展大道45号</span>
                        </li>
                        <li class="flex items-start">
                            <i class="fa fa-phone mt-1 mr-3 text-accent"></i>
                            <span class="text-gray-400">027-83521779</span>
                        </li>
                        <li class="flex items-start">
                            <i class="fa fa-envelope mt-1 mr-3 text-accent"></i>
                            <span class="text-gray-400">wh79zx@163.com</span>
                        </li>
                    </ul>
                </div>
                
                <div>
                    <h4 class="font-bold text-lg mb-6">订阅通讯</h4>
                    <p class="text-gray-400 mb-4">订阅我们的通讯，获取最新学校资讯</p>
                    <form class="flex">
                        <input type="email" placeholder="您的邮箱地址" class="flex-1 px-4 py-2 bg-gray-800 text-white rounded-l-lg focus:outline-none focus:ring-1 focus:ring-accent">
                        <button type="submit" class="bg-accent hover:bg-amber-500 text-white px-4 py-2 rounded-r-lg transition-colors">
                            <i class="fa fa-paper-plane"></i>
                        </button>
                    </form>
                </div>
            </div>
            
            <div class="border-t border-gray-800 pt-8 text-center text-gray-500">
                <p>&copy; 2023 武汉市七十九中学. 保留所有权利.</p>
            </div>
        </div>
    </footer>

    <!-- 返回顶部按钮 -->
    <button id="back-to-top" class="fixed bottom-8 right-8 bg-primary hover:bg-primary/90 text-white w-12 h-12 rounded-full flex items-center justify-center shadow-lg transition-all opacity-0 invisible">
        <i class="fa fa-arrow-up"></i>
    </button>

    <!-- JavaScript -->
    <script>
        // 页面加载完成后隐藏加载屏幕
        window.addEventListener('load', function() {
            setTimeout(function() {
                document.getElementById('loader').classList.add('opacity-0');
                setTimeout(function() {
                    document.getElementById('loader').style.display = 'none';
                    
                    // 显示动画元素
                    const animateElements = document.querySelectorAll('.animate-fade-in, .animate-slide-up');
                    animateElements.forEach(el => {
                        el.style.opacity = '1';
                    });
                }, 500);
            }, 800);
        });
        
        // 导航栏滚动效果
        window.addEventListener('scroll', function() {
            const navbar = document.getElementById('navbar');
            const backToTop = document.getElementById('back-to-top');
            
            if (window.scrollY > 50) {
                navbar.classList.add('nav-scrolled');
                backToTop.classList.remove('opacity-0', 'invisible');
                backToTop.classList.add('opacity-100', 'visible');
            } else {
                navbar.classList.remove('nav-scrolled');
                backToTop.classList.add('opacity-0', 'invisible');
                backToTop.classList.remove('opacity-100', 'visible');
            }
        });
        
        // 移动端菜单切换
        document.getElementById('menu-toggle').addEventListener('click', function() {
            const mobileMenu = document.getElementById('mobile-menu');
            mobileMenu.classList.toggle('hidden');
        });
        
        // 返回顶部按钮
        document.getElementById('back-to-top').addEventListener('click', function() {
            window.scrollTo({
                top: 0,
                behavior: 'smooth'
            });
        });
        
        // 平滑滚动
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                
                // 关闭移动端菜单
                document.getElementById('mobile-menu').classList.add('hidden');
                
                const targetId = this.getAttribute('href');
                if (targetId === '#') return;
                
                const targetElement = document.querySelector(targetId);
                if (targetElement) {
                    targetElement.scrollIntoView({
                        behavior: 'smooth'
                    });
                }
            });
        });
        
        // 学校发展数据图表
        window.addEventListener('load', function() {
            const ctx = document.getElementById('schoolChart').getContext('2d');
            const chart = new Chart(ctx, {
                type: 'line',
                data: {
                    labels: ['2018', '2019', '2020', '2021', '2022', '2023'],
                    datasets: [
                        {
                            label: '升学率',
                            data: [85, 88, 90, 92, 95, 98],
                            borderColor: '#1E40AF',
                            backgroundColor: 'rgba(30, 64, 175, 0.1)',
                            tension: 0.4,
                            fill: true
                        },
                        {
                            label: '获奖人数',
                            data: [25, 30, 35, 42, 48, 55],
                            borderColor: '#F59E0B',
                            backgroundColor: 'rgba(245, 158, 11, 0.1)',
                            tension: 0.4,
                            fill: true
                        }
                    ]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            position: 'top',
                        },
                        tooltip: {
                            mode: 'index',
                            intersect: false,
                        }
                    },
                    scales: {
                        y: {
                            beginAtZero: true,
                            grid: {
                                drawBorder: false
                            }
                        },
                        x: {
                            grid: {
                                display: false
                            }
                        }
                    }
                }
            });
        });
    </script>
</body>
</html>
