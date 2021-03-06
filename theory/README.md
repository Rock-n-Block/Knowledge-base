#### WEB3 теория

- [Подключение к ноде](#подключение-к-ноде)
- [Авторизация](#авторизация)
- [Отправка транзакций](#отправка-транзакций)
- [Мультиаккаунт](#мультиаккаунт)
- [Кошельки](#кошельки)

### Подключение к ноде

Есть два способа подключения к ноде:

- использовать собственную ноду (но поднятие собственной ноды не самая простая операция);
- подключение через провайдера.

Провайдер - это то, через что web3 общается с блокчейном. Провайдеры принимают запросы
JSON-RPC ([протокол](https://eth.wiki/json-rpc/API)) и возвращают ответ.

Провайдеры могут быть следующими:

- HttpProvider - устарел, так как не поддерживает подписки;
- WebsocketProvider - работает удаленно, но быстрее чем HttpProvider;
- IpcProvider - использует локальную файловую систему (самая быстрая и самая безопасная).

Если возникли сложности с выбором провайдера, то можете воспользоваться подсказкой:

- если у вас есть возможность запустить Web3 на том же компьютере, что и ноду, выберите IPC;
- если вам необходимо подключиться к узлу на другом компьютере, используйте Websockets;
- если ваш узел не поддерживает веб-сокеты, используйте HTTP.

Ещё есть вариант использовать **givenProvider**.

При использовании web3.js в браузере, совместимом с Ethereum, он будет настроен на текущего собственного провайдера
этого браузера, например, при использовании **Metamask**.

Также в качестве провайдера можно использовать сторонние сервисы, например, **infura.io** или **alchemy**.

Примеры подключения к ноде можно посмотреть в главе [Для Typescript](../web3-examples/typescript/README.md).

### Авторизация

При создании кошелька генерируется **Seed-фраза**, представляющая из себя число, записанное в виде хэша, из которого
можно получить мастер-ключ, из которого, в свою очередь, можно получить дерево приватных и публичных ключей.

Хранить или тем более запоминать **Seed-фразу** не очень удобно, особенно если пробовать записать её от руки в блокнот.
Чтобы решить эту проблему существуют **Мнемоники**.

**Мнемоники** - это набор слов, из которых можно получить **Seed-фразу**. Что предоставляет более простой способ
хранения доступов к вашему кошельку.

Самих же адресов кошельков можно нагенерировать бесконечно.

Будьте внимательны, обязательно сохраняйте **Мнемоники**, либо **Seed-фразу**, при их отсутствии нет никакой возможности
доказать, что кошелек принадлежит именно вам.

Когда мы используем готовые кошельки, они делают всё за нас, но при написании своего кошелька нужно самому просить 
**Seed-фразу** и превращать её в ключи.

Подробности в главе [HD-Wallets](../hd-wallets/README.md).

### Отправка транзакций

С помощью **Web3** можно отправлять транзакции от своего имени.

Для этого необходимы **приватный ключ** и некоторое количество **эфира** для оплаты **Fee**.

Для отправки транзакции необходимо создать объект транзакции и подписать эту транзакцию **приватным ключом**.

Если нужно снять с пользователя точную сумму и добавить к ней сверху **Fee** на проведение этой транзакции, то мы
рассчитываем **Fee** как произведение **количества газа** на **цену газа**.

При создании транзакции можно задать сколько **эфира** вы платите за каждую единицу газа (**цена газа**) и
максимальное **количество газа**, которое вы готовы оплатить.

Чем больше вы выделяете — тем более приоритетна ваша транзакция для потенциальных майнеров. Ведь по сути плата за
**газ** — это оплата работы майнеров по выполнению вашей транзакции и включению ее в очередной блок.

Количество же газа за транзакцию зависит от вычислительной сложности операций над данными.

Если данные в результате **транзакции** не меняются — то платить за **газ** не нужно.

Примеры отправки транзакций можно посмотреть в главе [Для Typescript](../web3-examples/typescript/README.md).

### Мультиаккаунт

Кошелек, в котором все используемые личные ключи были порождены из одного общего для всех ключей секрета (**мастер
ключа**). Особенность состоит в том, что есть возможность из одного **мастер-ключа** породить сколько угодно пар ключей
для электронной подписи.

Можно заводить несколько аккаунтов, для каждого из которых будут создаваться раздельные счета.

Подробности в главе [HD-Wallets](../hd-wallets/README.md).

### Кошельки

Кошельки наподобие **Metamask** также используют библиотеку **Web3**, хранят в себе **Seed-фразу** и подключаются к
своим нодам.

Подробности про Seed-фразу и кошельки можно узнать в следующих главах:

- Seed-фраза в главе [авторизация](#авторизация);
- Кошельки в главе [HD-Wallets](../hd-wallets/README.md).
