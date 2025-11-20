[pyetesor_interaktiv.html](https://github.com/user-attachments/files/23663904/pyetesor_interaktiv.html)
<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pyetësor: Bilanci Jetë Private - Jetë Profesionale</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 800px;
            margin: 0 auto;
            background: white;
            border-radius: 15px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.2);
            overflow: hidden;
        }

        .header {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 40px 30px;
            text-align: center;
        }

        .header h1 {
            font-size: 28px;
            margin-bottom: 15px;
        }

        .header p {
            font-size: 16px;
            line-height: 1.6;
            opacity: 0.95;
        }

        .progress-bar {
            width: 100%;
            height: 6px;
            background: rgba(255,255,255,0.3);
            margin-top: 20px;
        }

        .progress-fill {
            height: 100%;
            background: #4ecdc4;
            width: 0%;
            transition: width 0.3s ease;
        }

        .content {
            padding: 40px 30px;
        }

        .section {
            display: none;
            animation: fadeIn 0.5s ease;
        }

        .section.active {
            display: block;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .section-title {
            color: #667eea;
            font-size: 24px;
            margin-bottom: 30px;
            padding-bottom: 10px;
            border-bottom: 3px solid #667eea;
        }

        .question {
            margin-bottom: 30px;
        }

        .question-label {
            display: block;
            font-size: 16px;
            font-weight: 600;
            color: #333;
            margin-bottom: 15px;
        }

        .question-number {
            color: #667eea;
            margin-right: 8px;
        }

        .required {
            color: #dc3545;
            margin-left: 5px;
        }

        .radio-group, .checkbox-group {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .radio-option, .checkbox-option {
            display: flex;
            align-items: center;
            padding: 12px 15px;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .radio-option:hover, .checkbox-option:hover {
            border-color: #667eea;
            background: #f8f9fa;
        }

        .radio-option.selected, .checkbox-option.selected {
            border-color: #667eea;
            background: #f0f4ff;
        }

        .radio-option input[type="radio"],
        .checkbox-option input[type="checkbox"] {
            margin-right: 10px;
            cursor: pointer;
            width: 18px;
            height: 18px;
        }

        .linear-scale {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin: 20px 0;
            gap: 10px;
        }

        .scale-option {
            display: flex;
            flex-direction: column;
            align-items: center;
            cursor: pointer;
        }

        .scale-circle {
            width: 45px;
            height: 45px;
            border: 2px solid #e0e0e0;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            color: #666;
            transition: all 0.3s ease;
            margin-bottom: 5px;
        }

        .scale-option:hover .scale-circle {
            border-color: #667eea;
            transform: scale(1.1);
        }

        .scale-option input[type="radio"]:checked + .scale-circle {
            background: #667eea;
            border-color: #667eea;
            color: white;
            transform: scale(1.15);
        }

        .scale-label {
            font-size: 12px;
            color: #666;
            text-align: center;
        }

        .scale-endpoints {
            display: flex;
            justify-content: space-between;
            margin-top: 10px;
            font-size: 14px;
            color: #666;
        }

        textarea {
            width: 100%;
            min-height: 120px;
            padding: 15px;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            font-family: inherit;
            font-size: 15px;
            resize: vertical;
            transition: border-color 0.3s ease;
        }

        textarea:focus {
            outline: none;
            border-color: #667eea;
        }

        .grid-question {
            overflow-x: auto;
        }

        .grid-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 15px;
        }

        .grid-table th {
            background: #667eea;
            color: white;
            padding: 12px 8px;
            font-weight: 600;
            font-size: 14px;
            text-align: center;
        }

        .grid-table td {
            padding: 15px 8px;
            border-bottom: 1px solid #e0e0e0;
            text-align: center;
        }

        .grid-table td:first-child {
            text-align: left;
            font-weight: 500;
            color: #333;
        }

        .grid-table tr:hover {
            background: #f8f9fa;
        }

        .buttons {
            display: flex;
            justify-content: space-between;
            margin-top: 40px;
            padding-top: 30px;
            border-top: 2px solid #e0e0e0;
        }

        .btn {
            padding: 12px 30px;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .btn-primary {
            background: #667eea;
            color: white;
        }

        .btn-primary:hover {
            background: #5568d3;
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
        }

        .btn-secondary {
            background: #6c757d;
            color: white;
        }

        .btn-secondary:hover {
            background: #5a6268;
        }

        .btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }

        .error-message {
            color: #dc3545;
            font-size: 14px;
            margin-top: 10px;
            display: none;
        }

        .error-message.show {
            display: block;
        }

        .results {
            display: none;
            text-align: center;
            padding: 40px 20px;
        }

        .results.active {
            display: block;
        }

        .results-icon {
            font-size: 80px;
            margin-bottom: 20px;
        }

        .results h2 {
            color: #28a745;
            font-size: 32px;
            margin-bottom: 20px;
        }

        .results p {
            font-size: 18px;
            color: #666;
            line-height: 1.6;
            margin-bottom: 30px;
        }

        .download-btn {
            background: #28a745;
            color: white;
            padding: 15px 40px;
            border: none;
            border-radius: 8px;
            font-size: 18px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            margin: 10px;
        }

        .download-btn:hover {
            background: #218838;
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(40, 167, 69, 0.4);
        }

        .summary-card {
            background: #f8f9fa;
            border-radius: 10px;
            padding: 20px;
            margin: 20px 0;
            text-align: left;
        }

        .summary-card h3 {
            color: #667eea;
            margin-bottom: 15px;
        }

        .summary-item {
            padding: 10px 0;
            border-bottom: 1px solid #e0e0e0;
        }

        .summary-item:last-child {
            border-bottom: none;
        }

        .summary-label {
            font-weight: 600;
            color: #333;
            display: inline-block;
            min-width: 200px;
        }

        .summary-value {
            color: #666;
        }

        @media (max-width: 768px) {
            .container {
                border-radius: 0;
            }

            .content {
                padding: 30px 20px;
            }

            .linear-scale {
                flex-wrap: wrap;
            }

            .scale-circle {
                width: 40px;
                height: 40px;
            }

            .buttons {
                flex-direction: column;
                gap: 10px;
            }

            .btn {
                width: 100%;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>📊 Pyetësor: Bilanci Jetë Private - Jetë Profesionale</h1>
            <p>Gjenerata X (44-59 vjeç)</p>
            <p style="margin-top: 15px; font-size: 14px;">
                Ky pyetësor synon të eksplorojë bilancin ndërmjet jetës private dhe profesionale 
                për të kuptuar se si arrihet kënaqësia optimale në jetë. Do të zgjasë rreth 8-10 minuta.
            </p>
            <div class="progress-bar">
                <div class="progress-fill" id="progressFill"></div>
            </div>
        </div>

        <div class="content">
            <!-- SEKSIONI 1: TË DHËNA DEMOGRAFIKE -->
            <div class="section active" data-section="1">
                <h2 class="section-title">Seksioni 1: Të Dhëna Demografike</h2>

                <div class="question">
                    <label class="question-label">
                        <span class="question-number">1.</span>
                        Mosha juaj
                        <span class="required">*</span>
                    </label>
                    <div class="radio-group">
                        <label class="radio-option">
                            <input type="radio" name="q1" value="44-49 vjeç" required>
                            <span>44-49 vjeç</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q1" value="50-54 vjeç" required>
                            <span>50-54 vjeç</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q1" value="55-59 vjeç" required>
                            <span>55-59 vjeç</span>
                        </label>
                    </div>
                    <div class="error-message">Ju lutem zgjidhni një opsion</div>
                </div>

                <div class="question">
                    <label class="question-label">
                        <span class="question-number">2.</span>
                        Gjinia
                        <span class="required">*</span>
                    </label>
                    <div class="radio-group">
                        <label class="radio-option">
                            <input type="radio" name="q2" value="Mashkull" required>
                            <span>Mashkull</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q2" value="Femër" required>
                            <span>Femër</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q2" value="Prefer të mos përgjigjëm" required>
                            <span>Prefer të mos përgjigjëm</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q2" value="Tjetër" required>
                            <span>Tjetër</span>
                        </label>
                    </div>
                    <div class="error-message">Ju lutem zgjidhni një opsion</div>
                </div>

                <div class="question">
                    <label class="question-label">
                        <span class="question-number">3.</span>
                        Statusi martesor
                        <span class="required">*</span>
                    </label>
                    <div class="radio-group">
                        <label class="radio-option">
                            <input type="radio" name="q3" value="I/E martuar / Partner" required>
                            <span>I/E martuar / Partner</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q3" value="I/E divorcuar" required>
                            <span>I/E divorcuar</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q3" value="Beqar" required>
                            <span>Beqar</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q3" value="Ve" required>
                            <span>Ve</span>
                        </label>
                    </div>
                    <div class="error-message">Ju lutem zgjidhni një opsion</div>
                </div>

                <div class="question">
                    <label class="question-label">
                        <span class="question-number">4.</span>
                        A keni fëmijë?
                        <span class="required">*</span>
                    </label>
                    <div class="radio-group">
                        <label class="radio-option">
                            <input type="radio" name="q4" value="Jo" onclick="hideChildrenDetails()">
                            <span>Jo</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q4" value="Po" onclick="showChildrenDetails()">
                            <span>Po</span>
                        </label>
                    </div>
                    <div class="error-message">Ju lutem zgjidhni një opsion</div>
                    
                    <!-- Detajet e fëmijëve (shfaqet vetëm nëse zgjidhet "Po") -->
                    <div id="childrenDetails" style="display: none; margin-top: 20px; padding: 20px; background: #f8f9fa; border-radius: 8px; border-left: 4px solid #667eea;">
                        <label class="question-label" style="font-size: 15px; margin-bottom: 15px;">
                            Sa fëmijë keni?
                        </label>
                        <div class="radio-group">
                            <label class="radio-option">
                                <input type="radio" name="q4_number" value="1 fëmijë">
                                <span>1 fëmijë</span>
                            </label>
                            <label class="radio-option">
                                <input type="radio" name="q4_number" value="2 fëmijë">
                                <span>2 fëmijë</span>
                            </label>
                            <label class="radio-option">
                                <input type="radio" name="q4_number" value="3 fëmijë">
                                <span>3 fëmijë</span>
                            </label>
                            <label class="radio-option">
                                <input type="radio" name="q4_number" value="4 ose më shumë fëmijë">
                                <span>4 ose më shumë fëmijë</span>
                            </label>
                        </div>

                        <label class="question-label" style="font-size: 15px; margin-top: 20px; margin-bottom: 15px;">
                            Mosha e fëmijëve (mund të zgjidhni më shumë se një):
                        </label>
                        <div class="checkbox-group">
                            <label class="checkbox-option">
                                <input type="checkbox" name="q4_ages" value="0-5 vjeç (foshnjë/parafëmijëri)">
                                <span>0-5 vjeç (foshnjë/parafëmijëri)</span>
                            </label>
                            <label class="checkbox-option">
                                <input type="checkbox" name="q4_ages" value="6-12 vjeç (fëmijëri)">
                                <span>6-12 vjeç (fëmijëri)</span>
                            </label>
                            <label class="checkbox-option">
                                <input type="checkbox" name="q4_ages" value="13-17 vjeç (adoleshentë)">
                                <span>13-17 vjeç (adoleshentë)</span>
                            </label>
                            <label class="checkbox-option">
                                <input type="checkbox" name="q4_ages" value="18+ vjeç (të rritur)">
                                <span>18+ vjeç (të rritur)</span>
                            </label>
                        </div>
                    </div>
                </div>

                <div class="question">
                    <label class="question-label">
                        <span class="question-number">5.</span>
                        Statusi i punës
                        <span class="required">*</span>
                    </label>
                    <div class="radio-group">
                        <label class="radio-option">
                            <input type="radio" name="q5" value="Punonjës me orar të plotë" required>
                            <span>Punonjës me orar të plotë</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q5" value="Punonjës me orar të pjesshëm" required>
                            <span>Punonjës me orar të pjesshëm</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q5" value="Vetëpunësuar" required>
                            <span>Vetëpunësuar</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q5" value="Menaxher/Drejtues" required>
                            <span>Menaxher/Drejtues</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q5" value="Në pension" required>
                            <span>Në pension</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q5" value="Tjetër" required>
                            <span>Tjetër</span>
                        </label>
                    </div>
                    <div class="error-message">Ju lutem zgjidhni një opsion</div>
                </div>

                <div class="buttons">
                    <button class="btn btn-secondary" onclick="prevSection()" disabled>← Mbrapa</button>
                    <button class="btn btn-primary" onclick="nextSection()">Vazhdo →</button>
                </div>
            </div>

            <!-- SEKSIONI 2: JETA PROFESIONALE -->
            <div class="section" data-section="2">
                <h2 class="section-title">Seksioni 2: Jeta Profesionale</h2>

                <div class="question">
                    <label class="question-label">
                        <span class="question-number">6.</span>
                        Sa orë pune në javë kryeni mesatarisht?
                        <span class="required">*</span>
                    </label>
                    <div class="radio-group">
                        <label class="radio-option">
                            <input type="radio" name="q6" value="Më pak se 35 orë" required>
                            <span>Më pak se 35 orë</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q6" value="35-40 orë" required>
                            <span>35-40 orë</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q6" value="41-50 orë" required>
                            <span>41-50 orë</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q6" value="51-60 orë" required>
                            <span>51-60 orë</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q6" value="Mbi 60 orë" required>
                            <span>Mbi 60 orë</span>
                        </label>
                    </div>
                    <div class="error-message">Ju lutem zgjidhni një opsion</div>
                </div>

                <div class="question">
                    <label class="question-label">
                        <span class="question-number">7.</span>
                        Sa shpesh punoni jashtë orarit zyrtar? (email, thirrje, projekte)
                        <span class="required">*</span>
                    </label>
                    <div class="radio-group">
                        <label class="radio-option">
                            <input type="radio" name="q7" value="Kurrë" required>
                            <span>Kurrë</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q7" value="Rrallë (1-2 herë në muaj)" required>
                            <span>Rrallë (1-2 herë në muaj)</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q7" value="Ndonjëherë (1-2 herë në javë)" required>
                            <span>Ndonjëherë (1-2 herë në javë)</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q7" value="Shpesh (pothuajse çdo ditë)" required>
                            <span>Shpesh (pothuajse çdo ditë)</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q7" value="Gjithmonë" required>
                            <span>Gjithmonë</span>
                        </label>
                    </div>
                    <div class="error-message">Ju lutem zgjidhni një opsion</div>
                </div>

                <div class="question">
                    <label class="question-label">
                        <span class="question-number">8.</span>
                        Niveli i kënaqësisë në punë
                        <span class="required">*</span>
                    </label>
                    <div class="linear-scale" id="scale-q8">
                        <label class="scale-option" onclick="selectScale('q8', 1)">
                            <input type="radio" name="q8" value="1" style="display:none" required>
                            <div class="scale-circle">1</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q8', 2)">
                            <input type="radio" name="q8" value="2" style="display:none" required>
                            <div class="scale-circle">2</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q8', 3)">
                            <input type="radio" name="q8" value="3" style="display:none" required>
                            <div class="scale-circle">3</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q8', 4)">
                            <input type="radio" name="q8" value="4" style="display:none" required>
                            <div class="scale-circle">4</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q8', 5)">
                            <input type="radio" name="q8" value="5" style="display:none" required>
                            <div class="scale-circle">5</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q8', 6)">
                            <input type="radio" name="q8" value="6" style="display:none" required>
                            <div class="scale-circle">6</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q8', 7)">
                            <input type="radio" name="q8" value="7" style="display:none" required>
                            <div class="scale-circle">7</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q8', 8)">
                            <input type="radio" name="q8" value="8" style="display:none" required>
                            <div class="scale-circle">8</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q8', 9)">
                            <input type="radio" name="q8" value="9" style="display:none" required>
                            <div class="scale-circle">9</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q8', 10)">
                            <input type="radio" name="q8" value="10" style="display:none" required>
                            <div class="scale-circle">10</div>
                        </label>
                    </div>
                    <div class="scale-endpoints">
                        <span>Aspak i kënaqur</span>
                        <span>Jashtëzakonisht i kënaqur</span>
                    </div>
                    <div class="error-message">Ju lutem zgjidhni një vlerë</div>
                </div>

                <div class="question">
                    <label class="question-label">
                        <span class="question-number">9.</span>
                        Sa i stresuar ndiheni në punë?
                        <span class="required">*</span>
                    </label>
                    <div class="linear-scale" id="scale-q9">
                        <label class="scale-option" onclick="selectScale('q9', 1)">
                            <input type="radio" name="q9" value="1" style="display:none" required>
                            <div class="scale-circle">1</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q9', 2)">
                            <input type="radio" name="q9" value="2" style="display:none" required>
                            <div class="scale-circle">2</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q9', 3)">
                            <input type="radio" name="q9" value="3" style="display:none" required>
                            <div class="scale-circle">3</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q9', 4)">
                            <input type="radio" name="q9" value="4" style="display:none" required>
                            <div class="scale-circle">4</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q9', 5)">
                            <input type="radio" name="q9" value="5" style="display:none" required>
                            <div class="scale-circle">5</div>
                        </label>
                    </div>
                    <div class="scale-endpoints">
                        <span>Aspak i stresuar</span>
                        <span>Jashtëzakonisht i stresuar</span>
                    </div>
                    <div class="error-message">Ju lutem zgjidhni një vlerë</div>
                </div>

                <div class="buttons">
                    <button class="btn btn-secondary" onclick="prevSection()">← Mbrapa</button>
                    <button class="btn btn-primary" onclick="nextSection()">Vazhdo →</button>
                </div>
            </div>

            <!-- SEKSIONI 3: JETA PRIVATE -->
            <div class="section" data-section="3">
                <h2 class="section-title">Seksioni 3: Jeta Private</h2>

                <div class="question">
                    <label class="question-label">
                        <span class="question-number">10.</span>
                        Sa orë në ditë i kushtoni aktiviteteve personale/familjes? (jashtë punës dhe gjumit)
                        <span class="required">*</span>
                    </label>
                    <div class="radio-group">
                        <label class="radio-option">
                            <input type="radio" name="q10" value="Më pak se 2 orë" required>
                            <span>Më pak se 2 orë</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q10" value="2-3 orë" required>
                            <span>2-3 orë</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q10" value="4-5 orë" required>
                            <span>4-5 orë</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q10" value="6-7 orë" required>
                            <span>6-7 orë</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q10" value="Mbi 7 orë" required>
                            <span>Mbi 7 orë</span>
                        </label>
                    </div>
                    <div class="error-message">Ju lutem zgjidhni një opsion</div>
                </div>

                <div class="question">
                    <label class="question-label">
                        <span class="question-number">11.</span>
                        Sa shpesh gjeni kohë për hobi dhe interesa personale?
                        <span class="required">*</span>
                    </label>
                    <div class="radio-group">
                        <label class="radio-option">
                            <input type="radio" name="q11" value="Çdo ditë" required>
                            <span>Çdo ditë</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q11" value="3-4 herë në javë" required>
                            <span>3-4 herë në javë</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q11" value="1-2 herë në javë" required>
                            <span>1-2 herë në javë</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q11" value="Disa herë në muaj" required>
                            <span>Disa herë në muaj</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q11" value="Rrallë ose kurrë" required>
                            <span>Rrallë ose kurrë</span>
                        </label>
                    </div>
                    <div class="error-message">Ju lutem zgjidhni një opsion</div>
                </div>

                <div class="question">
                    <label class="question-label">
                        <span class="question-number">12.</span>
                        Cilësia e kohës me familjen/miqtë
                        <span class="required">*</span>
                    </label>
                    <div class="linear-scale" id="scale-q12">
                        <label class="scale-option" onclick="selectScale('q12', 1)">
                            <input type="radio" name="q12" value="1" style="display:none" required>
                            <div class="scale-circle">1</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q12', 2)">
                            <input type="radio" name="q12" value="2" style="display:none" required>
                            <div class="scale-circle">2</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q12', 3)">
                            <input type="radio" name="q12" value="3" style="display:none" required>
                            <div class="scale-circle">3</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q12', 4)">
                            <input type="radio" name="q12" value="4" style="display:none" required>
                            <div class="scale-circle">4</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q12', 5)">
                            <input type="radio" name="q12" value="5" style="display:none" required>
                            <div class="scale-circle">5</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q12', 6)">
                            <input type="radio" name="q12" value="6" style="display:none" required>
                            <div class="scale-circle">6</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q12', 7)">
                            <input type="radio" name="q12" value="7" style="display:none" required>
                            <div class="scale-circle">7</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q12', 8)">
                            <input type="radio" name="q12" value="8" style="display:none" required>
                            <div class="scale-circle">8</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q12', 9)">
                            <input type="radio" name="q12" value="9" style="display:none" required>
                            <div class="scale-circle">9</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q12', 10)">
                            <input type="radio" name="q12" value="10" style="display:none" required>
                            <div class="scale-circle">10</div>
                        </label>
                    </div>
                    <div class="scale-endpoints">
                        <span>Shumë e dobët</span>
                        <span>E shkëlqyer</span>
                    </div>
                    <div class="error-message">Ju lutem zgjidhni një vlerë</div>
                </div>

                <div class="question">
                    <label class="question-label">
                        <span class="question-number">13.</span>
                        Sa orë gjumë merrni mesatarisht në natë?
                        <span class="required">*</span>
                    </label>
                    <div class="radio-group">
                        <label class="radio-option">
                            <input type="radio" name="q13" value="Më pak se 5 orë" required>
                            <span>Më pak se 5 orë</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q13" value="5-6 orë" required>
                            <span>5-6 orë</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q13" value="7-8 orë" required>
                            <span>7-8 orë</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q13" value="Mbi 8 orë" required>
                            <span>Mbi 8 orë</span>
                        </label>
                    </div>
                    <div class="error-message">Ju lutem zgjidhni një opsion</div>
                </div>

                <div class="buttons">
                    <button class="btn btn-secondary" onclick="prevSection()">← Mbrapa</button>
                    <button class="btn btn-primary" onclick="nextSection()">Vazhdo →</button>
                </div>
            </div>

            <!-- SEKSIONI 4: BILANCI DHE MIRËQENIA -->
            <div class="section" data-section="4">
                <h2 class="section-title">Seksioni 4: Bilanci dhe Mirëqenia</h2>

                <div class="question">
                    <label class="question-label">
                        <span class="question-number">14.</span>
                        Si do ta vlerësonit bilancin tuaj aktual punë-jetë?
                        <span class="required">*</span>
                    </label>
                    <div class="linear-scale" id="scale-q14">
                        <label class="scale-option" onclick="selectScale('q14', 1)">
                            <input type="radio" name="q14" value="1" style="display:none" required>
                            <div class="scale-circle">1</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q14', 2)">
                            <input type="radio" name="q14" value="2" style="display:none" required>
                            <div class="scale-circle">2</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q14', 3)">
                            <input type="radio" name="q14" value="3" style="display:none" required>
                            <div class="scale-circle">3</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q14', 4)">
                            <input type="radio" name="q14" value="4" style="display:none" required>
                            <div class="scale-circle">4</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q14', 5)">
                            <input type="radio" name="q14" value="5" style="display:none" required>
                            <div class="scale-circle">5</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q14', 6)">
                            <input type="radio" name="q14" value="6" style="display:none" required>
                            <div class="scale-circle">6</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q14', 7)">
                            <input type="radio" name="q14" value="7" style="display:none" required>
                            <div class="scale-circle">7</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q14', 8)">
                            <input type="radio" name="q14" value="8" style="display:none" required>
                            <div class="scale-circle">8</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q14', 9)">
                            <input type="radio" name="q14" value="9" style="display:none" required>
                            <div class="scale-circle">9</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q14', 10)">
                            <input type="radio" name="q14" value="10" style="display:none" required>
                            <div class="scale-circle">10</div>
                        </label>
                    </div>
                    <div class="scale-endpoints">
                        <span>Aspak i balancuar</span>
                        <span>Plotësisht i balancuar</span>
                    </div>
                    <div class="error-message">Ju lutem zgjidhni një vlerë</div>
                </div>

                <div class="question">
                    <label class="question-label">
                        <span class="question-number">15.</span>
                        Cili aspekt dominon më shumë në jetën tuaj?
                        <span class="required">*</span>
                    </label>
                    <div class="radio-group">
                        <label class="radio-option">
                            <input type="radio" name="q15" value="Jeta profesionale" required>
                            <span>Jeta profesionale (puna zë shumicën e kohës dhe energjisë)</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q15" value="Jeta private" required>
                            <span>Jeta private (familja dhe koha personale janë prioritet)</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q15" value="Të ekuilibruara" required>
                            <span>Të ekuilibruara (balancë e mirë ndërmjet të dyjave)</span>
                        </label>
                    </div>
                    <div class="error-message">Ju lutem zgjidhni një opsion</div>
                </div>

                <div class="question">
                    <label class="question-label">
                        <span class="question-number">16.</span>
                        Sa të kënaqur jeni me jetën tuaj në përgjithësi?
                        <span class="required">*</span>
                    </label>
                    <div class="linear-scale" id="scale-q16">
                        <label class="scale-option" onclick="selectScale('q16', 1)">
                            <input type="radio" name="q16" value="1" style="display:none" required>
                            <div class="scale-circle">1</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q16', 2)">
                            <input type="radio" name="q16" value="2" style="display:none" required>
                            <div class="scale-circle">2</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q16', 3)">
                            <input type="radio" name="q16" value="3" style="display:none" required>
                            <div class="scale-circle">3</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q16', 4)">
                            <input type="radio" name="q16" value="4" style="display:none" required>
                            <div class="scale-circle">4</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q16', 5)">
                            <input type="radio" name="q16" value="5" style="display:none" required>
                            <div class="scale-circle">5</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q16', 6)">
                            <input type="radio" name="q16" value="6" style="display:none" required>
                            <div class="scale-circle">6</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q16', 7)">
                            <input type="radio" name="q16" value="7" style="display:none" required>
                            <div class="scale-circle">7</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q16', 8)">
                            <input type="radio" name="q16" value="8" style="display:none" required>
                            <div class="scale-circle">8</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q16', 9)">
                            <input type="radio" name="q16" value="9" style="display:none" required>
                            <div class="scale-circle">9</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q16', 10)">
                            <input type="radio" name="q16" value="10" style="display:none" required>
                            <div class="scale-circle">10</div>
                        </label>
                    </div>
                    <div class="scale-endpoints">
                        <span>Aspak i kënaqur</span>
                        <span>Plotësisht i kënaqur</span>
                    </div>
                    <div class="error-message">Ju lutem zgjidhni një vlerë</div>
                </div>

                <div class="question">
                    <label class="question-label">
                        <span class="question-number">17.</span>
                        Çfarë sfidash hasni në arritjen e balancës? (Zgjidhni deri në 3)
                    </label>
                    <div class="checkbox-group" id="q17-group">
                        <label class="checkbox-option">
                            <input type="checkbox" name="q17" value="Orë të gjata pune">
                            <span>Orë të gjata pune</span>
                        </label>
                        <label class="checkbox-option">
                            <input type="checkbox" name="q17" value="Kërkesa të larta nga punëdhënësi">
                            <span>Kërkesa të larta nga punëdhënësi</span>
                        </label>
                        <label class="checkbox-option">
                            <input type="checkbox" name="q17" value="Përgjegjësi familjare">
                            <span>Përgjegjësi familjare (fëmijë, prindër të moshuar)</span>
                        </label>
                        <label class="checkbox-option">
                            <input type="checkbox" name="q17" value="Vështirësi financiare">
                            <span>Vështirësi financiare</span>
                        </label>
                        <label class="checkbox-option">
                            <input type="checkbox" name="q17" value="Mungesë mbështetjeje">
                            <span>Mungesë mbështetjeje nga partneri/familja</span>
                        </label>
                        <label class="checkbox-option">
                            <input type="checkbox" name="q17" value="Teknologjia">
                            <span>Teknologjia (email, telefon konstant)</span>
                        </label>
                        <label class="checkbox-option">
                            <input type="checkbox" name="q17" value="Presion për sukses">
                            <span>Presion për të qenë i suksesshëm</span>
                        </label>
                        <label class="checkbox-option">
                            <input type="checkbox" name="q17" value="Mungesë kohë për vete">
                            <span>Mungesë kohë për vete</span>
                        </label>
                    </div>
                    <div class="error-message">Mund të zgjidhni maksimumi 3 opsione</div>
                </div>

                <div class="question">
                    <label class="question-label">
                        <span class="question-number">18.</span>
                        Sa të rëndësishme janë këto aspekte për ju?
                        <span class="required">*</span>
                    </label>
                    <div class="grid-question">
                        <table class="grid-table">
                            <thead>
                                <tr>
                                    <th>Aspekti</th>
                                    <th>1<br><small>Jo rënd.</small></th>
                                    <th>2<br><small>Pak rënd.</small></th>
                                    <th>3<br><small>Mes. rënd.</small></th>
                                    <th>4<br><small>Shumë rënd.</small></th>
                                    <th>5<br><small>Jashtëz.</small></th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td>Karriera dhe suksesi profesional</td>
                                    <td><input type="radio" name="q18_1" value="1"></td>
                                    <td><input type="radio" name="q18_1" value="2"></td>
                                    <td><input type="radio" name="q18_1" value="3"></td>
                                    <td><input type="radio" name="q18_1" value="4"></td>
                                    <td><input type="radio" name="q18_1" value="5"></td>
                                </tr>
                                <tr>
                                    <td>Koha me familjen</td>
                                    <td><input type="radio" name="q18_2" value="1"></td>
                                    <td><input type="radio" name="q18_2" value="2"></td>
                                    <td><input type="radio" name="q18_2" value="3"></td>
                                    <td><input type="radio" name="q18_2" value="4"></td>
                                    <td><input type="radio" name="q18_2" value="5"></td>
                                </tr>
                                <tr>
                                    <td>Shëndeti fizik dhe mental</td>
                                    <td><input type="radio" name="q18_3" value="1"></td>
                                    <td><input type="radio" name="q18_3" value="2"></td>
                                    <td><input type="radio" name="q18_3" value="3"></td>
                                    <td><input type="radio" name="q18_3" value="4"></td>
                                    <td><input type="radio" name="q18_3" value="5"></td>
                                </tr>
                                <tr>
                                    <td>Hobi dhe interesa personale</td>
                                    <td><input type="radio" name="q18_4" value="1"></td>
                                    <td><input type="radio" name="q18_4" value="2"></td>
                                    <td><input type="radio" name="q18_4" value="3"></td>
                                    <td><input type="radio" name="q18_4" value="4"></td>
                                    <td><input type="radio" name="q18_4" value="5"></td>
                                </tr>
                                <tr>
                                    <td>Siguria financiare</td>
                                    <td><input type="radio" name="q18_5" value="1"></td>
                                    <td><input type="radio" name="q18_5" value="2"></td>
                                    <td><input type="radio" name="q18_5" value="3"></td>
                                    <td><input type="radio" name="q18_5" value="4"></td>
                                    <td><input type="radio" name="q18_5" value="5"></td>
                                </tr>
                                <tr>
                                    <td>Zhvillimi personal</td>
                                    <td><input type="radio" name="q18_6" value="1"></td>
                                    <td><input type="radio" name="q18_6" value="2"></td>
                                    <td><input type="radio" name="q18_6" value="3"></td>
                                    <td><input type="radio" name="q18_6" value="4"></td>
                                    <td><input type="radio" name="q18_6" value="5"></td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                    <div class="error-message">Ju lutem plotësoni të gjitha rreshtat</div>
                </div>

                <div class="buttons">
                    <button class="btn btn-secondary" onclick="prevSection()">← Mbrapa</button>
                    <button class="btn btn-primary" onclick="nextSection()">Vazhdo →</button>
                </div>
            </div>

            <!-- SEKSIONI 5: STRATEGJI DHE ZGJIDHJE -->
            <div class="section" data-section="5">
                <h2 class="section-title">Seksioni 5: Strategji dhe Zgjidhje</h2>

                <div class="question">
                    <label class="question-label">
                        <span class="question-number">19.</span>
                        Cilat nga këto strategji i aplikoni për të ruajtur balancën?
                    </label>
                    <div class="checkbox-group">
                        <label class="checkbox-option">
                            <input type="checkbox" name="q19" value="Kufij të qartë">
                            <span>Vendos kufij të qartë (p.sh. nuk shoh email pas orarit)</span>
                        </label>
                        <label class="checkbox-option">
                            <input type="checkbox" name="q19" value="Pushime të rregullta">
                            <span>Pushime dhe ditë lirie të rregullta</span>
                        </label>
                        <label class="checkbox-option">
                            <input type="checkbox" name="q19" value="Delegim">
                            <span>Delegoj përgjegjësi në punë</span>
                        </label>
                        <label class="checkbox-option">
                            <input type="checkbox" name="q19" value="Praktikime relaksuese">
                            <span>Praktikime relaksuese (meditim, yoga, sport)</span>
                        </label>
                        <label class="checkbox-option">
                            <input type="checkbox" name="q19" value="Kohë për familjen">
                            <span>Kohë e caktuar për familjen</span>
                        </label>
                        <label class="checkbox-option">
                            <input type="checkbox" name="q19" value="Fleksibilitet">
                            <span>Work from home / Fleksibilitet në orar</span>
                        </label>
                        <label class="checkbox-option">
                            <input type="checkbox" name="q19" value="Asnjë strategji">
                            <span>Asnjë strategji specifike</span>
                        </label>
                    </div>
                </div>

                <div class="question">
                    <label class="question-label">
                        <span class="question-number">20.</span>
                        Nëse do të mund të ndryshonit një gjë për të përmirësuar balancën tuaj punë-jetë, çfarë do të ishte?
                    </label>
                    <textarea name="q20" placeholder="Shkruani përgjigjen tuaj këtu..."></textarea>
                </div>

                <div class="question">
                    <label class="question-label">
                        <span class="question-number">21.</span>
                        A ndiheni që gjenerata juaj (Gjenerata X) ka sfida unike në lidhje me balancën punë-jetë?
                        <span class="required">*</span>
                    </label>
                    <div class="radio-group">
                        <label class="radio-option">
                            <input type="radio" name="q21" value="Po" required>
                            <span>Po</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q21" value="Jo" required>
                            <span>Jo</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="q21" value="Nuk jam i sigurt" required>
                            <span>Nuk jam i sigurt</span>
                        </label>
                    </div>
                    <div class="error-message">Ju lutem zgjidhni një opsion</div>
                </div>

                <div class="question">
                    <label class="question-label">
                        <span class="question-number">22.</span>
                        Nëse përgjigjët PO, cilat janë këto sfida specifike të Gjeneratës X?
                    </label>
                    <p style="font-size: 14px; color: #666; margin-bottom: 10px;">
                        Shembuj: Kujdesi për prindër të moshuar, mbështetja financiare e fëmijëve të rritur, 
                        presioni ekonomik, ndryshime teknologjike në punë, etj.
                    </p>
                    <textarea name="q22" placeholder="Shkruani përgjigjen tuaj këtu..."></textarea>
                </div>

                <div class="question">
                    <label class="question-label">
                        <span class="question-number">23.</span>
                        Sa ka gjasa ta rekomandoni qasjen tuaj aktuale ndaj balancës punë-jetë te dikush tjetër?
                        <span class="required">*</span>
                    </label>
                    <div class="linear-scale" id="scale-q23">
                        <label class="scale-option" onclick="selectScale('q23', 0)">
                            <input type="radio" name="q23" value="0" style="display:none" required>
                            <div class="scale-circle">0</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q23', 1)">
                            <input type="radio" name="q23" value="1" style="display:none" required>
                            <div class="scale-circle">1</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q23', 2)">
                            <input type="radio" name="q23" value="2" style="display:none" required>
                            <div class="scale-circle">2</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q23', 3)">
                            <input type="radio" name="q23" value="3" style="display:none" required>
                            <div class="scale-circle">3</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q23', 4)">
                            <input type="radio" name="q23" value="4" style="display:none" required>
                            <div class="scale-circle">4</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q23', 5)">
                            <input type="radio" name="q23" value="5" style="display:none" required>
                            <div class="scale-circle">5</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q23', 6)">
                            <input type="radio" name="q23" value="6" style="display:none" required>
                            <div class="scale-circle">6</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q23', 7)">
                            <input type="radio" name="q23" value="7" style="display:none" required>
                            <div class="scale-circle">7</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q23', 8)">
                            <input type="radio" name="q23" value="8" style="display:none" required>
                            <div class="scale-circle">8</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q23', 9)">
                            <input type="radio" name="q23" value="9" style="display:none" required>
                            <div class="scale-circle">9</div>
                        </label>
                        <label class="scale-option" onclick="selectScale('q23', 10)">
                            <input type="radio" name="q23" value="10" style="display:none" required>
                            <div class="scale-circle">10</div>
                        </label>
                    </div>
                    <div class="scale-endpoints">
                        <span>Aspak ka gjasa</span>
                        <span>Shumë ka gjasa</span>
                    </div>
                    <div class="error-message">Ju lutem zgjidhni një vlerë</div>
                </div>

                <div class="question">
                    <label class="question-label">
                        <span class="question-number">24.</span>
                        Komente, mendime ose përvojë shtesë që doni të ndani:
                    </label>
                    <textarea name="q24" placeholder="Shkruani përgjigjen tuaj këtu..."></textarea>
                </div>

                <div class="buttons">
                    <button class="btn btn-secondary" onclick="prevSection()">← Mbrapa</button>
                    <button class="btn btn-primary" onclick="submitSurvey()">Dërgo Pyetësorin ✓</button>
                </div>
            </div>

            <!-- REZULTATET -->
            <div class="results" id="results">
                <div class="results-icon">✅</div>
                <h2>Faleminderit për kohën tuaj!</h2>
                <p>
                    Përgjigjet tuaja do të ndihmojnë në kuptimin më të mirë të sfidave dhe mundësive 
                    për arritjen e një bilanci të shëndetshëm ndërmjet jetës profesionale dhe asaj private 
                    tek Gjenerata X.
                </p>

                <div class="summary-card" id="summaryCard" style="display: none;">
                    <h3>📊 Përmbledhje e Përgjigjeve Tuaja</h3>
                    <div id="summaryContent"></div>
                </div>

                <button class="download-btn" onclick="downloadResults()">📥 Shkarko Përgjigjet (JSON)</button>
                <button class="download-btn" onclick="downloadCSV()" style="background: #17a2b8;">📊 Shkarko si CSV</button>
                <button class="download-btn" onclick="location.reload()" style="background: #6c757d;">🔄 Fillo Përsëri</button>
            </div>
        </div>
    </div>

    <script>
        let currentSection = 1;
        const totalSections = 5;
        const surveyData = {};

        // Inicializimi
        document.addEventListener('DOMContentLoaded', function() {
            updateProgress();
            setupEventListeners();
        });

        function showChildrenDetails() {
            document.getElementById('childrenDetails').style.display = 'block';
        }

        function hideChildrenDetails() {
            document.getElementById('childrenDetails').style.display = 'none';
            // Clear selections when hiding
            document.querySelectorAll('#childrenDetails input').forEach(input => {
                input.checked = false;
                if (input.type === 'checkbox') {
                    input.closest('.checkbox-option').classList.remove('selected');
                } else if (input.type === 'radio') {
                    input.closest('.radio-option').classList.remove('selected');
                }
            });
        }

        function setupEventListeners() {
            // Radio dhe checkbox styling
            document.querySelectorAll('.radio-option').forEach(option => {
                option.addEventListener('click', function() {
                    const radio = this.querySelector('input[type="radio"]');
                    if (radio) {
                        radio.checked = true;
                        // Hiq selected nga të gjitha
                        this.parentElement.querySelectorAll('.radio-option').forEach(opt => {
                            opt.classList.remove('selected');
                        });
                        // Shto selected te kjo
                        this.classList.add('selected');
                    }
                });
            });

            document.querySelectorAll('.checkbox-option').forEach(option => {
                option.addEventListener('click', function() {
                    const checkbox = this.querySelector('input[type="checkbox"]');
                    if (checkbox) {
                        checkbox.checked = !checkbox.checked;
                        this.classList.toggle('selected');
                        
                        // Kontrollo limitin për q17
                        if (checkbox.name === 'q17') {
                            checkCheckboxLimit('q17', 3);
                        }
                    }
                });
            });

            // Add event listeners to grid table radios to clear highlighting
            document.querySelectorAll('.grid-table input[type="radio"]').forEach(radio => {
                radio.addEventListener('change', function() {
                    const row = this.closest('tr');
                    if (row) {
                        row.style.backgroundColor = '';
                    }
                });
            });
        }

        function checkCheckboxLimit(name, max) {
            const checkboxes = document.querySelectorAll(`input[name="${name}"]:checked`);
            const allCheckboxes = document.querySelectorAll(`input[name="${name}"]`);
            
            if (checkboxes.length > max) {
                allCheckboxes.forEach(cb => {
                    if (!cb.checked) {
                        cb.disabled = true;
                        cb.parentElement.style.opacity = '0.5';
                    }
                });
            } else {
                allCheckboxes.forEach(cb => {
                    cb.disabled = false;
                    cb.parentElement.style.opacity = '1';
                });
            }
        }

        function selectScale(questionName, value) {
            const radio = document.querySelector(`input[name="${questionName}"][value="${value}"]`);
            if (radio) {
                radio.checked = true;
            }
        }

        function updateProgress() {
            const progress = (currentSection / totalSections) * 100;
            document.getElementById('progressFill').style.width = progress + '%';
        }

        function validateSection() {
            const currentSectionElement = document.querySelector(`.section[data-section="${currentSection}"]`);
            let isValid = true;

            // Reset error messages
            currentSectionElement.querySelectorAll('.error-message').forEach(msg => {
                msg.classList.remove('show');
            });

            // Validate radio buttons (only visible required ones)
            const radioGroups = {};
            currentSectionElement.querySelectorAll('input[type="radio"][required]').forEach(input => {
                // Skip if parent is hidden
                const parent = input.closest('.question, #childrenDetails');
                if (parent && parent.style.display === 'none') {
                    return;
                }
                
                if (!radioGroups[input.name]) {
                    radioGroups[input.name] = false;
                }
                if (input.checked) {
                    radioGroups[input.name] = true;
                }
            });

            for (let name in radioGroups) {
                if (!radioGroups[name]) {
                    isValid = false;
                    const question = currentSectionElement.querySelector(`input[name="${name}"]`).closest('.question');
                    if (question) {
                        const errorMsg = question.querySelector('.error-message');
                        if (errorMsg) {
                            errorMsg.classList.add('show');
                        }
                    }
                }
            }

            // Special validation for question 4 - check if main question is answered first
            if (currentSection === 1) {
                const q4Value = document.querySelector('input[name="q4"]:checked');
                if (!q4Value) {
                    isValid = false;
                    const question = currentSectionElement.querySelector('input[name="q4"]').closest('.question');
                    if (question) {
                        const errorMsg = question.querySelector('.error-message');
                        if (errorMsg) {
                            errorMsg.classList.add('show');
                        }
                    }
                } else if (q4Value.value === 'Po') {
                    // If "Po" is selected, validate children details
                    const childrenDetailsVisible = document.getElementById('childrenDetails').style.display !== 'none';
                    if (childrenDetailsVisible) {
                        // Check if number of children is selected
                        const q4Number = document.querySelector('input[name="q4_number"]:checked');
                        if (!q4Number) {
                            isValid = false;
                            alert('Ju lutem zgjidhni sa fëmijë keni.');
                        }
                        // Check if at least one age group is selected
                        const q4Ages = document.querySelectorAll('input[name="q4_ages"]:checked');
                        if (q4Ages.length === 0) {
                            isValid = false;
                            alert('Ju lutem zgjidhni të paktën një grup moshe për fëmijët tuaj.');
                        }
                    }
                }
            }

            // Validate grid questions (q18)
            if (currentSection === 4) {
                // Remove previous highlights
                document.querySelectorAll('.grid-table tr').forEach(tr => {
                    tr.style.backgroundColor = '';
                });
                
                let missingRows = [];
                for (let i = 1; i <= 6; i++) {
                    const gridRow = document.querySelector(`input[name="q18_${i}"]:checked`);
                    if (!gridRow) {
                        missingRows.push(i);
                        // Highlight the incomplete row
                        const firstRadio = document.querySelector(`input[name="q18_${i}"]`);
                        if (firstRadio) {
                            const row = firstRadio.closest('tr');
                            if (row) {
                                row.style.backgroundColor = '#ffebee';
                                row.style.transition = 'background-color 0.3s ease';
                            }
                        }
                    }
                }
                
                if (missingRows.length > 0) {
                    isValid = false;
                    const gridQuestion = currentSectionElement.querySelector('.grid-question').closest('.question');
                    const errorMsg = gridQuestion.querySelector('.error-message');
                    if (errorMsg) {
                        errorMsg.classList.add('show');
                        errorMsg.textContent = `Ju lutem plotësoni të gjitha rreshtat e tabelës (${missingRows.length} rresht pa përgjigje)`;
                    }
                    // Scroll to the grid table
                    gridQuestion.scrollIntoView({ behavior: 'smooth', block: 'center' });
                }
            }

            return isValid;
        }

        function nextSection() {
            if (!validateSection()) {
                window.scrollTo({ top: 0, behavior: 'smooth' });
                return;
            }

            saveSectionData();

            if (currentSection < totalSections) {
                document.querySelector(`.section[data-section="${currentSection}"]`).classList.remove('active');
                currentSection++;
                document.querySelector(`.section[data-section="${currentSection}"]`).classList.add('active');
                updateProgress();
                window.scrollTo({ top: 0, behavior: 'smooth' });
            }
        }

        function prevSection() {
            if (currentSection > 1) {
                document.querySelector(`.section[data-section="${currentSection}"]`).classList.remove('active');
                currentSection--;
                document.querySelector(`.section[data-section="${currentSection}"]`).classList.add('active');
                updateProgress();
                window.scrollTo({ top: 0, behavior: 'smooth' });
            }
        }

        function saveSectionData() {
            const currentSectionElement = document.querySelector(`.section[data-section="${currentSection}"]`);
            
            // Save all inputs
            currentSectionElement.querySelectorAll('input, textarea').forEach(input => {
                if (input.type === 'radio' || input.type === 'checkbox') {
                    if (input.checked) {
                        if (input.type === 'checkbox') {
                            if (!surveyData[input.name]) {
                                surveyData[input.name] = [];
                            }
                            if (!surveyData[input.name].includes(input.value)) {
                                surveyData[input.name].push(input.value);
                            }
                        } else {
                            surveyData[input.name] = input.value;
                        }
                    }
                } else if (input.type === 'text' || input.tagName === 'TEXTAREA') {
                    if (input.value.trim()) {
                        surveyData[input.name] = input.value.trim();
                    }
                }
            });

            // Special handling for question 4 - combine children data
            if (surveyData['q4'] === 'Po') {
                surveyData['q4_combined'] = {
                    has_children: 'Po',
                    number: surveyData['q4_number'] || 'Nuk është specifikuar',
                    ages: surveyData['q4_ages'] || []
                };
            }
        }

        function submitSurvey() {
            if (!validateSection()) {
                window.scrollTo({ top: 0, behavior: 'smooth' });
                return;
            }

            saveSectionData();

            // Ruaj timestamp
            surveyData.timestamp = new Date().toISOString();
            surveyData.completedAt = new Date().toLocaleString('sq-AL');

            // Shfaq rezultatet
            document.querySelector(`.section[data-section="${currentSection}"]`).classList.remove('active');
            document.getElementById('results').classList.add('active');
            
            // Krijo përmbledhjen
            createSummary();
            
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        function createSummary() {
            const summaryCard = document.getElementById('summaryCard');
            const summaryContent = document.getElementById('summaryContent');
            
            let html = '';
            
            // Pyetjet kryesore për përmbledhje
            const keyQuestions = {
                'q8': 'Kënaqësia në punë',
                'q9': 'Stresi në punë',
                'q12': 'Cilësia e kohës familjare',
                'q14': 'Bilanci punë-jetë',
                'q16': 'Kënaqësia e përgjithshme'
            };

            for (let key in keyQuestions) {
                if (surveyData[key]) {
                    html += `<div class="summary-item">
                        <span class="summary-label">${keyQuestions[key]}:</span>
                        <span class="summary-value">${surveyData[key]}/10</span>
                    </div>`;
                }
            }

            if (surveyData['q15']) {
                html += `<div class="summary-item">
                    <span class="summary-label">Dominimi:</span>
                    <span class="summary-value">${surveyData['q15']}</span>
                </div>`;
            }

            summaryContent.innerHTML = html;
            summaryCard.style.display = 'block';
        }

        function downloadResults() {
            const dataStr = JSON.stringify(surveyData, null, 2);
            const dataBlob = new Blob([dataStr], { type: 'application/json' });
            const url = URL.createObjectURL(dataBlob);
            const link = document.createElement('a');
            link.href = url;
            link.download = `pyetesor_bilanci_${new Date().getTime()}.json`;
            link.click();
        }

        function downloadCSV() {
            let csv = 'Pyetja,Pergjigja\n';
            
            for (let key in surveyData) {
                let value = surveyData[key];
                if (Array.isArray(value)) {
                    value = value.join('; ');
                }
                // Escape commas and quotes
                value = String(value).replace(/"/g, '""');
                if (value.includes(',') || value.includes('\n')) {
                    value = `"${value}"`;
                }
                csv += `${key},"${value}"\n`;
            }

            const blob = new Blob([csv], { type: 'text/csv;charset=utf-8;' });
            const url = URL.createObjectURL(blob);
            const link = document.createElement('a');
            link.href = url;
            link.download = `pyetesor_bilanci_${new Date().getTime()}.csv`;
            link.click();
        }
    </script>
</body>
</html>
