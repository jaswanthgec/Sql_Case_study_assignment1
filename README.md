# Sql_Case_study_assignment1
SQL Case Study required Data Base for Sales :
//For creating product table
CREATE TABLE product (
  product_id INT PRIMARY KEY,
  product_name VARCHAR(100),
  description VARCHAR(200),
  price DECIMAL(10, 2),
  category VARCHAR(50)
);

//For creating region table
CREATE TABLE region (
  region_id INT PRIMARY KEY,
  region_name VARCHAR(100)
);

//For creating time period table
CREATE TABLE time_period (
  timeperiod_id INT PRIMARY KEY,
  timeperiod_name VARCHAR(100)
);

//For creating customer table
CREATE TABLE customer (
  customer_id INT PRIMARY KEY,
  customer_name VARCHAR(100),
  address VARCHAR(200),
  age INT,
  loyalty_status VARCHAR(50)
);

//For creating purchase table
CREATE TABLE purchase (
  purchase_id INT PRIMARY KEY,
  customer_id INT,
  timeperiod_id INT,
  total_purchase_amount DECIMAL(10, 2),
  FOREIGN KEY (customer_id) REFERENCES customer (customer_id),
  FOREIGN KEY (timeperiod_id) REFERENCES time_period (timeperiod_id)
);

//For creating purchase product relationship
CREATE TABLE purchase_product (
  purchase_id INT,
  product_id INT,
  PRIMARY KEY (purchase_id, product_id),
  FOREIGN KEY (purchase_id) REFERENCES purchase (purchase_id),
  FOREIGN KEY (product_id) REFERENCES product (product_id)
);

//For creating product region relationship
CREATE TABLE product_region (
  product_id INT,
  region_id INT,
  PRIMARY KEY (product_id, region_id),
  FOREIGN KEY (product_id) REFERENCES product (product_id),
  FOREIGN KEY (region_id) REFERENCES region (region_id)
);

//For creating inventory table
CREATE TABLE inventory (
  inventory_id INT PRIMARY KEY,
  product_id INT,
  stock_level INT,
  FOREIGN KEY (product_id) REFERENCES product (product_id)
);
