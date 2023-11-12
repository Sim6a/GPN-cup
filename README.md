# Постановка задачи

Мы являемся управляющим магазина, который торгует различными товарами в разных городах. Основываясь на имеющихся исторических данных о наших ценах и ценах конкурентов, нужно выставить цены на следующий период. Цен указаываются в золотых, одна золотая делится на 100 серебряных, поэтому цена указывается до сотых.

**Правила ценообразования**
- одна цена на товар должна держаться больше, чем 3 дня;
- запрещается изменение цены больше, чем на 1 золотой за раз;
- цена не должна быть больше, чем на 20% выше цены конкурентов;

Необходимо составить расписание цен для 5 городов, 3 продуктов на 90 дней в соответствии с правилами, описанными выше. Результат отправляется в формате .parquet. Всего должно быть 1350 строк. Результат должен содержать следующие колонки:
- ```day_number``` — день, для которого выставляеся цена (от 1 до 90 включительно); 
- ```product``` — продукт (эстус, эльфийская пыльца, целебные травы);
- ```place``` — город наблюдения (Фалькония, Анор Лондо, Врата Балдура, Нокрон и Кеджистан);
- ```price``` — цена в золотых (округленная до сотых — серебряные)

Целевой результат - максимизировать прибыль, которая считается по формуле ```price*amount − cost*amount```

# Описание данных
1) **Данные о транзакциях**
- ```product``` — название продукта;
- ```price``` — цена одной унции продукта в золотых;
- ```amount``` — объем проданного товара в унциях;
- ```place``` — город продажи;
- ```datetime``` — дата и время продажи;
2) **Данные о ценах конкурентов**
- ```date``` — дата наблюдения за ценой конкурента;
- ```product``` — название продукта;
- ```competitor``` — название лавки конкурента;
- ```place``` — город, в котором была замечена данная цена;
- ```price``` — цена продукта у конкурента;
3) **Данные о погоде**
- ```date``` — дата наблюдения;
- ```place``` — место наблюдения;
- ```rain``` — был ли дождь в это время в этом месте;
- ```hot``` — была ли жара в это время в этом месте;
- ```snow``` — был ли снег в это время в этом месте;
4) **Данные о себестоимости**
- ```date``` — дата наблюдения;
- ```place``` — место наблюдения;
- ```product``` — продукт;
- ```cost``` — затраты на производство одной унции продукта;



