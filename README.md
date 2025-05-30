---

# script-backup-mysql.sh

![Version](https://img.shields.io/badge/version-1.0-blue.svg)
![License](https://img.shields.io/badge/license-GPL--3.0-green.svg)
![Status](https://img.shields.io/badge/status-active-brightgreen.svg)

## Descrição

Script para realizar o **backup/dump** de bancos de dados **MySQL/MariaDB**, com funcionalidades adicionais de **compactação** e **exclusão automática de backups antigos**.

> ✅ **Funcionalidades:**
>
> * Backup completo de bancos de dados.
> * Compactação opcional dos arquivos gerados.
> * Exclusão automática de backups antigos conforme a política definida.
> * Execução interativa ou automatizada via **cron**.
> * Geração e rotação de logs via **logrotate**.

---

## Autor

**Denilly Carvalho do Carmo**

📅 **Data de criação:** 15/05/2025

©️ **Copyright:** 2025 Denilly Carvalho do Carmo.

🛡️ **Licença:** GNU General Public License (GPL-3.0).

---

## Notas

Este script é fornecido "**como está**" e pode ser utilizado e modificado por terceiros, desde que os **créditos ao autor sejam mantidos**. Para uso em projetos, por favor, faça referência a este script e ao autor.

### Importante

* O script pode ser executado com ou sem argumentos:

  * Sem argumentos: será exibido um **menu interativo**.
  * Com argumentos: execução direta para uso em linha de comando ou via **cron**.

* Utilize a opção de ajuda `-h` ou `--help` para obter mais informações sobre as opções disponíveis.

* Os logs gerados podem ser rotacionados com o **logrotate** via configuração específica.

---

## Como usar

### 1. Criar o arquivo do script

```bash
sudo nano /usr/local/sbin/script-backup-mysql.sh
```

Cole o código deste repositório no editor. Ajuste os parâmetros indicados com `<--` conforme a necessidade e salve.

---

### 2. Conceder permissão de execução

```bash
sudo chmod 700 /usr/local/sbin/script-backup-mysql.sh
```

---

### 3. Executar o script para gerar o log e checar requisitos

```bash
sudo /usr/local/sbin/script-backup-mysql.sh -l -C
```

---

### 4. Recomendação

Mantenha uma cópia de segurança do script em:

```bash
/backup/scripts
```

---

### 5. Configurar logrotate

Crie o arquivo de configuração do logrotate:

```bash
sudo nano /etc/logrotate.d/script-backup-mysql
```

Cole o seguinte conteúdo, para ativar a rotação:

```logrotate
/var/log/script-backup-mysql.sh.log {
    su root adm
    daily
    rotate 10
    compress
    missingok
    notifempty
    delaycompress
    create 640 root adm
}
```

---

## Exemplos de uso

### Execução interativa:

```bash
sudo /usr/local/sbin/script-backup-mysql.sh
```

### Execução automática com parâmetros (exemplo):

```bash
sudo /usr/local/sbin/script-backup-mysql.sh -a -c -r 10 -o /backup/mysql
```

> Onde:
> `-a` realiza backup de todos os bancos de dados.
> `-c` ativa a compactação.
> `-r` define a retenção de backups (em dias).
> `-o` destino do backup.

---

## Contribuição

Contribuições são bem-vindas!
Sugestões, melhorias ou correções podem ser enviadas via **pull requests** ou **issues** neste repositório.

---

## Licença

Este projeto está licenciado sob a **GNU General Public License v3.0**.

---

