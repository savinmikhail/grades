### Codestyle

1. Если тело функции более 5 строк кода, писать docblock к функции - обязательно

    Примеры
    - Здесь комментарии излишни

    ```php
    public function saved(Order $order): void
        {
            event(new OrderSaved($order));
            event(new WorkDayChanged($order));
        }
    ```

    - Нужен комментарий, чтоб было проще понять логику
    ```php
        /**
         * Mark order as completed,
         * log that user completed given order,
         * activate the next one
         */
        public function completeOrder(CompleteOrderDTO $dto): CompleteOrderResource
        {
            Order::query()
                ->where('id', $dto->orderId)
                ->update([
                    'status' => OrderStatus::Completed->value,
                    'empty_bottles' => $dto->emptyBottles,
                    'discrepancy_reason_id' => $dto->discrepancyReasonId,
                ]);
            $userId = Order::getExpeditorIdByOrderId($dto->orderId);
            $this->logAction(
                action: ActionsToLog::Complete,
                userId: $userId,
            );
            $this->activateNextOrder($userId);

            return new CompleteOrderResource([]);
        }
    ```

1. Тело функции не должно превышать 30 строк

1. Количество аргументов, передаваемых в функцию, не должно превышать 5.

1. Аргументы должны быть типизированы

1. Тип возвращаемых данных должен быть указан

1. Соблюдать стандарт PSR12 (форматировать код средствами phpcs, или встроенными способами IDE)

1. Не выносить бизнес логику в контроллеры. Использовать либо Action классы, либо Service классы.

    - Пример тонкого контроллера (реквест валидирует данные, сервис их достает, возвращает ресурс)

    ```php
        /**
         * получить все заказы с товарами для указанной даты и текущего пользователя
         */
        public function getAll(GetOrdersRequest $request): JsonResponse
        {
            return $this->orderService->getAll($request->toDTO())->response();
        }
    ```
1. Комментарии писать на русском

1. Docker container'ы называть в стиле project_name_servcie

1. Формировать git commit messages в соответствии со [стандартом](https://www.conventionalcommits.org/en/v1.0.0/) 