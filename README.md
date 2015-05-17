# jschema

sample json으로부터 스키마를 자동으로 읽어와서 빌드<br>
구조에 대한 validation만 수행하기 때문에 별도의 json은 만들지 않아도 됨

__person.json___
```json
{
  "name" : "pjc",
  "location" : "korea",
  "iq" : 10,
  
  "skills" : ["c++", "ruby"],
  
  "items" : [
    {
      "name" : "macbook",
      "price" : 10
    },
    {
      "name" : "mouse",
      "price" : 1
    }
  ]
}
```
```ruby
p = Person.load data

# Simple Fields
puts p.name, p.location, p.iq

# Array type
p.skills.each do |skill|
  puts skill
end

# Object type
p.items.each do |item|
  puts item.name, item.price
end
```

왜
----
* 사용되는 json은 static한데 파서/제너레이터는 generic함
  * validation의 문제
  * 사용의 편의성<br>
      ```
      person["name"] -> person.name 
      ```
* JSON.parse의 결과는 Hash지만 Schema.load의 반환값은 빌드된 클래스 오브젝트의 인스턴스임
