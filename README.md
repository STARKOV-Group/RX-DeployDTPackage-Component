# Публикация пакета на сервер (RX DeployDTPackage Component)

## Описание:

Публикация пакета через DT на сервер видимый (без ВПН) из сети машины, на которой крутится раннер.

### Логика:

Если значение параметра DeployMode не равно "upload", то этап выполняется

Из параметров DeployUserName и DeployUserPassword (с префиксом [DeployDestination](https://github.com/STARKOV-Group/Completed-RXDTDeploy-Component#deploydestination), если он указан) извлекаются логин и пароль пользователя, под которым будет происходить публикация на машине, по протоколу [WebProtocol](https://github.com/STARKOV-Group/Completed-RXDTDeploy-Component#webprotocol), с адресом [DeployIpServer](https://github.com/STARKOV-Group/Completed-RXDTDeploy-Component#deployipserver) и портом [ServerHttpPort](https://github.com/STARKOV-Group/Completed-RXDTDeploy-Component#serverhttpport) или [ServerHttpsPort](https://github.com/STARKOV-Group/Completed-RXDTDeploy-Component#serverhttpsport) (в зависимости от протокола).

Если значение параметра [NeedApplySettings](https://github.com/STARKOV-Group/Completed-RXDTDeploy-Component#needapplysettings) равно "True", то после публикации на сервер машины применяются настройки

В артефакты этапа кладутся логи. Сами артефакты хранятся в течении 1 недели

## Переменные:

### Пользовательские настройки

### DeployMode

**Описание:** Режим публикации  
**Примечание**: Также используется в [компоненте выгрузки в корпоративное облако](https://github.com/STARKOV-Group/RX-UploadPackage-Component)  
**Обязательность:** Нет  
**Возможные значения:** upload, любое значение  
**Значение по умолчанию**: ""

> [!note]
>Далее указаны сетевые настройки, их лучше не указывать напрямую, а создать [переменные в CICD проекта](https://docs.gitlab.com/ci/variables/#define-a-cicd-variable-in-the-ui)

### (DeployDestination)DeployUser

**Описание:** Логин пользователя под которым будет происходить публикация  
**Обязательность:** Да  
**Пример:** Service user

### (DeployDestination)DeployPassword

**Описание:** Пароль пользователя под которым будет происходить публикация  
**Обязательность:** Да  
**Пример:** 1Qwerty

