# Coffee_Machine

materials = ['water', 'milk', 'coffee beans', 'disposable cups', 'money']
balance = [400, 540, 120, 9, 550]
espresso = [250, 0, 16, 1, 4]
latte = [350, 75, 20, 1, 7]
cappuccino = [200, 100, 12, 1, 6]

#показывает оставшееся количество материалов
def action_remaining():
  print('The coffee machine has:')
  for b in range(4):
    print(balance[b], 'of', materials[b])
  print('$' + str(balance[b]), 'of money')

#высчитывает затраты и прибыль на одну чашку выбранного кофе
def calculate(coffee_name):
  global balance
  #если ресурсов недостаточно, то не может осуществить приготовление кофе
  for c in range(4):
    if balance [c] < coffee_name[c]:
      print('Sorry, not enough', materials[c] + '!') 
      return
  print('I have enough resources, making your coffee!')
  for d in range(4):
    balance[d] -= coffee_name[d]
  balance[4] += coffee_name[4]

#выбор кофе\возвращение в меню
def action_buy():
  print('What do you want to buy? 1 - espresso, 2 - latte, 3 - cappuccino, back - to main menu: ')
  coffee_type = input()
  if coffee_type == '1':
    calculate(espresso)
  elif coffee_type == '2':
    calculate(latte)
  elif coffee_type == '3':
    calculate(cappuccino)

#пополняет запасы
def action_fill():
  global balance
  for f in range(4):
    print('Write how many ml of', materials[f], 'do you want to add:')
    balance[f] += int(input())

#действие - забрать деньги из кофемашины
def action_take():
  global balance
  print('I gave you $' + str(balance[4]), materials[4])
  balance[4] = 0

#цикл выбора действия до ввода слова "exit"
while True:
  print('Write action (buy, fill, take, remaining, exit):')
  action = input()
  if action == 'buy':
    action_buy()
  elif action == 'fill':
    action_fill()
  elif action == 'take':
    action_take()
  elif action == 'remaining':
    action_remaining()
  elif action == 'exit':
    break
