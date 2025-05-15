<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Forced Damped Pendulum Interactive Simulation</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.4.2/p5.min.js"></script>
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            margin: 0;
            padding: 20px;
            max-width: 1200px;
            margin-left: auto;
            margin-right: auto;
            background-color: #f0f0f0;
        }
        h2 {
            color: #2c3e50;
        }
        .container {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
        }
        .canvas-container {
            flex: 1;
            min-width: 300px;
        }
        .controls {
            flex: 1;
            min-width: 200px;
            padding: 10px;
            background-color: #fff;
            border-radius: 5px;
        }
        .section {
            margin-bottom: 20px;
            background-color: #fff;
            padding: 15px;
            border-radius: 5px;
        }
        label {
            display: block;
            margin: 10px 0 5px;
        }
        input[type="range"] {
            width: 100%;
        }
        canvas {
            border: 1px solid #ccc;
        }
    </style>
</head>
<body>
    <div class="section">
        <h2>Interactive Simulation</h2>
        <p>Adjust the sliders to explore the pendulum’s dynamics. The animation shows the pendulum’s motion, with plots for time series, phase portrait, and Poincaré section.</p>
        <div class="container">
            <div class="canvas-container">
                <div id="pendulum-canvas"></div>
                <div id="time-series-canvas"></div>
                <div id="phase-portrait-canvas"></div>
                <div id="poincare-canvas"></div>
            </div>
            <div class="controls">
                <label for="gamma">Damping Coefficient (γ): <span id="gamma-value">0.5</span></label>
                <input type="range" id="gamma" min="0" max="2" step="0.01" value="0.5">
                <label for="force">Driving Amplitude (F): <span id="force-value">1.2</span></label>
                <input type="range" id="force" min="0" max="2" step="0.01" value="1.2">
                <label for="omega">Driving Frequency (ω): <span id="omega-value">0.67</span></label>
                <input type="range" id="omega" min="0.1" max="5" step="0.01" value="0.67">
                <button onclick="resetSimulation()">Reset</button>
            </div>
        </div>
    </div>

    <script>
        let theta = 0.2; // initial angle
        let thetaDot = 0; // initial angular velocity
        let t = 0; // time
        let g = 9.81; // gravity
        let l = 1; // pendulum length
        let omega0 = Math.sqrt(g / l); // natural frequency
        let gamma = 0.5; // damping coefficient
        let F = 1.2; // driving amplitude
        let omega = 2/3; // driving frequency
        let dt = 0.02; // time step

        let timeSeries = [];
        let phasePortrait = [];
        let poincarePoints = [];
        let T = 2 * Math.PI / omega; // driving period
        let nextPoincareTime = T;

        let pendulumSketch, timeSeriesSketch, phasePortraitSketch, poincareSketch;

        // Pendulum animation
        pendulumSketch = function(p) {
            p.setup = function() {
                p.createCanvas(300, 300);
                p.background(255);
            };

            p.draw = function() {
                p.background(255);
                p.translate(p.width / 2, p.height / 4);
                let x = l * 100 * Math.sin(theta);
                let y = l * 100 * Math.cos(theta);
                p.stroke(0);
                p.line(0, 0, x, y);
                p.fill(255, 0, 0);
                p.ellipse(x, y, 20, 20);
            };
        };

        // Time series plot
        timeSeriesSketch = function(p) {
            p.setup = function() {
                p.createCanvas(300, 200);
                p.background(255);
            };

            p.draw = function() {
                p.background(255);
                p.beginShape();
                p.noFill();
                p.stroke(0, 0, 255);
                for (let i = 0; i < timeSeries.length; i++) {
                    let x = p.map(i, 0, timeSeries.length, 0, p.width);
                    let y = p.map(timeSeries[i], -Math.PI, Math.PI, p.height, 0);
                    p.vertex(x, y);
                }
                p.endShape();
                p.text('θ(t)', 10, 20);
                p.text('Time', p.width - 40, p.height - 10);
            };
        };

        // Phase portrait
        phasePortraitSketch = function(p) {
            p.setup = function() {
                p.createCanvas(300, 200);
                p.background(255);
            };

            p.draw = function() {
                p.background(255);
                p.beginShape();
                p.noFill();
                p.stroke(0, 255, 0);
                for (let point of phasePortrait) {
                    let x = p.map(point[0], -Math.PI, Math.PI, 0, p.width);
                    let y = p.map(point[1], -10, 10, p.height, 0);
                    p.vertex(x, y);
                }
                p.endShape();
                p.text('θ', 10, 20);
                p.text('dθ/dt', p.width - 40, p.height - 10);
            };
        };

        // Poincaré section
        poincareSketch = function(p) {
            p.setup = function() {
                p.createCanvas(300, 200);
                p.background(255);
            };

            p.draw = function() {
                p.background(255);
                p.fill(255, 0, 0);
                p.noStroke();
                for (let point of poincarePoints) {
                    let x = p.map(point[0], -Math.PI, Math.PI, 0, p.width);
                    let y = p.map(point[1], -10, 10, p.height, 0);
                    p.ellipse(x, y, 5, 5);
                }
                p.text('θ', 10, 20);
                p.text('dθ/dt', p.width - 40, p.height - 10);
            };
        };

        // Initialize sketches
        new p5(pendulumSketch, 'pendulum-canvas');
        new p5(timeSeriesSketch, 'time-series-canvas');
        new p5(phasePortraitSketch, 'phase-portrait-canvas');
        new p5(poincareSketch, 'poincare-canvas');

        // Update parameters from sliders
        document.getElementById('gamma').addEventListener('input', function() {
            gamma = parseFloat(this.value);
            document.getElementById('gamma-value').textContent = gamma.toFixed(2);
        });

        document.getElementById('force').addEventListener('input', function() {
            F = parseFloat(this.value);
            document.getElementById('force-value').textContent = F.toFixed(2);
        });

        document.getElementById('omega').addEventListener('input', function() {
            omega = parseFloat(this.value);
            document.getElementById('omega-value').textContent = omega.toFixed(2);
            T = 2 * Math.PI / omega;
            nextPoincareTime = t + T;
        });

        // Reset simulation
        function resetSimulation() {
            theta = 0.2;
            thetaDot = 0;
            t = 0;
            timeSeries = [];
            phasePortrait = [];
            poincarePoints = [];
            nextPoincareTime = T;
        }

        // Runge-Kutta 4th order
        function rk4() {
            let k1_theta = thetaDot;
            let k1_thetaDot = -gamma * thetaDot - omega0 * omega0 * Math.sin(theta) + F * Math.cos(omega * t);

            let theta2 = theta + 0.5 * k1_theta * dt;
            let thetaDot2 = thetaDot + 0.5 * k1_thetaDot * dt;
            let k2_theta = thetaDot2;
            let k2_thetaDot = -gamma * thetaDot2 - omega0 * omega0 * Math.sin(theta2) + F * Math.cos(omega * (t + 0.5 * dt));

            let theta3 = theta + 0.5 * k2_theta * dt;
            let thetaDot3 = thetaDot + 0.5 * k2_thetaDot * dt;
            let k3_theta = thetaDot3;
            let k3_thetaDot = -gamma * thetaDot3 - omega0 * omega0 * Math.sin(theta3) + F * Math.cos(omega * (t + 0.5 * dt));

            let theta4 = theta + k3_theta * dt;
            let thetaDot4 = thetaDot + k3_thetaDot * dt;
            let k4_theta = thetaDot4;
            let k4_thetaDot = -gamma * thetaDot4 - omega0 * omega0 * Math.sin(theta4) + F * Math.cos(omega * (t + dt));

            theta += (dt / 6) * (k1_theta + 2 * k2_theta + 2 * k3_theta + k4_theta);
            thetaDot += (dt / 6) * (k1_thetaDot + 2 * k2_thetaDot + 2 * k3_thetaDot + k4_thetaDot);
            t += dt;

            // Store data
            timeSeries.push(theta);
            phasePortrait.push([theta, thetaDot]);
            if (timeSeries.length > 500) timeSeries.shift();
            if (phasePortrait.length > 1000) phasePortrait.shift();

            // Poincaré section
            if (t >= nextPoincareTime) {
                poincarePoints.push([theta, thetaDot]);
                if (poincarePoints.length > 100) poincarePoints.shift();
                nextPoincareTime += T;
            }
        }

        // Animation loop
        setInterval(rk4, dt * 1000);
    </script>
</body>
</html>