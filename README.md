# Bravox Space — Administrador para Vercel

Pacote do administrador existente, separado dos cardápios de demonstração.
Sem imagens, produtos ou restaurantes pré-cadastrados. Os campos de upload de
imagens continuam disponíveis e são opcionais.

## Publicar pelo GitHub

1. Descompacte o ZIP.
2. Crie um repositório privado no GitHub, por exemplo `bravox-admin`.
3. Envie o conteúdo da pasta `bravox-admin-vercel` para a raiz do repositório:
   `public/`, `vercel.json` e este guia. Não envie apenas o ZIP.
4. Na Vercel, use Add New → Project e importe o repositório.
5. Use Root Directory na raiz, Framework Preset `Other`, Build Command vazio
   e Output Directory `public`. O arquivo vercel.json já define esses valores.
6. Clique em Deploy e abra o endereço de produção informado pela Vercel.

Não há dependências de build, variáveis de ambiente ou banco de dados remoto.
A página inicial já é o administrador; não é necessário acrescentar /admin.

## Primeiro uso

Clique em Nova loja, preencha nome, WhatsApp, horários, entrega, categorias,
produtos e preços. Fotos e logo são opcionais; os avisos de ausência de imagens
não impedem exportar. Os dados são salvos neste navegador.

Se já houver lojas cadastradas em outro endereço, exporte o backup naquela
instância e importe-o nesta. Para importar um cardápio existente com suas fotos,
use Importar loja.js → Escolher a pasta do site.

## Publicar os cardápios dos restaurantes

Exportar site gera um ZIP separado por restaurante. Hospedar o administrador
não publica os restaurantes automaticamente. Os passos Netlify presentes no
painel se referem ao destino original dos cardápios, não à hospedagem do admin.

Para hospedar um cardápio na Vercel, descompacte o ZIP gerado, envie os arquivos
internos do restaurante para outro repositório e importe-o como projeto estático
Other (sem build). Use o endereço real do restaurante na seção Link → Usar outro
endereço, depois exporte novamente e publique os arquivos atualizados. Não use
um endereço presumido para imprimir o QR Code. A publicação não é automática.

## Armazenamento e acesso

Este painel não tem login próprio nem backend. Ele usa IndexedDB do navegador;
os dados não ficam na Vercel e não sincronizam entre pessoas ou computadores.
Outro visitante não verá os seus cadastros locais, mas poderá abrir a interface
se a hospedagem estiver pública.

Utilize sempre o mesmo navegador e endereço de produção. Endereços de prévia,
outro domínio, outro perfil ou outro computador terão bases locais separadas.
Faça Exportar backup regularmente. Limpar os dados do navegador pode remover
os cadastros. Hospedar este pacote não cria o painel multiusuário do SaaS.

Se desejar restringir a interface, confira Settings → Deployment Protection na
Vercel. Verifique quais domínios estão protegidos: proteção de Preview não deve
ser tratada como garantia de proteção do domínio principal de Production.
Não foi adicionada senha em JavaScript, pois isso não protege um painel online.

## Bibliotecas externas

ZIP e QR Code usam JSZip e QRious carregadas de cdnjs com verificação de
integridade, conforme o projeto original. Fontes são carregadas do Google Fonts.
É necessário acesso a esses serviços para essas funções. Nenhuma imagem de
restaurante está incluída neste pacote.

## Verificação deste pacote

Foram conferidas a sintaxe JavaScript, as referências dos arquivos locais,
a configuração da pasta public e a ausência de assets de demonstração.
A publicação e a interação no seu ambiente Vercel precisam ser verificadas
após o Deploy. Nenhum login ou armazenamento em nuvem foi implementado.

Referências oficiais:
- https://vercel.com/docs/builds/configure-a-build
- https://vercel.com/docs/git/vercel-for-github
- https://vercel.com/docs/deployment-protection
