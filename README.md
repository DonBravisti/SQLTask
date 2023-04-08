# Создание таблиц

CREATE TABLE `products` (  
   `id` int NOT NULL AUTO_INCREMENT,  
   `name` varchar(45) NOT NULL,  
   `price` decimal(5,2) NOT NULL,  
   PRIMARY KEY (`id`)  
 ) ENGINE=InnoDB AUTO_INCREMENT=6 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci  
 
CREATE TABLE `orders` (  
   `id` int NOT NULL AUTO_INCREMENT,  
   `FIO` varchar(45) NOT NULL,  
   `address` varchar(45) NOT NULL,  
   `carrier_id` int NOT NULL,  
   PRIMARY KEY (`id`),  
   KEY `orders_carriers_idx` (`carrier_id`),  
   CONSTRAINT `orders_carriers` FOREIGN KEY (`carrier_id`) REFERENCES `carriers` (`id`)  
 ) ENGINE=InnoDB AUTO_INCREMENT=11 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci  
 
 CREATE TABLE `carriers` (  
   `id` int NOT NULL AUTO_INCREMENT,  
   `name` varchar(45) NOT NULL,  
   `phone_num` varchar(20) NOT NULL,  
   `car_num` varchar(20) NOT NULL,  
   PRIMARY KEY (`id`)  
 ) ENGINE=InnoDB AUTO_INCREMENT=4 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci  

CREATE TABLE `order_items` (  
   `id` int NOT NULL AUTO_INCREMENT,  
   `product_id` int NOT NULL,  
   `order_id` int NOT NULL,  
   `amount` int NOT NULL,  
   PRIMARY KEY (`id`),  
   KEY `products_order_items_idx` (`product_id`),  
   KEY `orders_order_items_idx` (`order_id`),  
   CONSTRAINT `orders_order_items` FOREIGN KEY (`order_id`) REFERENCES `orders` (`id`),  
   CONSTRAINT `products_order_items` FOREIGN KEY (`product_id`) REFERENCES `products` (`id`)  
 ) ENGINE=InnoDB AUTO_INCREMENT=6 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci

# 1. Получить всю информацию по ID заказа: продукты, количество, кто и куда доставляет, сумма заказа

SELECT o.FIO, o.address, p.name, oi.amount, p.price*oi.amount as Sum, c.name 
from shop.orders as o  

join shop.carriers as c  
on o.carrier_id = c.id  

join shop.order_items as oi  
on o.id = oi.order_id  

join shop.products as p  
on p.id = oi.product_id  

where o.id = 3  


# 2. Создание заказа
INSERT INTO shop.orders (FIO, address, carrier_id) VALUES ('Олег', 'Ватутина', '2');
INSERT INTO shop.order_items (product_id, order_id, amount) VALUES ('2', '3', '3');
INSERT INTO shop.order_items (product_id, order_id, amount) VALUES ('4', '4', '4');


# 3. Вывести все заказы для заданного ID курьера
SELECT x.FIO, x.address, p.name, oi.amount, p.price*oi.amount as Sum, c.name
FROM shop.orders as x  

join shop.carriers as c  
on x.carrier_id = c.id  

join shop.order_items as oi  
on x.id = oi.order_id  

join shop.products as p  
on p.id = oi.product_id  

where x.carrier_id = 1  


# 4. Увеличить количество продукта по имени продукта в конкретном заказе по ID
UPDATE shop.order_items  
SET amount = '15'  
WHERE (id = '2');  
