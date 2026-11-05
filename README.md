===============================================================================
                     CARNATIC PITCH & RAGA VISUALIZER
===============================================================================

A real-time, browser-based pitch tracking, gamaka visualization, and raga 
intonation practice suite for Carnatic vocalists and instrumentalists. Built as 
a zero-dependency, single-file web application using the Web Audio API and 
HTML5 Canvas.


===============================================================================
1. KEY FEATURES
===============================================================================

- Adhara Shadjam (Shruti) Selector:
  Full 12-semitone Kattai selection calibrated to G# (5.5 Kattai / 207.65 Hz) 
  with adjustable concert A4 tuning reference (430 - 450 Hz).

- Synthetic Tanpura Drone:
  Low-latency, multi-harmonic acoustic drone generator playing authentic 
  Pa - Sa - Sa - Sa open string overtones.

- Microtonal Gamaka Pitch Ribbon:
  Continuous, unquantized pitch contour plotted across Mandra, Madhya, and 
  Tara sthayis with dual-stage pre-filtering (70 Hz high-pass, 1100 Hz low-pass) 
  and segmented stroke drawing to prevent false vertical pitch plunges.

- Intelligent 3-Tier Note Classification:
  * Green (IN RAGA): Pitch aligns with the active raga scale.
  * Pink (NEAR RAGA (+/-1 Swara)): Vocalist is within +/-1 semitone of a 
    legitimate scale swara, preventing false-negative alerts during vocal 
    exploration and microtonal ornamentation.
  * Red (ANYA SWARA): Pitch falls outside the active scale boundaries.

- 30 ms Transition Hysteresis:
  Buffers discrete note declaration by 30 milliseconds to eliminate display 
  flicker during rapid gamaka transitions and glides, while keeping the 
  continuous pitch contour ribbon instant and unbuffered.

- Saraswati Veena Scale Synthesizer:
  Built-in acoustic Veena engine modeling attack transients, resonant kudam 
  filtering, and sympathetic upper-octave overtones. Automatically mutes 
  microphone input during Arohana/Avarohana playback to prevent acoustic feedback.

- Raga Library:
  Includes foundational Melakarta and asymmetric/vakra Janya ragas with 
  dedicated scale sequencing:
  * Mayamalavagowla
  * Shankarabharanam
  * Kharaharapriya
  * Kalyani
  * Hanumatodi
  * Mohanam
  * Sri Ragam
  * Anandabhairavi
  * Madhyamavati
  * Arabhi
  * Naatai

- Advanced DSP & Performance Drawer:
  * Target Frame Rate throttle (20 - 120 FPS).
  * Web Audio FFT Bin selector (1024, 2048, 4096, 8192) for mandra sthayi resolution.
  * In-tune pitch tolerance dial (+/-15 to +/-50 cents).
  * Autocorrelation clarity threshold, FFT smoothing, and pitch history trail depth.

- Live Visitor Counter:
  Integrated client-side badge displaying active session counts via CounterAPI.


===============================================================================
2. TECH STACK & ARCHITECTURE
===============================================================================

- Front-End: Vanilla HTML5, CSS3 (Modern Dark Theme), Canvas API.
- Audio DSP Engine: Web Audio API (AudioContext, AnalyserNode, BiquadFilterNode).
- Pitch Detection: Normalized Autocorrelation with octave jump / sub-harmonic 
  correction heuristics and 5-point median smoothing.
- Analytics: Asynchronous CounterAPI integration with fallback.
- Dependencies: None (Single-file self-contained deployment).


===============================================================================
3. QUICK START (LOCAL RUN)
===============================================================================

1. Clone the repository:
   git clone https://github.com/sudha-chel/carnatic-visualizer.git
   cd carnatic-visualizer

2. Open index.html directly in any modern browser:
   - macOS:   open index.html
   - Linux:   xdg-open index.html
   - Windows: start index.html

* Note on Microphone Access:
  Modern browsers require a secure context (HTTPS or localhost) to grant 
  microphone access via navigator.mediaDevices.getUserMedia().


===============================================================================
4. DEPLOYMENT TO GITHUB PAGES
===============================================================================

1. Ensure the primary HTML file is named "index.html":
   git add -A
   git commit -m "Prepare site for deployment"
   git push origin main

2. In your GitHub repository:
   - Navigate to Settings -> Pages.
   - Under Build and deployment -> Branch, select "main" and root ("/").
   - Click Save.
   - Your application will be live at:
     https://<your-username>.github.io/carnatic-visualizer/


===============================================================================
5. USAGE GUIDE
===============================================================================

1. Select Shruti:
   Click your Adhara Shadjam base key (default is G# / 5.5 Kattai).

2. Start Drone:
   Click "Start Drone" to initialize the reference Tanpura.

3. Select Raga:
   Choose a raga from the dropdown list.

4. Practice Scale:
   Click "Play Arohana / Avarohana" to listen to the correct sequence played 
   on the synthetic Veena (microphone automatically pauses during playback).

5. Start Singing:
   Click "Start Listening" and sing into your device microphone.
   - Observe real-time continuous curves on the pitch ribbon.
   - Monitor the Live Note Detection window for real-time Green, Pink, and 
     Red intonation feedback.

6. Adjust Settings:
   Open "Advanced Settings" in the upper-right corner to fine-tune FFT bins, 
   display frame rates, or pitch error margins.


===============================================================================
6. LICENSE
===============================================================================

MIT License. Free for all musicians, teachers, and researchers.
