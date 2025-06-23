# 📝 Formata-ABNT
**`Editor de Texto com Formatação ABNT`**

Editor web para formatação automática de documentos acadêmicos seguindo normas ABNT. Usa TinyMCE como base e aplica estilos padronizados com um clique.

<p align="left">
    <img alt="Vue.js" src="https://img.shields.io/badge/Vue.js-4FC08D?style=for-the-badge&logo=vue.js&logoColor=white"/>
    <img alt="TinyMCE" src="https://img.shields.io/badge/TinyMCE-2D2D2D?style=for-the-badge&logo=tinymce&logoColor=white"/>
    <img alt="Tailwind CSS" src="https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white"/>
</p>

---

## ⚡ Instalação

**1. Clone e instale**
```bash
git clone https://github.com/GabrielG71/Formata-ABNT
cd formata-abnt
npm install
```

**2. Configure a API do TinyMCE**
> Você precisa de uma chave da API do TinyMCE (gratuita). Substitua no código:
```javascript
api-key="sua_chave_aqui"
```

**3. Execute**
```bash
npm run dev
```

---

## 🎯 O que faz

- Aplica formatação ABNT automaticamente (Times New Roman 12pt, espaçamento 1,5, recuo 1,25cm)
- Editor completo com todas as ferramentas do TinyMCE
- Margens simuladas (3cm superior, 2cm inferior, 3cm esquerda, 2cm direita)
- Exporta para PDF e Word

Digite seu texto normalmente e clique em "Formatar em ABNT" para aplicar as normas.

**Acesse:** `http://localhost:5173`