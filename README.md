# -----------------------------------------------------------------------------
# Nome do arquivo de script: script-backup-mysql.sh
# Descrição: Script para realizar o backup/dump do banco de dados Mysql/Mariadb, 
#            compactação e exclusão de backups antigos.
# Autor: Denilly Carvalho do Carmo
# Data de Criação: 15/05/2025
# Copyright (c) 2025 Denilly Carvalho do Carmo. Todos os direitos reservados.
# Licença: GNU General Public License (GPL)
# Versão: 1.6

# NOTAS: Este script é fornecido "como está" e pode ser utilizado e modificado por terceiros,
#        desde que os créditos ao autor sejam mantidos. Para uso em projetos, por favor, faça
#        referência a este script e ao autor.
#
# IMPORTANTE: Execute este script com ou sem argumentos para realizar o backup/dump do banco
#             de dados dentre outras funções. Caso não seja informado nenhum argumento, será 
#             aberto um menu interativo.
#             Utilize argumentos para execução do script diretamente via comando ou agendamento
#             no Cron. Acesse a opção de ajuda "-h/--help" do script para maiores informações.
#             Os logs gerados pelo script podem ser rotacionados pelo logrotate 
#             (/etc/logrotate.d/script-backup-mysql).
#
# COMO USAR:
# 1. Crie o arquivo do script com o seu editor linux preferido:
#    $ nano /usr/local/sbin/script-backup-mysql.sh
# 2. Cole o código deste arquivo no editor, ajustes os parâmetros comentados com "<--" (quando  
#    necessário) e salve o arquivo.
# 3. Dê permissão de execução ao script:
#    $ chmod 700 script-backup-mysql.sh
# 4. Execute o script com "-l/--log" e "-C/--check" para criar o arquivo de log e checar requisitos:
#    $ sudo script-backup-mysql.sh -l -C
# 5. Mantenha uma cópia do script em /backup/scripts
# 6. Crie um arquivo de configuração do logrotate com o seu editor linux preferido
#    $ nano /etc/logrotate.d/script-backup-mysql
# 7. Cole o código exemplo abaixo (a partir de "/var..." até "}") retire o sinalizador de 
#    comentário "#    " para rotacionar o log.
#
#    /var/log/script-backup-mysql.sh.log {
#        su root adm
#        daily
#        rotate 10
#        compress
#        missingok
#        notifempty
#        delaycompress
#        create 640 root adm
#    }
# -----------------------------------------------------------------------------
