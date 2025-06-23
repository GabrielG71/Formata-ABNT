<template>
  <div class="min-h-screen bg-gray-50">
    <!-- Header -->
    <header class="bg-white shadow-sm border-b">
      <div class="max-w-4xl mx-auto px-6 py-8 text-center">
        <h1 class="text-3xl font-bold text-gray-900 mb-2">
          Formata<span class="text-blue-600">-ABNT</span>
        </h1>
        <p class="text-gray-600">Editor de texto com formatação automática em padrão ABNT</p>
      </div>
    </header>

    <main class="max-w-4xl mx-auto px-6 py-8">
      <!-- Informações sobre ABNT -->
      <div class="bg-blue-50 border border-blue-200 rounded-lg p-6 mb-6">
        <h2 class="text-lg font-semibold text-blue-900 mb-4">📋 Formatação ABNT Aplicada</h2>
        <div class="grid md:grid-cols-2 gap-6 text-sm text-blue-800">
          <div>
            <h3 class="font-medium mb-2">Características do Texto:</h3>
            <ul class="space-y-1">
              <li>• Fonte: Times New Roman, 12pt</li>
              <li>• Espaçamento: 1,5 entre linhas</li>
              <li>• Alinhamento: Justificado</li>
              <li>• Recuo: 1,25cm na primeira linha</li>
            </ul>
          </div>
          <div>
            <h3 class="font-medium mb-2">Margens (simuladas):</h3>
            <ul class="space-y-1">
              <li>• Superior: 3cm</li>
              <li>• Inferior: 2cm</li>
              <li>• Esquerda: 3cm</li>
              <li>• Direita: 2cm</li>
            </ul>
          </div>
        </div>
      </div>

      <!-- Editor -->
      <div class="bg-white rounded-lg shadow-sm border border-gray-200 overflow-hidden mb-6">
        <Editor
          ref="editorRef"
          api-key="sua_chave_aqui"
          :init="editorInit"
        />
      </div>

      <!-- Botão de Formatação -->
      <div class="text-center">
        <button 
          @click="formatarABNT"
          class="bg-blue-600 hover:bg-blue-700 text-white font-semibold py-3 px-8 rounded-lg shadow-sm transition-colors duration-200"
        >
          📄 Formatar em ABNT
        </button>
        <p class="text-gray-500 text-sm mt-2">Clique para aplicar formatação automática conforme normas ABNT</p>
      </div>
    </main>

    <!-- Footer -->
    <footer class="bg-white border-t mt-12">
      <div class="max-w-4xl mx-auto px-6 py-6 text-center">
        <p class="text-gray-500 text-sm">© 2025 Formata-ABNT - Ferramenta para formatação acadêmica</p>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import Editor from '@tinymce/tinymce-vue'

const editorRef = ref(null)

const editorInit = {
  height: 600,
  menubar: true,
  toolbar_mode: 'sliding',
  plugins: [
    'anchor', 'autolink', 'charmap', 'codesample', 'emoticons', 'image', 'link', 'lists', 'media', 'searchreplace', 'table', 'visualblocks', 'wordcount',
    'checklist', 'mediaembed', 'casechange', 'formatpainter', 'pageembed', 'a11ychecker', 'tinymcespellchecker', 'permanentpen', 'powerpaste', 'advtable',
    'advcode', 'editimage', 'advtemplate', 'ai', 'mentions', 'tinycomments', 'tableofcontents', 'footnotes', 'mergetags', 'autocorrect', 'typography',
    'inlinecss', 'markdown', 'importword', 'exportword', 'exportpdf'
  ],
  toolbar: 'undo redo | blocks fontfamily fontsize | bold italic underline strikethrough | link image media table mergetags | addcomment showcomments | spellcheckdialog a11ycheck typography | align lineheight | checklist numlist bullist indent outdent | emoticons charmap | removeformat | exportpdf exportword',
  tinycomments_mode: 'embedded',
  tinycomments_author: 'Usuário',
  mergetags_list: [
    { value: 'Nome', title: 'Nome' },
    { value: 'Email', title: 'Email' },
    { value: 'Data', title: 'Data' },
  ],
  ai_request: (request, respondWith) => respondWith.string(() => Promise.reject('Recurso de IA não configurado')),
  content_style: `
    body {
      font-family: 'Times New Roman', serif;
      font-size: 12pt;
      line-height: 1.5;
      margin: 1rem;
      text-align: justify;
    }
    p {
      text-indent: 1.25cm;
      margin: 0 0 6pt 0;
    }
    h1 {
      font-size: 14pt;
      font-weight: bold;
      margin-top: 12pt;
      margin-bottom: 6pt;
      text-align: left;
    }
    h2 {
      font-size: 13pt;
      font-weight: bold;
      margin-top: 12pt;
      margin-bottom: 6pt;
      text-align: left;
    }
    h3 {
      font-size: 12pt;
      font-weight: bold;
      margin-top: 12pt;
      margin-bottom: 6pt;
      text-align: left;
    }
  `,
  setup: (editor) => {
    editor.on('init', () => {
      editor.setContent('<p>Bem-vindo ao Formata-ABNT! Digite seu texto aqui e clique em "Formatar em ABNT" para aplicar a formatação acadêmica automaticamente.</p>')
    })
  }
}

const formatarABNT = () => {
  const editorInstance = editorRef.value?.getEditor?.()

  if (editorInstance) {
    const conteudo = editorInstance.getContent()

    const conteudoFormatado = `
      <div style="margin: 3cm 2cm 2cm 3cm; text-align: justify; line-height: 1.5;">
        ${conteudo
          .replace(/<p>/g, `<p style="font-family: 'Times New Roman', serif; font-size: 12pt; text-indent: 1.25cm; margin: 0 0 6pt 0;">`)
          .replace(/<h1>/g, `<h1 style="font-family: 'Times New Roman', serif; font-size: 14pt; font-weight: bold; text-align: left; margin-top: 12pt; margin-bottom: 6pt;">`)
          .replace(/<h2>/g, `<h2 style="font-family: 'Times New Roman', serif; font-size: 13pt; font-weight: bold; text-align: left; margin-top: 12pt; margin-bottom: 6pt;">`)
          .replace(/<h3>/g, `<h3 style="font-family: 'Times New Roman', serif; font-size: 12pt; font-weight: bold; text-align: left; margin-top: 12pt; margin-bottom: 6pt;">`)
        }
      </div>
    `

    editorInstance.setContent(conteudoFormatado)
  } else {
    console.warn('Editor ainda não está pronto.')
  }
}

</script>

<style>
* {
  transition: all 0.2s ease-in-out;
}

::-webkit-scrollbar {
  width: 8px;
}
::-webkit-scrollbar-track {
  background: #f1f1f1;
}
::-webkit-scrollbar-thumb {
  background: #3b82f6;
  border-radius: 4px;
}
::-webkit-scrollbar-thumb:hover {
  background: #2563eb;
}
</style>