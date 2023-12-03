# This is a sample Python script.

# Press Shift+F10 to execute it or replace it with your code.
# Press Double Shift to search everywhere for classes, files, tool windows, actions, and settings.

class driver():
    """Водитель"""
    def __init__(self, name, ID_dr, salary, ID_carpark):
        self.name = name
        self.ID_dr = ID_dr
        self.salary = salary
        self.ID_carpark = ID_carpark


class car_park():
    """Автопарк"""
    def __init__(self, ID_carpark, name_of_car_park):
        self.ID_carpark = ID_carpark
        self.name_of_car_park = name_of_car_park


class dr_car_park():
    """Для связи многие ко многим"""
    def __init__(self, ID_dr, ID_carpark):
        self.ID_dr = ID_dr
        self.ID_carpark = ID_carpark

drivers = [
    driver("Арсений", 1, 30000, 1),
    driver("Андрей", 2, 33000, 2),
    driver("Вася", 3, 32000, 1),
    driver("Дмитрий", 4, 34000, 3),
    driver("Федор", 5, 36000, 4),
]

carparks = [
    car_park(1, "Яндекс такси"),
    car_park(2, "отдел Delivery"),
    car_park(3, "отдел VK"),
    car_park(4, "Google taxi")
]

dr_carparks = [
    dr_car_park(1, 2),
    dr_car_park(2, 4),
    dr_car_park(3, 1),
    dr_car_park(4, 3)
]

def LinearSearch(lys, element):
    for i in range (len(lys)):
        if lys[i] == element:
            return i
    return -1

def Search(dr_carps, element):
    for i in range (len(dr_carps)):
        if LinearSearch(dr_carps, element):
            return

"""Задание 1"""
print("Задание 1")
for i in range(len(carparks)):
    if ("отдел" in carparks[i].name_of_car_park):
        for j in range(len(drivers)):
            if (drivers[j].ID_carpark == carparks[i].ID_carpark):
                print(drivers[j].name)

"""Задание 2"""
print("Задание 2")
for i in range(len(carparks)):
    count = 0
    emp = 0
    for j in range(len(drivers)):
        if (drivers[j].ID_carpark == carparks[i].ID_carpark):
            emp+=1
            count += drivers[j].salary
    print(carparks[i].name_of_car_park, " ", count/emp)

"""Задание 3"""
name = []
print("Задание 3")
for i in range(len(drivers)):
    if ("А" in drivers[i].name):
        for j in range(len(carparks)):
            if (drivers[i].ID_carpark == carparks[j].ID_carpark):
                name.append(carparks[j].name_of_car_park)
                for y in range(len(dr_carparks)):
                    if (dr_carparks[y].ID_dr == drivers[i].ID_dr):
                        for g in range(len(carparks)):
                            if (dr_carparks[y].ID_carpark == carparks[g].ID_carpark): name.append(carparks[g].name_of_car_park)

        print(drivers[i].name, " работает в отделе(ах) ", name)
    name.clear()




# See PyCharm help at https://www.jetbrains.com/help/pycharm/
