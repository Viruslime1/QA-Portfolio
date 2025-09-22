# 🐞 BugFix Example: Корзина не очищается после оформления заказа

## Bug Report (из Jira)
**ID:** BUG-03  
**Summary:** Корзина не очищается после оформления заказа  
**Severity:** Major  
**Priority:** High  
**Steps to Reproduce:**
1. Добавить товар в корзину
2. Перейти к оформлению заказа
3. Завершить заказ
4. Вернуться в корзину  

**Actual Result:** Корзина всё ещё содержит заказанный товар  
**Expected Result:** После успешного оформления корзина должна быть пустой  

---

## ❌ Код до исправления (с багом)

```python
class Cart:
    def __init__(self):
        self.items = []

    def add_item(self, item):
        self.items.append(item)

    def checkout(self):
        print("Заказ оформлен!")
        # ❌ Корзина НЕ очищается после оформления
        return True



## ✅ Код после исправления
class Cart:
    def __init__(self):
        self.items = []

    def add_item(self, item):
        self.items.append(item)

    def checkout(self):
        print("Заказ оформлен!")
        # ✅ После оформления очищаем корзину
        self.items.clear()
        return True

Тест после фикса
cart = Cart()
cart.add_item("Товар 1")
cart.add_item("Товар 2")

cart.checkout()

if len(cart.items) == 0:
    print("✅ Тест пройден: корзина очищается")
else:
    print("❌ Тест провален: корзина не пустая")


Вывод: ✅ Тест пройден: корзина очищается
