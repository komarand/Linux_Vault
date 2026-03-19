**Вопрос:** Что такое localhost и почему `ping localhost` может не работать?

**Ответ (кратко):**

- `localhost` — это “сам компьютер”. Обычно резолвится в:
    
    - IPv4: `127.0.0.1` (loopback)
        
    - IPv6: `::1`
        
- `ping localhost` может “падать” по нескольким причинам:
    
    1. **Не поднят loopback-интерфейс** (`lo`), либо сломана маршрутизация на него.
        
    2. **ICMP заблокирован** (фаерволом) или отключён sysctl-настройками.
        
    3. **Нет прав на raw-socket** (часто ошибка вида `Operation not permitted`): у `ping` нет `CAP_NET_RAW`/setuid.
        
    4. `localhost` резолвится в IPv6 (`::1`), а **IPv6 отключён** или ограничен.
        

**Проверки:**

- `ip addr show lo`
    
- `ip route show`
    
- `ping -4 localhost` / `ping -6 localhost`
    
- (права) `getcap $(which ping)`
    

**Связи:** [[Net — Ping и traceroute: сходство и как traceroute находит хопы]] · [[Net — Команда чтобы показать таблицу маршрутизации в Linux]] · [[Net — Ping IPv6: sendmsg operation not permitted после добавления адреса]]