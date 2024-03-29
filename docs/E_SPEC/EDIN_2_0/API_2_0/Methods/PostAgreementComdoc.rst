#####################################################################################
**Прийняти «Товарне узгодження» (Мережа)**
#####################################################################################

.. important::
   Даний метод виконується на стороні Мережі для підготовки «Товарного узгодження» до підписання (документ отримує статус "Готовий до підписання"). В результаті роботи методу відбувається формування «Товарної специфікації». 

Для роботи з цим методом користувач повинен бути `авторизованим <https://wiki.edin.ua/uk/latest/E_SPEC/EDIN_2_0/API_2_0/Methods/Authorization.html>`__.

.. csv-table:: 
  :file: PostAgreementComdoc.csv
  :widths:  10, 41
  :stub-columns: 0

**RESPONSE**

В тілі **відповіді** передається XML контента документа `Товарна специфікація (COMDOC_008) <https://wiki.edin.ua/uk/latest/E_SPEC/EDIN_2_0/XML/XML_structure.html#comdoc-008>`__ в заданому вигляді.
