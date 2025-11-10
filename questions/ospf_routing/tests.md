# Тесты: Маршрутизация OSPF

## Вопросы с множественным выбором

1. **Что означает аббревиатура OSPF?**  
   a) Open Shortest Path First  
   b) Optimized System Protocol Framework  
   c) Open System Packet Forwarding  
   d) Optimized Shortest Path Finder  
   **Правильный ответ: a**

2. **К какому типу протоколов относится OSPF?**  
   a) Exterior Gateway Protocol  
   b) Interior Gateway Protocol  
   c) Border Gateway Protocol  
   d) Link State Protocol  
   **Правильный ответ: b**

3. **Какой алгоритм использует OSPF для расчета кратчайших путей?**  
   a) Bellman-Ford  
   b) Dijkstra  
   c) Floyd-Warshall  
   d) Kruskal  
   **Правильный ответ: b**

4. **Что такое backbone area в OSPF?**  
   a) Area 1  
   b) Area 0  
   c) Area 0.0.0.0  
   d) Все вышеперечисленное  
   **Правильный ответ: d**

5. **Какой тип LSA описывает маршруты к сетям внутри области?**  
   a) Type 1 (Router LSA)  
   b) Type 2 (Network LSA)  
   c) Type 3 (Summary LSA)  
   d) Type 5 (AS External LSA)  
   **Правильный ответ: a**

6. **Что такое ABR в OSPF?**  
   a) Area Border Router  
   b) Autonomous System Border Router  
   c) Advanced Border Router  
   d) Access Border Router  
   **Правильный ответ: a**

7. **В каком состоянии OSPF соседи полностью синхронизированы?**  
   a) Two-way  
   b) Exstart  
   c) Full  
   d) Loading  
   **Правильный ответ: c**

8. **Какой порт использует OSPF для инкапсуляции пакетов?**  
   a) 89  
   b) 179  
   c) 520  
   d) 161  
   **Правильный ответ: a**

9. **Что такое stub area в OSPF?**  
   a) Область без маршрутизаторов  
   b) Область, которая не получает внешние маршруты  
   c) Область с одним ABR  
   d) Область без backbone  
   **Правильный ответ: b**

10. **Как рассчитывается стоимость маршрута в OSPF по умолчанию?**  
    a) Reference bandwidth / Interface bandwidth  
    b) Interface bandwidth / Reference bandwidth  
    c) Reference bandwidth * Interface bandwidth  
    d) Interface bandwidth + Reference bandwidth  
    **Правильный ответ: a**

11. **Что такое DR в OSPF?**  
    a) Designated Router  
    b) Dynamic Router  
    c) Default Router  
    d) Data Router  
    **Правильный ответ: a**

12. **Какой тип LSA анонсирует внешние маршруты в OSPF?**  
    a) Type 1  
    b) Type 3  
    c) Type 5  
    d) Type 7  
    **Правильный ответ: c**

13. **Что такое NSSA в OSPF?**  
    a) Not So Stubby Area  
    b) Network Stub System Area  
    c) New Stub System Area  
    d) Non-Standard Stub Area  
    **Правильный ответ: a**

14. **Какой multicast-адрес использует OSPF для всех маршрутизаторов?**  
    a) 224.0.0.1  
    b) 224.0.0.5  
    c) 224.0.0.6  
    d) 224.0.0.9  
    **Правильный ответ: b**

15. **Что такое виртуальная ссылка в OSPF?**  
    a) Физическое соединение между областями  
    b) Логическое соединение через транзитную область  
    c) Соединение с внешней сетью  
    d) Соединение между ABR  
    **Правильный ответ: b**

16. **Какие типы сетей поддерживает OSPF?**  
    a) Только broadcast  
    b) Только point-to-point  
    c) Broadcast, point-to-point, NBMA  
    d) Только wireless  
    **Правильный ответ: c**

17. **Какой команды нет в OSPF single-area конфигурации?**  
    a) router ospf 1  
    b) network 192.168.1.0 0.0.0.255 area 0  
    c) area 0 stub  
    d) ip ospf priority 100  
    **Правильный ответ: c**

## Инструкции

Каждый вопрос имеет 4 варианта ответа. Выберите один правильный. Правильные ответы отмечены в конце каждого вопроса для самопроверки.
