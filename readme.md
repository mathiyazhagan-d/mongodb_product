## 1) Find all the information about each products
db.products.find({}).toArray();

## // 2) Find the product price which are between 400 to 800
db.products.find({product_price:{$lt:800,$gt:400}}).toArray();

## // 3) Find the product price which are not between 400 to 600
db.products.find({product_price:{$not:{$lt:800,$gt:400}}}).toArray();

## // 4) List the four product which are grater than 500 in price
db.products.find({product_price:{$gte:500}}).limit(4).toArray();

## // 5)Find the product name and product material of each products
db.products.find({},{_id:1,product_name:1,product_material:1}).toArray();

## // Find the product with a row id of 10
db.products.find({id: "10"}).toArray();

## // Find only the product name and product material
db.products.find({},{_id:0,product_name:1,product_material:1}).toArray();

## // Find all products which contain the value of soft in product material
db.products.find({product_material: "Soft"}).toArray();

## Find products which contain product color indigo  and product price 492.00
db.products.find({ $or:[{product_price: 492.00},{product_color: "indigo"}]}).toArray()

## Delete the products which product price value are same
db.products.aggregate([{ $group: { _id: "$product_price", count: { $count: {} } } },{ $match: { count: { $gt: 1 } } }]);
db.products.deleteMany({ product_price: { $in: [36, 47] } }); 