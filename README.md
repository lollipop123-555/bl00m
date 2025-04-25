# bl00m
cool guy



<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>BL00M Cipher Decoder</title>
  <style>
    body {
      font-family: monospace;
      background: #111;
      color: #0f0;
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 40px;
    }
    textarea, input {
      background: #000;
      color: #0f0;
      border: 1px solid #0f0;
      padding: 10px;
      margin: 10px 0;
      width: 90%;
      max-width: 600px;
    }
    button {
      padding: 10px 20px;
      background: #0f0;
      color: #000;
      font-weight: bold;
      border: none;
      cursor: pointer;
    }
    .output {
      margin-top: 20px;
      white-space: pre-wrap;
    }
  </style>
</head>
<body>
  <h1>BL00M Cipher Decoder</h1>
  <textarea id="cipherInput" rows="5" placeholder="Enter your code (e.g. 65 3 171 999 68 0 0 13 3 19)"></textarea>
  <button onclick="decodeMessage()">Decode</button>
  <div class="output" id="output"></div>  <script>
    const cipherMap = {
      '4': 'A', '13': 'B', '6': 'C', '19': 'D', '3': 'E', '7': 'F',
      '65': 'G', '11': 'H', '1': 'I', '23': 'J', '177': 'K', '17': 'L',
      '69': 'M', '68': 'N', '0': 'O', '9': 'P', '01': 'Q', '16': 'R',
      '33': 'S', '171': 'T', '96': 'U', '77': 'V', '363': 'W', '76': 'X',
      '7777': 'Y', '787': 'Z',

      // Advanced rules
      '888': '[Laugh]', '666': '[Anger]', '314': '[Chill]', '70': '[Respect]',
      '999': ' ', '404': '[Fake]', '212': '[REVERSE]'
    };

    function decodeMessage() {
      const input = document.getElementById("cipherInput").value.trim();
      const parts = input.split(/\s+/);
      let output = "";
      let reverse = false;

      if (parts[0] === '212') {
        reverse = true;
        parts.shift();
      }

      if (reverse) parts.reverse();

      for (let i = 0; i < parts.length; i++) {
        const current = parts[i];
        const next = parts[i + 1] || '';

        // Handle special doubles
        if (current === next) {
          if (current === '3') {
            output += 'S';
          } else if (current === '0') {
            output += ' ';
          } else if (current === '1') {
            output += '!';
          } else if (current === '7') {
            output += '?';
          }
          i++; // Skip next one
        } else {
          output += cipherMap[current] || `[${current}]`;
        }
      }

      document.getElementById("output").textContent = output;
    }
  </script></body>
</html>
