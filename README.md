1. Скачайте и установите VamShop2 на сервер (https://vamshop.ru/download.html).
2. Скопируйте папку app в корень сайта с заменой файлов.
3. Установите модуль RBKmoney (Расширения->Модули).
4. Далее нужно заполнить необходимые поля для корректной работы модуля.
   Сделать это можно через админку в настройках модуля (Настройки->RBKmoney)
   Поля настройки модуля описаны ниже.
   После заполнения полей нажмите кнопку сохранить в конце страницы.



5. НАСТРОЙКА РЕКУРРЕНТОВ




Настройка модуля

1) API ключ - его необходимо взять в кабинете RBKmoney нажав по кнопке "перейти в магазин" и выбрав пункт API ключ 
   в меню слева
2) ID магазина - также берется в кабинете в пункте "Детали магазина"
3) Тип списания средств - укажите "мгновенное списание" чтобы средства у пользователя списывались сразу
   (недостаток в том, что возврат списанных средств - действие платное),
   "холд" чтобы стредства блокировались на карте и списывались только после подтверждения
   (возможно сделать во вкладке "Транзакции" модуля или в кабинете)
4) Списание средств по окончанию срока холдирования - если вы ничего не сделаете на протяжении ## дней
   (период блокирования средств), то деньги спишутся в пользу магазина или вернутся назад плательщику
   в зависимости от этой настройки. Работает при выбранном в п.4 значении "Холд"
5) Отображение кардхолдера в форме оплаты - отображать или нет в форме ввода данных карты строку "Владелец карты".
6) Затенять карточный cvv код - затенять ли (забивать звездочками) вводимый параметр CVV на форме
   ввода данных карты или не затенять и отображать вводимые цифры
7) Фискализация по 54-ФЗ - выберите "Использовать" если вы пользуетесь решением по фискализации от RBKmoney
8) Статус заказа при успешной оплате - данная опция указывает в какой статус переводить инвойс в VamShop2 при успешной оплате
9) Статус инвойса при холде - данная опция указывает в какой статус переводить инвойс в VamShop2 при
   инициализации холда средств. Работает при выбранном в п.4 значении "Холд".
   В этот статус инвойс переводится после инициализации холда. При подтверждении холда
   (окончательном списании средств в пользу магазина) статус инвойса переводится в статус, указанный в п9.
10) Статус заказа при отмене холда - данная опция указывает в какой статус переводить инвойс в VamShop2 при отмене холда
11) Статус заказа при возврате средств - данная опция указывает в какой статус переводить инвойс в VamShop2 при возврате средств
12) Ставка НДС - Данная ставка будет применятся ко всем товарам на сайте.
13) Ставка НДС для доставки - Данная ставка будет применятся ко всем доставкам.
14) Писать логи RBKmoney - Этот флаг определяет будут ли писаться логи запросов RBKmoney

Принцип работы рекуррентных товаров

1) Во вкладке "товары для регулярных платежей" необходимо указать артикулы тех товаров, которые будут
   работать как "подписки на регулярные платежи", а также настроить регулярные задачи согласно инструкции выше. 
2) После покупки такого товара-подписки (не важно есть ли в корзине еще обычные товары или нет)
   с пользователя списываются средства в размере стоимости этого товара. Далее происходят регулярные
   списания по расписанию, указанному вами в настройках выше. При каждом регулярном списании во вкладке
   "Транзакции" появится новая транзакция, соответствующая данной регулярной оплате,
   в неткате появится инвойс, соответствующий этому списанию. 
3) В момент первой оплаты товара-подписки конкретным пользователем сумма подписки для дальнейших списаний фиксируется.
   Если вы отредактируете стоимость товара-подписки, это не скажется на суммах, на которые подписались
   пользователи до этого, с них продолжат списываться зафиксированные ранее суммы. 
4) Если в момент списания на карте не было денег, или возникла иная проблема - повторных попыток списания
   этой регулярной оплаты не будет, но, когда наступит время следующего списания - оно также будет проведено один раз. 
5) Удалить подписки на регулярные списания и просмотреть текущие можно во вкладке "Регулярные платежи" модуля. 
6) Контроля уникальности подписок нет. Один и тот же пользователь может несколько раз подписаться 
   на один и тот же товар-подписку, и средства с него будут списываться несколько раз за период.