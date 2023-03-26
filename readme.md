# day 37 task Database - MongoDB

### you can check the code by using some of the online MongoDB compiler
## screenshot
<img src="./image/img (1).png" alt="ans-1">

## 1) Find all the information about each products
```js
db.products.find({}).toArray();
```
<img src="./image/img (2).png" alt="ans-1">

## 2) Find the product price which are between 400 to 800
```
db.products.find({product_price:{$lt:800,$gt:400}}).toArray();
```
<img src="./image/img (3).png" alt="ans-1">

## 3) Find the product price which are not between 400 to 600
db.products.find({product_price:{$not:{$lt:800,$gt:400}}}).toArray();
<img src="./image/img (4).png" alt="ans-1">

## 4) List the four product which are grater than 500 in price
db.products.find({product_price:{$gte:500}}).limit(4).toArray();
<img src="./image/img (5).png" alt="ans-1">

## 5)Find the product name and product material of each products
db.products.find({},{_id:1,product_name:1,product_material:1}).toArray();
<img src="./image/img (6).png" alt="ans-1">

## 6) Find the product with a row id of 10
db.products.find({id: "10"}).toArray();
<img src="./image/img (7).png" alt="ans-1">

## 7) Find only the product name and product material
db.products.find({},{_id:0,product_name:1,product_material:1}).toArray();
<img src="./image/img (8).png" alt="ans-1">

## 8) Find all products which contain the value of soft in product material
db.products.find({product_material: "Soft"}).toArray();
<img src="./image/img (9).png" alt="ans-1">

## 9) Find products which contain product color indigo  and product price 492.00
db.products.find({ $or:[{product_price: 492.00},{product_color: "indigo"}]}).toArray()
<img src="./image/img (10).png" alt="ans-1">

## 10) Delete the products which product price value are same
db.products.aggregate([{ $group: { _id: "$product_price", count: { $count: {} } } },{ $match: { count: { $gt: 1 } } }]);
db.products.deleteMany({ product_price: { $in: [36, 47] } }); 
<img src="./image/img (11).png" alt="ans-1">