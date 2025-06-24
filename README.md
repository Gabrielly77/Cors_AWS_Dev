# Cors_AWS_Dev

🔥 O que é CORS na AWS Developer?
CORS = Cross-Origin Resource Sharing (Compartilhamento de Recursos entre Origens Diferentes).

Imagina que você tá na sua casa (domínio A) e quer pedir uma pizza na casa da vizinha (domínio B). Só que, por segurança, a casa da vizinha não aceita pedidos de qualquer um que não seja da própria família dela. Aí você precisa que ela coloque seu nome na lista de permitidos pra poder pedir a pizza.

💡 Na web é igual:
Se seu site (frontend) hospedado em um domínio (tipo meusite.com) quer se conectar a uma API da AWS (como API Gateway, S3, etc.) que tá em outro domínio (api.minhapizza.com), o navegador, por segurança, bloqueia essa comunicação se não tiver CORS liberado.

Então o CORS serve pra dizer:
"Ei navegador, relaxa! Tá autorizado esse rolê entre esses domínios aí." ✅

🍕 Na prática na AWS:
No API Gateway, você ativa CORS pra permitir que aplicações de outros domínios possam consumir sua API.

No S3, se você hospeda imagens, vídeos ou arquivos pra serem carregados em sites hospedados em outros domínios, precisa configurar CORS no bucket.

⚙️ Exemplo de configuração de CORS no S3:
json
Copiar
Editar
[
 {
   "AllowedHeaders": ["*"],
   "AllowedMethods": ["GET"],
   "AllowedOrigins": ["*"],
   "ExposeHeaders": [],
   "MaxAgeSeconds": 3000
 }
]
👆 Esse exemplo permite que QUALQUER site ("*" no AllowedOrigins) faça requisições GET nos seus arquivos.

🚨 Importante:
Abrir CORS pra tudo (*) é fácil, mas não é recomendado pra produção se você quiser segurança. ⚠️

O ideal é colocar o domínio que realmente vai acessar (https://meusite.com).

🎸 Resumão modo punk rock:
CORS na AWS Developer = uma permissão que seu serviço dá pra aceitar pedidos de outros sites, quebrando as barreiras de segurança do navegador, de forma controlada.
