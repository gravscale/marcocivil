= Tutorial para configuração do Nginx para o Marco Civil =

== Campos que serão armazenados ==
* IP de origem
* porta de origem
* data
* timezone
* protocolo
* hostname
* uri

== Configuração no serviço ==

Coloque dentro da sessão http:

http {
  log_format marcocivil '$remote_addr $remote_port - $remote_user [$time_local] '
  '$scheme $host '
  '"$request" $status $body_bytes_sent '
  '"$http_referer" "$http_user_agent"';
                 
             
Agora dentro da sessão server, configure o log para:

server {
  access_log /var/log/nginx/access.log marcocivil;



== Rotacionamento de Logs ==

Configure o logrotato (no Ubuntu é /etc/logrotate.d/nginx) da seguinte forma:

/var/log/nginx/*.log {
  rotate 52
  weekly
}

Tiramos a opcao daily e colocamos a opcao weekly, assim teremos 52 arquivos no ano

As demais opcoes deixamos como estava

Mas podemos fazer tambem monthly e rotate 12

Optamos em todos os guias em manter 12 meses e nao apenas 6, que é o mínimo do Marco Civil, por segurança.



