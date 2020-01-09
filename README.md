# projeto Marco Civil
informações e tutoriais de como implementar a Lei 12965/2014 - Marco Civil em servidores brasileiros, em diferentes servicos

## para quem é esse projeto no github?
para quem gerencia um servidor, seja físico ou virtual ou até mesmo para quem cria aplicações de internet

## quem deve guardar o log?
* se você contratou uma hospedagem compartilhada, a princípio seu provedor vai guardar os logs, exceto se você subir um serviço em uma porta que não passe pelo servidor web (apache, nginx, IIS)

* se você contratou um servidor virtual / cloud ou um servidor dedicado em uma nuvem, como a da Under (www.under.com.br), AWS, Google Cloud, etc, então você mesmo deve configurar seu servidor para guardar os logs corretamente

* se você contratou um servidor 100% gerenciado, no qual você não possui acesso root / administrator, então provavelmente seu fornecedor de gerenciamento irá configurar a guarda de logs por você

## quanto tempo tenho que guardar os logs?
* o prazo para guarda de logs é de 6 meses, conforme a Lei 12965 artigo 15. 
* recomendamos guardar por até 12 meses

## se migrar servidor para outro preciso guardar logs?
* sim

## devo realizar backup dos logs também?
* sim, pois o artigo 15 fala em guardar em ambiente seguro

## é preferível guardar os logs fora do servidor?
* sim, pois assim separa as funções do servidor, como no caso de servidor virtual stateless, na qual se deseja aumentar ou reduzir o número de vms, ou então para não precisar realizar backup do servidor em vm stateless. Podemos sugerir algumas técnicas como:
** enviar os logs para storage NAS (NFS, CIFS)
** utilizar um concentrador de logs como o Elasticsearch
** enviar os logs periodicamente para Object Storage

## quais informações tem que constar nos logs?

## quais informações não podem constar nos logs?

## como aumento o tempo de guarda de logs do sistema operacional?
* No linux você deve configurar o logrotate
* No windows server você deve configurar o event viewer para não apagar os logs


