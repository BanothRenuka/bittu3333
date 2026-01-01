<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Automated Packaging System Design</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f7fa;
            color: #333;
            line-height: 1.6;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            background: linear-gradient(135deg, #2c3e50 0%, #4a6491 100%);
            color: white;
            padding: 30px 0;
            text-align: center;
            border-radius: 10px;
            margin-bottom: 30px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
        }
        
        .subtitle {
            font-size: 1.2rem;
            opacity: 0.9;
        }
        
        .system-description {
            background-color: white;
            padding: 25px;
            border-radius: 10px;
            margin-bottom: 30px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }
        
        .system-description h2 {
            color: #2c3e50;
            margin-bottom: 15px;
            border-bottom: 2px solid #3498db;
            padding-bottom: 8px;
        }
        
        .content-wrapper {
            display: flex;
            flex-wrap: wrap;
            gap: 30px;
            margin-bottom: 30px;
        }
        
        .diagram-section, .flowchart-section {
            flex: 1;
            min-width: 300px;
            background-color: white;
            border-radius: 10px;
            padding: 25px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }
        
        .section-title {
            color: #2c3e50;
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .section-title i {
            color: #3498db;
        }
        
        .circuit-container {
            position: relative;
            height: 400px;
            background-color: #f9f9f9;
            border-radius: 8px;
            overflow: hidden;
            margin-bottom: 20px;
        }
        
        .flowchart-container {
            position: relative;
            height: 400px;
            background-color: #f9f9f9;
            border-radius: 8px;
            overflow: hidden;
            margin-bottom: 20px;
        }
        
        .component {
            position: absolute;
            width: 80px;
            height: 80px;
            background-color: white;
            border-radius: 8px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s;
            cursor: pointer;
            text-align: center;
            padding: 5px;
        }
        
        .component:hover {
            transform: scale(1.05);
            z-index: 10;
        }
        
        .component i {
            font-size: 1.5rem;
            margin-bottom: 5px;
        }
        
        .sensor { border-left: 5px solid #2ecc71; }
        .actuator { border-left: 5px solid #e74c3c; }
        .controller { border-left: 5px solid #3498db; }
        .conveyor { border-left: 5px solid #f39c12; }
        .power { border-left: 5px solid #9b59b6; }
        
        .flow-step {
            position: absolute;
            width: 150px;
            background-color: white;
            border-radius: 8px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
            padding: 15px;
            text-align: center;
            transition: all 0.3s;
            cursor: pointer;
        }
        
        .flow-step:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 15px rgba(0, 0, 0, 0.1);
        }
        
        .flow-connector {
            position: absolute;
            height: 3px;
            background-color: #3498db;
            transform-origin: left center;
        }
        
        .flow-arrow {
            position: absolute;
            width: 0;
            height: 0;
            border-top: 7px solid transparent;
            border-bottom: 7px solid transparent;
            border-left: 10px solid #3498db;
        }
        
        .explanation-panel {
            background-color: white;
            padding: 25px;
            border-radius: 10px;
            margin-bottom: 30px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }
        
        .component-details {
            display: none;
            margin-top: 15px;
            padding: 15px;
            background-color: #f8f9fa;
            border-radius: 8px;
            border-left: 4px solid #3498db;
        }
        
        .component-details.active {
            display: block;
        }
        
        .component-list {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 15px;
            margin-top: 15px;
        }
        
        .component-item {
            background-color: #f8f9fa;
            padding: 15px;
            border-radius: 8px;
            display: flex;
            align-items: center;
            gap: 10px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        
        .component-item:hover {
            background-color: #e9ecef;
        }
        
        .component-item i {
            font-size: 1.5rem;
        }
        
        .report-section {
            background-color: white;
            padding: 25px;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }
        
        .report-section h2 {
            color: #2c3e50;
            margin-bottom: 20px;
            border-bottom: 2px solid #3498db;
            padding-bottom: 8px;
        }
        
        .report-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 25px;
        }
        
        .report-card {
            background-color: #f8f9fa;
            padding: 20px;
            border-radius: 8px;
            border-top: 4px solid #3498db;
        }
        
        .report-card h3 {
            color: #2c3e50;
            margin-bottom: 10px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .report-card h3 i {
            color: #3498db;
        }
        
        footer {
            text-align: center;
            padding: 20px;
            margin-top: 40px;
            color: #7f8c8d;
            font-size: 0.9rem;
            border-top: 1px solid #eee;
        }
        
        @media (max-width: 768px) {
            .content-wrapper {
                flex-direction: column;
            }
            
            h1 {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Automated Packaging System Design</h1>
            <p class="subtitle">Circuit Diagram & Flowchart with Explanation Report</p>
        </header>
        
        <div class="system-description">
            <h2><i class="fas fa-box-open"></i> System Overview</h2>
            <p>This automated packaging system is designed to efficiently package products using sensors, actuators, and a programmable logic controller (PLC). The system includes product detection, quality control, sorting, and packaging functions. The circuit diagram illustrates the electrical connections, while the flowchart demonstrates the logical flow of operations.</p>
        </div>
        
        <div class="content-wrapper">
            <div class="diagram-section">
                <h2 class="section-title"><i class="fas fa-project-diagram"></i> Circuit Diagram</h2>
                <div class="circuit-container" id="circuit-container">
                    <!-- Circuit components will be placed here by JavaScript -->
                </div>
                <div id="circuit-explanation" class="component-details">
                    <h3>Circuit Explanation</h3>
                    <p>Click on any component in the diagram to see its function and specifications.</p>
                </div>
            </div>
            
            <div class="flowchart-section">
                <h2 class="section-title"><i class="fas fa-sitemap"></i> System Flowchart</h2>
                <div class="flowchart-container" id="flowchart-container">
                    <!-- Flowchart steps will be placed here by JavaScript -->
                </div>
                <div id="flowchart-explanation" class="component-details">
                    <h3>Process Explanation</h3>
                    <p>Click on any step in the flowchart to see detailed information about that stage of the packaging process.</p>
                </div>
            </div>
        </div>
        
        <div class="explanation-panel">
            <h2 class="section-title"><i class="fas fa-info-circle"></i> System Components</h2>
            <div class="component-list">
                <div class="component-item sensor" data-component="photoelectric">
                    <i class="fas fa-lightbulb"></i>
                    <div>
                        <h4>Photoelectric Sensor</h4>
                        <p>Detects product presence</p>
                    </div>
                </div>
                <div class="component-item actuator" data-component="pneumatic">
                    <i class="fas fa-wind"></i>
                    <div>
                        <h4>Pneumatic Actuator</h4>
                        <p>Pushes products into boxes</p>
                    </div>
                </div>
                <div class="component-item controller" data-component="plc">
                    <i class="fas fa-microchip"></i>
                    <div>
                        <h4>PLC Controller</h4>
                        <p>Central control unit</p>
                    </div>
                </div>
                <div class="component-item conveyor" data-component="conveyor">
                    <i class="fas fa-conveyor-belt"></i>
                    <div>
                        <h4>Conveyor Belt</h4>
                        <p>Transports products</p>
                    </div>
                </div>
                <div class="component-item sensor" data-component="proximity">
                    <i class="fas fa-broadcast-tower"></i>
                    <div>
                        <h4>Proximity Sensor</h4>
                        <p>Detects metal objects</p>
                    </div>
                </div>
                <div class="component-item power" data-component="power">
                    <i class="fas fa-bolt"></i>
                    <div>
                        <h4>Power Supply</h4>
                        <p>24V DC system power</p>
                    </div>
                </div>
            </div>
            <div id="component-details" class="component-details">
                <h3>Component Details</h3>
                <p>Select a component from the list above to see detailed information.</p>
            </div>
        </div>
        
        <div class="report-section">
            <h2><i class="fas fa-file-alt"></i> System Design Report</h2>
            <div class="report-content">
                <div class="report-card">
                    <h3><i class="fas fa-cogs"></i> System Architecture</h3>
                    <p>The automated packaging system uses a modular architecture with a central PLC controller managing all operations. Input sensors detect product presence, dimensions, and quality, while output actuators control the conveyor, sorting mechanisms, and packaging equipment.</p>
                    <p>The system operates on 24V DC for safety and efficiency. All components are connected via shielded cables to prevent electromagnetic interference in industrial environments.</p>
                </div>
                
                <div class="report-card">
                    <h3><i class="fas fa-tachometer-alt"></i> Operational Process</h3>
                    <p>1. <strong>Product Detection:</strong> Photoelectric sensors detect arriving products on the conveyor belt.</p>
                    <p>2. <strong>Quality Check:</strong> Vision system and proximity sensors verify product quality and dimensions.</p>
                    <p>3. <strong>Sorting:</strong> Defective products are diverted to a rejection bin via pneumatic actuators.</p>
                    <p>4. <strong>Packaging:</strong> Approved products are packaged and sealed automatically.</p>
                    <p>5. <strong>Monitoring:</strong> The PLC monitors all processes and logs production data.</p>
                </div>
                
                <div class="report-card">
                    <h3><i class="fas fa-shield-alt"></i> Safety Features</h3>
                    <p>The system includes multiple safety mechanisms: emergency stop buttons, safety light curtains, overload protection on motors, and fault detection algorithms. The PLC is programmed with fail-safe routines that activate in case of power loss or component failure.</p>
                    <p>All moving parts are enclosed with safety guards that are interlocked with the control system to prevent operation when opened.</p>
                </div>
                
                <div class="report-card">
                    <h3><i class="fas fa-chart-line"></i> Performance Metrics</h3>
                    <p><strong>Throughput:</strong> Up to 120 packages per minute</p>
                    <p><strong>Accuracy:</strong> 99.8% detection accuracy</p>
                    <p><strong>Uptime:</strong> 95% operational availability</p>
                    <p><strong>Power Consumption:</strong> 2.5 kW average during operation</p>
                    <p><strong>Maintenance:</strong> Scheduled maintenance every 500 operating hours</p>
                </div>
            </div>
        </div>
        
        <footer>
            <p>Automated Packaging System Design | Task 3: Automation System Design</p>
            <p>This interactive design includes both circuit diagram and flowchart with detailed explanation report.</p>
        </footer>
    </div>

    <script>
        // Component data for the circuit diagram
        const circuitComponents = [
            { id: 1, type: 'controller', name: 'PLC Controller', icon: 'fas fa-microchip', x: 50, y: 160, description: 'Central Programmable Logic Controller (PLC) that processes all sensor inputs and controls actuators. Model: Siemens S7-1200, 24V DC operation, with digital and analog I/O modules.' },
            { id: 2, type: 'sensor', name: 'Photo Sensor', icon: 'fas fa-lightbulb', x: 200, y: 60, description: 'Photoelectric sensor detects product presence on the conveyor. Sensing range: 0-2m, Response time: 1ms, Output: NPN transistor.' },
            { id: 3, type: 'sensor', name: 'Proximity Sensor', icon: 'fas fa-broadcast-tower', x: 200, y: 260, description: 'Inductive proximity sensor for metal detection. Detection distance: 8mm, Output: PNP normally open, IP67 rated for dust/water resistance.' },
            { id: 4, type: 'actuator', name: 'Pneumatic Cylinder', icon: 'fas fa-wind', x: 350, y: 160, description: 'Double-acting pneumatic cylinder for product pushing. Bore: 32mm, Stroke: 100mm, Operating pressure: 4-6 bar, with magnetic piston position detection.' },
            { id: 5, type: 'conveyor', name: 'Conveyor Motor', icon: 'fas fa-conveyor-belt', x: 500, y: 160, description: 'AC motor with variable frequency drive for conveyor speed control. Power: 0.75kW, Speed range: 0-50Hz, with overload protection and braking resistor.' },
            { id: 6, type: 'power', name: 'Power Supply', icon: 'fas fa-bolt', x: 50, y: 300, description: '24V DC switching power supply for the control system. Input: 100-240V AC, Output: 24V DC/10A, with short-circuit and overload protection.' }
        ];
        
        // Flowchart steps data
        const flowchartSteps = [
            { id: 1, name: 'Start System', x: 50, y: 50, description: 'System initialization: Power on, self-test diagnostics, and reset to home position.' },
            { id: 2, name: 'Product Detection', x: 250, y: 50, description: 'Photoelectric sensor detects product arrival on the conveyor belt.' },
            { id: 3, name: 'Quality Check', x: 450, y: 50, description: 'Vision system and sensors verify product dimensions, orientation, and quality.' },
            { id: 4, name: 'Product OK?', x: 250, y: 150, description: 'Decision point: If product passes quality check, it proceeds to packaging. If not, it goes to rejection.' },
            { id: 5, name: 'Reject Product', x: 100, y: 250, description: 'Defective product diverted to rejection bin via pneumatic actuator.' },
            { id: 6, name: 'Package Product', x: 400, y: 250, description: 'Approved product is automatically packaged in designated container.' },
            { id: 7, name: 'Seal & Label', x: 600, y: 250, description: 'Package is sealed and labeled with product information and barcode.' },
            { id: 8, name: 'Dispatch', x: 600, y: 350, description: 'Finished package is moved to dispatch area for shipping.' },
            { id: 9, name: 'Continue?', x: 250, y: 350, description: 'Check if more products are in queue. If yes, return to step 2. If no, proceed to shutdown.' },
            { id: 10, name: 'System Shutdown', x: 450, y: 350, description: 'Orderly shutdown: Conveyor stops, actuators return to home position, and power is secured.' }
        ];
        
        // Component details for the list
        const componentDetails = {
            'photoelectric': {
                title: 'Photoelectric Sensor',
                description: 'Used for detecting product presence on the conveyor. Emits a light beam and detects when it is interrupted by a passing product. Key specifications: Sensing distance up to 2m, response time < 1ms, NPN output, IP67 protection rating.',
                function: 'Provides input signal to PLC when a product is detected.'
            },
            'pneumatic': {
                title: 'Pneumatic Actuator',
                description: 'Double-acting cylinder controlled by solenoid valves. Used for pushing products into packaging or diverting defective items. Operates at 4-6 bar pressure with position feedback via magnetic sensors.',
                function: 'Executes physical movement based on PLC commands.'
            },
            'plc': {
                title: 'PLC Controller',
                description: 'Siemens S7-1200 programmable logic controller with 24 digital inputs, 16 digital outputs, 4 analog inputs, and 2 analog outputs. Programmed using ladder logic and function block diagrams.',
                function: 'Central processing unit that controls the entire packaging system.'
            },
            'conveyor': {
                title: 'Conveyor Belt System',
                description: 'Motorized conveyor with variable speed control. Includes belt tracking mechanism, emergency stop pull cords, and safety guarding. Powered by 0.75kW AC motor with variable frequency drive.',
                function: 'Transports products through the packaging process.'
            },
            'proximity': {
                title: 'Proximity Sensor',
                description: 'Inductive proximity sensor for detecting metal objects. Used to verify product composition or detect metallic contaminants. Sensing distance: 8mm, PNP output, shielded design.',
                function: 'Provides metal detection capability for quality control.'
            },
            'power': {
                title: 'Power Supply Unit',
                description: '24V DC switching power supply with 10A output capacity. Converts 110-240V AC mains power to stable 24V DC for control circuitry. Includes overload and short-circuit protection.',
                function: 'Provides safe low-voltage power to all control system components.'
            }
        };
        
        // Initialize the circuit diagram
        function initCircuitDiagram() {
            const container = document.getElementById('circuit-container');
            
            // Create components
            circuitComponents.forEach(component => {
                const div = document.createElement('div');
                div.className = `component ${component.type}`;
                div.style.left = `${component.x}px`;
                div.style.top = `${component.y}px`;
                div.innerHTML = `<i class="${component.icon}"></i><span>${component.name}</span>`;
                div.addEventListener('click', () => showComponentDetails(component));
                container.appendChild(div);
            });
            
            // Create connections between components (simplified representation)
            createConnection(50, 200, 200, 100); // PLC to Photo Sensor
            createConnection(50, 200, 200, 300); // PLC to Proximity Sensor
            createConnection(50, 200, 350, 200); // PLC to Pneumatic Cylinder
            createConnection(50, 200, 500, 200); // PLC to Conveyor Motor
            createConnection(50, 340, 50, 200); // Power Supply to PLC
        }
        
        // Create a connection line in the circuit diagram
        function createConnection(x1, y1, x2, y2) {
            const container = document.getElementById('circuit-container');
            
            // Calculate distance and angle
            const dx = x2 - x1;
            const dy = y2 - y1;
            const distance = Math.sqrt(dx*dx + dy*dy);
            const angle = Math.atan2(dy, dx) * 180 / Math.PI;
            
            // Create line element
            const line = document.createElement('div');
            line.className = 'flow-connector';
            line.style.width = `${distance}px`;
            line.style.left = `${x1}px`;
            line.style.top = `${y1}px`;
            line.style.transform = `rotate(${angle}deg)`;
            
            container.appendChild(line);
        }
        
        // Initialize the flowchart
        function initFlowchart() {
            const container = document.getElementById('flowchart-container');
            
            // Create flowchart steps
            flowchartSteps.forEach(step => {
                const div = document.createElement('div');
                div.className = 'flow-step';
                div.style.left = `${step.x}px`;
                div.style.top = `${step.y}px`;
                div.innerHTML = `<strong>${step.name}</strong>`;
                div.addEventListener('click', () => showFlowchartStepDetails(step));
                container.appendChild(div);
            });
            
            // Create connections between steps
            createFlowchartConnection(80, 90, 250, 90); // Start to Product Detection
            createFlowchartConnection(330, 90, 450, 90); // Product Detection to Quality Check
            createFlowchartConnection(520, 90, 520, 150, false); // Quality Check down
            createFlowchartConnection(520, 150, 330, 150); // Down to decision left
            createFlowchartConnection(330, 180, 330, 250, false); // Decision to Reject
            createFlowchartConnection(170, 250, 170, 310, false); // Reject down
            createFlowchartConnection(170, 310, 330, 310); // Reject to Continue?
            createFlowchartConnection(330, 150, 430, 150); // Decision to Package
            createFlowchartConnection(470, 180, 470, 250, false); // Package down
            createFlowchartConnection(470, 250, 570, 250); // Package to Seal
            createFlowchartConnection(670, 280, 670, 350, false); // Seal down
            createFlowchartConnection(670, 350, 570, 350); // Seal to Dispatch
            createFlowchartConnection(570, 350, 430, 350); // Dispatch to Continue?
            createFlowchartConnection(380, 380, 380, 450, false); // Continue? down
            createFlowchartConnection(380, 450, 520, 450, true); // Continue? to Shutdown
            
            // Add arrows
            addArrow(250, 90, 'right');
            addArrow(450, 90, 'right');
            addArrow(520, 150, 'down');
            addArrow(330, 250, 'down');
            addArrow(170, 310, 'down');
            addArrow(470, 250, 'down');
            addArrow(670, 350, 'down');
            addArrow(380, 450, 'down');
        }
        
        // Create a connection in the flowchart
        function createFlowchartConnection(x1, y1, x2, y2, horizontalFirst = true) {
            const container = document.getElementById('flowchart-container');
            
            if (horizontalFirst) {
                // Horizontal then vertical
                const line1 = document.createElement('div');
                line1.className = 'flow-connector';
                line1.style.width = `${Math.abs(x2 - x1)}px`;
                line1.style.left = `${Math.min(x1, x2)}px`;
                line1.style.top = `${y1}px`;
                container.appendChild(line1);
                
                const line2 = document.createElement('div');
                line2.className = 'flow-connector';
                line2.style.width = `${Math.abs(y2 - y1)}px`;
                line2.style.height = '3px';
                line2.style.transform = `rotate(90deg)`;
                line2.style.transformOrigin = 'top left';
                line2.style.left = `${x2}px`;
                line2.style.top = `${Math.min(y1, y2)}px`;
                container.appendChild(line2);
            } else {
                // Vertical then horizontal
                const line1 = document.createElement('div');
                line1.className = 'flow-connector';
                line1.style.width = `${Math.abs(y2 - y1)}px`;
                line1.style.height = '3px';
                line1.style.transform = `rotate(90deg)`;
                line1.style.transformOrigin = 'top left';
                line1.style.left = `${x1}px`;
                line1.style.top = `${Math.min(y1, y2)}px`;
                container.appendChild(line1);
                
                const line2 = document.createElement('div');
                line2.className = 'flow-connector';
                line2.style.width = `${Math.abs(x2 - x1)}px`;
                line2.style.left = `${Math.min(x1, x2)}px`;
                line2.style.top = `${y2}px`;
                container.appendChild(line2);
            }
        }
        
        // Add an arrow to the flowchart
        function addArrow(x, y, direction) {
            const container = document.getElementById('flowchart-container');
            const arrow = document.createElement('div');
            arrow.className = 'flow-arrow';
            
            if (direction === 'right') {
                arrow.style.left = `${x}px`;
                arrow.style.top = `${y-7}px`;
            } else if (direction === 'down') {
                arrow.style.transform = 'rotate(90deg)';
                arrow.style.left = `${x-7}px`;
                arrow.style.top = `${y}px`;
            } else if (direction === 'left') {
                arrow.style.transform = 'rotate(180deg)';
                arrow.style.left = `${x-10}px`;
                arrow.style.top = `${y-7}px`;
            } else if (direction === 'up') {
                arrow.style.transform = 'rotate(270deg)';
                arrow.style.left = `${x-7}px`;
                arrow.style.top = `${y-10}px`;
            }
            
            container.appendChild(arrow);
        }
        
        // Show component details when clicked
        function showComponentDetails(component) {
            const detailsDiv = document.getElementById('circuit-explanation');
            detailsDiv.innerHTML = `
                <h3>${component.name}</h3>
                <p><strong>Type:</strong> ${component.type.charAt(0).toUpperCase() + component.type.slice(1)}</p>
                <p><strong>Description:</strong> ${component.description}</p>
                <p><strong>Function:</strong> ${component.type === 'sensor' ? 'Provides input to the PLC' : component.type === 'actuator' ? 'Executes physical actions based on PLC commands' : component.type === 'controller' ? 'Processes all system logic and controls' : 'Provides mechanical movement or power'}</p>
            `;
            detailsDiv.classList.add('active');
            
            // Also update the component details panel
            showComponentListDetails(component.type);
        }
        
        // Show flowchart step details when clicked
        function showFlowchartStepDetails(step) {
            const detailsDiv = document.getElementById('flowchart-explanation');
            detailsDiv.innerHTML = `
                <h3>${step.name}</h3>
                <p><strong>Step ${step.id}:</strong> ${step.description}</p>
                <p><strong>Process:</strong> ${getStepProcess(step.id)}</p>
            `;
            detailsDiv.classList.add('active');
        }
        
        // Get process description for flowchart steps
        function getStepProcess(stepId) {
            const processes = {
                1: 'System initialization and self-check routine.',
                2: 'Sensor monitoring and signal processing.',
                3: 'Image processing and measurement algorithms.',
                4: 'Decision logic based on quality parameters.',
                5: 'Actuator control for product rejection.',
                6: 'Packaging mechanism operation.',
                7: 'Sealing and labeling operations.',
                8: 'Conveyor control to dispatch area.',
                9: 'Queue management and system state check.',
                10: 'Orderly shutdown procedure.'
            };
            return processes[stepId] || 'Automated packaging system operation.';
        }
        
        // Show component details from the list
        function showComponentListDetails(componentKey) {
            const component = componentDetails[componentKey];
            if (!component) return;
            
            const detailsDiv = document.getElementById('component-details');
            detailsDiv.innerHTML = `
                <h3>${component.title}</h3>
                <p><strong>Description:</strong> ${component.description}</p>
                <p><strong>Primary Function:</strong> ${component.function}</p>
                <p><strong>Integration:</strong> Connected to the PLC via shielded cable. ${componentKey === 'photoelectric' || componentKey === 'proximity' ? 'Provides digital input signal.' : 'Receives control signals from PLC output modules.'}</p>
            `;
            detailsDiv.classList.add('active');
        }
        
        // Initialize the page when loaded
        document.addEventListener('DOMContentLoaded', function() {
            initCircuitDiagram();
            initFlowchart();
            
            // Add event listeners to component list items
            document.querySelectorAll('.component-item').forEach(item => {
                item.addEventListener('click', function() {
                    const componentKey = this.getAttribute('data-component');
                    showComponentListDetails(componentKey);
                });
            });
            
            // Show default details
            showComponentListDetails('plc');
        });
    </script>
</body>
</html>