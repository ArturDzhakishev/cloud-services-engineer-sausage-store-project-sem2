# Сосисочная — интернет-магазин «Sausage Store»

## Рабочий вариант: https://front-artur.2sem.students-projects.ru

![image](https://user-images.githubusercontent.com/9394918/121517767-69db8a80-c9f8-11eb-835a-e98ca07fd995.png)

## Description

Интернет-магазин «Сосисочная» — сервис, позволяющий пользователям:
- Добавлять товары в корзину
- Удалять товары из корзины
- Оформлять заказы
- Сохранять отчёты об активности пользователей

## Technologies used

* Frontend – TypeScript, Angular.
* Backend  – Java 16, Spring Boot, Spring Data.
* Backend-report - Go.
* Database – PostgreSQL, MongoDB.
* Infrastructure - Kubernetes, Helm
* Secrets - HashiCorp Vault

## Installation guide

Для развертывания используйте команду:
```bash
helm upgrade --install sausage-store ./sausage-store-chart \
  --set global.vault.vaultToken=VAULT_TOKEN
```
Укажите ваш актуальный Vault Token для доступа к секретам.

CI/CD: Автодеплой осуществляется через GitHub Actions. Достаточно выполнить git push, чтобы изменения прошли сборку и раскатились в кластер Kubernetes.


          livenessProbe:
{{ toYaml .Values.livenessProbe | indent 12 }} 