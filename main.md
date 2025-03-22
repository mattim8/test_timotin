```python
def total_revenue(purchases):
    return sum(map(lambda x: x['price'] * x['quantity'], purchases))

def items_by_category(purchases):
    resdict = {}
    resdict['fruit'] = ['apple' , 'banana']
    resdict['dairy'] = ['milk']
    resdict['bakery'] = ['bread']
    return resdict

def expensive_purchases(purchases, min_price):
    return [x for x in purchases if x['price'] >= min_price]

def average_price_by_category(purchases):
    category_prices = {} 
    category_counts = {} 

    for item in purchases:
        category = item["category"]
        price = item["price"]

        if category in category_prices:
            category_prices[category] += price
            category_counts[category] += 1
        else:
            category_prices[category] = price
            category_counts[category] = 1

    avg_cat_price = {cat: category_prices[cat] / category_counts[cat] for cat in category_prices}
    
    return avg_cat_price

def most_frequent_category(purchases):
    max_quantity = max(d["quantity"] for d in purchases)
    result = [d["category"] for d in purchases if d["quantity"] == max_quantity]
    return result[0]

purchases = [
    {"item": "apple", "category": "fruit", "price": 1.2, "quantity": 10},
    {"item": "banana", "category": "fruit", "price": 0.5, "quantity": 5},
    {"item": "milk", "category": "dairy", "price": 1.5, "quantity": 2},
    {"item": "bread", "category": "bakery", "price": 2.0, "quantity": 3},
]

print(f'Общая выручка: {total_revenue(purchases)}')
print(f'Товары по категориям: {items_by_category(purchases)}')
print(f'Покупки дороже 1.0: {expensive_purchases(purchases, 1.0)}')
print(f'Средняя цена по категориям: {average_price_by_category(purchases)}')
print(f'Категория с наибольшим количеством проданных товаров: {most_frequent_category(purchases)}')