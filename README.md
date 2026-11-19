# Para Onde Vai? — Protótipo Interativo de Educação Fiscal

> Protótipo funcional de alta fidelidade desenvolvido para a disciplina de **Interação Humano-Computador (IHC / HCI)**, com foco em visualização clara de dados tributários em notas fiscais ao consumidor (NFC-e) e educação fiscal simplificada.

🔗 **Acesse a demonstração ao vivo:** `https://nchorafa.github.io/para-onde-vai/`

---

## 🎯 Problema e Objetivo

A carga tributária sobre o consumo no Brasil (como ICMS, PIS e COFINS) é embutida no preço final dos produtos e muitas vezes passa despercebida pelo cidadão comum. O aplicativo **Para Onde Vai?** busca traduzir dados fiscais complexos em informações visuais simples e cotidianas, permitindo que o usuário entenda:
1. Quanto do valor pago em uma compra corresponde ao produto líquido e quanto vai para impostos.
2. Quais tributos incidem sobre a nota (esfera estadual vs. federal).
3. Como esses recursos são distribuídos em áreas públicas essenciais (Saúde, Educação, Infraestrutura e Segurança).

---

## 🧠 Decisões de Design e Princípios de IHC

O protótipo foi projetado como um aplicativo *mobile-first* (`max-width: 430px` centralizado em telas desktop)[cite: 1] aplicando conceitos fundamentais de usabilidade:

* **Arquitetura de Informação e Navegação:** Barra de navegação inferior fixa (*Bottom Navigation*) com 4 seções principais acompanhadas de ícones e rótulos textuais claros (*Escanear*, *Nota*, *Destino*, *Aprenda*), reduzindo a carga cognitiva e facilitando o alcance com o polegar em dispositivos móveis.
* **Feedback Visual e Affordance:**
  * Ilustração interativa na tela de login cujas pupilas acompanham o movimento do cursor ou toque do usuário;
  * Barra proporcional animada (`73%` vs. `27%`) para comparação imediata entre o valor líquido do produto e os tributos;
  * Barras de progresso animadas na tela de destinação dos recursos[cite: 1] e notificações temporárias (*toasts*) para status de leitura;
* **Prevenção e Recuperação de Erros:**
  * Validação imediata no formulário de login e na entrada da chave de acesso de 44 dígitos;
  * Caso o dispositivo não possua câmera ou o navegador não suporte a API `BarcodeDetector`, o sistema oferece entrada manual da chave numérica e um atalho de **"Usar nota de exemplo"** para garantir que o fluxo principal possa ser testado sem barreiras;
* **Linguagem Centrada no Usuário:** Substituição de jargões contábeis por explicações diretas, apoiadas por uma aba dedicada de FAQ em formato acordeão (*progressive disclosure*) para não sobrecarregar a tela;
* **Persistência de Estado:** Uso de `localStorage` para manter a sessão do usuário e o histórico de notas consultadas entre recarregamentos da página;

---

## 📱 Funcionalidades do Protótipo

1. **Autenticação Simulada:** Tela de boas-vindas com validação básica de campos (aceita qualquer login e senha com 4 ou mais caracteres);
2. **Leitura e Consulta de NFC-e:**
   * Leitura de QR Code via câmera traseira do dispositivo (`navigator.mediaDevices` + `BarcodeDetector`);
   * Inserção manual da chave de acesso de 44 dígitos;
   * Modo demonstração com geração instantânea de nota fictícia (`Usar nota de exemplo`);
   * Histórico de notas recentes acessíveis com um toque;
3. **Detalhamento Tributário:** Exibição do estabelecimento, CNPJ, data/hora, divisão percentual entre produto e imposto, e separação entre **ICMS (Estadual - 18%)** e **PIS/COFINS (Federal - 9%)**;
4. **Destinação Estimada:** Simulação visual da distribuição do imposto arrecadado entre Saúde Pública, Educação, Infraestrutura Urbana e Segurança;
5. **Educação Fiscal (Aprenda):** Cartões explicativos e seção de Perguntas Frequentes (FAQ) interativa;

---

## 🛠️ Tecnologias Utilizadas

O protótipo foi construído em um único arquivo estático (*single-file prototype*) sem dependências externas pesadas, facilitando a hospedagem e portabilidade[cite: 1]:

* **HTML5 Semântico** com suporte a `viewport-fit=cover` para telas móveis modernas;
* **CSS3** com variáveis customizadas (`:root`), Flexbox, CSS Grid, transições suaves e suporte a `prefers-color-scheme`;
* **JavaScript (Vanilla ES6+)** para gerenciamento de estado, roteamento de telas, manipulação do DOM, `Web Storage API` (`localStorage`) e `MediaDevices / BarcodeDetector API`;

---

## 🚀 Como Executar Localmente

1. Clone este repositório ou baixe o arquivo `index.html`.
2. Abra o arquivo `index.html` diretamente em qualquer navegador moderno (Chrome, Edge, Safari, Firefox).
   * *Nota:* Para testar a funcionalidade de acesso à câmera em dispositivos móveis, recomenda-se acessar via link HTTPS hospedado (como o link do GitHub Pages acima).

---

> **Aviso:** Os percentuais tributários (ICMS 18% e PIS/COFINS 9%) e a distribuição por áreas públicas utilizados neste protótipo são valores ilustrativos para fins acadêmicos e educativos;
