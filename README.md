# Проект API Яндекс.Прилавок

## Задачи

### 1. Проанализировать требования к новой функциональности бэкенда Яндекс.Прилавка в перечне документов:

- **[Требования к бэкенду](https://drive.google.com/file/d/1ttz8wA_cUfiIvbWqg_s7OlNx-wbOKLq5/view?usp=sharing)**
- **[Требования к расчёту доставки](https://drive.google.com/file/d/1NLOFtt7uXS_CyAQtNsto7IzOtGbH8llR/view?usp=drive_link)**
- **[Apidoc](https://github.com/orakul99/QA-yandex-prilavok/blob/main/apidoc.md)**

### 2. Спроектировать чек-листы, чтобы покрыть следующую функциональность: 

- добавление продуктов в набор
- курьерская служба привезём быстро,
- получение продуктов в корзине,
- добавление товаров в корзину
- удаление корзины

### 3. Протестировать API через Postman и завести баг-репорты

### 4. Написать отчёт о тестировании


## Тестовая документация

**[1. Чек-лист API Работа с наборами](https://docs.google.com/spreadsheets/d/1IMMzF_ZQVVAIxlBAVMZoIVqfDt9N0tnLzKYg2NFTD9I/edit?gid=0#gid=0)**

**[2. Чек-лист API Работа с курьерами](https://docs.google.com/spreadsheets/d/1IMMzF_ZQVVAIxlBAVMZoIVqfDt9N0tnLzKYg2NFTD9I/edit?gid=1243699577#gid=1243699577)**

**[3. Чек-лист API Работа с корзиной](https://docs.google.com/spreadsheets/d/1IMMzF_ZQVVAIxlBAVMZoIVqfDt9N0tnLzKYg2NFTD9I/edit?gid=725778654#gid=725778654)**

**[4. Баг-репорты](https://docs.google.com/spreadsheets/d/1IMMzF_ZQVVAIxlBAVMZoIVqfDt9N0tnLzKYg2NFTD9I/edit?gid=1825227566#gid=1825227566)**


## Отчёт

В процессе выполнения тестирования по написанным чек-листам были найдены блокирующие: [BUG-8](https://docs.google.com/spreadsheets/d/1IMMzF_ZQVVAIxlBAVMZoIVqfDt9N0tnLzKYg2NFTD9I/edit?gid=1825227566#gid=1825227566&range=9:9), [BUG-9](https://docs.google.com/spreadsheets/d/1IMMzF_ZQVVAIxlBAVMZoIVqfDt9N0tnLzKYg2NFTD9I/edit?gid=1825227566#gid=1825227566&range=10:10). [BUG-11](https://docs.google.com/spreadsheets/d/1IMMzF_ZQVVAIxlBAVMZoIVqfDt9N0tnLzKYg2NFTD9I/edit?gid=1825227566#gid=1825227566&range=12:12), [BUG-13](https://docs.google.com/spreadsheets/d/1IMMzF_ZQVVAIxlBAVMZoIVqfDt9N0tnLzKYg2NFTD9I/edit?gid=1825227566#gid=1825227566&range=14:14) и критические: [BUG-1](https://docs.google.com/spreadsheets/d/1IMMzF_ZQVVAIxlBAVMZoIVqfDt9N0tnLzKYg2NFTD9I/edit?gid=1825227566#gid=1825227566&range=2:2), [BUG-2](https://docs.google.com/spreadsheets/d/1IMMzF_ZQVVAIxlBAVMZoIVqfDt9N0tnLzKYg2NFTD9I/edit?gid=1825227566#gid=1825227566&range=3:3), [BUG-3](https://docs.google.com/spreadsheets/d/1IMMzF_ZQVVAIxlBAVMZoIVqfDt9N0tnLzKYg2NFTD9I/edit?gid=1825227566#gid=1825227566&range=4:4), [BUG-19](https://docs.google.com/spreadsheets/d/1IMMzF_ZQVVAIxlBAVMZoIVqfDt9N0tnLzKYg2NFTD9I/edit?gid=1825227566#gid=1825227566&range=20:20), [BUG-21](https://docs.google.com/spreadsheets/d/1IMMzF_ZQVVAIxlBAVMZoIVqfDt9N0tnLzKYg2NFTD9I/edit?gid=1825227566#gid=1825227566&range=22:22) баги, которые позволяют передавать из фронтенда в БД некорректные данные. А также один блокирующий баг [BUG-24](https://docs.google.com/spreadsheets/d/1IMMzF_ZQVVAIxlBAVMZoIVqfDt9N0tnLzKYg2NFTD9I/edit?gid=1825227566#gid=1825227566&range=25:25), не позволяющий использовать корзину из-за невозможности ее удаления.

Остальные баги со средним приоритетом также связаны с негативными сценариями передачи некорректных данных, без их передачи, но с непредусмотренными статусами ошибок – доступны по общей ссылке Баг-репорты.

API в таком состоянии использовать рискованно, релиз отложить до правки багов критичных для целостности БД и пользовательского опыта.  
