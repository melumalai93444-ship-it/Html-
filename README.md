<<!DOCTYPEDOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title> Elumalai Mixer dj</title>
    <style>
        :root {
            --bg-color: #121212;
            --panel-bg: #1e1e1e;
            --accent: #00ffcc;
            --accent-glow: rgba(0, 255, 204, 0.3);
            --text-color: #e0e0e0;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            margin: 0;
            padding: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
            min-height: 100vh;
        }

        h1 {
            margin-bottom: 5px;
            letter-spacing: 2px;
            color: #fff;
            text-shadow: 0 0 10px var(--accent-glow);
        }

        .subtitle {
            font-size: 0.9rem;
            color: #888;
            margin-bottom: 25px;
        }

        .mixer-container {
            display: grid;
            grid-template-columns: 2fr 1fr;
            gap: 20px;
            background: var(--panel-bg);
            padding: 25px;
            border-radius: 12px;
            box-shadow: 0 8px 24px rgba(0,0,0,0.6);
            border: 1px solid #333;
            max-width: 850px;
            width: 100%;
        }

        @media (max-width: 768px) {
            .mixer-container {
                grid-template-columns: 1fr;
            }
        }

        .channel-strip, .master-strip {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .channel-strip {
            border-right: 1px solid #333;
            padding-right: 20px;
        }

        @media (max-width: 768px) {
            .channel-strip {
                border-right: none;
                padding-right: 0;
                border-bottom: 1px solid #333;
                padding-bottom: 20px;
            }
        }

        h2 {
            font-size: 1.1rem;
            margin: 0 0 10px 0;
            color: var(--accent);
            border-bottom: 2px solid #333;
            padding-bottom: 5px;
        }

        .control-group {
            display: flex;
            flex-direction: column;
            gap: 5px;
            background: #252525;
            padding: 10px;
            border-radius: 8px;
        }

        .control-row {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 10px;
        }

        .fx-pad-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 8px;
        }

        label {
            font-size: 0.75rem;
            font-weight: bold;
            color: #aaa;
            text-transform: uppercase;
            display: flex;
            justify-content: space-between;
        }

        label span {
            color: #fff;
        }

        input[type="range"] {
            -webkit-appearance: none;
            width: 100%;
            height: 6px;
            background: #444;
            border-radius: 3px;
            outline: none;
        }

        input[type="range"]::-webkit-slider-thumb {
            -webkit-appearance: none;
            width: 14px;
            height: 14px;
            border-radius: 50%;
            background: var(--accent);
            cursor: pointer;
            box-shadow: 0 0 5px var(--accent);
        }

        .btn-container {
            display: flex;
            gap: 10px;
        }

        button {
            padding: 10px;
            font-weight: bold;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            text-transform: uppercase;
            font-size: 0.75rem;
            transition: background 0.2s, box-shadow 0.2s;
        }

        #playBtn {
            background: #00c853;
            color: #fff;
            flex: 1;
        }
        #playBtn:hover { background: #00e676; box-shadow: 0 0 10px rgba(0,200,83,0.4); }
        #playBtn.active { background: #d50000; box-shadow: 0 0 10px rgba(213,0,0,0.4); }

        .fx-pad {
            background: #333;
            color: var(--accent);
            border: 1px solid #444;
            padding: 12px;
            text-align: center;
            border-radius: 6px;
            cursor: pointer;
            font-weight: bold;
            font-size: 0.8rem;
            transition: 0.1s;
        }
        .fx-pad:hover { background: #3d3d3d; border-color: var(--accent); box-shadow: 0 0 8px var(--accent-glow); }
        .fx-pad:active { background: var(--accent); color: #121212; }

        .file-input-wrapper {
            position: relative;
            overflow: hidden;
            display: inline-block;
            flex: 1;
        }

        .file-input-wrapper input[type=file] {
            font-size: 100px;
            position: absolute;
            left: 0;
            top: 0;
            opacity: 0;
            cursor: pointer;
        }

        .btn-file {
            display: block;
            background: #333;
            color: #fff;
            padding: 10px;
            text-align: center;
            border-radius: 6px;
            font-size: 0.75rem;
            text-transform: uppercase;
            font-weight: bold;
            cursor: pointer;
        }
        .btn-file:hover { background: #444; }

        select {
            background: #333;
            color: #fff;
            border: none;
            padding: 8px;
            border-radius: 6px;
            outline: none;
            font-size: 0.85rem;
        }
    </style>
</head>
<body>

    <h1>ELUMALAI DJ FX MIXER</h1>
    <div class="subtitle">Pure Music & Electronic Sound Effects Processor</div>

    <div class="mixer-container">
        <!-- Deck / Channel 1 -->
        <div class="channel-strip">
            <h2>Music Deck & Sound Effects</h2>
            
            <div class="btn-container">
                <button id="playBtn">Play Music Loop</button>
                <div class="file-input-wrapper">
                    <span class="btn-file">Upload Music</span>
                    <input type="file" id="audiofile" accept="audio/*">
                </div>
            </div>

            <!-- Instrumental FX Trigger Pads -->
            <div class="control-group">
                <label>Music Sound Effects (No Voice)</label>
                <div class="fx-pad-grid">
                    <button class="fx-pad" id="fxRiser">Riser Sweep</button>
                    <button class="fx-pad" id="fxZap">Laser Zap</button>
                    <button class="fx-pad" id="fxDrop">Sub Bass Drop</button>
                    <button class="fx-pad" id="fxNoise">Noise Filter Swish</button>
                </div>
            </div>

            <!-- Gain -->
            <div class="control-group">
                <label>Gain / Trim <span id="gainVal">1.0</span></label>
                <input type="range" id="gain" min="0" max="2" step="0.05" value="1">
            </div>

            <!-- EQ (Bass, Mid, Treble) -->
            <div class="control-group">
                <label>Equalizer</label>
                <div class="control-row">
                    <div>
                        <label>Bass <span id="bassVal">0dB</span></label>
                        <input type="range" id="bass" min="-30" max="15" step="1" value="0">
                    </div>
                    <div>
                        <label>Mid <span id="midVal">0dB</span></label>
                        <input type="range" id="mid" min="-30" max="15" step="1" value="0">
                    </div>
                    <div>
                        <label>Treble <span id="trebleVal">0dB</span></label>
                        <input type="range" id="treble" min="-30" max="15" step="1" value="0">
                    </div>
                </div>
            </div>

            <!-- Filter -->
            <div class="control-group">
                <label>Filter Type</label>
                <select id="filterType">
                    <option value="lowpass">Low-Pass Filter</option>
                    <option value="highpass">High-Pass Filter</option>
                </select>
                <label>Filter Cutoff Freq <span id="filterFreqVal">20000 Hz</span></label>
                <input type="range" id="filterFreq" min="20" max="20000" step="10" value="20000">
            </div>

            <!-- Echo & Reverb -->
            <div class="control-group">
                <label>Audio Effects (FX)</label>
                <div class="control-row">
                    <div>
                        <label>Echo Wet <span id="echoVal">0%</span></label>
                        <input type="range" id="echo" min="0" max="1" step="0.05" value="0">
                    </div>
                    <div>
                        <label>Reverb Wet <span id="reverbVal">0%</span></label>
                        <input type="range" id="reverb" min="0" max="1" step="0.05" value="0">
                    </div>
                </div>
            </div>
        </div>

        <!-- Master Section -->
        <div class="master-strip">
            <h2>Master Output</h2>
            
            <div class="control-group" style="height: 100%; justify-content: center;">
                <label>Master Volume <span id="masterVal">80%</span></label>
                <input type="range" id="master" min="0" max="1" step="0.01" value="0.8" style="height: 150px; writing-mode: bt-lr; -webkit-appearance: slider-vertical; width: 100%; margin: 20px 0;">
            </div>
        </div>
    </div>

    <script>
        let audioCtx = null;
        let sourceNode = null;
        let isPlaying = false;
        let synthInterval = null;

        // Audio Nodes
        let gainNode, bassNode, midNode, trebleNode, filterNode;
        let echoNode, echoFeedback, echoWetNode;
        let convolverNode, reverbWetNode;
        let masterNode, fxBus;

        function initAudio() {
            if (audioCtx) return;
            audioCtx = new (window.AudioContext || window.webkitAudioContext)();

            // Create Master
            masterNode = audioCtx.createGain();
            masterNode.gain.value = 0.8;
            masterNode.masterBus = audioCtx.createGain();
            masterNode.connect(audioCtx.destination);

            // FX Bus for independent music sound effect triggers
            fxBus = audioCtx.createGain();
            fxBus.gain.value = 1.0;
            fxBus.connect(masterNode);

            // Create Reverb Convolver
            convolverNode = audioCtx.createConvolver();
            createImpulseResponse();

            reverbWetNode = audioCtx.createGain();
            reverbWetNode.gain.value = 0;
            convolverNode.connect(reverbWetNode);
            reverbWetNode.connect(masterNode);

            // Create Echo (Delay) Setup
            echoNode = audioCtx.createDelay();
            echoNode.delayTime.value = 0.35;
            echoFeedback = audioCtx.createGain();
            echoFeedback.gain.value = 0.4;
            echoWetNode = audioCtx.createGain();
            echoWetNode.gain.value = 0;

            echoNode.connect(echoFeedback);
            echoFeedback.connect(echoNode);
            echoNode.connect(echoWetNode);
            echoWetNode.connect(masterNode);

            // Create Channel Processing Chain
            gainNode = audioCtx.createGain();
            
            bassNode = audioCtx.createBiquadFilter();
            bassNode.type = 'lowshelf';
            bassNode.frequency.value = 250;

            midNode = audioCtx.createBiquadFilter();
            midNode.type = 'peaking';
            midNode.frequency.value = 1500;
            midNode.Q.value = 1;

            trebleNode = audioCtx.createBiquadFilter();
            trebleNode.type = 'highshelf';
            trebleNode.frequency.value = 4000;

            filterNode = audioCtx.createBiquadFilter();
            filterNode.type = 'lowpass';
            filterNode.frequency.value = 20000;

            // Chain connection
            gainNode.connect(bassNode);
            bassNode.connect(midNode);
            midNode.connect(trebleNode);
            trebleNode.connect(filterNode);

            filterNode.connect(masterNode);
            filterNode.connect(echoNode);
            filterNode.connect(convolverNode);
        }

        function createImpulseResponse() {
            let rate = audioCtx.sampleRate;
            let length = rate * 2.0;
            let impulse = audioCtx.createBuffer(2, length, rate);
            let left = impulse.getChannelData(0);
            let right = impulse.getChannelData(1);

            for (let i = 0; i < length; i++) {
                let decay = Math.exp(-i / (rate * 0.5));
                left[i] = (Math.random() * 2 - 1) * decay;
                right[i] = (Math.random() * 2 - 1) * decay;
            }
            convolverNode.buffer = impulse;
        }

        // Instrumental synth loop (Pure Music)
        function startSynthLoop() {
            if (synthInterval) clearInterval(synthInterval);
            let notes = [110, 146.83, 164.81, 220, 246.94, 293.66];
            let step = 0;

            synthInterval = setInterval(() => {
                if (!isPlaying || !audioCtx) return;
                let osc = audioCtx.createOscillator();
                let noteGain = audioCtx.createGain();

                osc.type = step % 4 === 0 ? 'sawtooth' : 'square';
                osc.frequency.value = notes[Math.floor(Math.random() * notes.length)];

                osc.connect(noteGain);
                noteGain.connect(gainNode);

                let now = audioCtx.currentTime;
                noteGain.gain.setValueAtTime(0.15, now);
                noteGain.gain.exponentialRampToValueAtTime(0.001, now + 0.3);

                osc.start(now);
                osc.stop(now + 0.35);
                step++;
            }, 250);
        }

        // --- Pure Instrumental Sound Effects (No Voice) ---
        function triggerRiserFX() {
            initAudio();
            let now = audioCtx.currentTime;
            let osc = audioCtx.createOscillator();
            let gain = audioCtx.createGain();
            
            osc.type = 'sawtooth';
            osc.frequency.setValueAtTime(100, now);
            osc.frequency.exponentialRampToValueAtTime(2000, now + 1.5);
            
            gain.gain.setValueAtTime(0.01, now);
            gain.gain.linearRampToValueAtTime(0.15, now + 1.4);
            gain.gain.linearRampToValueAtTime(0.001, now + 1.5);
            
            osc.connect(gain);
            gain.connect(fxBus);
            osc.start(now);
            osc.stop(now + 1.5);
        }

        function triggerZapFX() {
            initAudio();
            let now = audioCtx.currentTime;
            let osc = audioCtx.createOscillator();
            let gain = audioCtx.createGain();
            
            osc.type = 'sine';
            osc.frequency.setValueAtTime(800, now);
            osc.frequency.exponentialRampToValueAtTime(80, now + 0.25);
            
            gain.gain.setValueAtTime(0.2, now);
            gain.gain.exponentialRampToValueAtTime(0.001, now + 0.25);
            
            osc.connect(gain);
            gain.connect(fxBus);
            osc.start(now);
            osc.stop(now + 0.3);
        }

        function triggerDropFX() {
            initAudio();
            let now = audioCtx.currentTime;
            let osc = audioCtx.createOscillator();
            let gain = audioCtx.createGain();
            
            osc.type = 'triangle';
            osc.frequency.setValueAtTime(150, now);
            osc.frequency.exponentialRampToValueAtTime(30, now + 0.8);
            
            gain.gain.setValueAtTime(0.3, now);
            gain.gain.exponentialRampToValueAtTime(0.001, now + 0.8);
            
            osc.connect(gain);
            gain.connect(fxBus);
            osc.start(now);
            osc.stop(now + 0.85);
        }

        function triggerNoiseFX() {
            initAudio();
            let now = audioCtx.currentTime;
            let bufferSize = audioCtx.sampleRate * 0.6;
            let buffer = audioCtx.createBuffer(1, bufferSize, audioCtx.sampleRate);
            let data = buffer.getChannelData(0);
            for (let i = 0; i < bufferSize; i++) {
                data[i] = Math.random() * 2 - 1;
            }
            
            let noise = audioCtx.createBufferSource();
            noise.buffer = buffer;
            
            let filter = audioCtx.createBiquadFilter();
            filter.type = 'bandpass';
            filter.frequency.setValueAtTime(400, now);
            filter.frequency.exponentialRampToValueAtTime(4000, now + 0.5);
            filter.Q.value = 5;
            
            let gain = audioCtx.createGain();
            gain.gain.setValueAtTime(0.2, now);
            gain.gain.linearRampToValueAtTime(0.001, now + 0.6);
            
            noise.connect(filter);
            filter.connect(gain);
            gain.connect(fxBus);
            
            noise.start(now);
        }

        // Event Listeners
        document.getElementById('playBtn').addEventListener('click', async () => {
            initAudio();
            if (audioCtx.state === 'suspended') await audioCtx.resume();

            isPlaying = !isPlaying;
            const btn = document.getElementById('playBtn');
            if (isPlaying) {
                btn.textContent = "Stop Music Loop";
                btn.classList.add('active');
                startSynthLoop();
            } else {
                btn.textContent = "Play Music Loop";
                btn.classList.remove('active');
                if (synthInterval) clearInterval(synthInterval);
                if (sourceNode) { sourceNode.stop(); sourceNode.disconnect(); }
            }
        });

        document.getElementById('audiofile').addEventListener('change', async (e) => {
            initAudio();
            if (audioCtx.state === 'suspended') await audioCtx.resume();

            const file = e.target.files[0];
            if (!file) return;

            const reader = new FileReader();
            reader.readAsArrayBuffer(file);
            reader.onload = async function (ev) {
                const decodedData = await audioCtx.decodeAudioData(ev.target.result);
                
                if (sourceNode) { sourceNode.stop(); }
                if (synthInterval) clearInterval(synthInterval);
                isPlaying = true;
                document.getElementById('playBtn').textContent = "Stop Uploaded Music";
                document.getElementById('playBtn').classList.add('active');

                sourceNode = audioCtx.createBufferSource();
                sourceNode.buffer = decodedData;
                sourceNode.loop = true;
                sourceNode.connect(gainNode);
                sourceNode.start(0);
            };
        });

        // Effect Buttons Binding
        document.getElementById('fxRiser').addEventListener('click', triggerRiserFX);
        document.getElementById('fxZap').addEventListener('click', triggerZapFX);
        document.getElementById('fxDrop').addEventListener('click', triggerDropFX);
        document.getElementById('fxNoise').addEventListener('click', triggerNoiseFX);

        // Control Sliders Binding
        function bindControl(id, eventType, scaleText, updateFn) {
            const el = document.getElementById(id);
            el.addEventListener(eventType, (e) => {
                const val = parseFloat(e.target.value);
                document.getElementById(id + 'Val').textContent = scaleText(val);
                if (audioCtx) updateFn(val);
            });
        }

        bindControl('gain', 'input', v => v.toFixed(2), v => gainNode.gain.value = v);
        bindControl('bass', 'input', v => v + 'dB', v => bassNode.gain.value = v);
        bindControl('mid', 'input', v => v + 'dB', v => midNode.gain.value = v);
        bindControl('treble', 'input', v => v + 'dB', v => trebleNode.gain.value = v);
        bindControl('filterFreq', 'input', v => v + ' Hz', v => filterNode.frequency.value = v);
        bindControl('echo', 'input', v => Math.round(v * 100) + '%', v => echoWetNode.gain.value = v);
        bindControl('reverb', 'input', v => Math.round(v * 100) + '%', v => reverbWetNode.gain.value = v);
        bindControl('master', 'input', v => Math.round(v * 100) + '%', v => masterNode.gain.value = v);

        document.getElementById('filterType').addEventListener('change', (e) => {
            if (filterNode) filterNode.type = e.target.value;
        });
    </script>
</body>
</html>
