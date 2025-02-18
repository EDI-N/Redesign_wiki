🚛 API "ETTN" v3
####################

.. image:: Work_with_API/pics/Main_API_002.png
   :align: center
   :height: 700px
   :alt: Стандартна схема документообігу

Алгоритми обміну документами (API)
====================================

.. toctree::
   :maxdepth: 1
   
   Work_with_API/ETTNv3_API_work
   Additional_transactions

.. toctree::
   :maxdepth: 1

   Work_with_API/Proposalv3_API_work

.. toctree::
   :maxdepth: 1

   Work_with_API/DisagreementActv3_API_work
   Work_with_API/LoadRejectActv3_API_work
   Work_with_API/StopActv3_API_work
   Work_with_API/ResealingActv3_API_work
   Work_with_API/StorageDeliveryActv3_API_work
   Work_with_API/StoragePickUpActv3_API_work
   Work_with_API/ReloadActv3_API_work
   Work_with_API/ConsigneeChangeActv3_API_work
   Work_with_API/AdjustmentActv3_API_work

-------------------------------

.. hint::
    Всі запити нижче перерахованих API методів сервісу "ЕТТН" направляються на адресу: https://edo-v2.edin.ua 

Авторизація
==============

+-----------+-----------------------------+--------------------------------------------------------------------------------------------------------------+
| **Метод** |       **URL запиту**        |                                                   **Опис**                                                   |
+===========+=============================+==============================================================================================================+
| POST      | ``/api/authorization/hash`` | `Авторизація <https://wiki.edin.ua/uk/latest/integration_2_0/APIv2/Methods/Authorization.html>`__            |
+-----------+-----------------------------+--------------------------------------------------------------------------------------------------------------+
| GET       | ``/api/auth_check``         | `Перевірка активності сесії <https://wiki.edin.ua/uk/latest/integration_2_0/APIv2/Methods/AuthCheck.html>`__ |
+-----------+-----------------------------+--------------------------------------------------------------------------------------------------------------+

.. beauty list

.. toctree::
   :hidden:
   :glob:

   /integration_2_0/APIv2/Methods/Authorization
   /integration_2_0/APIv2/Methods/AuthCheck

.. _general:

Загальні методи сервісу "ЕТТН"
=============================================================

+-----------+---------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Метод** |         **URL запиту**          |                                                                                 **Опис**                                                                                  |
+===========+=================================+===========================================================================================================================================================================+
| GET       | ``/api/eds/doc/ettn/body``      | `Отримання (завантаження) тіла документа сервісу "ЕТТН" в JSON/XML/ECMR/PDF/ZIP форматі <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/GetEcmrDocumentBody.html>`__ |
+-----------+---------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| POST      | ``/api/eds/doc/ettn/sign``      | `Підписання даних сервісу "ЕТТН" (збереження підпису) <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/SaveEcmrSign.html>`__                                          |
+-----------+---------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| GET       | ``/api/eds/doc/tickets``        | `Отримання всіх квитанцій вказаного документа <https://wiki.edin.ua/uk/latest/integration_2_0/APIv2/Methods/GetTickets.html>`__                                           |
+-----------+---------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| GET       | ``/api/eds/doc``                | `Отримання інформації (мета-даних) про документ <https://wiki.edin.ua/uk/latest/integration_2_0/APIv2/Methods/GetDocument.html>`__                                        |
+-----------+---------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| GET       | ``/api/eds/doc/ettn/sign/info`` | `Отримання інформації про підписантів е-ТТН та Актів v3 (family=7) <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/GetEttnSignInfo.html>`__                          |
+-----------+---------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| PATCH     | ``/api/eds/docs``               | `Видалити документи-чернетки <https://wiki.edin.ua/uk/latest/integration_2_0/APIv2/Methods/DeleteDocuments.html>`__                                                       |
+-----------+---------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. beauty list

.. toctree::
   :hidden:
   :glob:

   Methods/GetEcmrDocumentBody
   Methods/SaveEcmrSign
   /integration_2_0/APIv2/Methods/GetTickets
   /integration_2_0/APIv2/Methods/GetDocument
   Methods/GetEttnSignInfo
   /integration_2_0/APIv2/Methods/DeleteDocuments

.. _ecmr-ttn:

Робота з "Електронною товарно-транспортною накладною" (е-ТТН)
=========================================================================================

+-----------+-------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Метод** |              **URL запиту**               |                                                                             **Опис**                                                                              |
+===========+===========================================+===================================================================================================================================================================+
| POST      | ``/api/eds/doc/ettn/ttn``                 | `Створення/редагування чернетки "Електронної товарно-транспортної накладної" (е-ТТН) <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/CreateEcmrEttn.html>`__ |
+-----------+-------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| PATCH     | ``/api/eds/doc/ettn/ttn/send``            | `Відправка електронної товарно-транспортної накладної ("е-ТТН") з Чернеток <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/SendEcmrDoc.html>`__              |
+-----------+-------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| POST      | ``/api/eds/doc/ettn/ttn/transaction``     | `Створення/редагування нової транзакції (чернетки) до е-ТТН документа <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/PostEcmrTransaction.html>`__           |
+-----------+-------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| PUT       | ``/api/eds/doc/ettn/ttn/transaction``     | `Відправка нової транзакції до е-ТТН документа <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/PutEcmrTransaction.html>`__                                   |
+-----------+-------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| PUT       | ``/api/eds/doc/ettn/ttn/reject``          | `Відхилення "Електронної товарно-транспортної накладної" (е-ТТН) <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/RejectEcmr.html>`__                         |
+-----------+-------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| POST      | ``/api/eds/doc/ettn/ttn/attachment``      | `Додавання до документа вкладення (pdf) до документа е-ТТН <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/PostEcmrAttachment.html>`__                       |
+-----------+-------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| GET       | ``/api/eds/doc/ettn/ttn/attachment``      | `Отримання (завантаження) файлу-вкладення до документа е-ТТН <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/GetEcmrAttachment.html>`__                      |
+-----------+-------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| PATCH     | ``/api/eds/doc/ettn/ttn/attachment``      | `Відправки вкладення на повторну реєстрацію (при виникненні помилки) <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/PatchEcmrAttachment.html>`__            |
+-----------+-------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| DELETE    | ``/api/eds/doc/ettn/ttn/attachment``      | `Видалення файлу-вкладення до документа е-ТТН <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/DeleteEcmrAttachment.html>`__                                  |
+-----------+-------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| POST      | ``/api/eds/doc/ettn/ttn/create_and_send`` | `Створення та відправка "е-ТТН" документа (без створення чернетки) <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/CreateAndSendTtn.html>`__                 |
+-----------+-------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. beauty list

.. toctree::
   :hidden:
   :glob:

   Methods/CreateEcmrEttn
   Methods/SendEcmrDoc
   Methods/PostEcmrTransaction
   Methods/PutEcmrTransaction
   Methods/RejectEcmr
   Methods/PostEcmrAttachment
   Methods/GetEcmrAttachment
   Methods/PatchEcmrAttachment
   Methods/DeleteEcmrAttachment
   Methods/CreateAndSendTtn

.. _ecmr-act:

Робота з актами ("Акт перевантаження", "Акт коригування", ...) до е-ТТН
=========================================================================================

+-----------+----------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Метод** |             **URL запиту**             |                                                                                   **Опис**                                                                                   |
+===========+========================================+==============================================================================================================================================================================+
| POST      | ``/api/eds/doc/ettn/adjustment``       | `Створення/редагування чернетки "Акта коригування" до е-ТТН <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/CreateAdjustmentAct.html>`__                                |
+-----------+----------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| POST      | ``/api/eds/doc/ettn/consignee_change`` | `Створення/редагування чернетки "Акта про заміну пункту призначення вантажу" до е-ТТН <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/CreateConsigneeChangeAct.html>`__ |
+-----------+----------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| POST      | ``/api/eds/doc/ettn/disagreement``     | `Створення/редагування чернетки "Акта розбіжностей про вантаж" до е-ТТН <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/CreateDisagreementAct.html>`__                  |
+-----------+----------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| POST      | ``/api/eds/doc/ettn/load_reject``      | `Створення/редагування чернетки "Акта про відмову вантажити" до е-ТТН <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/CreateLoadRejectAct.html>`__                      |
+-----------+----------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| POST      | ``/api/eds/doc/ettn/reload``           | `Створення/редагування чернетки "Акта перевантаження" до е-ТТН <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/CreateReloadAct.html>`__                                 |
+-----------+----------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| POST      | ``/api/eds/doc/ettn/resealing``        | `Створення/редагування чернетки "Акта перепломбування" до е-ТТН <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/CreateResealingAct.html>`__                             |
+-----------+----------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| POST      | ``/api/eds/doc/ettn/stop``             | `Створення/редагування чернетки "Акта примусового завершення е-ТТН" <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/CreateStopAct.html>`__                              |
+-----------+----------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| POST      | ``/api/eds/doc/ettn/storage_delivery`` | `Створення/редагування чернетки "Акта розвантаження на проміжному складі" до е-ТТН <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/CreateStorageDeliveryAct.html>`__    |
+-----------+----------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| POST      | ``/api/eds/doc/ettn/storage_pickup``   | `Створення/редагування чернетки "Акта завантаження на проміжному складі" до е-ТТН <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/CreateStoragePickUpAct.html>`__       |
+-----------+----------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

+-----------+---------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Метод** |            **URL запиту**             |                                                                       **Опис**                                                                       |
+===========+=======================================+======================================================================================================================================================+
| POST      | ``/api/eds/doc/ettn/act/transaction`` | `Створення/редагування нової транзакції (чернетки) до Актів сервісу <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/PostActTransaction.html>`__ |
+-----------+---------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
| PUT       | ``/api/eds/doc/ettn/act/transaction`` | `Відправка нової транзакції до Актів сервісу <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/PutActTransaction.html>`__                         |
+-----------+---------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
| PUT       | ``/api/eds/doc/ettn/act/reject``      | `Відхилення Актів сервісу <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/RejectAct.html>`__                                                    |
+-----------+---------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
| PATCH     | ``/api/eds/doc/ettn/act/send``        | `Відправка Актів з Чернеток <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/SendAct.html>`__                                                    |
+-----------+---------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+

.. beauty list

.. toctree::
   :hidden:
   :glob:

   Methods/CreateAdjustmentAct
   Methods/CreateConsigneeChangeAct
   Methods/CreateDisagreementAct
   Methods/CreateLoadRejectAct
   Methods/CreateReloadAct
   Methods/CreateResealingAct
   Methods/CreateStopAct
   Methods/CreateStorageDeliveryAct
   Methods/CreateStoragePickUpAct
   Methods/PostActTransaction
   Methods/PutActTransaction
   Methods/RejectAct
   Methods/SendAct

.. _subscribe:

Підписки на події
=========================================================================================

+-----------+-----------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Метод** |       **URL запиту**        |                                                                        **Опис**                                                                        |
+===========+=============================+========================================================================================================================================================+
| GET       | ``/api/mintrans/subscribe`` | `Отримання даних про підписки на події (отримання документів) <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/GetSubscribeController.html>`__     |
+-----------+-----------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
| POST      | ``/api/mintrans/subscribe`` | `Створення (оформлення) підписки на події (отримання документів) <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/PostSubscribeController.html>`__ |
+-----------+-----------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
| DELETE    | ``/api/mintrans/subscribe`` | `Видалення підписки на події (отримання документів) <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/DeleteSubscribeController.html>`__            |
+-----------+-----------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
| GET       | ``/api/mintrans/events``    | `Отримання списку подій з ЦБД <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/MintransEvents.html>`__                                             |
+-----------+-----------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
| GET       | ``/api/mintrans/doc``       | `Отримання документа з ЦБД <https://wiki.edin.ua/uk/latest/API_ETTNv3_1/Methods/GetMintransDoc.html>`__                                                |
+-----------+-----------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+

.. beauty list

.. toctree::
   :hidden:
   :glob:

   Methods/GetSubscribeController
   Methods/PostSubscribeController
   Methods/DeleteSubscribeController
   Methods/MintransEvents
   Methods/GetMintransDoc

---------------------------------

.. _ttn-errors:

Опис помилок сервісу "ЕТТН" v3
=========================================================================================

.. csv-table:: 
  :file: new_ttn_errors.csv
  :widths:  10, 20, 20, 40
  :stub-columns: 0

Помилки, що можуть виникнути на стороні ЦБД:

.. csv-table:: 
  :file: mintrans_errors.csv
  :widths:  10, 40, 40
  :stub-columns: 0

---------------------------------

.. _main-errors:

Загальні помилки при роботі з API (всі сервіси EDIN)
=========================================================================================

.. csv-table:: 
  :file: /_constant/main_api_errors.csv
  :widths:  10, 20, 60
  :stub-columns: 0
