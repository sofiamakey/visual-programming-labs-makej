```
flowchart TD
    Start([Старт: Выбор дат]) --> CheckDates{Есть свободные номера?}
    
    CheckDates -- Нет --> ChangeDates[Предложить клиенту другие даты]
    ChangeDates --> Start
    
    CheckDates -- Да --> EnterData[Ввод данных гостя и переход к оплате]
    EnterData --> Pay[Запрос на списание денег]
    Pay --> CheckPay{Оплата прошла?}
    
    CheckPay -- Нет --> Retry[Ошибка: сменить карту]
    Retry --> Pay
    
    CheckPay -- Да --> Confirm[Формирование ваучера и фиксация брони]
    Confirm --> Finish([Бронь подтверждена: Конец])
```