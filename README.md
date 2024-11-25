# Cecyber

Segue abaixo uma nova versão da solução, formatada como uma proposta para o cliente, incluindo um diagrama em formato **Mermaid**.

---

**Proposta de Solução para Iniciar e Acessar Máquinas Virtuais no Proxmox via Frontend**

---

### **Fluxo da Solução**

1. **Iniciar a Máquina Virtual via API:**
   - Sua aplicação frontend enviará uma solicitação para a API do Proxmox VE solicitando o início da VM específica.
   - Para segurança, será utilizado um token de API gerado previamente e armazenado em um ambiente seguro.

2. **Obter Ticket VNC e Porta de Comunicação:**
   - Após iniciar a VM, a aplicação requisitará à API um ticket temporário e a porta correspondente para o acesso remoto via VNC.

3. **Estabelecer Conexão com noVNC:**
   - Com o ticket gerado, o frontend carregará o cliente noVNC embutido no navegador e configurará a conexão com a VM por meio do WebSocket disponibilizado pelo Proxmox.

4. **Interação Remota pelo Navegador:**
   - O cliente final poderá acessar a interface gráfica da VM diretamente no navegador, interagindo em tempo real com o sistema operacional ou a aplicação hospedada.

---

### **Diagrama de Funcionamento**

<div class="mermaid">
graph TD
    A[Usuário no Browser] --> B[Frontend App]
    B --> C[Proxmox API]
    C --> D[Inicia VM no Proxmox]
    D --> E[Proxmox Hypervisor]
    E --> F[VM Iniciada]
    F --> G[Proxmox API - Ticket VNC]
    G --> H[Frontend noVNC Cliente]
    H --> I[WebSocket para VM]
    I --> J[Interação Remota na VM]
</div>

---

### **Monitoramento das Máquinas Virtuais**

**Backend:**
- O backend realizará requisições periódicas à API do Proxmox para obter métricas de desempenho das máquinas virtuais.

**Frontend:**
- Exibe essas métricas em painéis interativos, permitindo ao usuário monitorar o desempenho das VMs em tempo real.

---

### **Diagrama de Funcionamento**

<div class="mermaid">
graph TD
    A[Usuário no Browser] --> B[Frontend App]
    B --> C[Proxmox API]
    C --> D[Inicia VM no Proxmox]
    D --> E[Proxmox Hypervisor]
    E --> F[VM Iniciada]
    F --> G[Proxmox API - Ticket VNC]
    G --> H[Frontend noVNC Cliente]
    H --> I[WebSocket para VM]
    I --> J[Interação Remota na VM]
    E --> K[Proxmox API - Métricas de Monitoramento]
    K --> L[Backend - Coleta de Métricas]
    L --> M[Frontend - Painel de Monitoramento]
    M --> A
</div>

---

### **Configuração do Script do Mermaid**

Adicione o seguinte script ao cabeçalho do seu `README.md` ou página no GitHub Pages:

```html
<script src="https://cdn.jsdelivr.net/npm/mermaid/dist/mermaid.min.js"></script>
<script>
    mermaid.initialize({ startOnLoad: true });
</script>
