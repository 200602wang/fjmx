# fjmx
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>施工3D模型与注意事项展示</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', 'Microsoft YaHei', sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            color: #333;
            line-height: 1.6;
            padding: 20px;
            min-height: 100vh;
        }
        
        .container {
            max-width: 1400px;
            margin: 0 auto;
        }
        
        header {
            text-align: center;
            margin-bottom: 30px;
            padding: 20px;
            background: linear-gradient(90deg, #1a365d 0%, #2d4a7c 100%);
            border-radius: 12px;
            color: white;
            box-shadow: 0 6px 20px rgba(0, 0, 0, 0.1);
        }
        
        h1 {
            color: white;
            margin-bottom: 10px;
            font-size: 2.5rem;
            font-weight: 600;
        }
        
        .subtitle {
            color: rgba(255, 255, 255, 0.9);
            font-size: 1.1rem;
            max-width: 800px;
            margin: 0 auto;
        }
        
        .main-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
            margin-bottom: 40px;
        }
        
        .model-section {
            background-color: white;
            border-radius: 15px;
            padding: 25px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            display: flex;
            flex-direction: column;
            height: 600px;
        }
        
        .model-section:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.12);
        }
        
        .section-title {
            font-size: 1.8rem;
            color: #1a2b50;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid #0072ff;
            display: flex;
            align-items: center;
        }
        
        .section-title i {
            margin-right: 10px;
            font-size: 1.5rem;
        }
        
        .model-viewer {
            flex-grow: 1;
            background-color: #f8fafc;
            border-radius: 10px;
            overflow: hidden;
            margin-bottom: 20px;
            border: 1px solid #e1e8f0;
            min-height: 450px;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
        }
        
        .sketchfab-embed-wrapper {
            width: 100%;
            height: 100%;
        }
        
        .sketchfab-embed-wrapper iframe {
            width: 100%;
            height: 100%;
            border: none;
        }
        
        .construction-image-container {
            width: 100%;
            height: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            border-radius: 8px;
            background-color: #f0f4f8;
            position: relative;
        }
        
        .construction-image {
            max-width: 100%;
            max-height: 100%;
            object-fit: contain;
        }
        
        .construction-overlay {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: rgba(26, 43, 80, 0.85);
            color: white;
            padding: 15px;
            font-size: 0.9rem;
        }
        
        .details-section {
            grid-column: span 2;
            background-color: white;
            border-radius: 15px;
            padding: 30px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
            border-top: 5px solid #e63946;
        }
        
        .details-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 25px;
        }
        
        .detail-box {
            padding: 20px;
            border-radius: 10px;
            border-left: 4px solid;
            transition: all 0.3s ease;
        }
        
        .safety-box {
            background-color: #fff5f5;
            border-left-color: #e63946;
        }
        
        .process-box {
            background-color: #f0f9ff;
            border-left-color: #1d4ed8;
        }
        
        .quality-box {
            background-color: #f0fff4;
            border-left-color: #10b981;
        }
        
        .detail-box h3 {
            color: #1a2b50;
            margin-bottom: 15px;
            font-size: 1.4rem;
            display: flex;
            align-items: center;
        }
        
        .detail-box h3 i {
            margin-right: 10px;
        }
        
        .detail-box ul {
            list-style-type: none;
        }
        
        .detail-box li {
            margin-bottom: 12px;
            padding-left: 5px;
            position: relative;
        }
        
        .detail-box li:before {
            content: "•";
            font-weight: bold;
            display: inline-block;
            width: 1em;
            margin-left: -1em;
        }
        
        .safety-box li:before {
            color: #e63946;
        }
        
        .process-box li:before {
            color: #1d4ed8;
        }
        
        .quality-box li:before {
            color: #10b981;
        }
        
        .warning-section {
            background-color: #fff8e1;
            border-left: 4px solid #f59e0b;
            padding: 25px;
            border-radius: 10px;
            margin-top: 30px;
        }
        
        .warning-section h3 {
            color: #d97706;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
        }
        
        .warning-section h3 i {
            margin-right: 10px;
        }
        
        .warning-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 15px;
        }
        
        .warning-item {
            display: flex;
            align-items: flex-start;
            padding: 10px 0;
        }
        
        .warning-item i {
            color: #f59e0b;
            margin-right: 10px;
            margin-top: 3px;
            font-size: 1.2rem;
        }
        
        .model-info {
            margin-top: 15px;
            padding-top: 15px;
            border-top: 1px solid #eaeaea;
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
        }
        
        .model-info p {
            margin-bottom: 8px;
            font-size: 0.95rem;
            color: #555;
            flex-basis: 48%;
        }
        
        .sketchfab-credit {
            font-size: 13px;
            font-weight: normal;
            margin-top: 10px;
            color: #4A4A4A;
            text-align: center;
        }
        
        .sketchfab-credit a {
            font-weight: bold;
            color: #1CAAD9;
            text-decoration: none;
        }
        
        .sketchfab-credit a:hover {
            text-decoration: underline;
        }
        
        .priority-indicator {
            display: inline-block;
            padding: 2px 8px;
            border-radius: 4px;
            font-size: 0.75rem;
            font-weight: bold;
            margin-left: 8px;
        }
        
        .high-priority {
            background-color: #fecaca;
            color: #991b1b;
        }
        
        .medium-priority {
            background-color: #fed7aa;
            color: #9a3412;
        }
        
        .low-priority {
            background-color: #bbf7d0;
            color: #166534;
        }
        
        footer {
            text-align: center;
            margin-top: 40px;
            padding-top: 20px;
            color: #777;
            border-top: 1px solid #e1e8f0;
            font-size: 0.9rem;
        }
        
        .checklist-container {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            margin-top: 20px;
        }
        
        .checklist {
            flex: 1;
            min-width: 250px;
            background: #f8fafc;
            border-radius: 8px;
            padding: 15px;
        }
        
        .checklist h4 {
            color: #1a2b50;
            margin-bottom: 10px;
            border-bottom: 1px solid #ddd;
            padding-bottom: 5px;
        }
        
        .checklist-item {
            display: flex;
            align-items: center;
            margin-bottom: 8px;
        }
        
        .checklist-item input {
            margin-right: 10px;
        }
        
        @media (max-width: 1024px) {
            .main-content {
                grid-template-columns: 1fr;
                gap: 20px;
            }
            
            .details-section {
                grid-column: span 1;
            }
            
            .model-section {
                height: 500px;
            }
        }
        
        @media (max-width: 768px) {
            h1 {
                font-size: 2rem;
            }
            
            .model-section {
                padding: 20px;
                height: 450px;
            }
            
            .details-grid {
                grid-template-columns: 1fr;
            }
            
            .model-info p {
                flex-basis: 100%;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1><i class="fas fa-hard-hat"></i> 施工3D模型与注意事项展示</h1>
            <p class="subtitle">基于3D施工模型的现场施工注意事项、安全规范与质量控制要点</p>
        </header>
        
        <main>
            <div class="main-content">
                <!-- 左侧：3D施工模型区域 -->
                <section class="model-section">
                    <h2 class="section-title"><i class="fas fa-cube"></i> 施工3D模型预览</h2>
                    <div class="model-viewer">
                        <div class="sketchfab-embed-wrapper">
                            <iframe 
                                title="新建文件夹 (2)" 
                                frameborder="0" 
                                allowfullscreen 
                                mozallowfullscreen="true" 
                                webkitallowfullscreen="true" 
                                allow="autoplay; fullscreen; xr-spatial-tracking" 
                                xr-spatial-tracking 
                                execution-while-out-of-viewport 
                                execution-while-not-rendered 
                                web-share 
                                src="https://sketchfab.com/models/a39e745f182e4237a0e09cc8202b5645/embed">
                            </iframe>
                        </div>
                    </div>
                    <div class="model-info">
                        <p><strong>模型名称：</strong>施工结构模型</p>
                        <p><strong>应用场景：</strong>现场施工指导与安全规划</p>
                        <p><strong>作者：</strong>风车树下 (Feng-Che-Shu)</p>
                        <p><strong>平台：</strong>Sketchfab</p>
                    </div>
                </section>
                
                <!-- 右侧：施工示意图区域 -->
                <section class="model-section">
                    <h2 class="section-title"><i class="fas fa-hard-hat"></i> 施工安全示意图</h2>
                    <div class="model-viewer">
                        <div class="construction-image-container">
                            <img src="https://image2url.com/r2/bucket1/images/1767757569798-3a47e83f-039b-4815-8189-c55133fc8b76.png" alt="施工安全示意图" class="construction-image" id="construction-image">
                            <div class="construction-overlay">
                                <p><i class="fas fa-exclamation-circle"></i> 施工示意图用于标识安全区域、危险点位和关键施工路径</p>
                            </div>
                        </div>
                    </div>
                    <div class="model-info">
                        <p><strong>图示说明：</strong>红色-危险区域，黄色-警示区域，绿色-安全通道</p>
                        <p><strong>使用目的：</strong>现场安全指导与施工流程规划</p>
                    </div>
                </section>
                
                <!-- 下方：施工注意事项区域 -->
                <section class="details-section">
                    <h2 class="section-title"><i class="fas fa-clipboard-check"></i> 施工注意事项与安全规范</h2>
                    
                    <div class="details-grid">
                        <div class="detail-box safety-box">
                            <h3><i class="fas fa-shield-alt"></i> 安全注意事项
                                <span class="priority-indicator high-priority">高优先级</span>
                            </h3>
                            <ul>
                                <li>所有施工人员必须佩戴安全帽、安全鞋及反光背心等个人防护装备</li>
                                <li>高处作业必须系好安全带，设置安全防护网和警示标识</li>
                                <li>施工区域必须设置明显的安全警示标志和围挡设施</li>
                                <li>特种作业人员必须持证上岗，严禁无证操作</li>
                                <li>每日施工前进行安全交底，检查施工设备安全状态</li>
                                <li>施工现场必须配备足够数量的灭火器等消防设施</li>
                                <li>电气设备必须接地保护，临时用电需符合规范要求</li>
                            </ul>
                        </div>
                        
                        <div class="detail-box process-box">
                            <h3><i class="fas fa-tasks"></i> 施工流程注意事项
                                <span class="priority-indicator medium-priority">中优先级</span>
                            </h3>
                            <ul>
                                <li>严格按照3D模型和施工图纸进行施工，确保尺寸准确</li>
                                <li>材料进场需进行质量检验，不合格材料严禁使用</li>
                                <li>各工序之间需进行交接检查，确保上道工序合格</li>
                                <li>混凝土浇筑需连续进行，避免产生施工冷缝</li>
                                <li>钢结构安装需按顺序进行，确保结构稳定性</li>
                                <li>隐蔽工程在覆盖前必须经监理验收合格</li>
                                <li>施工记录必须真实、完整、及时，便于追溯</li>
                            </ul>
                        </div>
                        
                        <div class="detail-box quality-box">
                            <h3><i class="fas fa-award"></i> 质量控制注意事项
                                <span class="priority-indicator high-priority">高优先级</span>
                            </h3>
                            <ul>
                                <li>建立完善的质量管理体系，明确质量责任人</li>
                                <li>关键部位施工实行旁站监督，确保施工质量</li>
                                <li>定期对施工质量进行检查，发现问题及时整改</li>
                                <li>材料样品需封样保存，作为验收比对标准</li>
                                <li>严格执行施工规范和技术标准，不得擅自降低标准</li>
                                <li>完工后进行质量检测，确保符合设计要求</li>
                                <li>建立质量缺陷台账，制定整改措施并跟踪落实</li>
                            </ul>
                        </div>
                    </div>
                    
                    <div class="warning-section">
                        <h3><i class="fas fa-exclamation-triangle"></i> 关键风险提示与应急措施</h3>
                        <div class="warning-grid">
                            <div class="warning-item">
                                <i class="fas fa-hard-hat"></i>
                                <div>
                                    <strong>坍塌风险</strong>
                                    <p>基坑、模板支撑系统必须按方案施工，定期监测变形</p>
                                </div>
                            </div>
                            <div class="warning-item">
                                <i class="fas fa-bolt"></i>
                                <div>
                                    <strong>触电风险</strong>
                                    <p>临时用电实行三级配电两级保护，电缆线架空或埋地</p>
                                </div>
                            </div>
                            <div class="warning-item">
                                <i class="fas fa-fire"></i>
                                <div>
                                    <strong>火灾风险</strong>
                                    <p>动火作业需办理动火证，配备看火人和灭火器材</p>
                                </div>
                            </div>
                            <div class="warning-item">
                                <i class="fas fa-falling-rocks"></i>
                                <div>
                                    <strong>物体打击</strong>
                                    <p>高处作业工具必须系安全绳，下方设置警戒区域</p>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- 施工检查清单 -->
                    <div class="checklist-container">
                        <div class="checklist">
                            <h4><i class="fas fa-clipboard-list"></i> 每日施工前检查清单</h4>
                            <div class="checklist-item">
                                <input type="checkbox" id="check1">
                                <label for="check1">安全防护用品齐全有效</label>
                            </div>
                            <div class="checklist-item">
                                <input type="checkbox" id="check2">
                                <label for="check2">施工设备检查调试完成</label>
                            </div>
                            <div class="checklist-item">
                                <input type="checkbox" id="check3">
                                <label for="check3">作业环境安全检查完毕</label>
                            </div>
                            <div class="checklist-item">
                                <input type="checkbox" id="check4">
                                <label for="check4">当日安全交底已完成</label>
                            </div>
                        </div>
                        
                        <div class="checklist">
                            <h4><i class="fas fa-clipboard-list"></i> 每周安全检查清单</h4>
                            <div class="checklist-item">
                                <input type="checkbox" id="check5">
                                <label for="check5">脚手架及支撑系统检查</label>
                            </div>
                            <div class="checklist-item">
                                <input type="checkbox" id="check6">
                                <label for="check6">临时用电系统全面检查</label>
                            </div>
                            <div class="checklist-item">
                                <input type="checkbox" id="check7">
                                <label for="check7">消防设施有效性检查</label>
                            </div>
                            <div class="checklist-item">
                                <input type="checkbox" id="check8">
                                <label for="check8">应急预案演练与评估</label>
                            </div>
                        </div>
                    </div>
                </section>
            </div>
        </main>
        
        <footer>
            <p>© 2025 施工安全与质量管理展示系统 | 施工安全第一，预防为主</p>
            <p>本页面用于施工安全培训与现场指导，实际施工请严格遵守国家相关安全规范</p>
            <p>技术实现: HTML5 + CSS3 + Sketchfab嵌入API + Font Awesome图标</p>
        </footer>
    </div>

    <script>
        // 图片加载状态检查
        document.addEventListener('DOMContentLoaded', function() {
            const constructionImage = document.getElementById('construction-image');
            
            constructionImage.onload = function() {
                console.log('施工示意图加载成功');
            };
            
            constructionImage.onerror = function() {
                console.error('施工示意图加载失败');
                // 如果图片加载失败，显示施工安全示意图
                const imageContainer = document.querySelector('.construction-image-container');
                imageContainer.innerHTML = `
                    <div style="text-align: center; padding: 40px; color: #666; width: 100%;">
                        <i class="fas fa-hard-hat" style="font-size: 4rem; margin-bottom: 20px; display: block; color: #1a365d;"></i>
                        <h3 style="color: #1a365d; margin-bottom: 15px;">施工安全示意图</h3>
                        <div style="display: flex; justify-content: center; gap: 30px; margin-top: 25px; flex-wrap: wrap;">
                            <div style="text-align: center;">
                                <div style="width: 40px; height: 40px; background-color: #e63946; border-radius: 50%; margin: 0 auto 10px;"></div>
                                <div>危险区域</div>
                            </div>
                            <div style="text-align: center;">
                                <div style="width: 40px; height: 40px; background-color: #f59e0b; border-radius: 50%; margin: 0 auto 10px;"></div>
                                <div>警示区域</div>
                            </div>
                            <div style="text-align: center;">
                                <div style="width: 40px; height: 40px; background-color: #10b981; border-radius: 50%; margin: 0 auto 10px;"></div>
                                <div>安全通道</div>
                            </div>
                        </div>
                        <div class="construction-overlay">
                            <p><i class="fas fa-exclamation-circle"></i> 施工示意图用于标识安全区域、危险点位和关键施工路径</p>
                        </div>
                    </div>
                `;
            };
            
            // 为详情框添加交互效果
            const detailBoxes = document.querySelectorAll('.detail-box');
            detailBoxes.forEach(box => {
                box.addEventListener('mouseenter', function() {
                    this.style.transform = 'translateY(-5px)';
                    this.style.boxShadow = '0 8px 25px rgba(0, 0, 0, 0.15)';
                });
                
                box.addEventListener('mouseleave', function() {
                    this.style.transform = 'translateY(0)';
                    this.style.boxShadow = 'none';
                });
            });
            
            // 检查清单交互
            const checkboxes = document.querySelectorAll('.checklist-item input');
            checkboxes.forEach(checkbox => {
                checkbox.addEventListener('change', function() {
                    const label = this.nextElementSibling;
                    if (this.checked) {
                        label.style.textDecoration = 'line-through';
                        label.style.color = '#999';
                    } else {
                        label.style.textDecoration = 'none';
                        label.style.color = '#333';
                    }
                });
            });
            
            // 检查Sketchfab iframe加载状态
            const sketchfabIframe = document.querySelector('.sketchfab-embed-wrapper iframe');
            sketchfabIframe.onload = function() {
                console.log('Sketchfab 3D施工模型加载完成');
            };
        });
    </script>
</body>
</html>
