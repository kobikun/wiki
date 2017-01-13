# MongoDB

## Documents
* Document Oriented
* RDMS에서의 record와 비슷한 개념
* 한개이상의 key-value 쌍으로 이뤄짐

```
{
    "_id": ObjectId("123fabcd123123123"),
    "username": "kobikun",
    "name": { first: "kobi", last: "Kun" }
}
```

* key : _id, username, name
* value : 각 키의 오른쪽 값

## Collection
* Document 그룹
* Collection > Document
* RDMS처럼 schema가 존재하지 않음


## Databaes
* Collection들의 물리적인 컨테이너


## 비교연산자

|operator	| 설명 |
|---------|-----|
| $eq	  | (equals) 주어진 값과 일치하는 값 | 
| $gt	 | (greater than) 주어진 값보다 큰 값 |
| $gte	 |(greather than or equals) 주어진 값보다 크거나 같은 값
| $lt	| (less than) 주어진 값보다 작은 값
| $lte |	(less than or equals) 주어진 값보다 작거나 같은 값
| $ne	| (not equal) 주어진 값과 일치하지 않는 값
| $in	| 주어진 배열 안에 속하는 값
| $nin |	주어빈 배열 안에 속하지 않는 값

## 논리 연산자
| operator	| 설명 |
|------------|-----|
|$or	|주어진 조건중 하나라도 true 일 때 true
|$and	|주어진 모든 조건이 true 일 때 true
|$not	|주어진 조건이 false 일 때 true
|$nor	|주어진 모든 조건이 false 일때 true

## elemMatch
* 엔트리 내부 매칭

```
collection.find({'name': {$elemMatch : { 'first':'kobi' }}})
``` 

* python
```
#collection.find({'name': {'$elemMatch' : { 'first':'kobi' }}})
```

## Links

* [[MongoDB] 강좌](https://velopert.com/category/dev-log/tech-log/mongodb)

* [MongoDB 스키마 디자인을 위한 6가지 규칙 요약](http://www.haruair.com/blog/3055)

* [pymongo tutorial](http://dev.youngkyu.kr/23)
