# Investigação de Tráfego de Rede com Wireshark 

![Wireshark](https://img.shields.io/badge/WIRESHARK-1679A7?style=for-the-badge&logo=wireshark&logoColor=white)
![CyberChef](https://img.shields.io/badge/CYBERCHEF-A020F0?style=for-the-badge)
![Wireshark Display Filter](https://img.shields.io/badge/WIRESHARK%20DISPLAY%20FILTERS-000000?style=for-the-badge&logo=wireshark&logoColor=white)
![Linux](https://img.shields.io/badge/LINUX-FCC624?style=for-the-badge&logo=linux&logoColor=black)

Este laboratório prático foi desenvolvido com base no desafio oficial [Web Investigation (BookWorld)](https://cyberdefenders.org/blueteam-ctf-challenges/web-investigation/) da plataforma **CyberDefenders** 
A resolução teve como foco a aplicação de competências reais de Blue Team e Operações de Segurança (SOC), através de técnicas de Network e investigação de incidentes.

---

### Visão Geral

- **Descoberta da brecha no site:** Identificação do computador do invasor a testar o campo de pesquisa da loja para encontrar falhas
- **Visualização da base de dados:** Uso de uma ferramenta automática para listar as bases de dados e tabelas do sistema
- **Roubo de dados dos clientes:** Cópia de dados pessoais confidenciais dos utilizadores registados na loja.
- **Busca por páginas escondidas:** Varrimento de pastas até encontrar a área restrita do painel administrativo
- **Acesso de administrador e controlo:** Entrada com a palavra-passe correta no sistema e navegação na pasta de uploads para preparação de ficheiros

---

### Laboratório e Preparação

Para a execução da análise, utilizou-se o **Wireshark** para inspeção e filtragem do ficheiro de captura de tráfego (`WebInvestigation.pcap`)

- Abertura do ficheiro `.pcap` no Wireshark para isolamento dos pacotes HTTP e TCP
- Aplicação de filtros de exibição (*Display Filters*) baseados em métodos (`GET`, `POST`) e códigos de status
- Reconstituição de sessões completas através do recurso **Follow > HTTP Stream**
- Análise e validação dos dados exfiltrados e requisições suspeitas

---

### 1. Identificação do IP do Atacante e Endpoint Vulnerável

Identificação do IP de origem que gerou requisições suspeitas no endpoint de busca da aplicação web.

<img width="1064" height="657" alt="cyb1;1" src="https://github.com/user-attachments/assets/86104df3-2c6f-41f6-aceb-cceec9c9ca49" />

---

### 2. Leitura dos Esquemas do Banco (SQL Injection)

Deteção de injeção SQL automatizada via ferramenta ofensiva para enumerar as bases de dados do sistema[cite: 1, 5].

<img width="1071" height="649" alt="cyb2" src="https://github.com/user-attachments/assets/4c4f35ba-3681-45db-ae39-44e74a9d0d59" />

---

### 3. Exfiltração de Dados dos Clientes

Localização da tabela com dados sensíveis de clientes e identificação do conteúdo devolvido na resposta do servidor

<img width="772" height="587" alt="cyb3" src="https://github.com/user-attachments/assets/707ccfc3-ca45-4a84-a514-1cebe90171b2" />

---

### 4. Enumeração e Acesso ao Diretório Oculto

Identificação do varrimento de pastas via força bruta até à localização da rota restrita do painel[cite: 2].

<img width="1083" height="644" alt="cyb4" src="https://github.com/user-attachments/assets/16f4c069-1d99-455c-a85b-c84d274e545c" />

---

### 5. Comprometimento de Credenciais Administrativas

Identificação do momento exato em que o invasor realiza a autenticação com credenciais válidas no painel de login

<img width="789" height="623" alt="cyb6" src="https://github.com/user-attachments/assets/4d928ad9-5c3c-4939-a7b2-52549054f2e4" />

---

### 6. Acesso aos Uploads

Após aceder ao painel administrativo, o atacante navega até à pasta de transferências (`/admin/uploads/`) para preparar a inclusão e execução de artefactos no servidor[cite: 15].

<img width="787" height="626" alt="cyb7" src="https://github.com/user-attachments/assets/7a03c33f-a36f-4e21-8ec9-739ea9d61e81" />


---

### Conclusão

Nesta investigação prática, foi possível atingir os seguintes resultados:

- Mapeamento completo desde o conhecimento ate a cadeia de ataque (*Cyber Kill Chain*)
- Identificação precisa dos Indicadores de Comprometimento, como IPs de origem, endpoints explorados e tabelas acedidas
- Reconstrução de fluxos HTTP para verificar requisições POST, respostas do servidor e pastas 
- Desenvolvimento prático de competências em análise de pacotes (*PCAP analysis*) e filtragem no Wireshark

---

@2026 Gisele Alencar
