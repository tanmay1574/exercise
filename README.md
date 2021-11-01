Structure of 'restaurants' collection :
{
  "address": {
     "building": "1007",
     "coord": [ -73.856077, 40.848447 ],
     "street": "Morris Park Ave",
     "zipcode": "10462"
  },
  "borough": "Bronx",
  "cuisine": "Bakery",
  "grades": [
     { "date": { "$date": 1393804800000 }, "grade": "A", "score": 2 },
     { "date": { "$date": 1378857600000 }, "grade": "A", "score": 6 },
     { "date": { "$date": 1358985600000 }, "grade": "A", "score": 10 },
     { "date": { "$date": 1322006400000 }, "grade": "A", "score": 9 },
     { "date": { "$date": 1299715200000 }, "grade": "B", "score": 14 }
  ],
  "name": "Morris Park Bake Shop",
  "restaurant_id": "30075445"
}
Write a MongoDB query to display all the documents in the collection restaurants
db.restaurants.find();
Write a MongoDB query to display the fields restaurant_id, name, borough and cuisine for all the documents in the collection restaurant
Db.restaurants.find({},{“restaurant_id“:1,”name”:1,”borough”:1,”cuisine”:1});
 Write a MongoDB query to display the fields restaurant_id, name, borough and cuisine, but exclude the field _id for all the documents in the collection restaurant
Db.restaurants.find({},{“restaurant_id“:1,”name”:1,”borough”:1,”cuisine”:1,”_id”:0});
 Write a MongoDB query to display all the restaurant which is in the borough Bronx
Db.restaurants.find({“borough”:”Bronx”});
Write a MongoDB query to display the first 5 restaurant which is in the borough Bronx
Db.restaurants.find({“borough”:”Bronx”}).limit(5);
.Write a MongoDB query to display the next 5 restaurants after skipping first 5 which are in the borough Bronx.
Db.restaurants.find({“borough”:”Bronx”}).skip(5).limit(5);
Write a MongoDB query to find the restaurants that achieved a score, more than 80 but less than 100.
Db.restaurants.find({grades : { $elemMatch:{"score":{$gt : 80 , $lt :100}}}});
Write a MongoDB query to find the restaurants which locate in latitude value less than -95.754168.
Db.restaurants.find({"address.coord" : {$lt : -95.754168}});
Write a MongoDB query to find the restaurants which do not prepare any cuisine of 'American ' and achieved a grade point 'A' not belongs to the borough Brooklyn.
The document must be displayed according to the cuisine in descending order.
Db.restaurants.find( {
                             "cuisine" : {$ne : "American "},
                             "grades.grade" :"A",
                             "borough": {$ne : "Brooklyn"}
                       } 
                    ).sort({"cuisine":-1});
MongoDB Exercise - Find the restaurant Id, name, borough and cuisine for those restaurants which contain Wil as first three letters for its name
Db.restaurants.find(
{name: /^Wil/},
{
"restaurant_id" : 1,
"name":1,"borough":1,
"cuisine" :1
}
);
MongoDB Exercise - Find the restaurant Id, name, borough and cuisine for those restaurants which contain ces as last three letters for its name
db.restaurants.find(
{name: /ces$/},
{
"restaurant_id" : 1,
"name":1,"borough":1,
"cuisine" :1
}
);
MongoDB Exercise - Find the restaurant Id, name, borough and cuisine for those restaurants which are not belonging to the borough Staten Island or Queens or Bronxor Brooklyn
db.restaurants.find(
{"borough" :{$nin :["Staten Island","Queens","Bronx","Brooklyn"]}},
{
"restaurant_id" : 1,
"name":1,"borough":1,
"cuisine" :1
}
);
