print("Создание исключений.Некорректность")

class IncorrectVinNumber(Exception):

    def __init__(self, message):
        self.message = message
        print(self.message)


class IncorrectCarNumbers(Exception):

    def __init__(self, message):
        self.message = message
        print(self.message)



class Car:
    def __init__(self, model, vin, numbers):

        self.model = model
        if self.__is_valid_vin(vin) and self.__is_valid_numbers(numbers):
            self.__vin = vin
            self.__numbers = numbers
            print(f'{self.model} успешно создан')
        else:
            pass



    def __is_valid_vin(self, vin_number):# ой не так проверяют VIN, но работаем по ТЗ
        try:
            if   not isinstance (vin_number, int): # передано не целое число.
                raise IncorrectVinNumber('Некорректный тип vin номерa')
            if not ( 1000000 <= vin_number <= 9999999):  # Хоть передано и целое число, но переданное число находится не в диапазоне от 1000000 до 9999999 включительно.
                raise IncorrectVinNumber('Неверный диапазон для vin номера')
        except IncorrectVinNumber:
            pass
        else:
            return True # Чудо! VIN правильный#


    def __is_valid_numbers(self, numbers):#  Можно еще приколотить контроль номера по маске, на регулярках, подумать на будущем
        try:
            if not isinstance(numbers, str):
                raise IncorrectCarNumbers('Некорректный тип данных для номеров') # Номер не строка
            if len(numbers) != 6:
                raise IncorrectCarNumbers('Неверная длина номера')
        except IncorrectCarNumbers:
            pass
        else:
            return True # Чудо! Номер правильный.


car1 = Car('Model1', 100000000, 'f123dj')
car2 = Car('Model2', 300, 'т001тр')
car3 = Car('Model3', 2020202.99, 'нет номера')
car4 = Car('Model4', 5555555, 'c537УT')
car5 = Car('Model5', 1000000, 'f123dj')
