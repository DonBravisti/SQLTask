Создание базы данных
CREATE SCHEMA IF NOT EXISTS `online_shop` DEFAULT CHARACTER SET utf8

Создание таблиц

orders
CREATE TABLE IF NOT EXISTS `online_shop`.`orders` (
  `id` INT NOT NULL AUTO_INCREMENT,
  `customer_name` VARCHAR(45) NULL,
  `delivery_address` VARCHAR(100) NULL,
  `id_product` INT NULL,
  PRIMARY KEY (`id`))
ENGINE = InnoDB

products
CREATE TABLE IF NOT EXISTS `online_shop`.`products` (
  `id` INT NOT NULL AUTO_INCREMENT,
  `name` VARCHAR(45) NULL,
  `price` INT NULL,
  PRIMARY KEY (`id`))
ENGINE = InnoDB

carriers
CREATE TABLE IF NOT EXISTS `online_shop`.`carriers` (
  `id` INT NOT NULL AUTO_INCREMENT,
  `name` VARCHAR(45) NULL,
  `car_brand_and_number` VARCHAR(100) NULL,
  `id_order` INT NULL,
  PRIMARY KEY (`id`))
ENGINE = InnoDB

Заполнение таблиц

orders
INSERT INTO `online_shop`.`orders` (`id`, `customer_name`, `delivery_address`, `id_product`) VALUES (1, 'Олегов Олег Олегович', 'Куйбышева', 1);
INSERT INTO `online_shop`.`orders` (`id`, `customer_name`, `delivery_address`, `id_product`) VALUES (2, 'Петров Петр Петрович', 'Ватутина', 3);
INSERT INTO `online_shop`.`orders` (`id`, `customer_name`, `delivery_address`, `id_product`) VALUES (3, 'Диванов Алексей Петрович', 'Магкаева', 2);
INSERT INTO `online_shop`.`orders` (`id`, `customer_name`, `delivery_address`, `id_product`) VALUES (4, 'Кононов Валерий Алексеевич', 'Хадарцева', 4);
INSERT INTO `online_shop`.`orders` (`id`, `customer_name`, `delivery_address`, `id_product`) VALUES (5, 'Иванова Ирина Петровна', 'Минина', 4);

products
INSERT INTO `online_shop`.`products` (`id`, `name`, `price`) VALUES (1, 'Книга', 100);
INSERT INTO `online_shop`.`products` (`id`, `name`, `price`) VALUES (2, 'Тетрадь', 30);
INSERT INTO `online_shop`.`products` (`id`, `name`, `price`) VALUES (3, 'Ручка', 1000);
INSERT INTO `online_shop`.`products` (`id`, `name`, `price`) VALUES (4, 'Карандаш', 15);
INSERT INTO `online_shop`.`products` (`id`, `name`, `price`) VALUES (5, 'Закладки', 50);

carriers
INSERT INTO `online_shop`.`carriers` (`id`, `name`, `car_brand_and_number`, `id_order`) VALUES (1, 'Дмитриев Дмитрий Олегович', 'Lada 2101 н756нр', 1);
INSERT INTO `online_shop`.`carriers` (`id`, `name`, `car_brand_and_number`, `id_order`) VALUES (2, 'Мусаев Шахзод Шерали-Угли', 'BMW у007зб', 2);
INSERT INTO `online_shop`.`carriers` (`id`, `name`, `car_brand_and_number`, `id_order`) VALUES (3, 'Басурин Иван Иванович', 'Lada н654нн', 4);
