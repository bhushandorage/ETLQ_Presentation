<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ETLQ - Enterprise Data Integration Platform</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            overflow-x: hidden;
        }

        .presentation {
            max-width: 100vw;
            position: relative;
        }

        .slide {
            min-height: 100vh;
            display: none;
            padding: 80px 80px;
            position: relative;
            animation: slideIn 0.8s ease-out;
        }

        .slide.active {
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        @keyframes slideIn {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .slide-header {
            text-align: center;
            margin-bottom: 50px;
        }

        .slide-title {
            font-size: 5.5rem;
            font-weight: 700;
            margin-bottom: 30px;
            background: linear-gradient(45deg, #ff6b6b, #ffd93d, #6bcf7f, #4d79ff);
            background-size: 400% 400%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: gradientShift 3s ease-in-out infinite;
        }

        @keyframes gradientShift {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }

        .slide-subtitle {
            font-size: 2rem;
            opacity: 0.9;
            font-weight: 300;
        }

        .content-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(450px, 1fr));
            gap: 50px;
            margin: 60px 0;
        }

        .feature-card {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 20px;
            padding: 50px;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .feature-card:hover {
            transform: translateY(-10px);
            background: rgba(255, 255, 255, 0.15);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.2);
        }

        .feature-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(255, 255, 255, 0.1), transparent);
            transform: rotate(45deg);
            transition: all 0.6s;
            opacity: 0;
        }

        .feature-card:hover::before {
            opacity: 1;
            animation: shimmer 1.5s ease-in-out;
        }

        @keyframes shimmer {
            0% { transform: translateX(-100%) translateY(-100%) rotate(45deg); }
            100% { transform: translateX(100%) translateY(100%) rotate(45deg); }
        }

        .feature-icon {
            font-size: 4.5rem;
            margin-bottom: 30px;
            display: block;
        }

        .feature-title {
            font-size: 2.2rem;
            font-weight: 600;
            margin-bottom: 25px;
            color: #ffd93d;
        }

        .feature-description {
            font-size: 1.4rem;
            line-height: 1.6;
            opacity: 0.9;
        }

        .tech-list {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            margin-top: 30px;
        }

        .tech-tag {
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
            padding: 12px 24px;
            border-radius: 25px;
            font-size: 1.2rem;
            font-weight: 500;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
            transition: transform 0.3s ease;
        }

        .tech-tag:hover {
            transform: scale(1.1);
        }

        .architecture-diagram {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 20px;
            padding: 60px;
            margin: 60px 0;
            text-align: center;
        }

        .flow-diagram {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 40px;
        }

        .flow-box {
            background: linear-gradient(135deg, #667eea, #764ba2);
            border: 2px solid rgba(255, 255, 255, 0.3);
            border-radius: 15px;
            padding: 35px 25px;
            min-width: 200px;
            text-align: center;
            position: relative;
            transition: all 0.3s ease;
            font-size: 1.3rem;
        }

        .flow-box:hover {
            transform: scale(1.05);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
        }

        .flow-arrow {
            font-size: 3rem;
            color: #ffd93d;
            margin: 0 20px;
        }

        .navigation {
            position: fixed;
            bottom: 30px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            gap: 15px;
            z-index: 100;
        }

        .nav-btn {
            background: rgba(255, 255, 255, 0.2);
            border: 2px solid rgba(255, 255, 255, 0.3);
            color: white;
            padding: 16px 32px;
            border-radius: 30px;
            cursor: pointer;
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
            font-weight: 600;
            font-size: 1.2rem;
        }

        .nav-btn:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
        }

        .slide-indicator {
            position: fixed;
            top: 40px;
            right: 40px;
            background: rgba(255, 255, 255, 0.2);
            padding: 15px 30px;
            border-radius: 25px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.3);
            font-size: 1.2rem;
        }

        .benefits-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 40px;
            margin: 60px 0;
        }

        .benefit-item {
            background: linear-gradient(135deg, rgba(255, 107, 107, 0.2), rgba(76, 201, 240, 0.2));
            border-radius: 15px;
            padding: 40px;
            text-align: center;
            border: 1px solid rgba(255, 255, 255, 0.2);
            transition: transform 0.3s ease;
        }

        .benefit-item:hover {
            transform: translateY(-12px);
        }

        .benefit-number {
            font-size: 3.5rem;
            font-weight: 700;
            color: #ffd93d;
            margin-bottom: 20px;
        }

        @media (max-width: 768px) {
            .slide {
                padding: 40px 20px;
            }
            
            .slide-title {
                font-size: 2.5rem;
            }
            
            .content-grid {
                grid-template-columns: 1fr;
            }
            
            .flow-diagram {
                flex-direction: column;
            }
            
            .flow-arrow {
                transform: rotate(90deg);
            }
        }
    </style>
</head>
<body>
    <div class="presentation">
        <div class="slide-indicator">
            <span id="slideCounter">1 / 8</span>
        </div>

        <!-- Slide 1: Title -->
        <div class="slide active">
            <div class="slide-header">
                <h1 class="slide-title">ETLQ</h1>
                <p class="slide-subtitle">Enterprise Data Integration Platform</p>
            </div>
            <div class="architecture-diagram">
                <h2 style="margin-bottom: 40px; font-size: 3rem;">Universal Data Processing Engine</h2>
                <div class="flow-diagram">
                    <div class="flow-box">
                        <div style="font-size: 1.5rem; margin-bottom: 10px;">📥</div>
                        <strong>EXTRACT</strong><br>
                        Multiple Sources
                    </div>
                    <div class="flow-arrow">→</div>
                    <div class="flow-box">
                        <div style="font-size: 1.5rem; margin-bottom: 10px;">⚙️</div>
                        <strong>TRANSFORM</strong><br>
                        Data Processing
                    </div>
                    <div class="flow-arrow">→</div>
                    <div class="flow-box">
                        <div style="font-size: 1.5rem; margin-bottom: 10px;">💾</div>
                        <strong>LOAD</strong><br>
                        Data Storage
                    </div>
                    <div class="flow-arrow">→</div>
                    <div class="flow-box">
                        <div style="font-size: 1.5rem; margin-bottom: 10px;">🔍</div>
                        <strong>QUERY</strong><br>
                        Data Access
                    </div>
                </div>
            </div>
        </div>

        <!-- Slide 2: Data Ingestion -->
        <div class="slide">
            <div class="slide-header">
                <h1 class="slide-title">Data Ingestion</h1>
                <p class="slide-subtitle">Multiple Channels, Multiple Formats</p>
            </div>
            <div class="content-grid">
                <div class="feature-card">
                    <div class="feature-icon">🌐</div>
                    <h3 class="feature-title">Communication Protocols</h3>
                    <p class="feature-description">Seamlessly connect through various channels</p>
                    <div class="tech-list">
                        <span class="tech-tag">REST API</span>
                        <span class="tech-tag">SFTP</span>
                        <span class="tech-tag">Message Queue</span>
                        <span class="tech-tag">Solace</span>
                        <span class="tech-tag">Apache Kafka</span>
                    </div>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">📄</div>
                    <h3 class="feature-title">Data Formats</h3>
                    <p class="feature-description">Support for industry-standard formats</p>
                    <div class="tech-list">
                        <span class="tech-tag">XML</span>
                        <span class="tech-tag">JSON</span>
                        <span class="tech-tag">CSV</span>
                        <span class="tech-tag">Flat Files</span>
                        <span class="tech-tag">Custom Formats</span>
                    </div>
                </div>
            </div>
        </div>

        <!-- Slide 3: Data Transformation -->
        <div class="slide">
            <div class="slide-header">
                <h1 class="slide-title">Data Transformation</h1>
                <p class="slide-subtitle">Powerful Processing Engine</p>
            </div>
            <div class="content-grid">
                <div class="feature-card">
                    <div class="feature-icon">🔄</div>
                    <h3 class="feature-title">Transformation Capabilities</h3>
                    <p class="feature-description">Comprehensive data processing and enrichment</p>
                    <ul style="margin-top: 30px; line-height: 2; font-size: 1.3rem;">
                        <li>• Data validation and cleansing</li>
                        <li>• Format conversion and mapping</li>
                        <li>• Business rule application</li>
                        <li>• Data aggregation and computation</li>
                        <li>• Custom transformation logic</li>
                    </ul>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">⚡</div>
                    <h3 class="feature-title">Performance Features</h3>
                    <p class="feature-description">Optimized for high-volume processing</p>
                    <ul style="margin-top: 30px; line-height: 2; font-size: 1.3rem;">
                        <li>• Real-time and batch processing</li>
                        <li>• Parallel processing capabilities</li>
                        <li>• Memory-efficient operations</li>
                        <li>• Error handling and recovery</li>
                        <li>• Monitoring and alerting</li>
                    </ul>
                </div>
            </div>
        </div>

        <!-- Slide 4: Data Storage -->
        <div class="slide">
            <div class="slide-header">
                <h1 class="slide-title">Data Storage & Management</h1>
                <p class="slide-subtitle">Reliable and Scalable Data Persistence</p>
            </div>
            <div class="content-grid">
                <div class="feature-card">
                    <div class="feature-icon">🗄️</div>
                    <h3 class="feature-title">Database Integration</h3>
                    <p class="feature-description">Support for various database technologies</p>
                    <div class="tech-list">
                        <span class="tech-tag">PostgreSQL</span>
                        <span class="tech-tag">MySQL</span>
                        <span class="tech-tag">Oracle</span>
                        <span class="tech-tag">SQL Server</span>
                        <span class="tech-tag">MongoDB</span>
                        <span class="tech-tag">Cassandra</span>
                    </div>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">🔒</div>
                    <h3 class="feature-title">Data Management</h3>
                    <p class="feature-description">Enterprise-grade data governance</p>
                    <ul style="margin-top: 30px; line-height: 2; font-size: 1.3rem;">
                        <li>• ACID compliance</li>
                        <li>• Data encryption at rest</li>
                        <li>• Backup and recovery</li>
                        <li>• Data lineage tracking</li>
                        <li>• Audit trails</li>
                    </ul>
                </div>
            </div>
        </div>

        <!-- Slide 5: Data Distribution -->
        <div class="slide">
            <div class="slide-header">
                <h1 class="slide-title">Data Distribution</h1>
                <p class="slide-subtitle">Downstream System Integration</p>
            </div>
            <div class="content-grid">
                <div class="feature-card">
                    <div class="feature-icon">📤</div>
                    <h3 class="feature-title">Output Channels</h3>
                    <p class="feature-description">Send processed data to downstream systems</p>
                    <div class="tech-list">
                        <span class="tech-tag">REST API</span>
                        <span class="tech-tag">SFTP</span>
                        <span class="tech-tag">Message Queue</span>
                        <span class="tech-tag">Solace</span>
                        <span class="tech-tag">Apache Kafka</span>
                    </div>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">🎯</div>
                    <h3 class="feature-title">Delivery Features</h3>
                    <p class="feature-description">Reliable and configurable data delivery</p>
                    <ul style="margin-top: 30px; line-height: 2; font-size: 1.3rem;">
                        <li>• Guaranteed delivery</li>
                        <li>• Retry mechanisms</li>
                        <li>• Load balancing</li>
                        <li>• Format transformation</li>
                        <li>• Scheduling and triggers</li>
                    </ul>
                </div>
            </div>
        </div>

        <!-- Slide 6: API Capabilities -->
        <div class="slide">
            <div class="slide-header">
                <h1 class="slide-title">API Capabilities</h1>
                <p class="slide-subtitle">RESTful Data Access</p>
            </div>
            <div class="content-grid">
                <div class="feature-card">
                    <div class="feature-icon">🔗</div>
                    <h3 class="feature-title">GET API Endpoints</h3>
                    <p class="feature-description">Expose data through REST APIs</p>
                    <ul style="margin-top: 30px; line-height: 2; font-size: 1.3rem;">
                        <li>• RESTful architecture</li>
                        <li>• JSON/XML responses</li>
                        <li>• Query parameters</li>
                        <li>• Pagination support</li>
                        <li>• Response filtering</li>
                    </ul>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">🛡️</div>
                    <h3 class="feature-title">Security & Performance</h3>
                    <p class="feature-description">Enterprise-ready API features</p>
                    <ul style="margin-top: 30px; line-height: 2; font-size: 1.3rem;">
                        <li>• Authentication & authorization</li>
                        <li>• Rate limiting</li>
                        <li>• API versioning</li>
                        <li>• Caching mechanisms</li>
                        <li>• Comprehensive logging</li>
                    </ul>
                </div>
            </div>
        </div>

        <!-- Slide 7: Monitoring & Cloud -->
        <div class="slide">
            <div class="slide-header">
                <h1 class="slide-title">Monitoring & Cloud Infrastructure</h1>
                <p class="slide-subtitle">Enterprise-Grade Operations</p>
            </div>
            <div class="content-grid">
                <div class="feature-card">
                    <div class="feature-icon">📊</div>
                    <h3 class="feature-title">Monitoring & Observability</h3>
                    <p class="feature-description">Comprehensive monitoring and alerting system</p>
                    <ul style="margin-top: 30px; line-height: 2; font-size: 1.3rem;">
                        <li>• Real-time dashboards</li>
                        <li>• Performance metrics</li>
                        <li>• Data quality monitoring</li>
                        <li>• System health checks</li>
                        <li>• Custom KPI tracking</li>
                    </ul>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">🚨</div>
                    <h3 class="feature-title">Intelligent Alerting</h3>
                    <p class="feature-description">Proactive issue detection and notification</p>
                    <ul style="margin-top: 30px; line-height: 2; font-size: 1.3rem;">
                        <li>• Threshold-based alerts</li>
                        <li>• Multi-channel notifications</li>
                        <li>• Escalation policies</li>
                        <li>• Anomaly detection</li>
                        <li>• Alert correlation</li>
                    </ul>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">☁️</div>
                    <h3 class="feature-title">Cloud-Native Architecture</h3>
                    <p class="feature-description">Kubernetes-based deployment for maximum flexibility</p>
                    <ul style="margin-top: 30px; line-height: 2; font-size: 1.3rem;">
                        <li>• Google Kubernetes Engine</li>
                        <li>• Container orchestration</li>
                        <li>• Service mesh integration</li>
                        <li>• Rolling deployments</li>
                        <li>• High availability</li>
                    </ul>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">📈</div>
                    <h3 class="feature-title">Auto-Scaling Capabilities</h3>
                    <p class="feature-description">Dynamic resource management based on demand</p>
                    <ul style="margin-top: 30px; line-height: 2; font-size: 1.3rem;">
                        <li>• Horizontal pod autoscaling</li>
                        <li>• Vertical scaling</li>
                        <li>• Load-based scaling</li>
                        <li>• Cost optimization</li>
                        <li>• Resource quotas</li>
                    </ul>
                </div>
            </div>
        </div>

        <!-- Slide 8: Benefits -->
        <div class="slide">
            <div class="slide-header">
                <h1 class="slide-title">Key Benefits</h1>
                <p class="slide-subtitle">Why Choose ETLQ?</p>
            </div>
            <div class="benefits-grid">
                <div class="benefit-item">
                    <div class="benefit-number">01</div>
                    <h3 style="margin-bottom: 15px; font-size: 1.8rem;">Cost Effective</h3>
                    <p style="font-size: 1.3rem;">Pay-as-you-scale cloud infrastructure with automated optimization</p>bottom: 15px; font-size: 1.8rem;">Universal Connectivity</h3>
                    <p style="font-size: 1.3rem;">Connect to any system using multiple protocols and formats</p>
                </div>
                <div class="benefit-item">
                    <div class="benefit-number">02</div>
                    <h3 style="margin-bottom: 15px; font-size: 1.8rem;">Cloud-Native Scalability</h3>
                    <p style="font-size: 1.3rem;">Auto-scaling Kubernetes deployment handles any workload</p>
                </div>
                <div class="benefit-item">
                    <div class="benefit-number">03</div>
                    <h3 style="margin-bottom: 15px; font-size: 1.8rem;">Intelligent Monitoring</h3>
                    <p style="font-size: 1.3rem;">Comprehensive observability with proactive alerting</p>
                </div>
                <div class="benefit-item">
                    <div class="benefit-number">04</div>
                    <h3 style="margin-bottom: 15px; font-size: 1.8rem;">Easy Integration</h3>
                    <p style="font-size: 1.3rem;">Simple REST APIs for seamless integration with existing systems</p>
                </div>
                <div class="benefit-item">
                    <div class="benefit-number">05</div>
                    <h3 style="margin-bottom: 10px;">Cost Effective</h3>
                    <p>Pay-as-you-scale cloud infrastructure with automated optimization</p>
                </div>
                <div class="benefit-item">
                    <div class="benefit-number">06</div>
                    <h3 style="margin-bottom: 10px;">Enterprise Ready</h3>
                    <p>High availability, security, and compliance built-in</p>
                </div>
            </div>
        </div>
    </div>

    <div class="navigation">
        <button class="nav-btn" onclick="previousSlide()">← Previous</button>
        <button class="nav-btn" onclick="nextSlide()">Next →</button>
    </div>

    <script>
        let currentSlide = 0;
        const slides = document.querySelectorAll('.slide');
        const totalSlides = slides.length;

        function showSlide(index) {
            slides.forEach(slide => slide.classList.remove('active'));
            slides[index].classList.add('active');
            document.getElementById('slideCounter').textContent = `${index + 1} / ${totalSlides}`;
        }

        function nextSlide() {
            currentSlide = (currentSlide + 1) % totalSlides;
            showSlide(currentSlide);
        }

        function previousSlide() {
            currentSlide = (currentSlide - 1 + totalSlides) % totalSlides;
            showSlide(currentSlide);
        }

        // Keyboard navigation
        document.addEventListener('keydown', (e) => {
            if (e.key === 'ArrowRight' || e.key === ' ') {
                nextSlide();
            } else if (e.key === 'ArrowLeft') {
                previousSlide();
            }
        });

        // Auto-advance slides every 15 seconds (optional)
        // setInterval(nextSlide, 15000);
    </script>
</body>
</html>
