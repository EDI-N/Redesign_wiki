#########################################################################################################
**Видалити товарну позицію з власного "Прайс-листа" / Видалити власний "Прайс-лист"**
#########################################################################################################

Для роботи з цим методом користувач повинен бути `авторизованим <https://wiki.edin.ua/uk/latest/API_Openprice/Methods/Authorization.html>`__ .

.. attention::
   Даний метод використовується користувачами, що виступають в якості **Продавця (Виробника)**.

.. important:: 
   Якщо в запиті передається параметр **list_id**, то видаляється товарна позиція з власного "Прайс-листа"!
   
   Якщо параметр **list_id** в запиті відсутній або рівний 0, то видаляється власний "Прайс-лист" повністю!

.. csv-table:: 
  :file: EPriceListDelete.csv
  :widths:  10, 41
  :stub-columns: 0

**RESPONSE**

Код сервера 200 (ok).





                              

