<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Compra de Coins - Brasil RP</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-900 text-white">

  <!-- Logo Centralizada -->
  <div class="flex justify-center mt-6">
    <a href="https://ibb.co/j9vGGxj4">
      <img src="https://i.ibb.co/j9vGGxj4/file-00000000543461f78e1bacee51ce7350.png" alt="Logo JC RP" class="w-32 h-auto">
    </a>
  </div>

  <!-- Horário de Brasília -->
  <div class="text-center mt-2 text-purple-400 font-mono text-sm">
    <span id="brTime"></span>
  </div>

  <!-- Etapa 1: Dados Pessoais -->
  <div id="step1" class="p-6 max-w-md mx-auto">
    <h2 class="text-2xl font-bold mb-4 text-purple-400">DADOS PESSOAIS</h2>

    <input type="text" placeholder="Nome completo" class="w-full p-2 border border-purple-500 bg-gray-800 rounded mb-2" required>
    <input type="email" placeholder="E-mail" class="w-full p-2 border border-purple-500 bg-gray-800 rounded mb-2" required>
    <input type="text" placeholder="CPF" class="w-full p-2 border border-purple-500 bg-gray-800 rounded mb-2" required>
    <input type="tel" placeholder="(00) 00000-0000" class="w-full p-2 border border-purple-500 bg-gray-800 rounded mb-4" maxlength="15" required>

    <button onclick="nextStep()" class="w-full bg-purple-600 hover:bg-purple-700 text-white font-bold py-2 rounded">Próximo</button>
  </div>

  <!-- Etapa 2: Dados da Conta -->
  <div id="step2" class="p-6 max-w-md mx-auto hidden">
    <h2 class="text-2xl font-bold mb-4 text-purple-400">DADOS DA COMPRA</h2>

    <select class="w-full p-2 border border-purple-500 bg-gray-800 rounded mb-4 text-white">
      <option selected>JC RP 1</option>
    </select>

    <input type="text" placeholder="Nome de usuário (Nick)" class="w-full p-2 border border-purple-500 bg-gray-800 rounded mb-2">
    <input type="text" placeholder="ID da conta" class="w-full p-2 border border-purple-500 bg-gray-800 rounded mb-2">

    <!-- Quantidade de Coins -->
    <label class="block mb-2 text-purple-300 font-semibold">Quantidade de Coins</label>
    <input id="coinQty" type="number" value="1" min="1" class="w-full p-2 border border-purple-500 bg-gray-800 text-white rounded mb-2" oninput="updateValue()">

    <!-- Valor aparece só quando digitar -->
    <p id="coinValue" class="text-purple-400 font-medium mb-4 hidden">Valor: R$ <span id="valueDisplay"></span></p>

    <button class="w-full bg-purple-600 hover:bg-purple-700 text-white font-bold py-2 rounded">Finalizar</button>
  </div>

  <script>
    function nextStep() {
      document.getElementById('step1').classList.add('hidden');
      document.getElementById('step2').classList.remove('hidden');
    }

    function updateValue() {
      const qty = document.getElementById('coinQty').value;
      const value = qty * 1;
      document.getElementById('valueDisplay').innerText = value.toFixed(2).replace('.', ',');
      document.getElementById('coinValue').classList.remove('hidden');
    }

    function updateBrasiliaTime() {
      const now = new Date();
      const options = {
        timeZone: 'America/Sao_Paulo',
        hour: '2-digit',
        minute: '2-digit',
        second: '2-digit'
      };
      document.getElementById('brTime').textContent =
        `Horário de Brasília: ${now.toLocaleTimeString('pt-BR', options)}`;
    }

    setInterval(updateBrasiliaTime, 1000);
    updateBrasiliaTime();
  </script>

</body>
</html>
