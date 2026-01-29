<script lang="ts">
  let code = $state("console.log('Hello!');\nconsole.log(2 + 2);");
  let output = $state("");

  function runCode() {
    output = "";
    const logs: string[] = [];
    const originalLog = console.log;
    const originalError = console.error;

    // Override global console.log
    console.log = (...args) => {
      logs.push(args.map(a => typeof a === 'object' ? JSON.stringify(a, null, 2) : String(a)).join(' '));
      originalLog.apply(console, args);
    };

    console.error = (...args) => {
      logs.push("ERROR: " + args.map(a => String(a)).join(' '));
      originalError.apply(console, args);
    };

    try {
      new Function(code)(); // Execute
    } catch (err) {
      console.error(err);
    } finally {
      console.log = originalLog;
      console.error = originalError;
      output = logs.join('\n');
    }
  }
</script>

<div class="playground">
  <div class="header">
    <h3>JS Playground</h3>
    <button onclick={runCode}>▶ Run</button>
  </div>

  <div class="editor-container">
    <textarea bind:value={code} spellcheck="false"></textarea>
  </div>

  <div class="console">
    <div class="console-label">Output</div>
    <pre>{output || "Ready..."}</pre>
  </div>
</div>

<style>
  .playground {
    display: flex;
    flex-direction: column;
    height: 500px;
    border: 1px solid #ccc;
    border-radius: 8px;
    overflow: hidden;
    font-family: monospace;
    position: relative;
  }

  .header {
    height: 50px;
    background: #f5f5f5;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 1rem;
    border-bottom: 1px solid #ccc;
    position: absolute;
    top: 0; width: 100%; box-sizing: border-box;
  }

  button {
    background: #f7df1e;
    border: none;
    padding: 6px 12px;
    border-radius: 4px;
    cursor: pointer;
    font-weight: bold;
  }

  .editor-container {
    flex: 1;
    margin-top: 50px; 
    display: flex;
  }

  textarea {
    flex: 1;
    padding: 1rem;
    border: none;
    resize: none;
    outline: none;
    font-family: inherit;
    color: #333
  }

  .console {
    height: 150px;
    background: #1e1e1e;
    color: #0f0;
    display: flex;
    flex-direction: column;
    z-index: 10;
  }

  .console-label {
    background: #333;
    color: #ccc;
    font-size: 0.8rem;
    padding: 4px 8px;
  }

  pre {
    margin: 0;
    padding: 1rem;
    overflow: auto;
    white-space: pre-wrap;
  }
</style>
