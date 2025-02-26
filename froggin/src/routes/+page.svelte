<script>
  let inputText = "";
  let frogginText = "";
  
  const frogginMap = {
    'A': '🐸🐔🐟🦒', 'Á': '🐸🐔🦈🦒🦌', 'B': '🐔🐸🦈🦒', 'C': '🐸🐔🦈🦒', 'D': '🐔🐔🦈🦒',
    'E': '🐷🦈🐸🦒', 'É': '🐷🦈🐸🦒🦌', 'F': '🦈🐷🐸🦒', 'G': '🐷🐷🐸🦒', 'H': '🦈🦈🐸🦒',
    'I': '🐸🐷🐔🦒', 'Í': '🐸🐷🐔🦒🦌', 'J': '🐔🦈🐷🦒', 'K': '🐸🦈🐔🦒', 'L': '🐔🐷🦈🦒',
    'M': '🐷🐸🐔🦒', 'N': '🦈🐔🐸🦒', 'Ñ': '🦈🐔🐸🦒🦌', 'O': '🐷🦈🐸🐔🦒', 'Ó': '🐷🦈🐸🐔🦒🦌',
    'P': '🦈🐸🐷🐔🦒', 'Q': '🐸🐔🐷🦈🦒', 'R': '🐔🐸🦈🐷🦒', 'S': '🐸🐔🦈🐷🦒', 'T': '🐔🐸🐷🦈🦒',
    'U': '🦈🐷🐸🐔🦒', 'Ú': '🦈🐷🐸🐔🦒🦌', 'Ü':'🦈🐷🐸🐔🦒🦤','V': '🐷🦈🐔🐸🦒', 'W': '🐸🐷🐔🦈🦒', 'X': '🐔🦈🐷🐸🦒',
    'Y': '🐷🐸🐔🦈🦒', 'Z': '🦈🐔🐸🐷🦒',
    'a': '🐸🐔🐟', 'á': '🐸🐔🦈🦌', 'b': '🐔🐸🦈', 'c': '🐸🐔🦈', 'd': '🐔🐔🦈',
    'e': '🐷🦈🐸', 'é': '🐷🦈🐸🦌', 'f': '🦈🐷🐸', 'g': '🐷🐷🐸', 'h': '🦈🦈🐸',
    'i': '🐸🐷🐔', 'í': '🐸🐷🐔🦌', 'j': '🐔🦈🐷', 'k': '🐸🦈🐔', 'l': '🐔🐷🦈',
    'm': '🐷🐸🐔', 'n': '🦈🐔🐸', 'ñ': '🦈🐔🐸🦌', 'o': '🐷🦈🐸🐔', 'ó': '🐷🦈🐸🐔🦌',
    'p': '🦈🐸🐷🐔', 'q': '🐸🐔🐷🦈', 'r': '🐔🐸🦈🐷', 's': '🐸🐔🦈🐷', 't': '🐔🐸🐷🦈',
    'u': '🦈🐷🐸🐔', 'ú': '🦈🐷🐸🐔🦌', 'ü':'🦈🐷🐸🐔🦤','v': '🐷🦈🐔🐸', 'w': '🐸🐷🐔🦈', 'x': '🐔🦈🐷🐸',
    'y': '🐷🐸🐔🦈', 'z': '🦈🐔🐸🐷', ' ': '|', 
    '.': '🐴', ',': '🦄', '!': '🐎', '?': '🫏', ':': '🦌', ';': '🦬',
    '@': '🐴🐴', '#': '🦄🦄', '$': '🐎🐎', '%': '🫏🫏', '&': '🦌🦌',
    '^': '🦬🦬', '*': '🐴🦄', '(': '🐎🫏', ')': '🦌🦬', '{': '🐴🐎',
    '}': '🫏🦄', '[': '🦌🐎', ']': '🦬🐴', '<': '🐴🦬', '>': '🦄🫏',
    '"': '🦌🐴', "'": '🫏🐎', '`': '🦬🦄', '~': '🐴🦌',
    '0': '🦤', '1': '🐸', '2': '🐸🐸', '3': '🐸🐸🐸', '4': '🐸🐸🐸🐸',
    '5': '🐸🐸🐸🐸🐸', '6': '🐸🐸🐸🐸🐸🐸', '7': '🐸🐸🐸🐸🐸🐸🐸', '8': '🐸🐸🐸🐸🐸🐸🐸🐸', '9': '🐸🐸🐸🐸🐸🐸🐸🐸🐸'
  };
  
  const letterSeparator = '🐘';
  const reversedMap = Object.fromEntries(
    Object.entries(frogginMap).map(([k, v]) => [v, k])
  );
  
  function textToFroggin(text) {
    return text.split('').map(char => frogginMap[char] || char).join(letterSeparator);
  }
  
  function frogginToText(froggin) {
    let words = froggin.trim().split(letterSeparator);
    let decoded = words.map(code => reversedMap[code] ?? code).join('');
    decoded = decoded.replace(/\|/g, ' '); // Restore spaces correctly
    return decoded;
  }
  
  function translateToFroggin() {
    frogginText = textToFroggin(inputText);
  }
  
  function translateToText() {
    inputText = frogginToText(frogginText);
  }
  </script>
    
 <div class="flex flex-col items-center justify-center h-screen bg-gray-100 p-4">
    <div class="bg-white p-6 rounded-xl shadow-lg w-full max-w-md">
      <h2 class="text-2xl font-bold text-center text-gray-800 mb-4">Froggin Translator</h2>
      
      <textarea
        bind:value={inputText}
        class="w-full p-3 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500"
        rows="3"
        placeholder="Enter text..."
      ></textarea>
  
      <button 
        class="w-full bg-blue-500 hover:bg-blue-600 text-white font-bold py-2 px-4 rounded-md mt-3 transition"
        on:click={translateToFroggin}
      >
        Translate to Froggin
      </button>
  
      <textarea
        bind:value={frogginText}
        class="w-full p-3 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500 mt-3"
        rows="3"
        placeholder="Froggin output..."
      ></textarea>
  
      <button 
        class="w-full bg-green-500 hover:bg-green-600 text-white font-bold py-2 px-4 rounded-md mt-3 transition"
        on:click={translateToText}
      >
        Translate to Text
      </button>
    </div>
  </div>
  