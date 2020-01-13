# Tutorial para configuração do Apache para o Marco Civil

== Campos que serão armazenados ==

IP de origem
porta de origem
data
timezone
hostname
uri

== Configuração no serviço ==

Coloque na raiz do conf do apache ou dentro do <IfModule log_config_module>:
LogFormat "%v %h %{remote}p %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" marcocivil

Agora dentro da sessão <VirtualHost>, configure o log para:
CustomLog logs/hostname-access_log-ssl marcocivil

== Rotacionamento de Logs ==

Configure o logrotate (no CentOS é /etc/logrotate.d/httpd) da seguinte forma:

/var/log/httpd/*log { 
rotate 52 
weekly
}

Tiramos a opcao daily e colocamos a opcao weekly, assim teremos 52 arquivos no ano

As demais opcoes deixamos como estava

Mas podemos fazer tambem monthly e rotate 12

Optamos em todos os guias em manter 12 meses e nao apenas 6, que é o mínimo do Marco Civil, por segurança.
