<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Hosercoder | Algorithmic Trading System</title>
  <meta name="description" content="An extensible, modular algorithmic trading system by Hosercoder. This is my personal project showcasing clean architecture, plug-in strategies, and compliance-aware tooling." />
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
  <style>
    :root{
      --bg:#0b1220;
      --card:#121a2b;
      --muted:#9fb0d3;
      --text:#e8eefc;
      --accent:#67e8f9;
      --accent-2:#84cc16;
      --danger:#ef4444;
      --border:rgba(255,255,255,0.08);
      --shadow:0 10px 30px rgba(0,0,0,0.35);
    }
    *{box-sizing:border-box}
    html,body{margin:0;padding:0;background:var(--bg);color:var(--text);font-family:"Inter",system-ui,-apple-system,Segoe UI,Roboto,Ubuntu,"Helvetica Neue",Arial,sans-serif;}
    a{color:var(--accent);text-decoration:none}
    a:hover{text-decoration:underline}
    .container{max-width:1100px;margin:0 auto;padding:40px 24px}
    .hero{
      display:flex;gap:28px;align-items:center;flex-wrap:wrap;
      background:linear-gradient(180deg, rgba(103,232,249,0.08), rgba(132,204,22,0.05));
      border:1px solid var(--border);border-radius:20px;padding:28px;box-shadow:var(--shadow)
    }
    .badge{display:inline-flex;gap:8px;align-items:center;color:var(--muted);font-weight:600;letter-spacing:.02em}
    .pill{display:inline-block;padding:6px 10px;border:1px solid var(--border);border-radius:999px;background:rgba(255,255,255,0.03);color:var(--muted);font-size:13px}
    h1{font-size:32px;margin:4px 0 10px}
    h2{font-size:22px;margin:0 0 14px}
    p{color:#d8e3fb;line-height:1.6}
    .actions{display:flex;gap:12px;flex-wrap:wrap;margin-top:12px}
    .btn{
      display:inline-flex;align-items:center;gap:10px;padding:10px 14px;border:1px solid var(--border);
      border-radius:12px;background:var(--card);color:var(--text);box-shadow:var(--shadow);font-weight:600
    }
    .btn.primary{background:linear-gradient(90deg, #1f2937, #0ea5e9);border-color:#0ea5e9}
    .grid{display:grid;grid-template-columns:repeat(3,1fr);gap:16px;margin-top:26px}
    @media (max-width:960px){.grid{grid-template-columns:1fr 1fr}}
    @media (max-width:640px){.grid{grid-template-columns:1fr}}
    .card{background:var(--card);border:1px solid var(--border);border-radius:16px;padding:18px;box-shadow:var(--shadow)}
    .card h3{margin:0 0 8px;font-size:18px}
    .code{font-family:ui-monospace,SFMono-Regular,Menlo,Monaco,Consolas,"Liberation Mono","Courier New",monospace;background:#0a0f1a;border:1px solid var(--border);border-radius:12px;padding:14px;overflow:auto}
    .kpi{display:flex;gap:16px;flex-wrap:wrap}
    .kpi .stat{flex:1;min-width:220px;background:var(--card);border:1px solid var(--border);border-radius:14px;padding:14px}
    .stat strong{display:block;font-size:20px}
    .arch{display:grid;grid-template-columns:1fr 1fr;gap:16px;margin-top:18px}
    @media (max-width:880px){.arch{grid-template-columns:1fr}}
    .chip{display:inline-block;margin:4px 6px 0 0;padding:6px 10px;border:1px dashed var(--border);border-radius:12px;color:var(--muted);font-size:13px}
    .list{list-style:none;padding:0;margin:8px 0}
    .list li{margin:6px 0;padding-left:0}
    .footer{margin-top:32px;padding-top:20px;border-top:1px solid var(--border);color:var(--muted);font-size:14px}
    .note{border-left:3px solid var(--accent);padding:10px 12px;background:rgba(103,232,249,0.06);border-radius:8px}
    .success{border-left:3px solid var(--accent-2);background:rgba(132,204,22,0.06)}
    .warning{border-left:3px solid #f59e0b;background:rgba(245,158,11,0.06)}
  </style>
</head>
<body>
  <div class="container">
    <h1>Hosercoder — Algorithmic Trading System</h1>
    <div class="hero">
      <div style="flex:1">
        
          <h2 id="project-overview">Project overview</h2>
          <p>
            This project was initiated as an exploration of GitHub Copilot’s AI-assisted coding capabilities.
            To provide a suitably complex and data-intensive domain, I selected the financial markets as the
            foundation for developing an algorithmic trading system.
          </p>
          <p>
            The primary objective of this system is not raw performance or high-frequency trading, but rather to
            <strong>demonstrate software design patterns, architectural approaches, and best practices</strong>
            in building extensible systems. The focus is on creating a solution that is
            <strong>modular, maintainable, and scalable</strong>, with the flexibility to be deployed across any
            major cloud provider.
          </p>
          <h2 id="disclaimer">Disclaimer</h2>
          <p class="disclaimer">
            This project makes extensive use of GitHub Copilot for code generation and assistance. The code is
            provided strictly for <strong>educational and illustrative purposes</strong>. No guarantees are made
            regarding its accuracy, reliability, or suitability for production use.
          </p>
        <div class="actions">
          <a class="btn primary" href="https://github.com/hosercoder" target="_blank" rel="noopener">View GitHub Profile</a>
          <a class="btn primary" href="https://www.linkedin.com/in/mathewromstadt/" target="_blank" rel="noopener">LinkedIn Profile</a>
          <a class="btn" href="#modules">System Modules</a>
          <a class="btn" href="#goals">Design Goals</a>
          <a class="btn" href="#resume">Resume Highlights</a>
        </div>
      </div>
    </div>

    <section id="modules" class="card" style="margin-top:26px">
      <h2>System modules</h2>
      <p class="note">Modular NuGet packages and client systems organized for maximum reusability and separation of concerns.</p>
      <div class="arch" style="align-items: flex-start;">
        <div class="card" style="height: 100%;">
          <h3>Core System — NuGet Packages</h3>
          <div style="display: grid; gap: 12px;">
            <div class="note success" style="padding: 12px;">
              <h4 style="margin: 0 0 8px 0;">Strategy Builder</h4>
              <div style="margin: 4px 0 8px 0;">
                <span class="chip">.NET 8.0</span>
                <span class="chip">xunit</span>
              </div>
              <p>Status: Feature Complete (Pending Refinement)</p>
              <p style="margin: 0 0 8px 0; font-size: 14px;">Framework for creating and configuring trading strategies</p>
              <div style="display: flex; gap: 8px;">
                <a class="btn" href="https://github.com/hosercoder/StrategyBuilder" target="_blank" rel="noopener" style="font-size: 12px; padding: 6px 10px;">GitHub</a>
                <a class="btn" href="./Diagrams/StrategybuilderDiagram.png" style="font-size: 12px; padding: 6px 10px;">Architecture</a>
              </div>
            </div>
            <div class="note success" style="padding: 12px;">
              <h4 style="margin: 0 0 8px 0;">TechnicalCalculators</h4>
              <div style="margin: 4px 0 8px 0;">
                <span class="chip">.NET 8.0</span>
                <span class="chip">TALib.NETCore</span>
                <span class="chip">xunit</span>
              </div>
              <p>Status: Feature Complete (Pending Refinement)</p>
              <p style="margin: 0 0 8px 0; font-size: 14px;">Technical indicator calculations and market analysis tools</p>
              <div style="display: flex; gap: 8px;">
                <a class="btn" href="https://github.com/hosercoder/TechnicalCalculators" target="_blank" rel="noopener" style="font-size: 12px; padding: 6px 10px;">GitHub</a>
                <a class="btn" href="./Diagrams/technicalCalculatorDiagram.png" target="_blank" rel="noopener" style="font-size: 12px; padding: 6px 10px;">Architecture</a>
              </div>
            </div>
            <div class="note warning" style="padding: 12px;">
              <h4 style="margin: 0 0 8px 0;">Common</h4>
                <div style="margin: 4px 0 8px 0;">
                  <span class="chip">.NET 8.0</span>
              </div>
              <p>Status: In Development</p>
              <p style="margin: 0 0 8px 0; font-size: 14px;">Shared infrastructure components</p>
              <div style="margin: 8px 0 8px 0;">
                <div style="margin: 4px 0; padding-left: 12px; border-left: 2px solid var(--border);">
                  <strong style="font-size: 13px;">Models:</strong> <span style="font-size: 13px;">Domain entities and data structures</span>
                </div>
                <div style="margin: 4px 0; padding-left: 12px; border-left: 2px solid var(--border);">
                  <strong style="font-size: 13px;">Data:</strong> <span style="font-size: 13px;">Data access layer and repository patterns</span>
                </div>
              </div>
              <div style="display: flex; gap: 8px;">
                <a class="btn" href="https://github.com/hosercoder/Common" target="_blank" rel="noopener" style="font-size: 12px; padding: 6px 10px;">GitHub</a>
              </div>
            </div>
          </div>
        </div>
        <div class="card" style="height: 100%;">
          <h3>Executable Systems (containers)</h3>
          <div style="display: grid; gap: 12px;">
            <div class="note warning" style="padding: 12px;">
              <h4 style="margin: 0 0 8px 0;">Strategy Tester</h4>
              <p>Status: In Development</p>
              <p style="margin: 0 0 8px 0; font-size: 14px;">Interactive application for backtesting and validating trading strategies</p>
              <div style="display: flex; gap: 8px;">
                <a class="btn" href="" target="_blank" rel="noopener" style="font-size: 12px; padding: 6px 10px;">GitHub</a>
                <a class="btn" href="" style="font-size: 12px; padding: 6px 10px;">Architecture</a>
              </div>
            </div>
            <div class="note" style="padding: 12px;">
              <h4 style="margin: 0 0 8px 0;">Trade Analyzer</h4>
              <p>Status: In Planning</p>
              <p style="margin: 0 0 8px 0; font-size: 14px;">Using ML to analyze trades for optimum performance, and recommend strategy adjustments as needed.</p>
              <div style="display: flex; gap: 8px;">
                <a class="btn" href="" target="_blank" rel="noopener" style="font-size: 12px; padding: 6px 10px;">GitHub</a>
                <a class="btn" href="" style="font-size: 12px; padding: 6px 10px;">Architecture</a>
              </div>
            </div>
            <div class="note" style="padding: 12px;">
              <h4 style="margin: 0 0 8px 0;">Market Analyzer</h4>
              <p>Status: In Planning</p>
              <p style="margin: 0 0 8px 0; font-size: 14px;">System that will use ML to analyze the markets looking for patterns and correlations</p>
              <div style="display: flex; gap: 8px;">
                <a class="btn" href="" target="_blank" rel="noopener" style="font-size: 12px; padding: 6px 10px;">GitHub</a>
                <a class="btn" href="" style="font-size: 12px; padding: 6px 10px;">Architecture</a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="goals" class="card" style="margin-top:26px">
      <h2>Project Design Goals</h2>
      <div class="card" style="margin-top:16px">
        <h3>Multi‑Cloud, Multi‑Tenant Architecture</h3>
        <p>Our system is being designed as a multi‑cloud, multi‑tenant platform, capable of securely hosting multiple tenants while distributing workloads across different cloud providers. This approach ensures that the platform is not tied to a single vendor, while also improving resilience and flexibility.</p>
        <div class="arch">
          <div class="card">
            <h4 style="color: var(--accent-2); margin-bottom: 12px;">Benefits</h4>
            <ul class="list">
              <li><strong>Resiliency & Uptime:</strong> Reduces risk of outages by leveraging multiple providers.</li>
              <li><strong>Cost & Performance Optimization:</strong> Ability to select the most efficient services from each cloud.</li>
              <li><strong>Regulatory Flexibility:</strong> Supports compliance with regional data residency and governance requirements.</li>
              <li><strong>Scalability:</strong> Tenants can be onboarded and scaled independently across providers.</li>
            </ul>
          </div>
          <div class="card">
            <h4 style="color: var(--danger); margin-bottom: 12px;">Considerations</h4>
            <ul class="list">
              <li><strong>Increased Complexity:</strong> Requires consistent identity, monitoring, and governance across environments.</li>
              <li><strong>Operational Overhead:</strong> Higher costs and more demanding DevOps practices to maintain portability.</li>
              <li><strong>Latency & Integration:</strong> Cross‑cloud communication can introduce performance trade‑offs.</li>
            </ul>
          </div>
        </div>
        <div class="note success" style="margin-top: 16px;">
          <h4 style="margin: 0 0 8px; color: var(--accent-2);">Goal</h4>
          <p style="margin: 0;">The architecture balances these trade‑offs by prioritizing security, scalability, and maintainability, while acknowledging the additional overhead of managing distributed infrastructure. The result is a platform that is flexible, future‑proof, and tenant‑ready.</p>
        </div>
        <div class="note warning" style="margin-top: 16px;">
            <h4 style="margin: 0 0 8px; color: #f59e0b;">The How</h4>
            <p style="margin: 0;">How do I intend to accomplish this and mitigate risk:</p>
            <ul class="list">
                <li><strong>Terraform:</strong> I intend to use Terraform for infrastructure provisioning and management, ensuring consistent and reproducible environments across cloud providers.</li>
                <li><strong>Automation:</strong> I intend to use Automation (CI/CD pipelines) to streamline the build, test, and deployment processes for NuGet packages and services.</li>
                <li><strong>Monitoring & Logging:</strong> I intend to implement robust monitoring and logging solutions to track system performance, identify issues, and ensure operational health across modules and cloud environments.</li>
                <li><strong>Resiliency:</strong> I intend to automate teardown/buildups on a regular basis to ensure system stability and availability.</li>
              </ul>
          </div>
      </div>
      <div class="card" style="margin-top:16px">
      <h3>Independent Modular Architecture</h3>
        <p>The goal of adopting an independent modular architecture is to design a system composed of loosely coupled, self‑contained modules that can be developed, deployed, and scaled independently. To achieve this, the project leverages NuGet packages as the primary distribution and integration mechanism. Each module is packaged and versioned as a NuGet library, enabling clean separation of concerns, controlled dependencies, and consistent reuse across services. This approach emphasizes extensibility, maintainability, and adaptability, ensuring that new features or services can be added without disrupting the entire system.</p>
        <div class="arch">
          <div class="card">
            <h4 style="color: var(--accent-2); margin-bottom: 12px;">Benefits</h4>
            <ul class="list">
              <li><strong>Flexibility & Extensibility:</strong> New modules can be introduced or replaced simply by publishing updated NuGet packages.</li>
              <li><strong>Scalability:</strong> Each module can scale independently, while NuGet ensures consistent dependency resolution.</li>
              <li><strong>Team Autonomy:</strong> Failures in one module are isolated, and NuGet dependency management reduces integration risks.</li>
              <li><strong>Resilience:</strong> Tenants can be onboarded and scaled independently across providers.</li>
              <li><strong>Reusability:</strong> Shared functionality (e.g., logging, compliance, or data access) can be distributed as common NuGet packages.</li>
            </ul>
          </div>
          <div class="card">
            <h4 style="color: var(--danger); margin-bottom: 12px;">Considerations</h4>
            <ul class="list">
              <li><strong>Integration Overhead:</strong> Requires strong API contracts and governance to ensure NuGet packages remain backward‑compatible.</li>
              <li><strong>Operational Complexity:</strong> Package versioning, dependency resolution, and CI/CD pipelines must be carefully managed.</li>
              <li><strong>Performance Trade‑offs:</strong> Inter‑module communication (via APIs or messaging) can introduce latency, even if modules are packaged cleanly.</li>
              <li><strong>Consistency Challenges:</strong> Maintaining data integrity and shared state across independently packaged modules can be complex.</li>
              <li><strong>Dependency Management:</strong> Without strict versioning policies, NuGet packages can introduce conflicts or “dependency hell.”</li>
            </ul>
          </div>
        </div>
        
        <div class="note success" style="margin-top: 16px;">
          <h4 style="margin: 0 0 8px; color: var(--accent-2);">Goal</h4>
          <p style="margin: 0;">Build an independent, modular architecture—delivered through NuGet packages—that is extensible, maintainable, and scalable across cloud providers, prioritizing clarity of design patterns over raw performance.</p>
        </div>
        <div class="note warning" style="margin-top: 16px;">
            <h4 style="margin: 0 0 8px; color: #f59e0b;">The How</h4>
            <p style="margin: 0;">How do I intend to accomplish this and mitigate risk:</p>
            <ul class="list">
                <li><strong>Automation:</strong> I intend to use Automation (CI/CD pipelines) to streamline the build, test, and deployment processes for NuGet packages and services.</li>
                <li><strong>Use of Fitness Functions:</strong> I intend to use Fitness Functions to validate and test the correctness of my code, ensuring that it meets the required specifications and constraints.</li>
                <li><strong>Monitoring & Logging:</strong> I intend to implement robust monitoring and logging solutions to track system performance, identify issues, and ensure operational health across modules and cloud environments.</li>
                <li><strong>Resiliency:</strong> I intend to build in chaos engineering practices to test system resilience and identify potential failure points.</li>
                <li><strong>Security:</strong> I intend to implement security best practices, including secure coding, encryption, and access controls, to protect sensitive data and systems.</li>
                <li><strong>Testing:</strong> I intend to implement comprehensive testing strategies, including unit tests, integration tests, and end-to-end tests, to ensure the reliability and correctness of the system.</li>
                <li><strong>Documentation:</strong> I intend to maintain comprehensive documentation for all modules, APIs, and processes to ensure clarity and ease of onboarding for new team members.</li>
                <li><strong>Integrations:</strong> I intend to integrate with third-party providers such as SonarQube to ensure compliance</li>
              </ul>
          </div>
      </div>
    </section>

    <section id="resume" class="card" style="margin-top:26px">
      <h2>Resume highlights</h2>
      <div class="card" style="margin-bottom: 20px;">
        <h3>Technology stack</h3>
        <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 16px; margin: 16px 0;">
          <div class="card" style="padding: 12px; text-align: center;">
            <strong style="color: var(--accent-2);">Core</strong>
            <p style="margin: 4px 0 0 0; font-size: 13px;">C#/.NET, strong typing for domain safety</p>
          </div>
          <div class="card" style="padding: 12px; text-align: center;">
            <strong style="color: var(--accent-2);">Storage</strong>
            <p style="margin: 4px 0 0 0; font-size: 13px;">Parquet/CSV for research datasets</p>
          </div>
          <div class="card" style="padding: 12px; text-align: center;">
            <strong style="color: var(--accent-2);">APIs</strong>
            <p style="margin: 4px 0 0 0; font-size: 13px;">REST/WebSocket adapters</p>
          </div>
          <div class="card" style="padding: 12px; text-align: center;">
            <strong style="color: var(--accent-2);">Testing</strong>
            <p style="margin: 4px 0 0 0; font-size: 13px;">Deterministic seeds + scenario fixtures</p>
          </div>
          <div class="card" style="padding: 12px; text-align: center;">
            <strong style="color: var(--accent-2);">Packaging</strong>
            <p style="margin: 4px 0 0 0; font-size: 13px;">NuGet for SDK distribution</p>
          </div>
          <div class="card" style="padding: 12px; text-align: center;">
            <strong style="color: var(--accent-2);">Infrastructure</strong>
            <p style="margin: 4px 0 0 0; font-size: 13px;">Docker, Kubernetes, CI/CD pipelines, Terraform</p>
          </div>
          <div class="card" style="padding: 12px; text-align: center;">
            <strong style="color: var(--accent-2);">Documentation</strong>
            <p style="margin: 4px 0 0 0; font-size: 13px;">Markdown, Mermaid diagrams</p>
          </div>
        </div>
      </div>

      <ul class="list">
        <li><strong>Architected clean interfaces:</strong> Strategies, risk, data, and execution decoupled</li>
        <li><strong>Built reproducible backtests:</strong> Deterministic runs + scenario sweeps</li>
        <li><strong>Implemented compliance overlays:</strong> Pre-trade risk, audit logs, circuit breakers</li>
        <li><strong>Designed plug-in framework:</strong> Rapid onboarding of strategies/data/venues</li>
        <li><strong>Delivered observability:</strong> Structured logs, metrics, exportable artifacts</li>
      </ul>
      <div class="actions">
        <a class="btn primary" href="https://github.com/hosercoder" target="_blank" rel="noopener">View GitHub</a>
        <a class="btn primary" href="https://www.linkedin.com/in/mathewromstadt/" target="_blank" rel="noopener">LinkedIn Profile</a>
      </div>
    </section>
    <div class="footer">
      © <span id="y"></span> Hosercoder • Extensible Algorithmic Trading System
    </div>
  </div>
  <script>
    document.getElementById('y').textContent = new Date().getFullYear();
  </script>
</body>
</html>
