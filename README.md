[html.html](https://github.com/user-attachments/files/23833686/html.html)
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Galgame导航站</title>
    <style>
        /* 全局样式 */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Microsoft YaHei', '微软雅黑', sans-serif;
        }
        
        body {
            color: #fff;
            line-height: 1.6;
            overflow-x: hidden;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        /* 页面背景样式 */
        .page {
            display: none;
            position: relative;
            min-height: 100vh;
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
        }
        
        .page::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.6);
            z-index: 1;
        }
        
        .page.active {
            display: block;
            animation: fadeIn 0.8s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        .page-content {
            position: relative;
            z-index: 2;
            padding: 2rem 0;
        }
        
        /* 导航栏样式 */
        header {
            background-color: rgba(0, 0, 0, 0.7);
            padding: 1rem 0;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
        }
        
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            display: flex;
            align-items: center;
        }
        
        .logo i {
            margin-right: 10px;
            font-size: 1.5rem;
        }
        
        .nav-links {
            display: flex;
            list-style: none;
        }
        
        .nav-links li {
            margin-left: 1.5rem;
        }
        
        .nav-links a {
            color: white;
            text-decoration: none;
            font-weight: 500;
            transition: all 0.3s ease;
            padding: 5px 10px;
            border-radius: 4px;
        }
        
        .nav-links a:hover {
            background-color: rgba(255, 255, 255, 0.2);
        }
        
        /* 首页样式 */
        #home {
            background-image: url('https://ps.ssl.qhimg.com/sdmt/354_266_100/t047f9420f31481f2c2.webp');
        }
        
        .hero {
            text-align: center;
            padding: 5rem 0;
        }
        
        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 1.5rem;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
        }
        
        .hero p {
            font-size: 1.3rem;
            max-width: 800px;
            margin: 0 auto 2.5rem;
            text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.5);
        }
        
        .btn {
            display: inline-block;
            background-color: rgba(106, 17, 203, 0.8);
            color: white;
            padding: 0.9rem 2rem;
            border-radius: 30px;
            text-decoration: none;
            font-weight: bold;
            transition: all 0.3s ease;
            border: none;
            cursor: pointer;
            font-size: 1.1rem;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
        }
        
        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 7px 20px rgba(0, 0, 0, 0.3);
            background-color: rgba(106, 17, 203, 0.9);
        }
        
        .intro {
            background-color: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            padding: 2.5rem;
            border-radius: 15px;
            margin-bottom: 2rem;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }
        
        .intro h2 {
            color: #fff;
            margin-bottom: 1.5rem;
            border-bottom: 2px solid rgba(255, 255, 255, 0.3);
            padding-bottom: 0.8rem;
            font-size: 2rem;
        }
        
        .intro p {
            margin-bottom: 1.2rem;
            font-size: 1.1rem;
        }
        
        .company-cards {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 1.8rem;
            margin-top: 2.5rem;
        }
        
        .company-card {
            background-color: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 15px;
            overflow: hidden;
            transition: all 0.4s ease;
            cursor: pointer;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }
        
        .company-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 12px 25px rgba(0, 0, 0, 0.3);
            background-color: rgba(255, 255, 255, 0.15);
        }
        
        .card-img {
            height: 180px;
            background-size: cover;
            background-position: center;
        }
        
        .card-content {
            padding: 1.8rem;
        }
        
        .card-content h3 {
            color: #fff;
            margin-bottom: 0.8rem;
            font-size: 1.4rem;
        }
        
        .card-content p {
            color: rgba(255, 255, 255, 0.8);
            font-size: 0.95rem;
        }
        
        /* 分页样式 */
        .game-detail {
            background-color: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 15px;
            overflow: hidden;
            margin-top: 2rem;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }
        
        .game-hero {
            height: 350px;
            background-size: cover;
            background-position: center;
            position: relative;
        }
        
        .game-hero::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 120px;
            background: linear-gradient(transparent, rgba(0, 0, 0, 0.7));
        }
        
        .game-info {
            padding: 2.5rem;
        }
        
        .game-title {
            display: flex;
            align-items: center;
            margin-bottom: 2rem;
        }
        
        .game-title h1 {
            color: #fff;
            font-size: 2.5rem;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
        }
        
        .company-logo {
            width: 90px;
            height: 90px;
            background-color: rgba(255, 255, 255, 0.2);
            border-radius: 15px;
            margin-right: 1.5rem;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            color: #fff;
            font-size: 1.5rem;
            backdrop-filter: blur(5px);
            border: 1px solid rgba(255, 255, 255, 0.3);
        }
        
        .game-desc {
            margin-bottom: 2.5rem;
        }
        
        .game-desc h2 {
            color: #fff;
            margin-bottom: 1.5rem;
            border-bottom: 2px solid rgba(255, 255, 255, 0.3);
            padding-bottom: 0.8rem;
            font-size: 1.8rem;
        }
        
        .game-desc p {
            margin-bottom: 1.2rem;
            font-size: 1.1rem;
        }
        
        .characters {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 1.8rem;
            margin-top: 2rem;
        }
        
        .character {
            text-align: center;
            background-color: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(5px);
            border-radius: 15px;
            padding: 1.5rem 1rem;
            transition: all 0.3s ease;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }
        
        .character:hover {
            transform: translateY(-5px);
            background-color: rgba(255, 255, 255, 0.15);
        }
        
        .character-img {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            margin: 0 auto 1.2rem;
            background-size: cover;
            background-position: center;
            border: 3px solid rgba(255, 255, 255, 0.5);
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
        }
        
        .character h3 {
            color: #fff;
            margin-bottom: 0.8rem;
            font-size: 1.3rem;
        }
        
        .character p {
            color: rgba(255, 255, 255, 0.8);
            font-size: 0.9rem;
        }
        
        /* 页脚样式 */
        footer {
            background-color: rgba(0, 0, 0, 0.8);
            color: white;
            text-align: center;
            padding: 2rem 0;
            margin-top: 3rem;
        }
        
        /* 响应式设计 */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }
            
            .hero h1 {
                font-size: 2.5rem;
            }
            
            .hero p {
                font-size: 1.1rem;
            }
            
            .company-cards {
                grid-template-columns: 1fr;
            }
            
            .characters {
                grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
            }
            
            .game-title {
                flex-direction: column;
                text-align: center;
            }
            
            .company-logo {
                margin-right: 0;
                margin-bottom: 1rem;
            }
            
            .game-title h1 {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="container">
            <nav>
                <div class="logo">
                    <i>🌸</i> Galgame导航
                </div>
                <ul class="nav-links">
                    <li><a href="#" class="nav-link" data-page="home">首页</a></li>
                    <li><a href="#" class="nav-link" data-page="yuzusoft">柚子社</a></li>
                    <li><a href="#" class="nav-link" data-page="madosoft">Madosoft</a></li>
                    <li><a href="#" class="nav-link" data-page="navel">Navel</a></li>
                    <li><a href="#" class="nav-link" data-page="palette">Palette</a></li>
                </ul>
            </nav>
        </div>
    </header>
    
    <main>
        <!-- 首页 -->
        <section id="home" class="page active">
            <div class="container page-content">
                <div class="hero">
                    <h1>欢迎来到Galgame世界</h1>
                    <p>探索视觉小说的魅力，体验日式美少女游戏的精彩故事与角色</p>
                    <a href="#" class="btn nav-link" data-page="yuzusoft">开始探索</a>
                </div>
                
                <div class="intro">
                    <h2>什么是Galgame？</h2>
                    <p>Galgame（ギャルゲーム）是一种以美少女为主题的恋爱冒险游戏，起源于日本。这类游戏通常以精美的插画、动人的音乐和丰富的剧情为特色，玩家通过选择不同的选项来影响故事的发展，体验与虚拟角色的互动。</p>
                    <p>Galgame不仅是一种娱乐形式，更是一种独特的文化现象，融合了视觉艺术、文学和音乐等多种元素，为玩家提供沉浸式的故事体验。</p>
                </div>
                
                <h2 style="color: #fff; margin-bottom: 1.5rem; font-size: 2rem;">知名游戏公司</h2>
                <div class="company-cards">
                    <div class="company-card nav-link" data-page="yuzusoft">
                        <div class="card-img" style="background-image: url('https://ps.ssl.qhimg.com/sdmt/316_266_100/t01f709afa32b30cee0.png');"></div>
                        <div class="card-content">
                            <h3>柚子社 (Yuzusoft)</h3>
                            <p>以高质量的原画和轻松愉快的剧情著称，代表作《千恋万花》</p>
                        </div>
                    </div>
                    
                    <div class="company-card nav-link" data-page="madosoft">
                        <div class="card-img" style="background-image: url('https://so.360tres.com/dmsmfl/123_82_/t01feec0ec92607c2b8.webp?size=1108x400&phash=-7828245009566449234');"></div>
                        <div class="card-content">
                            <h3>窗社（Madosoft）</h3>
                            <p>以独特的角色设计和幽默的剧情闻名，代表作《常规脱离Creative》</p>
                        </div>
                    </div>
                    
                    <div class="company-card nav-link" data-page="navel">
                        <div class="card-img" style="background-image: url('https://so.360tres.com/dmsmfl/123_82_/t01c1f952a8e9eb6bb7.webp?size=675x400&phash=5986310835453235612');"></div>
                        <div class="card-content">
                            <h3>（近月社）Navel</h3>
                            <p>以《近月少女的礼仪》系列闻名，擅长创作女装题材作品</p>
                        </div>
                    </div>
                    
                    <div class="company-card nav-link" data-page="palette">
                        <div class="card-img" style="background-image: url('https://storage.moegirl.org.cn/moegirl/commons/e/eb/Palette%28%E6%B8%B8%E6%88%8F%E5%85%AC%E5%8F%B8%29.png!/fw/300/watermark/url/L21vZWdpcmwvd2F0ZXJtYXJrLnBuZw==/align/southeast/margin/10x10/opacity/50?v=20210622014029');"></div>
                        <div class="card-content">
                            <h3>（调色板社）Palette</h3>
                            <p>以《9nine》系列闻名，作品以悬疑和超自然元素为特色</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        
        <!-- 柚子社页面 -->
        <section id="yuzusoft" class="page" style="background-image: url('https://p2.ssl.qhimgs1.com/sdr/400__/t014901e22f5b2c164c.jpg');">
            <div class="container page-content">
                <div class="game-detail">
                    <div class="game-hero" style="background-image: url('https://ps.ssl.qhimg.com/sdmt/316_266_100/t01f709afa32b30cee0.png');"></div>
                    <div class="game-info">
                        <div class="game-title">
                            <div class="company-logo">YUZU</div>
                            <h1>柚子社 - 《千恋万花》</h1>
                        </div>
                        
                        <div class="game-desc">
                            <h2>公司介绍</h2>
                            <p>柚子社（Yuzusoft）是日本一家知名的美少女游戏品牌，成立于2005年。以其高质量的原画、轻松愉快的剧情和优秀的音乐著称。柚子社的作品通常具有鲜明的角色个性和温馨的故事氛围，深受玩家喜爱。</p>
                            
                            <h2>《千恋万花》简介</h2>
                            <p>《千恋万花》是柚子社于2016年发售的和风恋爱冒险游戏。故事发生在一个名为"穗织"的小镇，主角有地将臣在祭典上拔出了一把传说中的神刀"丛雨丸"，从而与当地名门朝武家的女儿朝武芳乃立下婚约，并卷入了一系列神秘事件中。</p>
                            
                            <h2>主要角色</h2>
                            <div class="characters">
                                <div class="character">
                                    <div class="character-img" style="background-image: url('https://p5.ssl.qhimgs1.com/sdr/400__/t01d92cb880f6c1acc5.jpg');"></div>
                                    <h3>朝武 芳乃</h3>
                                    <p>朝武家的巫女，性格认真但有些天然</p>
                                </div>
                                <div class="character">
                                    <div class="character-img" style="background-image: url('https://p5.ssl.qhimgs1.com/sdr/400__/t019c3f85f1cd0002ef.jpg');"></div>
                                    <h3>丛雨</h3>
                                    <p>神刀"丛雨丸"的付丧神，外表是幼小的少女</p>
                                </div>
                                <div class="character">
                                    <div class="character-img" style="background-image: url('https://so.360tres.com/dmsmfl/123_121_/t01900439c6c79694db.webp?size=500x500');"></div>
                                    <h3>常陆 茉子</h3>
                                    <p>负责保护芳乃的女忍者，擅长家务的温柔女孩</p>
                                </div>
                                <div class="character">
                                    <div class="character-img" style="background-image: url('https://p2.ssl.qhimgs1.com/sdr/400__/t043f7c18688a66f152.jpg');"></div>
                                    <h3>蕾娜·莉希特娜瓦</h3>
                                    <p>来自外国的留学生，活泼开朗的混血少女</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        
        <!-- Madosoft页面 -->
        <section id="madosoft" class="page" style="background-image: url('https://p5.ssl.qhimgs1.com/sdr/400__/t0465759263674263df.jpg');">
            <div class="container page-content">
                <div class="game-detail">
                    <div class="game-hero" style="background-image: url('https://i2.hdslb.com/bfs/article/3f74c1b297cfd4bfac214c9283c32d73a0f5d5f4.png@1106w_270h.avif');"></div>
                    <div class="game-info">
                        <div class="game-title">
                            <div class="company-logo">MADO</div>
                            <h1>Madosoft - 《常规脱离Creative》</h1>
                        </div>
                        
                        <div class="game-desc">
                            <h2>公司介绍</h2>
                            <p>Madosoft是日本一家美少女游戏公司，以其独特的角色设计和幽默的剧情风格闻名。公司的作品通常具有鲜明的个性和创新的设定，带给玩家新鲜的游戏体验。</p>
                            
                            <h2>《常规脱离Creative》简介</h2>
                            <p>《常规脱离Creative》是Madosoft的代表作之一，讲述了一群创作者们打破常规、追求创新的故事。游戏以轻松幽默的方式探讨了创作与生活的平衡，角色个性鲜明，剧情充满惊喜。</p>
                            
                            <h2>主要角色</h2>
                            <div class="characters">
                                <div class="character">
                                    <div class="character-img" style="background-image: url('https://p3.ssl.qhimgs1.com/sdr/400__/t046c02df9b94a89ebd.jpg');"></div>
                                    <h3>和泉 妃爱</h3>
                                    <p>男主的亲妹妹，业界知名声优，歌手，曾经是著名儿童演员，艺名“小泉妃爱”</p>
                                </div>
                                <div class="character">
                                    <div class="character-img" style="background-image: url('http://tiebapic.baidu.com/forum/w%3D580/sign=a32cfb9d9fb44aed594ebeec831d876a/9befcc610c338744ceccd7ab140fd9f9d62aa02d.jpg?tbpicau=2025-12-10-05_70c4a189a36141b8b7b500ba956ccf91');"></div>
                                    <h3>常磐 华乃</h3>
                                    <p>男主的同班同学，业界知名画师，艺名“乃乃花”</p>
                                </div>
                                <div class="character">
                                    <div class="character-img" style="background-image: url('https://p5.ssl.qhimgs1.com/sdr/400__/t04b81bcb077b3762b5.jpg');"></div>
                                    <h3>锦 明日海</h3>
                                    <p>音乐制作人，兼Vtuber，艺名“雪景四季”</p>
                                </div>
                                <div class="character">
                                    <div class="character-img" style="background-image: url('https://p3.ssl.qhimgs1.com/sdr/400__/t045a565be3a3559523.jpg');"></div>
                                    <h3>镰仓 诗樱</h3>
                                    <p>著名小说家，艺名“星紫苑”</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        
        <!-- Navel页面 -->
        <section id="navel" class="page" style="background-image: url('https://p0.ssl.qhimgs1.com/sdr/400__/t01daf44203179db0e4.jpg');">
            <div class="container page-content">
                <div class="game-detail">
                    <div class="game-hero" style="background-image: url('https://so.360tres.com/dmsmfl/123_82_/t01c1f952a8e9eb6bb7.webp?size=675x400&phash=5986310835453235612');"></div>
                    <div class="game-info">
                        <div class="game-title">
                            <div class="company-logo">NVL</div>
                            <h1>Navel - 《近月少女的礼仪》</h1>
                        </div>
                        
                        <div class="game-desc">
                            <h2>公司介绍</h2>
                            <p>Navel是日本一家知名的美少女游戏品牌，以其独特的剧情和精美的原画著称。公司最著名的作品是《近月少女的礼仪》系列，该系列以其独特的女装题材和深刻的角色塑造赢得了大量粉丝。</p>
                            
                            <h2>《近月少女的礼仪》简介</h2>
                            <p>《近月少女的礼仪》讲述了大藏游星为了学习服装设计，伪装成女仆"小仓朝日"进入名门女子学园的故事。游戏以其独特的设定、精美的服装设计和深刻的情感描写成为经典之作。</p>
                            
                            <h2>主要角色</h2>
                            <div class="characters">
                                <div class="character">
                                    <div class="character-img" style="background-image: url('https://p0.ssl.qhimgs1.com/sdr/400__/t010f49eee1a8494b5a.jpg');"></div>
                                    <h3>大藏游星</h3>
                                    <p>主角，伪装成女仆"小仓朝日"</p>
                                </div>
                                <div class="character">
                                    <div class="character-img" style="background-image: url('https://img.moegirl.org.cn/common/d/d8/Tsuki_luna.jpg');"></div>
                                    <h3>樱小路露娜</h3>
                                    <p>天才服装设计师，游星的主人</p>
                                </div>
                                <div class="character">
                                    <div class="character-img" style="background-image: url('https://img.moegirl.org.cn/common/thumb/2/25/Minato.png/420px-Minato.png');"></div>
                                    <h3>柳之濑凑</h3>
                                    <p>游星的青梅竹马，知道他的秘密</p>
                                </div>
                                <div class="character">
                                    <div class="character-img" style="background-image: url('https://img.moegirl.org.cn/common/thumb/b/bf/Ruisui.jpg/420px-Ruisui.jpg');"></div>
                                    <h3>花之宫瑞穗</h3>
                                    <p>学园的学生会长，优雅的大小姐</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        
        <!-- Palette页面 -->
        <section id="palette" class="page" style="background-image: url('https://p2.ssl.qhimgs1.com/sdr/400__/t04d973220c94ade838.jpg');">
            <div class="container page-content">
                <div class="game-detail">
                    <div class="game-hero" style="background-image: url('https://storage.moegirl.org.cn/moegirl/commons/e/eb/Palette%28%E6%B8%B8%E6%88%8F%E5%85%AC%E5%8F%B8%29.png!/fw/300/watermark/url/L21vZWdpcmwvd2F0ZXJtYXJrLnBuZw==/align/southeast/margin/10x10/opacity/50?v=20210622014029');"></div>
                    <div class="game-info">
                        <div class="game-title">
                            <div class="company-logo">PAL</div>
                            <h1>Palette - 《9nine》系列</h1>
                        </div>
                        
                        <div class="game-desc">
                            <h2>公司介绍</h2>
                            <p>Palette是日本一家美少女游戏公司，以其独特的剧情设计和精美的原画著称。《9nine》系列是Palette的代表作，以其悬疑的剧情和超自然元素吸引了大量玩家。</p>
                            
                            <h2>《9nine》系列简介</h2>
                            <p>《9nine》系列是一个由多部作品组成的系列，讲述了主角新海翔与同伴们使用名为"Artifact"的神秘物品，解决各种超自然事件的故事。系列以其悬疑的剧情和深刻的角色塑造受到好评。</p>
                            
                            <h2>主要角色</h2>
                            <div class="characters">
                                <div class="character">
                                    <div class="character-img" style="background-image: url('https://p2.ssl.qhimgs1.com/sdr/400__/t014aa79d9b3eb68602.jpg');"></div>
                                    <h3>新海天</h3>
                                    <p>主角的亲妹妹，对主角怀有别样的情感</p>
                                </div>
                                <div class="character">
                                    <div class="character-img" style="background-image: url('https://p2.ssl.qhimgs1.com/sdr/400__/t0124eab95fcae7e828.png');"></div>
                                    <h3>九条都</h3>
                                    <p>翔的同班同学，擅长运动</p>
                                </div>
                                <div class="character">
                                    <div class="character-img" style="background-image: url('https://storage.moegirl.org.cn/moegirl/commons/5/57/Kousaka_Haruka.jpeg!/fw/600/watermark/url/L21vZWdpcmwvd2F0ZXJtYXJrLnBuZw==/align/southeast/margin/10x10/opacity/50?v=20190516092858');"></div>
                                    <h3>香坂春风</h3>
                                    <p>翔的学姐，温柔体贴</p>
                                </div>
                                <div class="character">
                                    <div class="character-img" style="background-image: url('https://storage.moegirl.org.cn/moegirl/commons/c/ca/9-nine-Ep.4_sale.jpg!/fw/600/watermark/url/L21vZWdpcmwvd2F0ZXJtYXJrLnBuZw==/align/southeast/margin/10x10/opacity/50?v=20220110162649');"></div>
                                    <h3>结城希亚</h3>
                                    <p>神秘转学生，与事件有关</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>
    </main>
    
    <footer>
        <div class="container">
            <p>© 2023 Galgame导航站 - 探索视觉小说的魅力</p>
            <p>本网站仅供学习交流使用，不用于商业用途</p>
        </div>
    </footer>
    
    <script>
        // 页面切换功能
        document.addEventListener('DOMContentLoaded', function() {
            const navLinks = document.querySelectorAll('.nav-link');
            const pages = document.querySelectorAll('.page');
            
            navLinks.forEach(link => {
                link.addEventListener('click', function(e) {
                    e.preventDefault();
                    
                    const targetPage = this.getAttribute('data-page');
                    
                    // 隐藏所有页面
                    pages.forEach(page => {
                        page.classList.remove('active');
                    });
                    
                    // 显示目标页面
                    document.getElementById(targetPage).classList.add('active');
                    
                    // 滚动到顶部
                    window.scrollTo(0, 0);
                });
            });
        });
    </script>
</body>
</html>
