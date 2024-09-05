## Работа с хранилищем секретов ansible-vault
### Плейбук настраивает доступ по паролю для сервера nginx

1. Создаем vault файл с секретами:
```bash
ansible-vault create nginx.vault
```  
Для редактирования используем:
```bash
ansible-vault edit nginx.vault
```

2. Добавляем в файл секреты:
```shell
nginx_user: USER
nginx_password: PASSWORD
```
Сохраяем и закрываем

3. Чтобы не вводить пароль от vault создадим файл в котором запишем пароль в открытом виде
```shell
nano vault_pass.txt 
```

4. Запускаем плейбук
```shell
ansible-playbook -i inventory.yaml site.yml -e "@nginx.vault" --vault-password-file vault_pass.txt
```

5. При переходе на страницу появится окно с авторизацией


