##########################################################################################################################
**"Акт коригування"**
##########################################################################################################################

.. https://docs.google.com/spreadsheets/d/1eiLgIFbZBOK9hXDf2pirKB88izrdOqj1vSdV3R8tvbM/edit?pli=1#gid=1779967940

.. important::
   Зверніть увагу, що поля в json та `в xml форматі <https://wiki.edin.ua/uk/latest/Docs_ETTNv3/ADJUSTMENT_ACT/ADJUSTMENT_ACTpage_v3.html>`__ відрізняються! 

**JSON:**

.. code:: json

  {
    "ram": "urn:un:unece:uncefact:data:standard:ReusableAggregateBusinessInformationEntity:103",
    "udt": "urn:un:unece:uncefact:data:standard:UnqualifiedDataType:27",
    "qdt": "urn:un:unece:uncefact:data:standard:QualifiedDataType:103",
    "act": {
      "documentContext": {
        "transactionID": "0",
        "documentCode": {
          "id": "urn:ua:e-transport.gov.ua:act:01"
        },
        "documentSubCode": {
          "id": "urn:ua:e-transport.gov.ua:act:01:adjustment:001"
        }
      },
      "exchangedDocument": {
        "id": "123123",
        "issueDateTime": {
          "dateTime": "2022-10-26T21:32:52+02:00"
        },
        "issueLogisticsLocation": {
          "name": "Місце складання документу",
          "description": "79000, м.Львів, вул. Словацького, 1"
        },
        "includedNote": []
      },
      "adjustmentActPayload": {
        "previousAdministrativeReferencedDocuments": [
          {
            "typeCode": "730",
            "id": "004edd76-e217-4d73-be16-769896530f16",
            "formattedIssueDateTime": {
              "dateTime": "2023-07-18T19:17:00.000Z"
            }
          }
        ],
        "initiatorTradeParty": {
          "id": {
            "schemeAgencyID": "ЄДРПОУ",
            "value": "85854949"
          },
          "name": "ТОВ \"ТЕСТ 3\"",
          "roleCode": "CN"
        },
        "specifiedGovernmentRegistrations": [
          {
            "id": "9864065738701",
            "typeCode": "TRADEPARTY_GLN"
          }
        ],
        "carrierTradeParty": {
          "id": {
            "schemeAgencyID": "ЄДРПОУ",
            "value": "85854949"
          },
          "name": "ТОВ \"ТЕСТ 2\"",
          "roleCode": "CA"
        },
        "consignorTradeParty": {
          "id": {
            "schemeAgencyID": "ЄДРПОУ",
            "value": "85854949"
          },
          "name": "ТОВ \"ТЕСТ\"",
          "roleCode": "CZ"
        },
        "adjustedSupplyChainConsignment": {
          "includedSupplyChainConsignmentItems": [
            {
              "sequenceNumeric": "1",
              "natureIdentificationTransportCargo": {
                "identification": "Датчики руху автоматизовані"
              }
            }
          ]
        },
        "initiatorNotes": "Помилки в найменувані товару"
      },
      "certifyingPartyPayload": {
        "certifyingTradeParty": [
          {
            "id": {
              "schemeAgencyID": "РНОКПП",
              "value": "1234567890"
            },
            "name": "Бухгалтер",
            "roleCode": "CN",
            "tradeContact": {
              "personName": "Бухгалтер Тестового Постачальника"
            }
          }
        ]
      }
    }
  }

.. role:: orange

.. raw:: html

    <embed>
    <iframe src="https://docs.google.com/spreadsheets/d/e/2PACX-1vRPbzkPgNe3yqDqIzd_3PyYlNGPbaL27tiF7z5CPd5iexGV74qv6KkAGquRrJL9OQ/pubhtml?gid=638340231&single=true" width="1100" height="8750" frameborder="0" marginheight="0" marginwidth="0">Loading...</iframe>
    </embed>

-------------------------

.. [#] Під визначенням колонки **Тип поля** мається на увазі скорочене позначення:

   * M (mandatory) — обов'язкові до заповнення поля;
   * O (optional) — необов'язкові (опціональні) до заповнення поля.

.. [#] елементи структури мають наступний вигляд:

   * параметрЗіЗначенням;
   * **об'єктЗПараметрами**;
   * :orange:`масивОб'єктів`

.. data from table (remember to renew time to time)

    № з/п,Параметр²,Тип¹,Формат,Опис
    I,act,M,,(початок змісту документа)
    1,documentContext,M,,Технічні дані
    1.1,transactionID,M,string,Номер версії документа (транзакції) в ланцюгу підписання документів
    1.2.1,documentCode.id,M,string,код документа
    1.3.1,documentSubCode.id,M,unsignedByte,підтип документа
    2,exchangedDocument,M,,Реквізити Акта
    2.1,id,M,string,номер документа
    2.2.1,issueDateTime.dateTime,M,datetime (2021-12-13T14:19:23+02:00),Дата і час складання Акта
    2.3,remarks,O,string,Інші примітки
    2.4.1,issueLogisticsLocation.name,M,string,Найменування місця складання Акта
    2.4.2,issueLogisticsLocation.description,M,string,Опис (адреса) місця складання Акта
    3,adjustmentActPayload,M,,Зміст «Акта коригування»
    3.1,previousAdministrativeReferencedDocuments (TypeCode=730),M,,"Інформація про е-ТТН, для якої складається акт"
    3.1.1,typeCode,M,decimal,Тип документа (730 - ТТН). Довідник кодів документів
    3.1.2,id,M,string,Номер документа-підстави (ТТН); має відповідати номеру документа ExchangedDocument.ID еТТН
    3.1.3.1,formattedIssueDateTime.dateTime,M,datetime (2021-12-13T14:19:23+02:00),Дата та час документа-підстави (ТТН); має відповідати даті документа ExchangedDocument.IssueDateTime еТТН
    3.1.4,attachedSpecifiedBinaryFile,M,,"Дані е-ТТН, для якої складається акт"
    3.1.4.1,id,M,string,Ідентифікатор (guid) документа-підстави (ТТН); має відповідати document.id еТТН в ЦБД (значення ettnId з методу Отримання списку подій з ЦБД = значення external_doc_id Отримання мета-даних документа)
    3.1.4.2,uriid,O,string,посилання на документ
    3.1.4.3,MIMECode,O,string,MIME типізація
    3.1.4.4,SizeMeasure,O,long,розмір файлу в байтах
    3.2,previousAdministrativeReferencedDocuments,-/M,,"Інформація про попередній акт, у випадку наступної транзакції"
    3.2.1,typeCode,M,decimal,Тип документа. Довідник кодів документів
    3.2.2,id,M,string,Номер документа-підстави (Акт); має відповідати номеру документа ExchangedDocument.ID Акта
    3.2.3.1,formattedIssueDateTime.dateTime,M,datetime (2021-12-13T14:19:23+02:00),Дата та час документа-підстави (Акта)
    3.3,initiatorTradeParty,M,,"Ініціатор акта (Замовник). Тут наведено приклад, коли ініціатором Акта є Замовник (який не є ні Вантажовідправником, ні Вантажоодержувачем) - в документа буде чотири сторони-підписувачі: Замовник, Вантажовідправник, Перевізник та Вантажоодержувач"
    3.3.1.1,id.schemeAgencyID,M,string,ЄДРПОУ / РНОКПП Замовника
    3.3.1.2,id.value,M,decimal,Значення
    3.3.2,name,M,string,"Повне найменування Замовника (юридичної особи або ПІБ фізичної-особи підприємця), що проводить одержання (оприбуткування) перелічених в ТТН товарно-матеріальних цінностей"
    3.3.3,roleCode,M,string,Роль учасника (Замовник - OB). Довідник ролей
    3.3.4,tradeContact,O, ,Контакти відповідального представника
    3.3.4.1,personName,O,string,ПІБ
    3.3.4.2.1,telephoneUniversalCommunication.completeNumber,O,string,Основний телефон
    3.3.4.3.1,mobileTelephoneUniversalCommunication.completeNumber,O,string,Мобільний телефон
    3.3.4.4.1,emailURIUniversalCommunication.completeNumber,O,string,Електронна адреса
    3.3.5,postalTradeAddress,M, ,Юридична адреса Замовника
    3.3.5.1,postCode,O,decimal,Індекс
    3.3.5.2,streetName,M,string,Адреса (назва вулиці + номер будівлі)
    3.3.5.3,cityName,M,string,Місто (назва населеного пункту)
    3.3.5.4,countryID,M,string,Країна (UA)
    3.3.5.5,countrySubDivisionName,O,string,Область та район (за наявності)
    3.3.6.1,taxRegistration.id,O,string,РНОКПП відповідальної особи
    3.3.7,specifiedGovernmentRegistrations,M/O, ,GLN Замовника (блок обов'язковий до заповнення для відправника транзакції)
    3.3.7.1,id,M/O,decimal,GLN Замовника (поле обов'язкове до заповнення для відправника транзакції)
    3.3.7.2,typeCode,O,string,"Код типу:

    * TRADEPARTY_GLN"
    3.4,consignorTradeParty,M,,Вантажовідправник
    3.4.1.1,id.schemeAgencyID,M,string,ЄДРПОУ / РНОКПП Вантажовідправника
    3.4.1.2,id.value,M,decimal,Значення
    3.4.2,name,M,string,"Повне найменування Вантажовідправника (юридичної особи або ПІБ фізичної-особи підприємця), що проводить відвантаження (списання) перелічених в ТТН товарно-матеріальних цінностей"
    3.4.3,roleCode,M,string,Роль учасника (Вантажовідправник - CZ). Довідник ролей
    3.4.4,tradeContact,O, ,Контакти відповідального представника
    3.4.4.1,personName,O,string,ПІБ
    3.4.4.2.1,telephoneUniversalCommunication.completeNumber,O,string,Основний телефон
    3.4.4.3.1,mobileTelephoneUniversalCommunication.completeNumber,O,string,Мобільний телефон
    3.4.4.4.1,emailURIUniversalCommunication.completeNumber,O,string,Електронна адреса
    3.4.5,postalTradeAddress,M, ,Юридична адреса Вантажовідправника
    3.4.5.1,postCode,O,decimal,Індекс
    3.4.5.2,streetName,M,string,Адреса (назва вулиці + номер будівлі)
    3.4.5.3,cityName,M,string,Місто (назва населеного пункту)
    3.4.5.4,countryID,M,string,Країна (UA)
    3.4.5.5,countrySubDivisionName,O,string,Область та район (за наявності)
    3.4.6.1,taxRegistration.id,O,string,РНОКПП відповідальної особи
    3.4.7,specifiedGovernmentRegistrations,M/O, ,GLN Вантажовідправника (блок обов'язковий до заповнення для відправника транзакції)
    3.4.7.1,id,M/O,decimal,GLN Вантажовідправника (поле обов'язкове до заповнення для відправника транзакції)
    3.4.7.2,typeCode,O,string,"Код типу:

    * TRADEPARTY_GLN"
    3.5,carrierTradeParty,M,,Перевізник
    3.5.1.1,id.schemeAgencyID,M,string,ЄДРПОУ / РНОКПП Перевізника
    3.5.1.2,id.value,M,decimal,Значення
    3.5.2,name,M,string,"Повне найменування Перевізника (юридичної особи або фізичної особи - підприємця) або прізвище, ім’я, по батькові фізичної особи, з яким вантажовідправник уклав договір на надання транспортних послуг"
    3.5.3,roleCode,M,string,Роль учасника (Перевізник - CA). Довідник ролей
    3.5.4,tradeContact,M, ,Контакти відповідального представника
    3.5.4.1,personName,M,string,"ПІБ водія, що керуватиме ТЗ при перевезенні вантажу"
    3.5.4.2.1,telephoneUniversalCommunication.completeNumber,O,string,Основний телефон
    3.5.4.3.1,mobileTelephoneUniversalCommunication.completeNumber,O,string,Мобільний телефон
    3.5.4.4.1,emailURIUniversalCommunication.completeNumber,O,string,Електронна адреса
    3.5.5,postalTradeAddress,M, ,Юридична адреса Перевізника
    3.5.5.1,postCode,O,decimal,Індекс
    3.5.5.2,streetName,M,string,Адреса (назва вулиці + номер будівлі)
    3.5.5.3,cityName,M,string,Місто (назва населеного пункту)
    3.5.5.4,countryID,M,string,Країна (UA)
    3.5.5.5,countrySubDivisionName,O,string,Область та район (за наявності)
    3.5.6.1,taxRegistration.id,M,string,РНОКПП відповідальної особи (водія)
    3.5.7,specifiedGovernmentRegistrations,M, ,Посвідчення Водія / GLN Водія / GLN компанії-учасника
    3.5.7.1,id,M/O,"* string
    * decimal при typeCode=DRIVER_GLN / TRADEPARTY_GLN","* Серія та номер водійського посвідчення Водія (поле обов'язкове до заповнення). Заповнюється в форматі «3 заголовні кириличні літери + 6 цифр без пробілів», наприклад: DGJ123456, АБВ123456
    * для typeCode=DRIVER_GLN - GLN Водія (поле опціональне до заповнення)
    * для typeCode=TRADEPARTY_GLN - GLN компанії-учасника (поле обов'язкове до заповнення для відправника транзакції)"
    3.5.7.2,typeCode,O,string,"Код типу:

    * DRIVER_GLN
    * TRADEPARTY_GLN"
    3.6,consigneeTradeParty,O,,Новий Вантажоодержувач
    3.6.1.1,id.schemeAgencyID,M,string,ЄДРПОУ Вантажоодержувача
    3.6.1.2,id.value,M,decimal,Значення
    3.6.2,name,M,string,Повне найменування Вантажоодержувача
    3.6.3,roleCode,M,string,Роль учасника (Вантажоодержувач - CN). Довідник ролей
    3.6.4,tradeContact,O,,Контакти відповідального представника
    3.6.4.1,personName,O,string,ПІБ
    3.6.4.2.1,telephoneUniversalCommunication.completeNumber,O,string,Основний телефон
    3.6.4.3.1,mobileTelephoneUniversalCommunication.completeNumber,O,string,Мобільний телефон
    3.6.4.4.1,emailURIUniversalCommunication.completeNumber,O,string,Електронна адреса
    3.6.5,postalTradeAddress,M,,Юридична адреса Вантажоодержувача (юридична адреса юридичної особи або адреса реєстрації фізичної особи-підприємця)
    3.6.5.1,postCode,O,decimal,Індекс
    3.6.5.2,streetName,M,string,Адреса (назва вулиці + номер будівлі)
    3.6.5.3,cityName,M,string,Місто (назва населеного пункту)
    3.6.5.4,countryID,M,string,Країна (UA)
    3.6.5.5,countrySubDivisionName,O,string,Область та район (за наявності)
    3.6.6.1,specifiedTaxRegistration.id,O,string,РНОКПП відповідальної особи Вантажоодержувача
    3.6.7,specifiedGovernmentRegistrations,M,,GLN Вантажоодержувача
    3.6.7.1,id,M/O,decimal,GLN компанії-учасника (поле обов’язкове до заповнення для відправника транзакції)
    3.6.7.2,typeCode,O,string,"Код типу:
      TRADEPARTY_GLN"
    3.7,adjustedSupplyChainConsignment,M,,Таблиця коригувань
    3.7.1,consignor,O,,Вантажовідправник
    3.7.1.1,name,M,string,"Повне найменування Вантажовідправника (юридичної особи або ПІБ фізичної-особи підприємця), що проводить відвантаження (списання) перелічених в ТТН товарно-матеріальних цінностей"
    3.7.1.2,tradeContact,O,,Контакти відповідального представника
    3.7.1.2.1,personName,O,string,ПІБ
    3.7.1.2.2.1,telephoneUniversalCommunication.completeNumber,O,string,Основний телефон
    3.7.1.2.3.1,mobileTelephoneUniversalCommunication.completeNumber,O,string,Мобільний телефон
    3.7.1.2.4.1,emailURIUniversalCommunication.completeNumber,O,string,Електронна адреса
    3.7.1.3,postalTradeAddress,M,,Юридична адреса Вантажовідправника
    3.7.1.3.1,postCode,O,decimal,Індекс
    3.7.1.3.2,streetName,M,string,Адреса (назва вулиці + номер будівлі)
    3.7.1.3.3,cityName,M,string,Місто (назва населеного пункту)
    3.7.1.3.4,countryID,M,string,Країна (UA)
    3.7.1.3.5,countrySubDivisionName,O,string,Область та район (за наявності)
    3.7.1.4.1,specifiedGovernmentRegistrations.id,M/O,decimal,GLN Вантажовідправника (поле обов’язкове до заповнення для відправника транзакції)
    3.7.1.4.2,specifiedGovernmentRegistrations.typeCode,O,string,"Код типу:
      TRADEPARTY_GLN"
    3.7.2,consignee,O,,Вантажоодержувач
    3.7.2.1,name,M,string,"Повне найменування Вантажоодержувача (юридичної особи або ПІБ фізичної-особи підприємця), що проводить одержання (оприбуткування) перелічених в ТТН товарно-матеріальних цінностей"
    3.7.2.2,tradeContact,O,,Контакти відповідального представника
    3.7.2.2.1,personName,O,string,ПІБ
    3.7.2.2.2.1,telephoneUniversalCommunication.completeNumber,O,string,Основний телефон
    3.7.2.2.3.1,mobileTelephoneUniversalCommunication.completeNumber,O,string,Мобільний телефон
    3.7.2.2.4.1,emailURIUniversalCommunication.completeNumber,O,string,Електронна адреса
    3.7.2.3,postalTradeAddress,O,,Юридична адреса Вантажоодержувача
    3.7.2.3.1,postCode,O,decimal,Індекс
    3.7.2.3.2,streetName,M,string,Адреса (назва вулиці + номер будівлі)
    3.7.2.3.3,cityName,M,string,Місто (назва населеного пункту)
    3.7.2.3.4,countryID,M,string,Країна (UA)
    3.7.2.3.5,countrySubDivisionName,O,string,Область та район (за наявності)
    3.7.2.4.1,specifiedGovernmentRegistrations.id,M/O,decimal,GLN Вантажоодержувача (поле обов’язкове до заповнення для відправника транзакції)
    3.7.2.4.2,specifiedGovernmentRegistrations.typeCode,O,string,"Код типу:
      TRADEPARTY_GLN"
    3.7.3,carrier,O,,Перевізник
    3.7.3.1,name,M,string,"Повне найменування Перевізника (юридичної особи або фізичної особи - підприємця) або прізвище, ім’я, по батькові фізичної особи, з яким вантажовідправник уклав договір на надання транспортних послуг"
    3.7.3.2,tradeContact,O,,Контакти відповідального представника
    3.7.3.2.1,personName,M,string,"ПІБ водія, що керуватиме ТЗ при перевезенні вантажу"
    3.7.3.2.2.1,telephoneUniversalCommunication.completeNumber,O,string,Основний телефон
    3.7.3.2.3.1,mobileTelephoneUniversalCommunication.completeNumber,O,string,Мобільний телефон
    3.7.3.2.4.1,emailURIUniversalCommunication.completeNumber,O,string,Електронна адреса
    3.7.3.3,postalTradeAddress,M,,Юридична адреса Перевізника
    3.7.3.3.1,postCode,O,decimal,Індекс
    3.7.3.3.2,streetName,M,string,Адреса (назва вулиці + номер будівлі)
    3.7.3.3.3,cityName,M,string,Місто (назва населеного пункту)
    3.7.3.3.4,countryID,M,string,Країна (UA)
    3.7.3.3.5,countrySubDivisionName,O,string,Область та район (за наявності)
    3.7.3.4.1,specifiedGovernmentRegistrations.id,M/O,"* string
    * decimal при typeCode=DRIVER_GLN / TRADEPARTY_GLN","Серія та номер водійського посвідчення Водія (поле обов’язкове до заповнення). Заповнюється в форматі «3 заголовні кириличні літери + 6 цифр без пробілів», наприклад: DGJ123456, АБВ123456

    для typeCode=DRIVER_GLN - GLN Водія (поле опціональне до заповнення)

    для typeCode=TRADEPARTY_GLN - GLN компанії-учасника (поле обов’язкове до заповнення для відправника транзакції)"
    3.7.3.4.2,specifiedGovernmentRegistrations.typeCode,O,string,"Код типу:
      DRIVER_GLN

    TRADEPARTY_GLN"
    3.7.4,notifiedTradeParties (роль - FW),O,,Експедитор
    3.7.4.1.1,id.schemeAgencyID,M,string,ЄДРПОУ / РНОКПП Експедитора
    3.7.4.1.2,id.value,M,decimal,Значення
    3.7.4.2,name,M,string,"Повне найменування Експедитора (юридичної особи або фізичної особи - підприємця) або прізвище, ім’я, по батькові фізичної особи, з яким вантажовідправник (замовник) уклав договір траспортного експедирування"
    3.7.4.3,roleCode,M,string,Роль учасника (Експедитор - FW). Довідник ролей
    3.7.4.4,tradeContact,O,,Контакти відповідального представника
    3.7.4.4.1,personName,O,string,ПІБ
    3.7.4.4.2.1,telephoneUniversalCommunication.completeNumber,O,string,Основний телефон
    3.7.4.4.3.1,mobileTelephoneUniversalCommunication.completeNumber,O,string,Мобільний телефон
    3.7.4.4.4.1,emailURIUniversalCommunication.completeNumber,O,string,Електронна адреса
    3.7.4.5,postalTradeAddress,O,,Юридична адреса Експедитора
    3.7.4.5.1,postCode,O,decimal,Індекс
    3.7.4.5.2,streetName,M,string,Адреса (назва вулиці + номер будівлі)
    3.7.4.5.3,cityName,M,string,Місто (назва населеного пункту)
    3.7.4.5.4,countryID,M,string,Країна (UA)
    3.7.4.5.5,countrySubDivisionName,O,string,Область та район (за наявності)
    3.7.4.6.1,taxRegistration.id,O,string,РНОКПП відповідальної особи
    3.7.4.7.1,specifiedGovernmentRegistrations.id,M/O,decimal,GLN Експедитора (поле обов’язкове до заповнення для відправника транзакції)
    3.7.4.7.2,specifiedGovernmentRegistrations.typeCode,O,string,"Код типу:
      TRADEPARTY_GLN"
    3.7.5,notifiedTradeParties (роль - OB),O,,Замовник
    3.7.5.1.1,id.schemeAgencyID,M,string,ЄДРПОУ / РНОКПП Замовника
    3.7.5.1.2,id.value,M,decimal,Значення
    3.7.5.2,name,M,string,"Повне найменування Замовника (юридичної особи або фізичної особи - підприємця) або прізвище, ім’я, по батькові фізичної особи, що проводить оплату транспортної роботи і послуг"
    3.7.5.3,roleCode,M,string,Роль учасника (Замовник - OB). Довідник ролей
    3.7.5.4,tradeContact,O,,Контакти відповідального представника
    3.7.5.4.1,personName,O,string,ПІБ
    3.7.5.4.2.1,telephoneUniversalCommunication.completeNumber,O,string,Основний телефон
    3.7.5.4.3.1,mobileTelephoneUniversalCommunication.completeNumber,O,string,Мобільний телефон
    3.7.5.4.4.1,emailURIUniversalCommunication.completeNumber,O,string,Електронна адреса
    3.7.5.5,postalTradeAddress,O,,Юридична адреса Замовника
    3.7.5.5.1,postCode,O,decimal,Індекс
    3.7.5.5.2,streetName,M,string,Адреса (назва вулиці + номер будівлі)
    3.7.5.5.3,cityName,M,string,Місто (назва населеного пункту)
    3.7.5.5.4,countryID,M,string,Країна (UA)
    3.7.5.5.5,countrySubDivisionName,O,string,Область та район (за наявності)
    3.7.5.6.1,taxRegistration.id,O,string,РНОКПП відповідальної особи
    3.7.5.7.1,specifiedGovernmentRegistrations.id,M/O,decimal,GLN Замовника (поле обов’язкове до заповнення для відправника транзакції)
    3.7.5.7.2,specifiedGovernmentRegistrations.typeCode,O,string,"Код типу:
      TRADEPARTY_GLN"
    3.7.6,notifiedTradeParties (роль - WD),O,,Проміжний склад
    3.7.6.1.1,id.schemeAgencyID,M,string,ЄДРПОУ / РНОКПП Проміжного складу
    3.7.6.1.2,id.value,M,decimal,Значення
    3.7.6.2,name,M,string,"Повне найменування Проміжного складу (Вантажовідправник/Перевізник/Експедитор/Вантажоодержувач/Товарний склад), що приймає від Перевізника на тимчасове зберігання вантаж"
    3.7.6.3,roleCode,M,string,Роль учасника (Проміжний склад - WD). Довідник ролей
    3.7.6.4,tradeContact,O,,Контакти відповідального представника
    3.7.6.4.1,personName,O,string,ПІБ
    3.7.6.4.2.1,telephoneUniversalCommunication.completeNumber,O,string,Основний телефон
    3.7.6.4.3.1,mobileTelephoneUniversalCommunication.completeNumber,O,string,Мобільний телефон
    3.7.6.4.4.1,emailURIUniversalCommunication.completeNumber,O,string,Електронна адреса
    3.7.6.5,postalTradeAddress,O,,Юридична адреса Проміжного складу
    3.7.6.5.1,postCode,O,decimal,Індекс
    3.7.6.5.2,streetName,M,string,Адреса (назва вулиці + номер будівлі)
    3.7.6.5.3,cityName,M,string,Місто (назва населеного пункту)
    3.7.6.5.4,countryID,M,string,Країна (UA)
    3.7.6.5.5,countrySubDivisionName,O,string,Область та район (за наявності)
    3.7.6.6.1,taxRegistration.id,O,string,РНОКПП відповідальної особи
    3.7.6.7.1,specifiedGovernmentRegistrations.id,M/O,decimal,GLN Проміжного складу (поле обов’язкове до заповнення для відправника транзакції)
    3.7.6.7.2,specifiedGovernmentRegistrations.typeCode,O,string,"Код типу:
      TRADEPARTY_GLN"
    3.7.7,notifiedTradeParties (роль - COP),O,,Охоронна компанія
    3.7.7.1.1,id.schemeAgencyID,M,string,ЄДРПОУ / РНОКПП Охоронної компанії
    3.7.7.1.2,id.value,M,decimal,Значення
    3.7.7.2,name,M,string,"Повне найменування Охоронної компанії, що надає охоронні послуги вантажу під час перевезення"
    3.7.7.3,roleCode,M,string,Роль учасника (Охоронна компанія - COP). Довідник ролей
    3.7.7.4,tradeContact,O,,Контакти відповідального представника
    3.7.7.4.1,personName,O,string,"ПІБ представника Замовника, який уповноважений супроводжувати вантаж, що підлягає спеціальній охороні"
    3.7.8,carrierAcceptanceLogisticsLocation,O,,Пункт навантаження
    3.7.8.1.1,id.schemeAgencyID,M,string,КАТОТТГ пункту навантаження
    3.7.8.1.2,id.value,M,string,Значення
    3.7.8.2,name,M,string,Найменування пункту навантаження
    3.7.8.3,typeCode,M,decimal,Тип операції: 10 - навантаження; 5 - розвантаження
    3.7.8.4,description,M,string,Опис (адреса) пункту навантаження
    3.7.8.5,physicalGeographicalCoordinate,M,,Географічні координати
    3.7.8.5.1,latitudeMeasure,O,string,Географічні координати (Широта)
    3.7.8.5.2,longitudeMeasure,O,string,Географічні координати (Довгота)
    3.7.8.5.3.1,systemId.schemeAgencyID,M,string,GLN
    3.7.8.5.3.2,systemId.value,M,decimal,Значення
    3.7.9,consigneeReceiptLogisticsLocation,O,,Пункт розвантаження
    3.7.9.1.1,id.schemeAgencyID,M,string,КАТОТТГ пункту розвантаження
    3.7.9.1.2,id.value,M,string,Значення
    3.7.9.2,name,M,string,Найменування пункту розвантаження
    3.7.9.3,typeCode,M,decimal,Тип операції: 10 - навантаження; 5 - розвантаження
    3.7.9.4,description,M,string,Опис (адреса) пункту розвантаження
    3.7.9.5,physicalGeographicalCoordinate,M,,Географічні координати
    3.7.9.5.1,latitudeMeasure,O,string,Географічні координати (Широта)
    3.7.9.5.2,longitudeMeasure,O,string,Географічні координати (Довгота)
    3.7.9.5.3.1,systemId.schemeAgencyID,M,string,GLN
    3.7.9.5.3.2,systemId.value,M,decimal,Значення
    3.7.10,deliveryTransportEvent,O,,Розвантажувальні роботи
    3.7.10.1,id,O,string,Порядковий номер події (події завжди нумеруються в порядку поступового зростання за принципом N+1)
    3.7.10.2,typeCode,O,decimal,"Тип операції (розвантаження=5, завантаження=10)"
    3.7.10.3,description,O,string,Опис
    3.7.10.4.1,actualOccurrenceDateTime.dateTime,O,datetime (2021-12-13T14:19:23+02:00),Дата та час прибуття автомобіля на розвантаження
    3.7.10.5.1,scheduledOccurrenceDateTime.dateTime,O,datetime (2021-12-13T14:19:23+02:00),Дата та час вибуття автомобіля з-під розвантаження
    3.7.10.6.1,applicableNotes (з кодом DOWNTIME).contentCode,O,string,Код DOWNTIME
    3.7.10.6.2,applicableNotes (з кодом DOWNTIME).content,O,unsignedByte,Час (години) простою під розвантаженням
    3.7.11,pickUpTransportEvent,M,,Навантажувальні роботи
    3.7.11.1,id,O,string,Порядковий номер події (події завжди нумеруються в порядку поступового зростання за принципом N+1)
    3.7.11.2,typeCode,O,string,"Тип операції (розвантаження=5, завантаження=10)"
    3.7.11.3,description,O,string,Опис
    3.7.11.4.1,actualOccurrenceDateTime.dateTime,O,datetime (2021-12-13T14:19:23+02:00),Дата та час прибуття автомобіля під навантаження
    3.7.11.5.1,scheduledOccurrenceDateTime.dateTime,O,datetime (2021-12-13T14:19:23+02:00),Дата та час вибуття автомобіля з-під навантаження
    3.7.11.6.1,applicableNotes (з кодом DOWNTIME).contentCode,O,string,Код DOWNTIME
    3.7.11.6.2,applicableNotes (з кодом DOWNTIME).content,O,unsignedByte,Час простою
    3.7.12,includedSupplyChainConsignmentItems,O,,Відомості про вантаж
    3.7.12.1.1,globalID.schemeAgencyID,O,string (min 4 - max 10),УКТЗЕД (код продукції)
    3.7.12.1.2,globalID.value,O,string,Значення
    3.7.12.2.1,natureIdentificationTransportCargo.identification,O,string,Найменування вантажу
    3.7.12.3.1,applicableTransportDangerousGoods.UNDGIdentificationCode,O,decimal,"Клас небезпечних речовин, до якого віднесено вантаж (у разі перевезення небезпечних вантажів). Код UNDG, 0 - якщо не використовується"
    3.7.12.4.1,associatedReferencedDocuments.id,O,string,"Документи з вантажем. Номер документа, який водій отримує від вантажовідправника і передає вантажоодержувачеві разом з вантажем (товарні, залізничні накладні, сертифікати, свідоцтва тощо)"
    3.7.12.4.2,associatedReferencedDocuments.remarks,O,string,UUID супровідного документа
    3.7.12.5,transportLogisticsPackage,O,,Транспортно-логістичний пакет. ВАЖЛИВО: в Україні дозволяється лише один LogisticsPackage для одного ConsignmentItem!
    3.7.12.5.1,itemQuantity,O,decimal,"Кількість місць, які визначаються за кожним найменуванням вантажу (це можуть бути ящики, кошики, мішки тощо; якщо вантаж упаковано на піддонах - вказують кількість піддонів)"
    3.7.12.5.2,typeCode,O,string,Вид пакування (Довідник видів упаковок)
    3.7.12.5.3,type,O,string,Одиниця виміру для itemQuantity
    3.7.12.5.4,physicalLogisticsShippingMarks,O,,Маркування
    3.7.12.5.4.1,marking,O,string,"Назва транспортної упаковки (вільна назва), в якій перевозиться вантаж"
    3.7.12.5.4.2.1,barcodeLogisticsLabel.id,O,string (max 128),Штрихкод товару
    3.7.12.6.1,applicableNotes (з кодом VENDOR_CODE).contentCode,O,string,Код VENDOR_CODE
    3.7.12.6.2,applicableNotes (з кодом VENDOR_CODE).content,O,string,Артикул товару
    3.7.12.7.1,applicableNotes (з кодом QUANTITY).contentCode,O,string,Код QUANTITY
    3.7.12.7.2,applicableNotes (з кодом QUANTITY).content,O,string,Кількість товару
    3.7.12.8.1,applicableNotes (з кодом URL).contentCode,O,string,Код URL
    3.7.12.8.2,applicableNotes (з кодом URL).content,O,string,Посилання на документ
    3.7.12.9.1,applicableNotes (з кодом BASE_UOM).contentCode,O,string,Код BASE_UOM
    3.7.12.9.2,applicableNotes (з кодом BASE_UOM).content,O,string,Одиниця виміру кількості товару для QUANTITY
    3.7.12.10.1,applicableNotes (з кодом BUYER_CODE).contentCode,O,string,Код BUYER_CODE
    3.7.12.10.2,applicableNotes (з кодом BUYER_CODE).content,O,string,Артикул покупця (використовується для ідентифікації товарної позиції при прийманні)
    3.7.12.11.1,applicableNotes (з кодом PRICE_WITH_VAT).contentCode,O,string,Код PRICE_WITH_VAT
    3.7.12.11.2,applicableNotes (з кодом PRICE_WITH_VAT).content,O,string,Ціна за одиницю з ПДВ
    3.7.12.12.1,applicableNotes (з кодом SUM_WITHOUT_VAT).contentCode,O,string,Код SUM_WITHOUT_VAT
    3.7.12.12.2,applicableNotes (з кодом SUM_WITHOUT_VAT).content,O,string,Загальна сума без ПДВ
    3.7.12.13.1,applicableNotes (з кодом RETURN_TARE).contentCode,O,string,Код RETURN_TARE
    3.7.12.13.2,applicableNotes (з кодом RETURN_TARE).content,O,string,Ознака «зворотня тара»
    3.7.12.14.1,applicableNotes (з кодом NET_WEIGHT).contentCode,O,string,Код NET_WEIGHT
    3.7.12.14.2,applicableNotes (з кодом NET_WEIGHT).content,O,string,Маса нетто
    3.7.12.15.1,applicableNotes (з кодом RTP_QUANTITY).contentCode,O,string,Код RTP_QUANTITY
    3.7.12.15.2,applicableNotes (з кодом RTP_QUANTITY).content,O,string,Кількість транспортної упаковки (використовується для обліку оборотної тари)
    3.7.13,deliveryInstructions,O,,Вид перевезень
    3.7.13.1,description,O,string,"Опис (вид роботи перевізника: за відрядним тарифом, за погодинним тарифом, за покілометровим тарифом, централізовані перевезення тощо)"
    3.7.13.2,descriptionCode,M,string,Код (TRANSPORTATION_TYPE)
    3.8,initiatorNotes,M,string,Короткий або повний опис причин складання акта (Замовник)
    3.9,consignorNotes,O,string,Особливі відмітки / Інформація щодо незгоди зі змістом Акта (Вантажовідправник)
    3.10,carrierNotes,O,string,Особливі відмітки / Інформація щодо незгоди зі змістом Акта (Перевізник)
    3.11,consigneeNotes,O,string,Особливі відмітки / Інформація щодо незгоди зі змістом Акта (Вантажоодержувач)
    4,certifyingPartyPayload,M,,Інформація про відповідальних осіб
    4.1,certifyingTradeParty (RoleCode=ОВ),M,,Інформація про Замовника
    4.1.1.1,id.schemeAgencyID,O,string,РНОКПП
    4.1.1.2,id.value,O,decimal,Значення
    4.1.2,name,M,string,Посада Замовника
    4.1.3,roleCode,M,string,Роль учасника (Замовник - OB). Довідник ролей
    4.1.4.1,tradeContact.personName,M,string,ПІБ Замовника
    4.2,certifyingTradeParty (RoleCode=CZ),M,,Інформація про відповідальних осіб Вантажовідправника
    4.2.1.1,id.schemeAgencyID,O,string,РНОКПП
    4.2.1.2,id.value,O,decimal,Значення
    4.2.2,name,M,string,Посада відповідальної особи Вантажовідправника
    4.2.3,roleCode,M,string,Роль учасника (Вантажовідправник - CZ). Довідник ролей
    4.2.4.1,tradeContact.personName,M,string,ПІБ відповідальної особи Вантажовідправника
    4.3,certifyingTradeParty (RoleCode=CA),M,,Інформація про Перевізника
    4.3.1.1,id.schemeAgencyID,O,string,РНОКПП
    4.3.1.2,id.value,O,decimal,Значення
    4.3.2,name,M,string,Посада Перевізника
    4.3.3,roleCode,M,string,Роль учасника (Перевізник - CA). Довідник ролей
    4.3.4.1,tradeContact.personName,M,string,ПІБ Перевізника
    4.4,certifyingTradeParty (RoleCode=CN),O,,Інформація про відповідальних осіб Вантажоодержувача
    4.4.1.1,id.schemeAgencyID,O,string,РНОКПП
    4.4.1.2,id.value,O,decimal,Значення
    4.4.2,name,M,string,Посада відповідальної особи Вантажоодержувача
    4.4.3,roleCode,M,string,Роль учасника (Вантажоодержувач - CN). Довідник ролей
    4.4.4.1,tradeContact.personName,M,string,ПІБ відповідальної особи Вантажоодержувача
    II,signatureStorage,M,,Підписи
    5,signatures (SigningPartyRoleCode=OB),M,,КЕП Замовника
    5.1,signingPartyRoleCode,M,string,Роль підписанта (Замовник - OB). Довідник ролей
    5.2,partySignature,M,string,Підпис (base64 підпису p7s)
    5.3,name,M,string,ПІБ підписанта (Замовника)
    5.4,position,O,string,Посада підписанта (Замовника)
    5.5.1,specifiedTaxRegistration.id,M,string,РНОКПП підписанта (Замовника)
    6,signatures (SigningPartyRoleCode=CZ),M,,КЕП Вантажовідправника
    6.1,signingPartyRoleCode,M,string,Роль підписанта (Вантажовідправник - CZ). Довідник ролей
    6.2,partySignature,M,string,Підпис (base64 підпису p7s)
    6.3,name,M,string,ПІБ підписанта (відповідальної особи Вантажовідправника)
    6.4,position,O,string,Посада підписанта (відповідальної особи Вантажовідправника)
    6.5.1,specifiedTaxRegistration.id,M,string,РНОКПП підписанта (відповідальної особи Вантажовідправника)
    7,signatures (SigningPartyRoleCode=CA),M,,КЕП Перевізника
    7.1,signingPartyRoleCode,M,string,Роль підписанта (Перевізник - CA). Довідник ролей
    7.2,partySignature,M,string,Підпис (base64 підпису p7s)
    7.3,name,M,string,ПІБ підписанта (Перевізника)
    7.4,position,O,string,Посада підписанта (Перевізника)
    7.5.1,specifiedTaxRegistration.id,M,string,РНОКПП підписанта (Перевізника)
    8,signatures (SigningPartyRoleCode=CN),M,,КЕП Вантажоодержувача
    8.1,signingPartyRoleCode,M,string,Роль підписанта (Вантажоодержувач - CN). Довідник ролей
    8.2,partySignature,M,string,Підпис (base64 підпису p7s)
    8.3,name,M,string,ПІБ підписанта (відповідальної особи Вантажоодержувача)
    8.4,position,O,string,Посада підписанта (відповідальної особи Вантажоодержувача)
    8.5.1,specifiedTaxRegistration.id,M,string,РНОКПП підписанта (відповідальної особи Вантажоодержувача)


.. old style

  Таблиця 1 - Специфікація "Акта коригування" (JSON)

  .. csv-table:: 
    :file: for_csv/adjustment_act_v3_json.csv
    :widths:  1, 1, 5, 12, 41
    :header-rows: 1
    :stub-columns: 0
