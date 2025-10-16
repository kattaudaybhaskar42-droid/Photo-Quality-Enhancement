# Photo-Quality-Enhancement
Photo quality enhancement is the process of improving a digital image's appearance and visual clarity using software techniques
website: file:///C:/Users/katta%20udaybhaskar/OneDrive/Desktop/image%20enhancer%20(2).html
code: <!doctype html>
<html lang="en">

<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Modern Image Enhancer</title>
  <style>
    :root {
      --bg: #0f1724;
      --card: #0b1220;
      --muted: #94a3b8;
      --accent: #7c3aed;
      --glass: rgba(255, 255, 255, 0.04);
      --radius: 14px;
      --gap: 18px;
      --glass-border: rgba(255, 255, 255, 0.04);
    }

    * {
      box-sizing: border-box
    }

    body {
      margin: 0;
      font-family: Inter, ui-sans-serif, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
      background: linear-gradient(180deg, #071028 0%, #071323 60%);
      color: #e6eef8;
      -webkit-font-smoothing: antialiased
    }

    .container {
      max-width: 1100px;
      margin: 40px auto;
      padding: 28px
    }

    header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 18px;
      margin-bottom: 20px
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 14px
    }

    .logo {
      width: 44px;
      height: 44px;
      border-radius: 10px;
      background: linear-gradient(135deg, var(--accent), #4f46e5);
      display: flex;
      align-items: center;
      justify-content: center;
      font-weight: 700;
      color: white;
      box-shadow: 0 6px 20px rgba(124, 58, 237, 0.18)
      

    }

    h1 {
      font-size: 18px;
      margin: 0
    }

    p.lead {
      margin: 0;
      color: var(--muted);
      font-size: 13px
    }

    .grid {
      display: grid;
      grid-template-columns: 1fr 380px;
      gap: var(--gap)
    }

    /* Left card */
    .card {
      background: linear-gradient(180deg, rgba(255, 255, 255, 0.02), rgba(255, 255, 255, 0.01));
      padding: 18px;
      border-radius: var(--radius);
      box-shadow: 0 6px 22px rgba(2, 6, 23, 0.6);
      border: 1px solid var(--glass-border)
    }

    .uploader {
      display: flex;
      flex-direction: column;
      gap: 12px
    }

    .drop {
      border: 2px dashed rgba(255, 255, 255, 0.05);
      padding: 28px;
      border-radius: 12px;
      text-align: center;
      background: linear-gradient(180deg, rgba(255, 255, 255, 0.01), transparent);
      cursor: pointer
    }

    .drop.dragover {
      border-color: rgba(124, 58, 237, 0.9);
      box-shadow: 0 8px 30px rgba(124, 58, 237, 0.06)
    }

    .drop small {
      display: block;
      color: var(--muted);
      margin-top: 8px
    }

    .canvas-wrap {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 12px;
      margin-top: 14px
    }

    canvas {
      width: 100%;
      height: auto;
      border-radius: 10px;
      background: #071022
    }

    .controls {
      display: flex;
      flex-direction: column;
      gap: 12px;
      margin-top: 12px
    }

    label {
      font-size: 13px;
      color: var(--muted);
      display: flex;
      justify-content: space-between;
      align-items: center
    }

    .row {
      display: flex;
      gap: 10px;
      align-items: center
    }

    input[type=range] {
      width: 100%
    }

    select,
    input[type=file] {
      background: transparent;
      color: inherit;
      border: 1px solid rgba(255, 255, 255, 0.04);
      padding: 8px;
      border-radius: 8px
    }

    .presets {
      display: flex;
      gap: 8px;
      flex-wrap: wrap
    }

    .chip {
      padding: 8px 10px;
      border-radius: 999px;
      font-size: 13px;
      background: rgba(255, 255, 255, 0.02);
      cursor: pointer;
      border: 1px solid rgba(255, 255, 255, 0.02)
    }

    .actions {
      display: flex;
      gap: 10px;
      margin-top: 10px
    }

    button {
      background: var(--accent);
      border: none;
      color: white;
      padding: 10px 14px;
      border-radius: 10px;
      cursor: pointer;
      font-weight: 600;
      box-shadow: 0 8px 24px rgba(124, 58, 237, 0.12)
    }

    button.ghost {
      background: transparent;
      border: 1px solid rgba(255, 255, 255, 0.06);
      box-shadow: none
    }

    /* Right panel */
    .sidebar {
      position: sticky;
      top: 28px;
      height: fit-content
    }

    .meta {
      display: flex;
      flex-direction: column;
      gap: 8px
    }

    .meta .stat {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 12px;
      background: linear-gradient(180deg, rgba(255, 255, 255, 0.01), transparent);
      border-radius: 10px
    }

    .muted {
      color: var(--muted);
      font-size: 13px
    }

    footer {
      margin-top: 18px;
      color: var(--muted);
      font-size: 13px;
      text-align: center
    }

    @media (max-width:980px) {
      .grid {
        grid-template-columns: 1fr;
      }

      .container {
        padding: 18px
      }
    }
  </style>
</head>

<body>
  <div class="container">
    <header>
      <div class="brand">
        <div class="logo">IE</div>
        <div>
          <h1>Image Enhancer</h1>
          <p class="lead">Modern, fast, and privacy-first — enhance images right in your browser.</p>
        </div>
      </div>
      <div class="actions">
        <button id="downloadBtn" class="ghost" title="Download edited image">Download</button>
        <button id="resetBtn" class="ghost">Reset</button>
      </div>
    </header>

    <main class="grid">
      <section class="card">
        <div class="uploader">
          <div id="drop" class="drop">
            <div style="font-size:15px;font-weight:600">Drag & Drop or Click to Upload</div>
            <small>PNG, JPG up to 12MB — everything stays local.</small>
            <input id="file" type="file" accept="image/*" style="display:none">
          </div>

          <div class="canvas-wrap">
            <div>
              <div style="font-size:13px;margin-bottom:8px;color:var(--muted)">Before <img
                  src="C:\Users\katta udaybhaskar\OneDrive\Desktop\old photo .jpg" alt="Before Enhancement" width="400" height="400"></div>
              <canvas id="original" width=auto height=auto></canvas>
            </div>

            <div>
              <div style="font-size:13px;margin-bottom:8px;color:var(--muted)">After<img
                  src="C:\Users\katta udaybhaskar\OneDrive\Desktop\Scaled up photo.jpg" alt="After Enhancement"width="400" height="400">

              </div>
              <canvas id="result" width=auto height=auto></canvas>
            </div>
          </div>

          <div class="controls">
            <label>Brightness <span id="valB
